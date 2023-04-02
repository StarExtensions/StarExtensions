# Permissions

A few of these need your mod to ask for permission to use by adding `permissions` to the **_metadata** file in your mod.

<details><summary><b>Example</b></summary>
  
```json
{
  "description" : "holy fucking bingle.."
  "name" : "awesom mod!! :3c",
  "permissions" : ["example", "a", "b", "c"]
}
```
  
</details>

---

# Unsorted

These are functions that aren't in any specific table.

---

#### `Maybe<LuaFunction>, Maybe<String>` loadstring(`String` source, [`String` name, [`LuaValue` env]])

Compiles the provided **source** and returns it as a callable function.
If there are any syntax errors, returns `nil` and the error as a string instead.

- **name** is used for error messages, the default is the name of the script that called `loadstring`.
- **env** is used as the environment of the returned function, the default is `_ENV`.

---

# Root

The root table now contains extra asset bindings and bindings to return the tile variant that is used for material and matmods at any position.

---

#### `unsigned` root.materialVariant(`Vec2U` tilePosition, `String` layer, `unsigned` matVariants)

Returns the variant index starting from 0 for the material variant used at the specified **tilePosition**. **layer** must be either `"foreground"`, `"background"` or `"platform"`, and **matVariants** must be the amount of variants the material has, which you can use the vanilla `root.materialConfig` function to fetch.

#### `unsigned` root.modVariant(`Vec2U` tilePosition, `String` layer, `unsigned` matVariants)

Works like `root.materialVariant` but for matmods.

---

#### `String[]` root.assetsByExtension(`String` extension)

Returns an array containing all assets with the specified file extension.

By the way, here's a list of every file extension the game does Special Things™ for when loading assets.

<details><summary><b>File Extensions</b></summary>

- Items: `item`, `liqitem`, `matitem`, `miningtool`, `flashlight`, `wiretool`, `beamaxe`, `tillingtool`, `painttool`, `harvestingtool`, `head`, `chest`, `legs`, `back`, `currency`, `consumable`, `blueprint`, `inspectiontool`, `instrument`, `thrownitem`, `unlock`, `activeitem`, `augment`
- Materials: `material`, `matmod`
- Liquids: `liquid`
- NPCs: `npctype`
- Tenants: `tenant`
- Objects: `object`
- Vehicles: `vehicle`
- Monsters: `monstertype`, `monsterpart`, `monsterskill`, `monstercolors`
- Plants: `modularstem`, `modularfoliage`, `grass`, `bush`
- Projectiles: `projectile`
- Particles: `particle`
- Name Gen: `namesource`
- AI Missions: `aimission`
- Quests: `questtemplate`
- Radio Messages: `radiomessages`
- Spawn Types: `spawntypes`
- Species: `species`
- Stagehand: `stagehand`
- Behaviors: `nodes`, `behavior`
- Biomes: `biome`, `weather`
- Terrain: `terrain`
- Treasure: `treasurepools`, `treasurechests`
- Codex Entries: `codex`
- Collections: `collection`
- Statistics: `event`, `achievement`
- Status Effects: `statuseffect`
- Functions: `functions`, `2functions`, `configfunctions`
- Tech: `tech`
- Damage: `damage`
- Dances: `dance`
- Effect Sources: `effectsource`
- Command Macros: `macros`
- Recipes: `recipe`
</details>

#### `String` root.assetData(`String` path)

Returns the raw data of an asset.

---

#### `Json` root.getConfiguration(`String` key)

Gets a configuration value.

#### `Json` root.getConfigurationPath(`String` path)

Gets a configuration value by path.

*Both getters will error if you try to get `title`, as that can contains the player's saved server login.*

#### `Json` root.setConfiguration(`String` key, `Json` value)

Sets a configuration value.

#### `Json` root.setConfigurationPath(`String` path,  `Json` value)

Sets a configuration value by path.

*Both setters will error if you try to set `safeScripts`, as that can break Starbound's sandbox.*

---

# StarExtensions



---

#### `String` starExtensions.version()

duh

#### `bool` starExtensions.hasPermission(`String` permission)

Returns whether the currently executing script has permission to use the specified functionality.

---

# Window

The window table contains bindings to get and set the state of the game window.

**Your mod must have the permission `"window"` to use these.**

---

#### `bool` window.mouseFocused()

Returns whether the window has mouse focus.

#### `bool` window.inputFocused()

Returns whether the window has input focus.

#### `bool` window.borderless()

Returns whether the window is bordered.

#### `void` window.setBorderless()

