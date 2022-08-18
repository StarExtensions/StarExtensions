# *StarExtensions*
### QoL enhancement mod written in C++ for Starbound.

## Origin

By a truly unbelievable coincidence, I was recently out for a walk when I saw a small package fall off a truck ahead of me.  As I got closer, the typeface slowly came into focus: **Starbound**. Inside, I found a pack of jammie dodgers, a furry poster (tells you something about their audience I guess!) and the latest version of the **Starbound source code**!!

![bag_crop](https://user-images.githubusercontent.com/80987908/185361129-9883fb92-9597-4ba4-b003-4be3dc4971a3.png)

<sup>*this is a joke Tiyuri, please don't send Saul Goodman to my house.*</sup>
## Features
**Type /guide in-game to learn how to use these.**

<details>
<summary><b>Character Swapper</b></summary>

Swap with your other selves. The ship of the character you joined as stays, and will save to the original character's ship file.

Swapping immediately saves the previous character. Ship upgrades for a visiting character will not be applied until you join as that character.

![swapper](https://user-images.githubusercontent.com/80987908/185360435-b03d31ec-74cf-4499-9820-09f28cfdc835.gif)

</details>

<details>
<summary><b>Character Editor</b></summary>

Repurposes Starbound's character creation pane as an in-game editor, so you can edit your appearance live.

![editor](https://user-images.githubusercontent.com/80987908/185359481-3a46fb16-fee0-4ee3-90bd-26f668215596.gif)

</details>

<details>
<summary><b>Identity Modification</b></summary>

For more advanced character editing, you can use the new identity commands to directly modify your character's identity.

![identity_mod](https://user-images.githubusercontent.com/80987908/185365614-1eb5c6b3-a115-436e-847e-4047c682a0f3.gif)

</details>

<details>
<summary><b>Chat Opacity & Directives</b></summary>

You can now set the opacity of chat text, which was originally a hardcoded 50%.

You can now apply processing directives to the chat font, the default is `?border=1;000;0000`.

![chat](https://user-images.githubusercontent.com/80987908/185368435-d694a2fc-e76c-4b70-aa63-77fbb6bbac5e.gif)

</details>

<details>
<summary><b>Night Vision</b></summary>

Makes the dark.. not so dark.

![nv](https://user-images.githubusercontent.com/80987908/185371133-766de8e7-05c2-4f7b-9e21-0687afd89fe0.gif)

</details>


<details>
<summary><b>Better Tech Scaling</b></summary>

Beautifies tech scaling by changing how it's rendered to scale the drawables instead of the sprites. Works with any scaling tech!

This also fixes various offset issues with scaling, such as your head detaching when you crouch.

![image](https://user-images.githubusercontent.com/80987908/185363859-8afecdaf-80cd-45b4-a92a-9b41330b7bd7.png)

</details>


<details>
<summary><b>Generated Clothes Baker</b></summary>
  
Internally bakes the extremely long directives of [generated clothes](https://silverfeelin.github.io/Starbound-NgOutfitGenerator/) to a spritesheet, so they no longer destroy performance.

</details>

## Fixes

• Fixed the game crashing when you're disconnected from the server with the inventory open.

• Fixed the connection error screen sometimes vanishing, leaving only the game title and forcing you to restart.

• Fixed chat color state being lost from text wrapping to the next line.

![image](https://user-images.githubusercontent.com/80987908/185369315-db8a641c-4e3b-435b-8251-acaaa4715fe6.png)
