### Important
---
- This mod requires [AceCoreLib](https://gitlab.com/accensi/hd-addons/acecorelib).
- The mod needs at least GZDoom 4.5.0 (or a dev build) to run. LZDoom does not currently have a compiled version that supports it. However, the mod will work with the next stable version of LZDoom. It will also work if you compile LZDoom yourself.

**NOTE: *Freylis' sprites are not for public use. Please do not use them anywhere. Thank you.***

### Quickstart
---
- Bind the command menu key in the mod's options menu.
- The same key that opens the menu also closes it.

### Weapons
---
The followers have access to the following weapons:
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
- `Shift` allows you to select multiple followers. Acts as a modifier and works either with the number keys or with Quick Access;
- `Ctrl + A` select all;
- `Ctrl + D` deselects all;
- `Ctrl + I` inverts the selection.
- `Ctrl + Alt` modifies the selection to only affect the current page.
- `Enter` applies the selection.

##### Inventory management
---
Most of the navigation is on-screen, but there are a few things that aren't obvious due to lack of space to put said info.
- When selecting amount for transfer, Shift + Left/Right arrow keys increases the amount by 20 instead of 2.

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
- You can now recruit friendly/converted marines as followers. Does not work if the marines were resurrected. If it's smoking, forget about it. You can also recruit hostile marines if they have been incapped. For both of them you need to look at the marine (be within 2m of it) and press the follower menu key.

Marines basically function the exact same way as regular followers, and you can command them as such. A few exceptions exist:
1. They are expendable, so you won't get any notification for leaving any behind when moving between maps. You can, however, carry them between maps to create an army. Of course, at some point it is going to become hell to manage.
2. They don't have the full arsenal the regular followers have.
3. All marines are stored as a single inventory item in first-in-last-out order.
4. Their index in the follower list is also not static. Marines are sorted in the order they were recruited/placed.

### Modding
---
- New followers can be added by inheriting from HDFollower and overriding the provided virtuals (if desired). Their arsenal can be changed too if you like.
- When making new followers, use a higher index. Internally, the three followers use indices 1-6. The index in KEYCONF and HDFollower.FollowerInfo needs to be the same number in both places. This index controls which follower gets manipulated by the reset/warp commands and where they get put in the list. To prevent conflicts, it is recommended to use numbers between 100 and 100 000 000 (excl.) to avoid conflicts with the base mod.
- Do **NOT** add an `hdf_followers` option. This is an internal CVar and its only purpose is to allow players to control the built-in followers. If you don't want an addon follower to show up, don't load the addon.