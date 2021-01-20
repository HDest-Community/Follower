### Important
---
The mod needs at least GZDoom 4.5.0 (or a dev build) to run. LZDoom does not currently have a compiled version that supports it. However, the mod will work with the next stable version of LZDoom. It will also work if you compile LZDoom yourself.

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

### Modding
---
- New followers can be added by inheriting from HDFollower and overriding the provided virtuals. Their arsenal can be changed if you like.