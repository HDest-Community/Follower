Original mod by Ace: https://gitlab.com/accensi/hd-addons/follower

This is a fixed and improved version by mickromash.

### Changes
---
- Mod updated to Hideous Destructor v4.11.3d
- Followers now targeting small monsters (like Lost Soul or Babuin) much better
- Followers reloading their weapons and healing between battles
- Followers now trying to follow player through portals
- Followers now tell player if they are lagging behind ("MissedPlayer" For audio) (FollowersName.."_FOLLOW_MISS_"..Index for message in language file)
- Followers now actually picking up armour (was broken in 4.8.2a fix)
- Fixed liberator mags
- Fixed followers aim
- Fixed followers not healing themselfs on 90% health or 0.1 boddy damage
- Localized all text that I could find





---
### ORIGINAL REAMDE
---



### Important
---
- This mod requires [AceCoreLib](https://gitlab.com/accensi/hd-addons/acecorelib).
- The mod needs at least GZDoom 4.11.0 to run. LZDoom does not currently have a compiled version that supports it. However, the mod will work with the next stable version of LZDoom. It will also work if you compile LZDoom yourself.

**NOTE: *Freylis's sprites are not for public use. Please do not use them anywhere. Thank you.***

### Quickstart
---
- Bind the command menu key in the mod's options menu.
- The same key that opens the menu also closes it.

### Weapons
---
The followers can use the following weapons:
- SMG
- Hunter
- ZM66
- Rocket Launcher
- Liberator
- Brontornis
- Boss

### Mechanics
---
For the most part the mechanics are fairly simple and straightforward. Documented here are more niche things that are not obvious at all and can only be found either by trial or error or by looking at the source code.

##### Multiselecting
---
- `Shift` makes selection additive. Acts as a modifier and works either with the number keys or with Quick Access. Works with groups as well;
- `Ctrl + A` select all;
- `Ctrl + D` deselects all;
- `Ctrl + I` inverts the selection;
- `Ctrl + Alt` modifies the selection to only affect the current page;
- `Ctrl + Alt + 0-9` assigns the selection to a squad. 0 means no squad;
- `Ctrl + 1-9` selects the squad;
- `Enter` applies the selection.

##### Inventory management
---
Most of the navigation is on-screen, but there are a few things that aren't obvious due to lack of space to put said info.
- When selecting amount for transfer, Shift + Left/Right arrow keys increases the amount by 20 instead of 2.
- You can give followers weapons through the inventory management menu. This will enable them to use the weapons, assuming it's a valid weapon to begin with. Keep in mind that the weapons given to them will not be exactly the same as the ones they'll actually use. That is, giving your followers a factory chamber boss will automatically turn it into a custom chamber. This will not change. Too much trouble to account for all of the variations. You also can't take back weapons. Once you give them, they're gone forever.
- You can use Ctrl + 0-9 to reload the weapon at that index. Only works for singular selections.

To see all of the available input field commands, type "HDF_InputCommands" in the console. To terminate input without applying, use Ctrl + C.

##### Loadouts
---
The follower options now support a string input like with the player loadouts, although it's recommended to edit those through the console because menu input is janky. The standard loadout codes apply. Only valid items can be given. If your follower doesn't have any weapons that utilize a battery, nothing will happen and no battery will be given to them. Numbers can be used. For armor, you can use a floating point value, e.g `0.5`. Items are comma-separated, just like player loadouts. Example of a valid loadout code: `smg, 930 5, stm 3, awg 0.5`

##### Revival
---
- Blues: the cost starts at 2 sips and scales to a full potion depending on how damaged the follower's body is. Fire damages it badly so that's usually the only time you'll need to use a full potion.
- Blood: get a medikit because you'll need it. Don't attempt a blood revival if you're not at max health. To revive the follower this way, you must be crouched for the entire duration and looking at them. If red particles appear, you're doing it right.

##### Incapacitation
---
- If your follower is incapped, you can help them get up faster by crouching and looking at them. Just imagine you're helping them get up. Of course, injecting them with a stim would also help with that.
- If it's you who got incapped, the follower will rush to your aid when you manually give them the order (assuming there are no hostiles around), and help you get up faster, so it's a two-way street. If you are bleeding and you have given them a medikit, they will use it, but only if you are still in incap and unable to get up. If you are able to get up, the AI will assume you're capable of taking care of yourself from then on.

##### Orders
---
- Orders are mostly straightforward except for some details, such as "go there and cover me", which will make the follower stop whatever they're doing and run to their destination. Be sure to cover them if you can because they won't engage any enemies on the way.

##### Recruiting
---
You can now recruit friendly/converted marines as followers. Does not work if the marines were resurrected. If it's smoking, forget about it. You can also recruit hostile marines if they have been incapped. For both of them you need to look at the marine (be within 2m of it) and press the follower menu key.

Marines basically function the exact same way as regular followers, and you can command them as such. A few exceptions exist:
1. They are expendable, so you won't get any notification for leaving any behind when moving between maps. You can, however, carry them between maps to create an army. Of course, at some point it is going to become hell to manage.
2. All marines are stored as a single inventory item in first-in-last-out order.

##### Miscellaneous
---
- If you go prone, you can pick up followers below you from farther away. Imagine they're grabbing onto your hand and you pull them up.
- Followers will move out of the way if you're moving towards them while holding the Sprint key.
- Holding Shift while giving orders will not close the menu.
- While in input mode, pressing the Up and Down arrow keys moves through the command history.
- Telling followers to stop in front of a linedef (e.g. switch or door) will activate it as if the player did it, allowing for some basic remote control.
- Followers will put out the fires of other nearby followers (within 1m), including yourself. You can do the same for them by being near.
- Followers won't staple you if you are wearing armor. For convenience, the opposite does not apply.

### Modding
---
- New followers can be added by inheriting from HDFollower and overriding the provided virtuals (if desired).
- Do **NOT** add an `hdf_followers` option. This is an internal CVar and its only purpose is to allow players to control the built-in followers. If you don't want an addon follower to show up, don't load the addon.

### Known Issues
---
- Sometimes followers will fail to follow the player or other followers while in specific sectors even if nothing obvious is blocking their way. This primarily happens on older maps that use the REJECT lump for sight checking. I don't know of a possible fix without side effects that I could implement on the mod's side.
