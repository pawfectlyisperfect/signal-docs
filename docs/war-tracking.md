# War Tracking

Signal watches your in-game chat for a specific set of war-related messages and turns them into live waypoints and notifications automatically. You don't have to do anything for this to work, it's passive.

## What it's looking for

The parser matches three message formats:

- `[War] <attacker> is attacking <town> at (x, y, z)`
- `[War] <attacker> captured chunk (chunkX, chunkZ) from <town>`
- `[War] Attack at (x, y, z) defeated by <defender>`

If your server's war plugin outputs chat lines in those formats, Signal picks them up on its own.

## What happens for each one

**Attack.** A war waypoint gets placed at the reported location, tinted by threat, and a notification goes out to the group. This waypoint sticks around until it's actually resolved, not on a timer.

**Capture.** Same idea, converted from chunk coordinates to a world position, with a notification that calls out whether it's a fresh capture or a recapture from whoever held it before.

**Defended.** This one's a bit smarter than just "someone said defended so show a message." The relay keeps a short-term cache of recent attacks (who, where, against which town) for about 20 minutes. When a "defended" message comes in, it only counts if it matches a cached attack at the *exact* same coordinates. If there's no matching attack on record, the message is dropped entirely, no notification, no waypoint. This stops random or unrelated "defended" chat lines from generating fake resolution events. When it does match, you get a proper notification (something like "so-and-so defended Apollonia against so-and-so") and the attack waypoint at that spot swaps out for a brief "defended" confirmation marker that clears itself after a few seconds.

## Why the caching matters

Without matching against a real cached attack, a "defended" message is just a coordinate and a name, there's no way to know if it actually corresponds to anything real, or which town/attacker it was even about. Caching attacks by exact location means a defended event can only fire if it's actually resolving something Signal already knows is under attack, which keeps the war feed accurate instead of just trusting every chat line at face value.