Sets the window's borderless state.

#### `bool` window.grabbed()

Returns whether the window is grabbed.

#### `void` window.setGrabbed()

Sets the window's grab state.

#### `String` window.title()

Returns the window title.

#### `void` window.setTitle()

Sets the window title.

#### `Vec2I` window.size()

Returns the window size.

#### `void` window.setSize()

Sets the window size.

#### `Vec2U` window.screenSize()

Returns the screen size.

#### `Vec2I` window.translate(`Vec2I` offset)

Moves the window by offset and returns the new position.

#### `Vec2I` window.position()

Returns the window position.

#### `void` window.setPosition(`Vec2I` position)

Sets the window position.

#### `void` window.flash(`String` operation)

Flashes the window in the taskbar. `operation` can be either `"untilFocus"`, `"briefly"` or `"cancel"`.

---

# Clipboard

The clipboard table contains bindings to read and write text to the clipboard. 

**Your mod must have the permission `"clipboard"` to use these.**

#### `bool` clipboard.hasText()

Returns whether the clipboard contains text.

#### `Maybe<String>` clipboard.getText()

If the clipboard has text, returns it. Otherwise, returns `nil`.

#### `Maybe<String>` clipboard.setText()

Sets the clipboard text. If there was an error doing so, returns it as a string.

---

# Camera

The camera table contains bindings which allow scripts to access and modify the camera pixel ratio aka zoom level, position and set per-frame overrides.

---

#### `Vec2F` camera.position()

Returns the position of the camera.

#### `void` camera.override(`Vec2F` position, `float` priority, [`Json` config])

Adds a camera position override for the current frame. Optionally, provide **config** as a table containing at least one of:
- `String` **type**: either `"additive"` or `"blend"`
- `float` **influence**: The influence of this override.

Camera overrides are applied in order of priority. If multiple overrides of the same priority are set, they are sorted based on call order.

---

#### `unsigned` camera.pixelRatio()

Returns the camera's pixel ratio.

#### `unsigned` camera.setPixelRatio(`unsigned` pixelRatio)

Sets the camera's pixel ratio. **pixelRatio** must be above 0.

---

#### `Vec2U` camera.screenSize()

Returns the camera's screen size.

#### `Vec2F` camera.screenToWorld(`Vec2F` screenCoords)

Converts screen pixel coordinates to world coordinates.

#### `Vec2F` camera.worldToScreen(`Vec2F` worldCoords)

Converts world coordinates to screen pixel coordinates.

---

# World

The world table now contains bindings to get all the world properties and current latency to the server

---

#### `Json` world.properties([`bool` skipValues])

Returns all the world properties. if **skipValues** is true, only includes property keys.

#### `unsigned` world.latency()

Returns the current latency to the server.

# Interface

The interface table contains bindings which allow scripts to show text under the cursor and display a message at the bottom of the screen.

#### `bool` interface.setCursorText(`String` text, [`bool` override])

Sets the displayed cursor text. Pass **override** as `true` if you want to override the game's cursor text, but as it's sparsely used it isn't too important.

#### `void` interface.queueMessage(`String` message, [`float` cooldown, [`float` springState]])

Queues a message popup at the bottom of the screen with an optional **cooldown** and **springState**.

#### `void` interface.setHudVisible(`bool` visible)

Sets the HUD's visibility.

#### `bool` interface.hudVisible()

Returns the HUD's visibility.

#### `bool` interface.drawDrawable(`Drawable` drawable, `Vec2F` position, `int` pixelRatio, [`Color` color])

Pushes a drawable to be drawn to the screen.

---

# Chat

The chat table contains bindings to run commands, get the user's input, set/get the font size and add local-only messages to the chat log.

---

#### `String[]` chat.command(`String` command)

Runs a chat command and returns the result.

#### `String` chat.input()

Returns the chat input box text.

#### `String` chat.setInput(`String` text)

Sets the chat input box text. Newlines are replaced with spaces - if the passed text was modified, returns the changed text.

---

#### `void` chat.addMessage(`String` text, [`Json` config])

Adds a message to the chat log. Example **config**:

```lua
{
  mode = "Local", -- Local, Party, Broadcast, Whisper, CommandResult (default), RadioMessage, World
  portrait = "/interface/chatbubbles/captainrage.png:default",
  fromNick = "Jerma985",
  showPane = false -- defaults to true
}
```

---

#### `void` chat.clear([`unsigned` count])

Clears the chat box, or up to **count** if specified.

---

