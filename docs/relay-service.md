# Relay Service

Everything real-time in Signal (chat, positions, waypoints, war events) goes through a small relay server instead of peer-to-peer or through the Minecraft server itself. This page is for anyone who wants to self-host it or just understand how it works under the hood.

## Stack

The relay is a plain Node.js WebSocket server with a Postgres database behind it. No frameworks beyond what's needed for the socket handling and DB access, it's intentionally simple.

## What's persisted vs what's not

Postgres holds anything that needs to survive a reconnect or a server restart:

- Groups, squads, and squad links
- Group membership, roles, and squad assignment
- Mutes and bans
- Persistent group/squad waypoints
- Join requests and pending squad link requests

Everything else lives purely in memory on the relay and is allowed to just disappear:

- Chat messages (no chat history is stored anywhere, client or server)
- Pings and death markers
- Live war state (recent attacks get cached for about 20 minutes so "defended" messages can be matched against them, then they age out)
- Squad leader position heartbeats

If you're expecting chat scrollback to survive a relog, it won't right now, that would need a dedicated messages table, which doesn't exist yet.

## Permissions on the server side

The relay mirrors the same permission model the client uses (see [Roles & Permissions](roles-and-permissions.md)), it doesn't trust the client to self-report what it's allowed to do. Every action that needs a permission gets checked server-side before anything happens, using the same permission names (group config, member manage full, member mute, squad admin).

## Scoped broadcasts

A lot of what the relay does is deciding who should receive a given message. Group-wide stuff (like group chat) goes to everyone connected under that group. Squad-scoped stuff (squad chat, pings, waypoints) goes only to sockets in the sender's squad plus any linked squad, computed fresh each time rather than assuming a cached list is still accurate.

## Deploying

The relay is deployed as a normal Node process, no special infrastructure required beyond a Postgres instance it can reach. Point your client's relay URL setting at wherever you're running it (`wss://...` for a proper TLS setup).

If you're running your own instance, keep in mind the client and relay need to agree on the WebSocket message shapes described throughout these docs, if you're modifying one side you'll need to update the other to match.
