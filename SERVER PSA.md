### PSA for Starbound server owners

The humanoid identity structure holds the player's character customization. It has become common for players on popular servers to directly modify this to further customize their character.

You can modify your humanoid identity by converting your player file to the JSON format, editing it and then converting it back. If you have StarExtensions installed, you can simply use the **/identity** command in-game. 
For example, you could [generate directives](https://rexmeck.github.io/Drawable-Generator/) and put the output in your identity's hairDirectives to customize your hair.

Unfortunately, there is a bug in Starbound that causes the server to serialize the player's whole humanoid identity in every EntityUpdate sent over the network, **even if the identity has not changed.** This makes life difficult for users on low-end connections, and wastes bandwidth!

I tried to create a client-side workaround for StarExtensions but unfortunately, this is not possible. That is where you come in. If you host a server, **you** can fix this.
# 
Make sure you are hosting Starbound version 1.4.4. Then, open the server executable in a hex editor and replace the 7 bytes at the given offset with 0x90 to remove a line of code. Please use the offset instead of performing a byte search, as otherwise you could end up replacing the wrong occurrences of the instruction.

- linux server x86_64 1.4.4: `C6 83 E0 08 00 00 01` @ `0x9B616D`
- windows server x64 1.4.4: `C6 86 20 09 00 00 01` @ `0x399060`
- windows server x32 1.4.4: `C6 83 3C 06 00 00 01` @ `0x309107`

If you cannot follow these instructions for whatever reasons, server binaries with this patch pre-applied are available [for download](https://files.catbox.moe/pw0fyb.zip).

# 
### Technical Details

`getNetStates` is called right after an update is received for an entity. In `Player::getNetStates`, this code is written:
```cpp
bool updated = m_identityNetState.m_updated;
m_identityNetState.m_updated = false;
if (updated) {
  m_identity = m_identityNetState.m_value;
  m_identityUpdated = true; //This is the line the guide above removes.
  m_humanoid->setIdentity(m_identity);
}
```

`setNetStates` is called right before an update is serialized from an entity. **The server shouldn't call this if it does not own the entity, but does so anyway**. In `Player::setNetStates`, this code is written:
```cpp
if (m_identityUpdated) {
  m_identityNetState.push(m_identity); //This causes m_identityNetState.m_updated to become true.
  m_identityUpdated = false;
}
```

This results in an endless cycle. When `Player::setNetStates` is called, it causes m_identity to be pushed to m_identityNetState. This is not necessary, as m_identityNetState already holds the identity received from the client. Now m_updated is true, and so the if statement in `Player::getNetStates` evaluates true and sets m_identityUpdated to true allowing this to repeat.

### Footnote

Open source your tragedy already, Finn!
