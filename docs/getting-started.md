# Getting Started

## Installing

Signal is a Fabric mod, so you'll need:

- Minecraft 1.21.11
- Fabric Loader 0.19.3 or newer
- Fabric API 0.141.4+1.21.11 or newer

Drop the mod jar in your `mods` folder alongside Fabric API and launch normally. There's nothing to install on the server side, Signal doesn't require a server-side plugin or mod.

## Opening the menu

Signal adds a keybind to open the main screen (check your controls menu if you're not sure what it's bound to). That's where everything lives: your group, your squad, chat, waypoints, settings, all of it.

The menu is split into three categories:

- **Group** - your group's roster, board, group chat, and group config.
- **Squad** - squad overview (leaders/subleaders only), your squad's roster, squad chat, and squad config.
- **Other** - developer tools, the Player Manager (mutes/bans), your personal settings, the audit log, and info.

Which tabs show up under each category depends on your role. A regular Member won't see Group Config or Squad Overview, for example, because those need real permissions.

## Joining a group

Groups are created and joined by name, with an optional password depending on how the group's join mode is set (open, password-protected, or invite/apply-only). Ask whoever runs your group for the group name and, if needed, the password.

Once you're in, you'll land in the group's default squad automatically. Someone with squad-admin permissions (Leader, Sub Leader, or Captain) can move you into a different squad later.

## First things to check

- Open **Other > Settings** and make sure the overlays you want are turned on (Squad HUD, squad glow, role icons, the comm wheel, etc). Everything in there is off/on per player, so what you see doesn't affect what anyone else sees.
- If you're a squad leader, position heartbeats start sending automatically the moment you're in a squad, that's what lets your squad see you on the HUD even when you're way outside their render distance.
- War tracking works automatically as long as your server posts the expected `[War] ...` chat lines. Nothing to configure there.
