# Waypoints

Signal renders several different kinds of waypoints on your screen, all through the same overlay, but they behave pretty differently depending on what they are.

## Kinds of waypoints

**Persistent group/squad waypoints.** Placed manually by a Leader/Sub Leader (group-scoped) or a Squad Admin (squad-scoped). These don't expire and survive relogs, they're stored server-side. Rename them any time from the waypoint itself, and if you merge squads or move someone between squads, the waypoint lists refresh automatically so nobody's stuck looking at stale data.

**Pings.** Placed through the comm wheel (see [Comm Wheel](comm-wheel.md)). These are short-lived call-outs, tinted with the sender's squad color, and they fade out smoothly as they get close to expiring instead of blinking on and off.

**Death markers.** A skull icon that shows up briefly at a squad or linked-squad member's death location. Also tinted with squad color, also short-lived.

**War markers.** These come from war chat parsing (see [War Tracking](war-tracking.md)) and cover attacks, captures, and defends. Attack and capture markers stick around until they're actually resolved, they're not on a timer, because an ongoing threat shouldn't just disappear because a few seconds passed. A "defended" marker, on the other hand, is a brief confirmation that shows for a few seconds and then clears itself.

## Visibility

Which waypoints you see depends on your squad and any squads you're linked to. Group-scoped waypoints are visible to the whole group regardless of squad. Squad-scoped waypoints are visible to your own squad plus anything linked to it.

You can hide categories of waypoints entirely from your personal Settings tab (comm wheel pings, death markers, group waypoints, squad waypoints, independently of each other), without it affecting what anyone else sees.

## On-screen behavior

Waypoints fade out with distance and fully off-screen ones collapse into a smaller edge indicator so they don't clutter your view. Distance is shown under each icon, and for pings specifically, the full label (like "Enemy Spotted") only shows when you're looking roughly at it or close enough to it, otherwise it's just a distance readout to keep things clean.
