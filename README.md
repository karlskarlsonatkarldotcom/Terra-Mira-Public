<img width="1260" height="1000" alt="New Project" src="https://github.com/user-attachments/assets/85b5eaae-1c7b-4c45-b422-f545cb4b2dd0" />

## Summary

Terra Mira is a CDDA inspired high fantasy simulation game with a custom C++ ECS engine based on D&D (specifically Pathfinder 1e) mechanics and lore. It is a 2D grid based game with z-levels and a heavy focus on simulation and automation. The idea is CDDA but high fantasy with D&D inspired combat mechanics/spells/items, expanded NPC control/colony sim mechanics, a much greater focus on NPCs in general, and in depth automation both for the NPCs and player. I am hoping to combine the best aspects of survival simulations and colony sims while addressing what I believe to be the primary issues of both; tedium and performance.

**WARNING**


The game is currently in an engine/mechanics test phase. Graphics are purely functional colored squares while core systems are being built out.


**DISCLAIMER**


I use AI for education and code review.
I do NOT use AI for asset generation or game design.


**IF YOU WANT TO PLAY**

The game is free to download under releases.  Phase 1 will always be free and is intended as a demo.

The highlights of the current systems are:

* **Basic Crafting**
* **Basic automated NPC hauling**
* **Basic spell system and summons**
* **CDDA style pocket system**
* **Interleaved AP/combat system**
* **Modern mouse controls and mouse wheel zoom/stepping**
* **Attribute system inspired by D&D**
* **Leveling system**

as well as most of the basics you'd expect

The current game loop is a defend the inn scenario
* basic inn defense against orc waves ending with a boss wave
* involves a friendly courier who drops off supplies on an interval for the player to craft potions
* survive until the final wave

There is a help card in the game that explains the controls and has more information

<img width="2559" height="1439" alt="image" src="https://github.com/user-attachments/assets/5a0f2f26-5f08-49b8-9fc8-0b5baea0473a" />

**IF YOU WANT TO DISCUSS THE GAME OR ASK ME QUESTIONS**

https://discord.gg/VPCpfkkDzW

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

MULTIPLAYER
------------

So I have multiplayer designed too.  I think it should work but I won't try implementing it until phase 2 is complete.  Here's the gist:

Detaching tick progression from the player and onto a 0.6 - 1 second server pulse.  Player inputs are queued into the intent processing pipeline; the same one NPCs use except stored in a list to allow for queuing multiple inputs.  Intents are processed in strict receive order which eliminates race conditions.  Movement/action conflicts would have existing solutions from NPC work/testing.

Regarding fast forwarding I have two ideas, consensus time skipping and player pawn routines.

Consensus time skipping is the easiest and most straight forward.  There will be times when all players are locked in a long action (sleep, crafting, meditation etc...)  The systems can identify when all players are locked in and can prompt them to increase speed.  All the existing interrupt structure would already exist so that the speed would come back down to 1 when needed.

Player pawn routines is not multiplayer specific but it certainly solves the fast forwarding issue.  I will be working on surfacing the NPC behavior routines to the player for use when wanted. i.e., the player should be able to flip a switch and activate "pawn mode" to automate their character.  With the ECS structure this is literally just component additions.

Further I want to develop tools so that these "pawn modes" can be configured and customized.  For example a breakfast routine that you flip on after waking up that has your character gather food ingredients, cook, eat, clean, organize, and then prompt you for further input.  All of this would take around 6-7 keystrokes in CDDA JUST for the gathering ingredients/cooking/eating part.  Add movement, organizing, storing leftovers and its 20+ keystrokes.  Every time you wake up.

For combat I want to implement a logic waterfall type thing like Dragon Age Origins has.  Simple to start but we'll see how it can be expanded.  This is mostly so that the player can edit their controlled minions/pawns routines and do what they want in combat, but it can make multiplayer combat work in higher game speeds as well.  Or just use it at normal speed why not.

So I think this should work just fine.  Like I said I won't sincerely try to implement any of this until phase 2 is complete but as far as I can tell this should work lol.

---

### Phase 1 - Testing Room - Current Phase

Phase 1 is well into development

in addition to what was mentioned above I am working on the following:

* more items and spells
* expanding the playable area to include a procedural cave dungeon under the basement cave area
* filling that cave dungeon with loot and new, stronger enemies
* expanded combat system to simulate limbs and blood, with wounds and debuffs
* a verbose combat log inspired by Dwarf Fortress
* basic classes and abilities
* an advanced inventory management window/system similar to CDDAs
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

# On phase 3 design and optimization systems
So I have pretty grand plans for phase 3 and I want to outline the systems I have in mind to help keep things fast.

*actor = entity that can act (i.e. NPCs and players)*
# SETTLEMENT BUBBLES
A settlement will have a kind of reality bubble around it that defines its "sphere of influence" and is a function of the # of actors assigned to it and its general wealth.  Actors assigned to that settlement live under its "bubble" and don't need to know what's going on in the rest of the world.  The only things that an actor assigned to a settlement need to worry about are settlement duties and their own well being.  Thus, their awareness of the world map is contained to this bubble entirely.  All of their checks and behaviors run on what is within that bubble; this acts as a leash for intent generation, pathfinding, and crucially, entity ID lookups.

# BATTLEFIELD BUBBLES
Battlefield bubbles work on the same concept and are spawned dynamically when any actor begins hostilities with another.  The size of the bubble is a function of the # of combatants and their combat rating (another system that functions as an effective power level, weighing actual stats vs baseline stats to reflect buffs/debuffs etc...)  These bubbles will exist until only one faction is left standing.  These bubbles will act as leashes in the same way but for the combatants of a specific fight.

