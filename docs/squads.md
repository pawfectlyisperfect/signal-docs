# Squads

Every group is split into squads. This isn't optional, a group always has at least one squad (a default one created automatically), and every member always belongs to exactly one squad at a time.

## Why squads exist

Group-wide chat and pings get noisy fast once you've got more than a handful of people active during a war. Squads let a smaller cluster of players coordinate tightly (chat, waypoints, HUD) without drowning out or being drowned out by the rest of the group.

## Squad Overview

Leaders and Sub Leaders get a Squad Overview tab that lists every squad in the group: name, color, member count, and who the squad leader is (or a warning if nobody's been set as one). From there you can create, rename, recolor, merge, or disband squads, and manage members.

Captains have the same underlying permissions (Squad Admin) but work through each squad's own config panel instead of the Overview tab.

A few rules:

- The default squad can't be disbanded while it's still the default, and no squad can be disbanded while it has members in it.
- Merging a squad moves its members and its existing waypoints into the target squad, nothing gets lost.
- A squad always needs a squad leader once it has members. If you remove the current one, someone needs to be assigned before that gap causes weirdness on the HUD/tracking side.

## Squad color

Every squad has a color. That color is what shows up everywhere squad identity matters:

- Squad glow (the outline around teammates)
- Above-head role icons
- Waypoint and ping tint
- Squad HUD

Recoloring a squad updates all of that live, you don't need to relog.

## Squad Links

By default, a squad only sees its own squad's chat and waypoints. If you want two squads to coordinate closely (like during a joint push), a Squad Admin can create a direct link between them, which is instant and shows up for everyone.

If a squad leader wants to request a link with a squad they don't have admin rights over, they can send a link request instead. That goes to the target squad's leader as a toast notification, and it sticks around (it's saved server-side) even if nobody's online to see it right away. The target leader can accept or deny it whenever.

Once two squads are linked, their members can see each other's squad chat, waypoints, and pings. It's mutual, there's no "linked to them but they can't see us" state.

## Squad Leaders and long-range tracking

Every squad needs a squad leader. What makes that role special on the tech side is position tracking: a squad leader's client sends a lightweight position update every couple seconds while they're a squad leader, and that gets relayed to their (and linked) squad's members. That's what lets the Squad HUD and the squad leader marker show a live position even when the leader is way outside normal render/tracking range.

If a squad leader goes offline or the heartbeat goes stale (goes quiet for about 10 seconds), their marker flips to an "Offline" state instead of freezing in place or vanishing. If they're in a different dimension, it shows "In Another World" instead of trying to project a screen position that wouldn't make sense.
