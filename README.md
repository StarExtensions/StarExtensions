![StarExtensions](https://files.catbox.moe/s32cbb.png)

### QoL enhancement mod written in C++ for Starbound.

## Installation
Go to the [releases tab](https://github.com/StarExtensions/StarExtensions/releases). Download the build that appeals to you the most - your build, the build that was meant for you - and extract it to the folder of the same name in the Starbound directory.

The replacement **SDL2.dll** (mostly) fixes audio being permanently lost when the output device is disconnected, and loads StarExtensions.
### If you appreciate my work, feel free to tip me through the sponsorship link on this page.

## Origin

By a truly unbelievable coincidence, I was recently out for a walk when I saw a small package fall off a truck ahead of me.  As I got closer, the typeface slowly came into focus: **Starbound**. Inside, I found a pack of jammie dodgers, a furry poster (tells you something about their audience I guess!) and the latest version of the **Starbound source code**!!

![bag_crop](https://user-images.githubusercontent.com/80987908/185361129-9883fb92-9597-4ba4-b003-4be3dc4971a3.png)

<sup>*disclaimer: this is a joke Tiyuri - please don't call Saul*</sup>
## Features
Type **/guide** in-game to learn how to use these.

<details>
<summary><b>Character Swapper</b></summary>

Swap with your other selves. The ship of the character you joined as stays & saves to the original character's ship file.

Swapping immediately saves the previous character. Ship upgrades for a visiting character will not be applied until you join as that character.

![swapper](https://user-images.githubusercontent.com/80987908/185360435-b03d31ec-74cf-4499-9820-09f28cfdc835.gif)

</details>

<details>
<summary><b>Character Editor</b></summary>

Repurposes Starbound's character creation pane as an in-game editor, so you can edit your appearance live.

![editor](https://user-images.githubusercontent.com/80987908/185359481-3a46fb16-fee0-4ee3-90bd-26f668215596.gif)

</details>

<details>
<summary><b>Identity Editor</b></summary>

For more advanced character editing, you can use the new identity commands to directly modify your character's identity.

![identity_mod](https://user-images.githubusercontent.com/80987908/185365614-1eb5c6b3-a115-436e-847e-4047c682a0f3.gif)

</details>

<details>
<summary><b>Player Inspection</b></summary>

Originally present in Starbound's beta, player inspection is back! The **/description** command lets you change your character's description.

![description](https://user-images.githubusercontent.com/80987908/185783346-3383114f-995b-4ab6-bb66-249dc5fce976.gif)


</details>

<details>
<summary><b>Text to Speech</b></summary>

Players and NPCs now use [Software Automatic Mouth](https://discordier.github.io/sam/). You can enable & customize it with **/speech**!

Glitch get a voice by default. You may want to set a **/speech rule** after so it doesn't speak all of your text.

Google's V8 JavaScript engine is embedded in StarExtensions to run the JavaScript version of SAM, as the C version is unstable.

</details>

<details>
<summary><b>Humanoid Breathing, Head Rotation & Vapor Trail</b></summary>
  
Players and NPCs now breathe, and player heads rotate when sitting, dancing or holding an item. Both are togglable.
  
![breathing](https://user-images.githubusercontent.com/80987908/185374557-b0eb1165-42f9-4115-86d9-6680060c65a6.gif)
![aiming](https://user-images.githubusercontent.com/80987908/185373968-1dc89371-f43a-4171-a493-c81a65dc37c9.gif)

Chucklefish gave humanoids [a vapor trail](https://playstarbound.com/21st-july-progress/). It's meant to appear when you fall but it seems they had forgotten to actually hook it up, so I did. It also now rotates with your velocity, and fades in.

![vapor_trail](https://user-images.githubusercontent.com/80987908/185793966-153761ed-14a2-4419-9ba3-fac31644fb61.gif)

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
<summary><b>Chat Emotes</b></summary>
  
You can now type emotes! Only StarExtensions users can see emotes.

![RrnSvF](https://user-images.githubusercontent.com/80987908/187029093-0f1f08ef-6aeb-4279-9227-e6e96fcaa69a.gif)

<details>
<summary>Emote List</summary>
<b>Does not list personal emotes.</b>

```
ralsei
ralseiweed
asexual
transgender
aroace
genderfluid
bigender
nonbinary
aromantic
bisexual
pansexual
LGBT / pride
lesbian
gay
looky
fnich
why
trollface
stare
ruin
sadde
sad
letsgo
laughedat
flubshed
desolate
bruhe
coolwoah
alcoholism
booba
yes
BibleThump
4Head
ResidentSleeper
NotLikeThis
WutFace
THEROCK
sussybaka
peepoSad
peepoBlanket
WeirdChamp
peepoLove
weSmart
REEeee
monkaGun
FeelsGoodMan
peepoHappy
FeelsOkayMan
HYPERS
YEP
FeelsBadMan
Sadge
widepeepoSad
PepeLaugh
monkaS
monkaW
POGGERS
KEKW
LULW
Pepega
widepeepoHappy
PepeHands
Pog
OMEGALUL
clown_mfs
parrot_wot
deranged_cowboy
morbius
NOOOO
PepeSus
SadCat
TrollDespair
ayy_lmao
clueless
eyes
monkaEyes
gigachad
moyai
wasted
```

</details>

</details>


<details>
<summary><b>Generated Clothes Baker</b></summary>
  
Internally bakes the extremely long directives of [generated clothes](https://silverfeelin.github.io/Starbound-NgOutfitGenerator/) to a spritesheet, so they no longer destroy performance.

</details>

<details>
<summary><b>Tile Prediction</b></summary>
  
Placing tiles on servers is now predicted to make building smoother.

</details>

<details>
<summary><b>Item & Portrait Protection</b></summary>
  
When another player tries to use a Lua script to copy your item, they get a dollar store version with most important parameters removed.

When another player tries to use [world.entityPortrait](https://starbound-unofficial.readthedocs.io/en/latest/lua/world.html#jsonarray-world-entityportrait-entityid-entityid-string-portraitmode) to copy your clothing and you've put the parameter `"portraitProtected" : true` on it, they don't get the directives.

</details>


## Fixes

• Fixed being unable to hear another player's song if you load them after they begin playing.

• Fixed the game crashing when you're disconnected from the server with the inventory open.

• Fixed the connection error screen sometimes vanishing, leaving only the game title and forcing you to restart.

• Fixed chat color state being lost from text wrapping to the next line.

![image](https://user-images.githubusercontent.com/80987908/185369315-db8a641c-4e3b-435b-8251-acaaa4715fe6.png)

• Fixed players & NPCs talking shit about beans on toast. Beans on toast is a delicacy.
