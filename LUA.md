# Root

The root table now contains bindings which expose the RNG of rendered material and matmod variants.

---

#### `unsigned` root.materialVariant(`Vec2U` tilePosition, `String` layer, `unsigned` matVariants)

Returns the variant index starting from 0 for the material variant used at the specified **tilePosition**. **layer** must be either `"foreground"`, `"background"` or `"platform"`, and **matVariants** must be the amount of variants the material has, which you can use the vanilla `root.materialConfig` function to fetch.

#### `unsigned` root.modVariant(`Vec2U` tilePosition, `String` layer, `unsigned` matVariants)

Works like `root.materialVariant` but for matmods.

---

# Input

The input table contains bindings which provide the key down, held and up states for each key.
The following key names are valid:

<details>
<summary><b>Keys</b></summary>
  
`Backspace, Tab, Clear, Return, Esc, Space, Exclamation, Quote, Hash, Dollar, Ampersand, Apostrophe, LeftParenthesis, RightParenthesis, Multiply, Plus, Comma, Minus, Period, ForwardSlash, Zero, One, Two, Three, Four, Five, Six, Seven, Eight, Nine, Colon, Semicolon, LessThan, Equals, GreaterThan, QuestionMark, At, LeftBracket, BackSlash, RightBracket, Accent, Underline, Grave, A, B, C, D, E, F, G, H, I, J, K, L, M, N, O, P, Q, R, S, T, U, V, W, X, Y, Z, Del, Kp0, Kp1, Kp2, Kp3, Kp4, Kp5, Kp6, Kp7, Kp8, Kp9, Kp_period, Kp_divide, Kp_multiply, Kp_minus, Kp_plus, Kp_enter, Kp_equals, Up, Down, Right, Left, Ins, Home, End, PageUp, PageDown, F1, F2, F3, F4, F5, F6, F7, F8, F9, F10, F11, F12, F13, F14, F15, NumLock, CapsLock, ScrollLock, RShift, LShift, RCtrl, LCtrl, RAlt, LAlt, RGui, LGui, AltGr, Compose, Help, PrintScreen, SysReq, Pause, Menu, Power`

</details>

---

#### `bool` input.key(`String` keyId)

Returns true if the specified key is being held.

#### `bool` input.keyDown(`String` keyId)

Returns true if the specified key was pressed this frame.

#### `bool` input.keyUp(`String` keyId)

Returns true if the specified key was released this frame.

---

# Player

The player table now contains bindings which provide and allow scripts to play songs and get/set the player's identity, mode and aim position.

---

#### `String` player.name()

Returns the player's name.

#### `void` player.setName(`String` name)

Sets the player's name.

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

#### `void` player.playSong(`String` band, `String` resource, `String` abc)

Makes the player break into song if they're holding an instrument.


---

# Effects Animator

The effectsAnimator table is now available wherever the player table is, and allows you to call animator.* functions on the player's effects animator.
