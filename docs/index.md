# Signal

Signal is a Fabric mod for Minecraft 1.21.11 that adds group and squad coordination on top of a small relay server. It's built for war/faction servers where you need to know where your people are, what's under attack, and who's saying what, without everyone crammed into one chat.

Think of it like a lightweight in-game Discord for your group, plus a live map layer for waypoints and pings, plus a war tracker that watches chat and turns "you're under attack" messages into something you can actually see and react to.

## What it does

- **Groups and squads.** Join a group, get split into squads, and see squad-specific stuff (chat, waypoints, HUD) without it bleeding into everyone else, unless squads are linked.
- **Roles and permissions.** Six roles, from Member up to Leader, each with a real set of permissions instead of one flat "mod or not" toggle.
- **Waypoints.** Pings, death markers, persistent group/squad waypoints, and live war markers, all rendered on your screen in real time.
- **War tracking.** Signal reads your server's war chat messages (attacks, captures, defends) and turns them into waypoints and notifications automatically.
- **Squad HUD.** A small always-on overlay showing your squad's health, position, and status, including squad leaders who are way outside render distance.
- **In-house notifications.** A slim notification system that replaced vanilla toasts and titles for everything: chat pings, alerts, and war events.

## Where to start

Start with [Getting Started](getting-started.md), then read [Squads](squads.md) and [Roles & Permissions](roles-and-permissions.md) to understand how a group is actually structured.

## A note on how this is built

Signal is entirely client-driven on the Minecraft side. It doesn't touch server-side plugins or require anything installed on the Minecraft server itself. All the real-time coordination (chat, positions, waypoints) goes through a small Node.js relay over WebSockets, backed by Postgres for anything that needs to survive a reconnect (group membership, roles, mutes, bans, persistent waypoints). Anything transient, like a ping or a live war marker, just lives in memory and expires on its own.
