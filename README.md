# Terra Mira

## Summary

Terra Mira is a CDDA inspired wizard tower simulation game with a custom C++ ECS engine based on D&D (specifically Pathfinder 1e) mechanics and lore. It is a 2D grid based game with z-levels and a heavy focus on simulation and automation. The idea is CDDA but high fantasy with D&D inspired combat mechanics/spells/items, expanded NPC control/colony sim mechanics, a much greater focus on NPCs in general, and in depth automation both for the NPCs and player. I am hoping to combine the best aspects of survival simulations and colony sims while addressing what I believe to be the primary issues of both; tedium and performance.

**WARNING**


The game is currently in an engine/mechanics test phase. Graphics are purely functional colored squares while core systems are being built out.


**DISCLAIMER**


I use AI for education and code review.
I do NOT use AI for asset generation or game design.


**IF YOU WANT TO PLAY**

The game is free to download under releases.  Phase 1 will always be free and is intended as a demo.

Here are the default keybinds; they are adjustable in the escape menu

Also there are mouse controls; 

left click to automove/select entities

right click for context menu

mouse wheel in most step menus

| Action | Key |
| :--- | :---: |
| **Move North** | <kbd>E</kbd> |
| **Move South** | <kbd>C</kbd> |
| **Move West** | <kbd>S</kbd> |
| **Move East** | <kbd>F</kbd> |
| **Move NW** | <kbd>W</kbd> |
| **Move NE** | <kbd>R</kbd> |
| **Move SW** | <kbd>X</kbd> |
| **Move SE** | <kbd>V</kbd> |
| **Stairs Up** | <kbd>Q</kbd> |
| **Stairs Down** | <kbd>A</kbd> |
| **Wait Turn** | <kbd>D</kbd> |
| **Interact / Pickup / Dig** | <kbd>G</kbd> |
| **Toggle Inventory Menu** | <kbd>I</kbd> |
| **Toggle Crafting Menu** | <kbd>U</kbd> |
| **Toggle Character Sheet Menu** | <kbd>K</kbd> |
| **Rest / Wait Menu** | <kbd>T</kbd> |
| **Cast: Familiar** | <kbd>1</kbd> |
| **Cast: Mud Golem** | <kbd>2</kbd> |
| **Crystallize Mana** | <kbd>3</kbd> |
| **Cast: Heal Wounds** | <kbd>4</kbd> |
| **Cast: Regeneration** | <kbd>5</kbd> |
| **Toggle FPS** | <kbd>F3</kbd> |

The current gameplay loop is a simple wave survival.

Orcs will spawn in the basement on game launch and then by a timer.  They will increase in difficulty ending in an Orc Champion who drops a unique item.

A courier will arrive  on a set timer to deliver materials you can use for crafting potions.  Potions require mana crystals which can be created with the "Crystallize Mana" spell.  Clay golems will haul items to the chest on the bottom left corner of z1 for you.

Attributes and leveling are implemented, I am next working on UI/user experience touch ups and then gameloop/systems expansion

You can read more about the development path below.

## Development Path and Goals

So this is a long term passion project like DF or CDDA. The actual development process is broken up into phases, each with their own scope and completion metrics.

Essentially I will be doing semi development cycles for each phase, so phase 1 will have a pre-alpha stage, alpha stage, and beta stage (I will be adding at least a tileset, maybe some audio no promises)

However, once a phase is beta complete I will be moving onto the next phase instead of polishing/gold standardizing.

### Phase 0 - Design - Complete

Creation myth lore is complete and distinguished from Pathfinder.

