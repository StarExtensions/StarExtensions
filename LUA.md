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


#### `String` root.assetData(`String` path)

Returns the raw data of an asset.

---

# Camera

The camera table contians bindings which allow scripts to access and modify the camera pixel ratio aka zoom level, position and set per-frame overrides.

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

---  

# Player

The player table now contains bindings which contains functions to access and modify the player's identity, mode, aim, emote and more.

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

#### `String, float` player.setDescription(`String` description)

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