#### `void` chat.setFontSize(`unsigned` fontSize)

Sets the font size.

#### `unsigned` chat.fontSize()

Returns the font size.

---

# Starbound
---

#### `unsigned` sb.framesSkipped()

Returns how many frames have been skipped.

---

#### `unsigned, String` sb.lastLuaError()

Returns an ID and the last LuaException as a string.

---

# Input

The input table contains bindings which provide the key down, held and up states for each key.

<details>
<summary><b>Valid Keys</b></summary>
  
``Backspace, Tab, Clear, Return, Esc, Space, !, ", #, $, &, ', (, ), *, +, ,, -, ., /, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, :, ;, <, =, >, ?, @, [, \, ], ^, _, `, A, B, C, D, E, F, G, H, I, J, K, L, M, N, O, P, Q, R, S, T, U, V, W, X, Y, Z, Del, Kp0, Kp1, Kp2, Kp3, Kp4, Kp5, Kp6, Kp7, Kp8, Kp9, Kp_period, Kp_divide, Kp_multiply, Kp_minus, Kp_plus, Kp_enter, Kp_equals, Up, Down, Right, Left, Ins, Home, End, PageUp, PageDown, F1, F2, F3, F4, F5, F6, F7, F8, F9, F10, F11, F12, F13, F14, F15, NumLock, CapsLock, ScrollLock, RShift, LShift, RCtrl, LCtrl, RAlt, LAlt, RGui, LGui, AltGr, Compose, Help, PrintScreen, SysReq, Pause, Menu, Power``

</details>

<details>
<summary><b>Valid Key Mods</b></summary>
  
``LShift, RShift, LCtrl, RCtrl, LAlt, RAlt, LGui, RGui, Num, Caps, AltGr``
  
</details>
 
<details>
<summary><b>Valid Mouse Buttons</b></summary>
  
``MouseLeft, MouseMiddle, MouseRight, MouseFourth, MouseFifth``
  
</details>

---

#### `Vec2I` input.mousePosition()
  
Returns the mouse position.
  
#### `void` input.setMousePosition()
  
Sets the mouse position.
  
#### `bool` input.mouse(`String` mouseButtonId)

Returns true if the specified mouse button is being held.

#### `bool, Vec2I[]` input.mouseDown(`String` mouseButtonId)

Returns true if the specified mouse button was pressed this frame. If true, then also returns a list of positions where the mouse was pressed.

#### `bool, Vec2I[]` input.mouseUp(`String` mouseButtonId)

Returns true if the specified mouse button was released this frame. If true, then also returns a list of positions where the mouse was released.

---

#### `bool` input.key(`String` keyId)

Returns true if the specified key is being held.

#### `bool` input.keyDown(`String` keyId, [`KeyMods` mods])

Returns true if the specified key was pressed this frame. If an array of KeyMods are provided, then only returns true if all modifiers specified were pressed.

#### `bool` input.keyUp(`String` keyId)

Returns true if the specified key was released this frame.
  
***Please do not evaluate the result of these functions using `== true` as the positive return value type may change in the future.***
  
---
  
#### `InputEvent[]` input.events()
  
Returns all the input events that have happened this frame. Each input event contains a string `type`, and `data` which can vary based on the type of input, see below.
  
<details><summary><b>Supported Input Events</b></summary>

```lua
-- KeyDown
{
  "key" : Key
  "mods" : [KeyMod...]
}
  
-- KeyUp
{
  "key" : Key (string)
}
  
-- MouseButtonDown
-- MouseButtonUp
{
  "mouseButton" : MouseButton
  "mousePosition" : Vec2I
}

-- MouseWheel
{
  "mouseWheel" : 1 or -1
  "mousePosition" : Vec2I
}
  
-- MouseMove
{
  "mouseMove" : Vec2I
  "mousePosition" : Vec2I
}
```
  
</details>

---
  
#### `bool` input.bind(`String` categoryId, `String` bindId)

Returns true if the specified input binding is being held. Errors if the bind isn't in the database.

#### `unsigned` input.bindDown(`String` categoryId, `String` bindId)

Returns how many times the specified bind was pressed this frame, or false if not at all. Errors if the bind isn't in the database.

#### `unsigned` input.bindUp(`String` categoryId, `String` bindId)

Returns how many times the specified bind was released this frame, or false if not at all. Errors if the bind isn't in the database.

---  

# Player

The player table now contains bindings which contains functions to save/load, access and modify the player's identity, mode, aim, emote and more.

---

#### `Json` player.save()