Combat mechanics are based on Pathfinder 1e with some adjustments/exceptions. The spell slot system has been translated into mana. There is a stamina system similar to CDDA but more forgiving/workable due to magic/enchanted gear/classes (don't worry its not that bad lol)

There is a limb system and an injury system that replaces the crit system, and a blood system meant to compliment the limb/wound system and act as a "total health pool" in a sense.

World mechanics are modeled off of CDDA with a focus on being high fantasy and D&D based. There are many aspects of CDDA that should not be adopted and I am very aware of that lol.

The core gameplay loop is basically just Rimworld + CDDA, with the colony sim aspects being optional if you really don't want that. The game will be playable as a basic roguelike, with towns and dungeons and loot and stats.

It will also not require the player to be magic capable, you can play however you want as long as I've implemented it.

Sound design will be minimal. I want to record my own high quality ambient sounds but this is not a promise lol and I don't know how it will pan out.

Narrative design will be very limited until phase 3 when the map is expanded. I have plenty of ideas and notes but nothing will be implemented until then.

Initial art design is towards the end of phase 1. It won't be a lot, likely just personal touch ups on some free 16x16 and 32x32 assets with generous licenses that I can find.

As you can see I do want to do my own audio/art but I am not an artist and my skills lie elsewhere. We'll see how it goes.

Again, to clarify, I WILL NOT be using AI generated art/audio/assets of any kind. I'd rather have colored squares and silence.

I will focus on an early iteration of modding/player editing after phase 1 is complete.

Multiplayer is planned. To my knowledge it's as simple as detaching tick progression from the player and onto a pulse. Player intents are queued along the existing pipeline AI intents are except stored in a unique player list to allow for queueing multiple actions over multiple ticks.

---

### Phase 1 - Testing Room - Current Phase

Phase 1 is well into development

The highlights of the current systems are:

* **DEFEND THE INN GAMEPLAY LOOP**
* basic inn defense against orc waves followed by dungeon crawling under the inn to kill invading orcs
* involves a friendly courier who drops off supplies on an interval for the player to craft potions


* **BASIC CRAFTING**
* **BASIC HAULING**
* **BASIC SPELL SYSTEM AND SUMMONING**
* **CDDA STYLE POCKET SYSTEM**
* **INTERLEAVED AP/TIME SYSTEM**
* **MODERN MOUSE CONTROLS WITH CLICK DRAGGING AND MOUSE STEPPING**

as well as everything you'd expect like HP/AP/mana/stamina, inventory, items, etc...

current implementations are basic while I broaden the system base

in addition to the above mentioned systems I am working on the following:

* attribute system inspired by D&D
* Leveling and basic classes (warrior and mage to start)
* expanded combat system to simulate limbs and blood, with wounds and debuffs
* expansion to the existing systems
* an advanced inventory management window/system similar to CDDAs
* detaching ticks from player input into a real time system - you can choose how you want to play and also this functionality is the foundation for multiplayer
* and more

---

### Phase 2 - Wizard Tower

The second phase will be a wizard tower colony sim similar to Rimworld. The idea is to expand the map from the Inn to a Rimworld sized map and refactor things as needed. After the phase 1 systems work with the bigger map I will implement Rimworld esque mechanics like building (and dynamic building destruction), more complex entity stats (hunger, morale, sleep), and expanded gameplay loop with raids based on "wealth" and other map events. Also during this phase the existing phase 1 systems will be greatly expanded (more spells, more friendlies, more enemies, items, gear, materials, crafting, etc...)

---

### Phase 3 - Expanded Map

The third phase will be another map expansion and the addition of towns and dungeons. The idea is to create a hand crafted map with specific landmarks and POI in an attempt to create a realistic slice of high fantasy life. I have pages written on lore and world building and a rough idea of how this should look. This phase will have more systems expansions like phase 2 but will mostly focus on exploration expansions. Towns, villages, cities, dungeons, hostile fortresses, and so on. Some of these will be handcrafted but here I will be using procedural generation for some things (villages, bandit camps, and dungeons etc...)

An additional focus of phase 3 is the implementation of the "settlement" and palace manager system. Long story short, I want certain POIs to be living, expanding regions on the map. The actors in these regions should be governed by a palace manager who acts like any AI opponent would in any RTS with the actors as their units. Actors will have their own routines and needs but will also have times when they are idle. The palace manager will then take over and direct them towards settlement needs.

Settlements will also act as behavioral and pathfinding leashes for their inhabitants as well as major pathfinding landmarks for the open world hierarchical pathfinding system.

---

### Phase 4+ - Narrative/Exploration expansion

Once the hand handcrafted map and simulation mechanics are complete and functional it will be time for Narrative expansion, with implementation of world building/mythology/factions. I have ideas for some storylines involving the beings from the creation myth and their plans. Also this phase involves additional exploration expansion with other map regions acting similar to Rimworlds multiple base functionality. Planar travel also offers some fun late game potential.

---

## Design & Technical Rationale

### WHY A HANDCRAFTED MAP

One of the key reasons of the handcrafted map instead of procedural generation is that I want the ENTIRE MAP to be the reality bubble. I don't like the idea of simulation regions being abstracted into simpler forms when the player is not nearby. It took CDDA YEARS to figure out how to make fires in basements go out properly over time or how to not have fresh milk spawn 6 months after the world ended. I don't want to deal with it.

This is the reason for the ECS engine and focus on performance. I do also have ideas for general amortization and queuing systems for non-combat entities, but these are not the same as completely abstracting something into a different state permanently until the player nears.

---

### WHY C++

When people complain about C++ they typically say things like "its unsafe, difficult to learn, and slow to build with."

What you will never hear anybody say about C++ is "it runs slow," so that's reason one.

Reason 2 is source code security.

I initially started with C#, completed the Monogame tutorial, then came to [this section](https://docs.monogame.net/articles/tutorials/building_2d_games/25_packaging_game/index.html?tabs=windows&utm_source=gemini#code-obfuscation)

That and the section below it "The Reality of Modern Society" were the last nails in the coffin for me using C#. I was already annoyed with the garbage collector and restrictions/performance overhead in general.

**tl;dr** - raw C# compile output has basically zero security. Anybody can take your exe, throw it in some decompilation program, and output your source code in almost the format you sent to your compiler. A bunch of metadata (Identifiers, type definitions, external references, control flow statements etc...) is just still there in the IL. You can obfuscate it, but simple ones get cracked and advanced ones have an additional performance cost. You can AOT it, but that has weird stupid restrictions. All of this bullshit while still having to deal with the GC.

No.

So we're using C++ which compiles to machine code and removes this problem almost entirely while ALSO being the inherently faster language.

C# decompilation gives you a basic jigsaw puzzle. These can be solved in an afternoon.

C++ decompilation gives you a jigsaw puzzle where all the pieces are rectangular and you have to carve the connections yourself. Also there's no image on the pieces you have to figure that out too. But you do have all the pieces. (it takes months, years for complex code bases)

You get this security for NO PERFORMANCE COST on an INHERENTLY FASTER LANGUAGE. It's just a little harder to learn lol.

To clarify, I just mean source code protection. I don't care if you crack or pirate my game, it's free right now anyway lol.
