---
title: Environment - Entry design
description: Entry page for Environment design
draft: "false"
date: YYYY-MM-DD
---
# 1. Overview:
The game visual consists of these layers, sorted from bottom to top:
- Background: Change the background art depending on the MC’s location. MC cannot interact directly with this layer (Later)
- Walls: The tile-based layer lies behind MC, mainly supporting decorations and showing different biomes in the game. MC can interact by using some tool (Later)
- Blocks: A main tile-based layer of the game that MC stands on and interacts with.
![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdV1FF9kno4u6rhlSVfNHoceJQAf6isxJw81j0-haFj21fRKjftgGRJJHumlvrJs3jPCGCvCi5FvlnMbb1j0Ux85g--7mhQcjof9S85M7zKVbN_A5JIOneWXKpyS4mlHErI3lq5-g?key=agnXhTnd2Pw57Ikzf0bBJrqo)

**Map size:** The total map size will be 200x200 (tiles). The “surface” width is 20 tiles and the underground is 180 tiles.![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdoFHZm4UgNB7fkbxPnl1ee9oYeZjYuT7Fdy3fakNNeLeBvTPrXuEyqXU-w7yu0BICQ9SIJp50FdW2ustzdkQiNo9GaJm-QbyrU-0jzYIKP6KAClwDCm22TCiikuzOFT3W429YDgQ?key=agnXhTnd2Pw57Ikzf0bBJrqo)

# 2. Level generation:

The current version will manually make a level consisting of both parts using the tilemap editor in Unity.
**Surface:** The surface part is automatically generated when the player makes a new save, with fixed contents:
- Town core: This is the main object that MC must protect, if the core reaches 0 HP, the game ends.
	- The core’s size is 3x5, stay in the middle of the map
	- It has HP (configurable). Only monsters can attack and reduce the core’s HP.
	- Currently, there’s no interaction that player can do with it
- Mine entrance: In the form of a hatch (will always open this version)
	- The hatch size is 5x2, on the right side of the map (near the town)
**Underground:** The Underground part will have its layout automatically generated each time the player enters (PCG for Roguelite, will do later).

# 3. Interactions:
MC interacts with the environment using tools. 
**Quickbar:** Temporarily when inventory is not implemented, the game will have a “quick bar” to switch between items. 
- The bar will be in the top-left corner with 5 slots to switch, using keys 1-5.
- The equipped item will be switched according to the selected keys.
**Pickaxe:** Pickaxe will be in slot 1 of the quick bar and is equipped by default.
- Stats (for making base item attributes): 
	- Type: Tools
	- Attack speed (also animation swing speed): 1 (time/s)
	- Damage (enemies): 15
	- Damage (blocks): 1
	- Item tier: 1 (currently, all blocks are considered tier 1, except “Hard rock”)
- Interactions:
	- Using on air: MC swings the pickaxe, dealing dmg if hits enemies (later).
	- Using, with the mouse cursor on blocks: MC swings the pickaxe, dealing dmg to the targetted block.
**Underground materials:** There’ll be types of “blocks” which are interact-able with the pickaxe. Every block in the game will have these attributes:
- HP: When reaches 0, the blocks will be destroyed
	- Exception: When ore blocks reach 0, it is replaced into a Hard rock
- Tier: WIP
- isOre: When mined, resources will be given to the player.