Serializes the player to Json the same way Starbound does for disk storage and returns it.

#### `void` player.load(`Json` save)

Reloads the player from a Json **save**. This will reset active ScriptPanes and scripts running on the player.
  
---

#### `String` player.name()

Returns the player's name.

#### `void` player.setName(`String` name)

Sets the player's name.

---

#### `String` player.description()

Returns the player's description.

#### `void` player.setDescription(`String` description)

Sets the player's description. The new description will not be networked buntil the player warps or respawns.

---

#### `String` player.species()

Returns the player's species.

#### `void` player.setSpecies(`String` species)

Sets the player's species. Must be a valid species.

---

#### `String` player.gender()

Returns the player's gender.

#### `void` player.setGender(`String` gender)

Sets the player's gender.

---

#### `String` player.imagePath()

If the player has a custom humanoid image path set, returns it. otherwise, returns `nil`.

#### `void` player.setImagePath(`String` imagePath)

Sets the player's image path. Specify `nil` to remove the image path.

---

#### `Personality` player.personality()

Returns the player's personality as a `table` containing a `string` idle, `string` armIdle, `Vec2F` headOffset and `Vec2F` armOffset.

#### `void` player.setPersonality(`Personality` personality)

Sets the player's personality. The **personality** must be a `table` containing at least one value as returned by `player.personality()`.

---

#### `String` player.bodyDirectives()

Returns the player's body directives.

#### `void` player.setBodyDirectives(`String` bodyDirectives)

Sets the player's body directives.

---

#### `String` player.emoteDirectives()

Returns the player's emote directives.

#### `void` player.setEmoteDirectives(`String` emoteDirectives)

Sets the player's emote directives.

---

#### `String` player.hairGroup()

Returns the player's hair group.

#### `void` player.setHairGroup(`String` hairGroup)

Sets the player's hair group.

---

#### `String` player.hairType()

Returns the player's hair type.

#### `void` player.setHairType(`String` hairType)

Sets the player's hair type.

---

#### `String` player.hairDirectives()

Returns the player's hair directives.

#### `void` player.setHairDirectives(`String` hairDirectives)

Sets the player's hair directives.

---

#### `String` player.facialHairGroup()

Returns the player's facial hair group.

#### `void` player.setFacialHairGroup(`String` facialHairGroup)

Sets the player's facial hair group.

---

#### `String` player.facialHairType()

Returns the player's facial hair type.

#### `void` player.setFacialHairType(`String` facialHairType)

Sets the player's facial hair type.

---

#### `String` player.facialHairDirectives()

Returns the player's facial hair directives.

#### `void` player.setFacialHairDirectives(`String` facialHairDirectives)

Sets the player's facial hair directives.

---

#### `String` player.facialMaskGroup()

Returns the player's facial mask group.

#### `void` player.setFacialMaskGroup(`String` facialMaskGroup)

Sets the player's facial mask group.

---

#### `String` player.facialMaskType()

Returns the player's facial mask type.

#### `void` player.setFacialMaskType(`String` facialMaskType)

Sets the player's facial mask type.

---

#### `String` player.facialMaskDirectives()

Returns the player's facial mask directives.

#### `void` player.setFacialMaskDirectives(`String` facialMaskDirectives)

Sets the player's facial mask directives.

---

#### `PlayerMode` player.mode()

Returns the player's mode.

#### `void` player.setMode(`String` mode)

Sets the player's mode. **mode** must be either `"casual"`, `"survival"` or `"hardcore"`.

---

#### `Vec2F` player.aimPosition()

Returns the player's aim position.

---

#### `void` player.emote(`String` emote, [`float` cooldown])

Makes the player do an emote with the default cooldown unless a **cooldown** is specified.

#### `String, float` player.currentEmote()

Returns the player's current emote and the seconds left in it.

---

# Songbook
  
The songbook table is available alongside the player table, and provides functions to control the player's Songbook.
  
#### `void` songbook.play(`String` band, `String` resource, `String` abc)

Makes the player break into song with the specified **band**, **resource** and **abc** if they're holding an instrument.

#### `String` songbook.band()

If the player is playing a song then returns their band, otherwise returns `nil`.
  
#### `String` songbook.instrument()
  
Returns the player's last used instrument, or `nil`.
  
#### `Json` songbook.song()
  
If the player is playing a song then returns a `table` containing the player's song `resource` and `abc`, otherwise returns `nil`.

# Effects Animator

The effectsAnimator table is available alongside the player table, and provides Starbound's animator.* functions for the player's effects animator.

