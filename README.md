![StarExtensions](https://files.catbox.moe/qlqnge.png)

### QoL enhancement mod written in C++ for Starbound.

## Installation
Go to the [latest release](https://github.com/StarExtensions/StarExtensions/releases/latest). Download either the win64 or win32 build, depending on which version of Starbound you use - and extract it to the folder of the same name in the Starbound directory.

StarExtensions does not work on Windows 7, which Microsoft [ended support & security updates for over three years ago](https://support.microsoft.com/en-us/windows/windows-7-support-ended-on-january-14-2020-b75d4580-2cc7-895a-2c9c-1466d9a53962).

The replacement **SDL2.dll** (mostly) fixes audio being permanently lost when the output device is disconnected, and loads StarExtensions. You can create a file called **libraries.txt** in the win64/win32 folder and list other DLLs to load on each line.
### If you appreciate my work, feel free to tip me through the sponsorship link on this page.
[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/Q5Q1EH3WV)

## Origin

By a truly unbelievable coincidence, I was recently out for a walk when I saw a small package fall off a truck ahead of me.  As I got closer, the typeface slowly came into focus: **Starbound**. Inside, I found a pack of jammie dodgers, a furry poster (tells you something about their audience I guess!) and the latest version of the **Starbound source code**!!

![bag_crop](https://user-images.githubusercontent.com/80987908/185361129-9883fb92-9597-4ba4-b003-4be3dc4971a3.png)

<sup>*disclaimer: this is a joke Tiyuri - please don't call Saul*</sup>
## Features
Type **/guide** in-game with one of the following options: `chat`, `character`, `humanoid`, `misc`.

<details>
<summary><b>Proximity Voice Chat</b></summary>

StarExtensions adds **proximity voice chat**.

Type **/voice** to open the menu, but don't forget to set the push-to-talk bind in **/binds**.

![image](https://user-images.githubusercontent.com/80987908/232179267-13c3111a-1a6e-4cdc-ac3c-75380fa9ebde.png)

</details>

<details>
<summary><b>Input Binds</b></summary>

StarExtensions adds support for mods to add custom bindings. Type <b>/binds</b> to open the bindings menu.

Modders: to add your own binds, add a .binds file anywhere in your mod. Be careful not to overwrite someone elses .binds file.
Here is an example .binds file, which adds a bind with two defaults.

```json
{
  "examplemod": {
    "name": "Example Mod",
    "bannerName" : "Example Mod!!",
    "binds": {
      "awesomebind": {
        "default": [{
          "type": "key",
          "value": "C",
          "mods": ["LShift"]
        },
        {
          "type": "key",
          "value": "V",
          "mods": ["LShift"]
        }],
        "name": "Awesome Bind"
      }
    }
  }
}
```

You can then use the **input.bind\*** functions.

</details>

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

You can give other species a default voice with a patch. Here's the patch used for Glitch as an example:

**/species/glitch.species.patch**
```json
[
  {
    "op": "add",
    "path": "/samVoiceProfiles",
    "value": {
      "male": {
        "pitch": 50,
        "mouth": 142,
        "throat": 142
      },
      "female": {
        "pitch": 32,
        "mouth": 180,
        "throat": 165
      }
    }
  }
]
```

These are the default variables:
```json
{
  "sing" : false,
  "pitch" : 64,
  "speed" : 72,
  "mouth" : 128,
  "throat" : 128,
  "audioSpeed" : 1.0
}
```

Many thanks to thedjinn for [porting SAM to Rust](https://github.com/thedjinn/rustsam)!

</details>

<details>
<summary><b>Humanoid Breathing, Head Rotation, Dynamics & Vapor Trail</b></summary>
  
Humanoids now breathe, and player heads rotate when sitting, dancing or holding an item. Both are togglable.
  
![breathing](https://user-images.githubusercontent.com/80987908/185374557-b0eb1165-42f9-4115-86d9-6680060c65a6.gif)
![aiming](https://user-images.githubusercontent.com/80987908/185373968-1dc89371-f43a-4171-a493-c81a65dc37c9.gif)
  
Chucklefish gave humanoids [a vapor trail](https://playstarbound.com/21st-july-progress/). It's meant to appear when you fall but it seems they had forgotten to actually hook it up, so I did. It also now rotates with your velocity, and fades in.

![vapor_trail](https://user-images.githubusercontent.com/80987908/185793966-153761ed-14a2-4419-9ba3-fac31644fb61.gif)

<details>
<summary>Humanoid Guide</summary>

### NPCs
To disable breathing or dynamics on NPCs, these can be put in their status properties:
```json
{
  "disableBreathing" : true,
  "disableDynamics" : true
}
```

### Humanoid Overrides
In your .species config file, you can specify the following in `"humanoidOverrides" : {}`:
 
<details>
<summary>.species:humanoidOverrides example</summary>
  
```json
"humanoidOverrides" : {
  "headSliceY" : 25,
  // THIS IS DEPRECATED! cleaves the body in two, using the upper slice as part of the head for rotation.
  
  // if your body spritesheet has pixels that must appear attached to the head,
  // then these two are available for head rotation compatibility.
  "useBodyMask" : true,
  // adds a ?blendmult=/humanoid/<species>/mask/<gender>body.png to the body drawable's directives
  "useBodyHeadMask" : true,
  // 1. copies the body drawable
  // 2. prefixes ?blendmult=/humanoid/<species>/headmask/<gender>body.png to the directives
  // 3. moves it as if part of the head, overrides headSliceY
  
  "headUsesBodyFrame" : true,
  // makes the head copy the body's frame when drawn
  "hairUsesBodyFrame" : true,
  // makes the hair copy the body's frame when drawn
  "facialHairUsesBodyFrame" : true,
  // makes the facial hair copy the body's frame when drawn
}
```
 
</details>

If you are using the `xUsesBodyFrame` options, you will need to add .frames files to your `/humanoid/<species>/` folder that match the body frames.
<details>
<summary>template [female/male]head.frames OR hair/default.frames</summary>
  
```json
{
  "frameGrid" : {
    "size" : [43, 43],
    "dimensions" : [9, 6],

    "names" : [
      [ null, "idle.1", "idle.2", "idle.3", "idle.4", "idle.5", "sit.1", null, "duck.1" ],
      [ null, "walk.1", "walk.2", "walk.3", "walk.4", "walk.5", "walk.6", "walk.7", "walk.8" ],
      [ null, "run.1", "run.2", "run.3", "run.4", "run.5", "run.6", "run.7", "run.8" ],
      [ null, "jump.1", "jump.2", "jump.3", "jump.4", "fall.1", "fall.2", "fall.3", "fall.4" ],
      [ null, "climb.1", "climb.2", "climb.3", "climb.4", "climb.5", "climb.6", "climb.7", "climb.8" ],
      [ null, "swimIdle.1", null, null, "swim.1", "swim.2", "swim.3", "swim.4" ]
    ]
  },
  "aliases" : {
    "swimIdle.2" : "swimIdle.1",
    "swim.5" : "swimIdle.1",
    "swim.6" : "swimIdle.1",
    "swim.7" : "swimIdle.1",
    "lay.1" : "run.8",
    //aliases for vanilla compatibility
    "normal" : "idle.1",
    "climb" : "climb.1"
  }
}
```
  
</details>
  
### Dynamics
  
To add support for a modded species, add these files with a mod:
- `/humanoid/<species>/dynamic/base/<gender>body.png` - Base layer
- `/humanoid/<species>/dynamic/<gender>body.png` - Moving layer
- Used instead if the player has generated body directives (very very rare, you can just make 'em blank)
  - `/humanoid/<species>/dynamic/mask/<gender>body.png` - Moving mask
  - `/humanoid/<species>/dynamic/basemask/<gender>body.png` - Base mask
  
To add support for an armor item, add these files to the armor item's directory with a mod, \<image> being the same name of the original spritesheet such as 'chestf'.
- `dynamic/base/<image>` - Base layer
- `dynamic/<image>` - Moving layer
- `dynamic/mask/<image>` - Mask to cut pixels out of the humanoid moving layer if necessary.

<b>You must add `"dynamic" : true` to the parameters (not the config) of an item instance to enable dynamics.</b>

For <b>[vanilla-compatible generated clothing](https://silverfeelin.github.io/Starbound-NgOutfitGenerator/)</b>:
- Add a table called `dynamicData` {} to the parameters. In it, you can insert the following generated directives from the outfit generator of your choice with these names:
  - `base` - Base layer
  - `moving` - Moving layer
  - `mask` - Mask to cut pixels out of the humanoid moving layer if necessary.
  - `overlay` - Non-moving overlay layer.
  - You can also insert a `multiplier` number value to multiply the dynamics intensity.

<b>Please remember to include a standard `directives` parameter for players without this mod or dynamics enabled!</b>

</details>

---

</details>

<details>
<summary><b>Chat Opacity & Directives</b></summary>

You can now set the opacity of chat text, which was originally a hardcoded 50%.

You can now apply processing directives to the chat font, the default is `?border=1;000;0000`.

![chat](https://user-images.githubusercontent.com/80987908/185368435-d694a2fc-e76c-4b70-aa63-77fbb6bbac5e.gif)

</details>

<details>
<summary><b>Enhanced Liquid</b></summary>

Smoothens out the appearance of liquid and adds a highlight to the top.
![healing_liquid](https://user-images.githubusercontent.com/80987908/215626572-3fd5ec7a-b5cc-49df-a6f2-52161bbe265f.gif)


</details>

<details>
<summary><b>Night Vision</b></summary>

Makes the dark.. not so dark.

![nv](https://user-images.githubusercontent.com/80987908/185371133-766de8e7-05c2-4f7b-9e21-0687afd89fe0.gif)

</details>


<details>
<summary><b>Better Scaling</b></summary>

Beautifies tech and status scaling by changing how it's rendered to scale the drawables instead of the sprites. Works with parent directives set from tech and status effect scripts, and primary directives from status primary scripts!

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

<details>
<summary><b>Item Drop Tooltips</b></summary>

You can now hover over item drops to get to know them a little better.

![](https://user-images.githubusercontent.com/80987908/211474220-c79eefb1-5098-486e-8f5f-bc9ac7cf9b5c.gif)


</details>

<details>
<summary><b>Image & Armor Rendering</b></summary>
Use the <b>/render</b> command to render an image with directives to your clipboard. This is useful for recovering sprites.
You can also render your worn armor to the clipboard - type <b>/render</b> on its own for more information.
</details>

## Fixes

• Fixed being unable to hear another player's song if you load them after they begin playing.

• Fixed the game crashing when you're disconnected from the server with the inventory open.

• Fixed the connection error screen sometimes vanishing, leaving only the game title and forcing you to restart.

• Fixed chat color state being lost from text wrapping to the next line.

![image](https://user-images.githubusercontent.com/80987908/185369315-db8a641c-4e3b-435b-8251-acaaa4715fe6.png)

• Fixed players & NPCs talking shit about beans on toast. Beans on toast is a delicacy.
