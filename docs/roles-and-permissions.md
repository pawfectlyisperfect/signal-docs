# Roles & Permissions

Signal uses six roles, plus one separate concept sitting above all of them: the group Owner.

## The Owner

Every group has exactly one Owner. This isn't a role in the list below, it's a separate flag on the group itself, kind of like being the owner of a Discord server versus just having the top role in it. The Owner is the only one who can hand out the Leader role. Nobody, including a Leader, can promote someone to Leader on their own.

## The six roles

From highest to lowest:

| Role | Icon | What they can do |
|---|---|---|
| Leader | crown | Everything: group config, full member management, mutes, squad admin. |
| Sub Leader | star | Same as Leader, minus being able to assign Leader (that's Owner-only). |
| Captain | swords | Full member management, mutes, and squad admin, but no group config. |
| Officer | shield | Can mute members. Nothing else administrative. |
| Specialist | sparkle | No admin permissions. Cosmetic rank only. |
| Member | user | Base role, no admin permissions. |

## Why it's not just a rank ladder

Older versions of the permission system used a simple "rank 3 and above can do X" style check. That fell apart once Captain showed up, because Captain needed moderation and squad-admin powers but explicitly *not* group config, and that doesn't fit on a single line. So permissions are now their own thing, checked directly, not inferred from where a role sits in the list.

The actual permissions are:

- **Group Config** - rename the group, toggle group chat notifications, relabel roles, turn squads-related group settings on or off.
- **Member Manage Full** - promote, demote, kick, and ban members.
- **Member Mute** - mute and unmute members in chat.
- **Squad Admin** - create, rename, recolor, merge, and disband squads, assign members to squads, set squad leaders, manage squad links.
- **Assign Leader** - Owner-only, not tied to any role at all.

Only Leader and Sub Leader hold Group Config. Leader, Sub Leader, and Captain hold Member Manage Full and Squad Admin. Leader, Sub Leader, Captain, and Officer hold Member Mute. Specialist and Member hold nothing extra.

## Assigning roles

Whoever is assigning a role can only hand out roles at or below what they're allowed to touch. A Captain, for instance, can set someone to Officer, Specialist, or Member, but can't create another Captain or anything above it. Only the Owner can make someone a Leader.

## Role labels

Group Config lets a Leader or Sub Leader rename how roles display for their specific group. The underlying role (and its permissions) don't change, it's purely a display label, so you can call your Captain role "Squad Lead" or whatever fits your group without touching how permissions actually work.