# AMORTIZATION  AND QUEUING
Put simply, amortization is just doing things over long periods of time instead of every tick.  For example hunger does not need to be checked every tick it can be checked every minute of in game time, or even 10 minutes.  Non-combat entities probly don't need their health/mana and other non-AP vitals checked every tick, how about every 10 seconds instead?  Non-combat entities also don't need the interleaving AP system; that system really doesn't add much value to non-combat scenarios.  

Pathfinding can be amortized as well.  You can have an entity pathfinds only up to 50 tiles in one tick and then stop, saving the work and finishing the rest of the path next tick.  You can also have a pathfinding queue that goes in order and only processes a certain number of intents before pausing for the tick.  There are A LOT of options here.

So the default for most NPCs would be amortization and a queued processing system.  Full system resolution would only occur for entities in combat.

I think these systems will solve a majority of the performance issues you would expect from the phase 3 goals while also making settlements and battlefields operate in a more controlled and effective manner.

---

## Technical Aspects

# Generational ECS
Generational indexing with a recycling system keeps entity lists clean, unique, and safe.  The high level idea of this system is that it adds an extra dimension to entityIDs to more easily make them unique.  It prevents a very severe issue known as the **Zombie Entity**

With a freelist/recycling system its possible to have an entity be destroyed and then have that entityID be recycled while intents are still targetting the old user of that ID.  This leads to "teleporting effects" as those effects will affect the new entity because it has the old ID the effect was targeting.

Generation is an addition to the EntityID struct that simply adds a 2nd dimension to it, which makes it much more unique.  On entity destruction, the generation of that ID is incremented.

Now the effect sees "ID: 4 GEN: 2"
it knows this new generation of ID 4 is not "ID: 4 GEN 1" and thus the effect fizzles out.

# Interleaved AP/combat system
The game is tick based but each tick is played out in accordance to a strict AP hierarchy.  At the beginning of a turn the entity with the highest AP gets to act.  After that action the entity with the next highest entity gets to act.  If that happens to be the same entity, it gets to act twice before anybody else.  This cycle repeats until all entity AP is spent and then the tick is over.

In this system AP generation is speed and AP max is initiative basically.  It allows for interrupts and multi-attacks based on speed.

# Flattened arrays and scratchpad pathfinding
Flattened arrays are contiguous in memory and allow for efficient A* traversal between z levels.  Gridspace (the games hidden 3D lattice of nodes on which the actual tiles are drawn on) is flattened into a 1D array using this equation,

```cpp
(x + (y * GRID_WIDTH) + (z * GRID_AREA));
```

A good visual aid for this is those plastic multiplication blocks from elementary school.  You had ones that were planes, rows, and singles.  The planes would be separated into individual tiles with grooves but still connected overall, forming a tiled plane.

So to visualize this, imagine stacking 10 of those planar shaped things on top of each other.
z here is sifting through those planes.  z = 4 has you skipping the first 4 planes from the bottom to land on the 5th plane. (because of indices starting at 0)

y here is sifting through the rows within that plane, from the top.  so y = 5 would have you skip the first 5 rows within that plane from the top, landing on the 6th row.

x here is moving you tile by tile within the y axis row, moving right from x = 0.  so x = 7 would have you skip 7 tiles to the right and land on the 8th tile.

This is how gridspace is stored in memory.

Regarding the scratchpad, normally A* has to dynamically allocate during its processing.  Dynamic allocation involves talking to the OS and searching for adequate memory.  The size of my gridspace is explicitly known which allows us to pre-allocate a scratchpad of the exact needed size for A* to use instead of dynamic allocation.  This avoids dynamic allocation entirely.

Also because of the single allocation the scratchpad is one contiguous pieces of memory.

Oh also it's flattened just like gridspace so directly checking a node is O(1) lol.

# Sparse Sets
```
m_Sparse (Index = Entity ID):
Index:  [ 0 ]   [ 1 ]   [ 2 ]   [ 3 ]   [ 4 ]   [ 5 ]   [ 6 ]   [ 7 ]  ... [ 9999 ]
Value:  [NULL]  [NULL]  [NULL]  [ 0 ]   [NULL]  [NULL]  [NULL]  [ 1 ]  ... [ NULL ]
                                  │                               │
                                  └──────────────┐ ┌──────────────┘
                                                 ▼ ▼
m_Dense (Contiguous components):        [ Health #1 ] [ Health #2 ]
                                Index:      [ 0 ]         [ 1 ]
                                Entity:    Entity 3      Entity 7  <-- (Tracked by m_DenseEntities)
```

So the way this works is that when a component is added to an entity, that entity will be added to the corresponding sparse list index.  The index of that entry on the sparse set is the EntityID.  You can see above that entity 3 is given index 3 on the sparse, and entity 7 is given index 7.

Then there are two dense arrays, one for the component data and one for the entity ID.  These correspond with each other and work on a stack system which ensures contiguity.  New entities are placed directly next to old ones.

On component removal, the last entity in the lists information is copied into the index of the destroyed entity and the last element is popped off of the dense arrays.  So in the above example, if entity 3 lost its health component then entity 7s information would be copied into index 0 of the dense arrays and element 1 of these arrays would be popped off (vector size - 1)

And that's it; it functions entirely off of component addition and removal.  Previously I had a static 10k vector which had to be completely iterated through each time a system needed to process entities.  This brings the number of iterations down from a guaranteed 10k to the number of active components (currently maybe 20 - 40 at any given time).  Individual entity lookups like "does this entity have mana?" are now O(1) which is basically one step away from free.

## Whys

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

Nah.

So we're using C++ which compiles to machine code and removes this problem almost entirely while ALSO being the inherently faster language.

To clarify, I just mean source code protection. I don't care if you crack or pirate my game, it's free right now anyway lol.
