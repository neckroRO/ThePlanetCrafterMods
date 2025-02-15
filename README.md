# ThePlanetCrafterMods
BepInEx+Harmony mods for the Unity/Steam game The Planet Crafter

Steam: https://store.steampowered.com/app/1284190/The_Planet_Crafter/

Guide on dnSpy-based manual patches: https://steamcommunity.com/sharedfiles/filedetails/?id=2784319459

## Version <a href='https://github.com/akarnokd/ThePlanetCrafterMods/releases'><img src='https://img.shields.io/github/v/release/akarnokd/ThePlanetCrafterMods' alt='Latest GitHub Release Version'/></a>

:arrow_down_small: Download files from the releases: https://github.com/akarnokd/ThePlanetCrafterMods/releases/latest

## Supported Game Version: 0.6.007

Public releases are relatively infrequent (once in a few months). I'll do my best to keep my mods up-to-date in case something drastic changes inside the main game.

:warning: I have not tested my mods with the developer/preview/demo releases. They might work just fine or suddenly break.
I don't promise to fix my mods for these versions as they can get quite out-of-sync with the public release.

## Preparation

In order to use my or anyone other's mods, you need to install BepInEx first. The wiki has a guide for this:

https://planet-crafter.fandom.com/wiki/Modding#Using_Mods

When installing my mods, unzip the mod into the `BepInEx\Plugins` directory, including the folder inside the zip file.

You'll have a directory structure like this:

`BepInEx\Plugins\akarnokd - (UI) Pin Recipe to Screen\UIPinRecipe.dll`

Such organization avoids overwriting each others' files if they happen to be named the same as well as allows removing plugin files together 
by deleting the directory itself.


# Mods

### Content

- [Command Console](#feat-command-console)
- [Multiplayer](https://github.com/akarnokd/ThePlanetCrafterMods/wiki/%28Feat%29-Multiplayer)
- [Technician's Exile](#feat-technicians-exile)
- [Space Cows](#feat-space-cows)
- [Plugin Update Checker](https://github.com/akarnokd/ThePlanetCrafterMods/wiki/%28Misc%29-Plugin-Update-Checker)

### Cheats

- [Asteroid Landing Position Override](#cheat-asteroid-landing-position-override)
- [Auto Consume Oxygen-Water-Food](#cheat-auto-consume-oxygen-water-food)
- [Auto Harvest](#cheat-auto-harvest)
- [Auto Launch Rockets](#cheat-auto-launch-rockets)
- [Auto Sequence DNA](#cheat-auto-sequence-dna)
- [Highlight Nearby Resources](#cheat-highlight-nearby-resources)
- [Inventory Stacking](#cheat-inventory-stacking)
- [Machines Deposit Into Remote Containers](#cheat-machines-deposit-into-remote-containers)
- [Minimap](#cheat-minimap)
- [Photomode Hide Water](#cheat-photomode-hide-water)
- [Teleport to Nearest Minable](#cheat-teleport-to-nearest-minable)

### User Interface or Quality of Life

- [Craft Equipment Inplace](#ui-craft-equipment-inplace)
- [Customize Inventory Sort Order](#ui-customize-inventory-sort-order)
- [Don't Close Craft Window](#ui-dont-close-craft-window)
- [Hotbar](#ui-hotbar)
- [Inventory Move Multiple Items](#ui-inventory-move-multiple-items)
- [Magyar Fordítás](#ui-hungarian-translation) (Hungarian translation)
- [Menu Shortcut Keys](#ui-menu-shortcut-keys)
- [Overview Panel](#ui-overview-panel)
- [Pin Recipe to Screen](#ui-pin-recipe-to-screen)
- [Prevent Accidental Deconstruct](#ui-prevent-accidental-deconstruct)
- [Save When Quitting](#ui-save-when-quitting)
- [Show Consumable Counts](#ui-show-consumable-counts)
- [Show Container Content Info](#ui-show-container-content-info)
- [Show Grab N Mine Count](#ui-show-grab-n-mine-count)
- [Show MultiTool Mode](#ui-show-multitool-mode)
- [Show Player Inventory Counts](#ui-show-player-inventory-counts)
- [Show Player Tooltip Item Count](#ui-show-player-tooltip-item-count)
- [Show Rocket Counts](#ui-show-rocket-counts)
- [Sort Saves](#ui-sort-saves)
- [Traduzione Italiana](#ui-italian-translation) (Italian translation)

### Other

- [Reduce Save Size](#perf-reduce-save-size)
- [Support Mods with Load n Save](#lib-support-mods-with-load-n-save)
- [Save Auto Backup](#save-auto-backup)
- [Auto Save](#save-auto-save)
- [Unbrick Save](#fix-unbrick-save)
- [Unofficial Patches](#fix-unofficial-patches)


## (Cheat) Asteroid Landing Position Override

Fixes the asteroid landing position relative to the player by an offset.
This includes asteroids from rockets and random meteor showers.

Note that currently, this may fail if the landing position is determined by the game as invalid. Be in the clear open!

### Configuration

`akarnokd.theplanetcraftermods.cheatasteroidlandingposition.cfg`

```
[General]

## Relative position east-west (east is positive).
# Setting type: Int32
# Default value: 100
DeltaX = 100

## Relative position north-south (north is positive).
# Setting type: Int32
# Default value: 0
DeltaZ = 0
```

## (Cheat) Auto Consume Oxygen-Water-Food

When the Oxygen, Thirst and Health meters reach a critical level, this mod will automatically
consume an Oxygen bottle, Water bottle or any food item from the player's inventory.

Marked as cheat because it is expected the player does these manually.

### Configuration

`akarnokd.theplanetcraftermods.cheatautoconsume.cfg`

```
[General]

## The percentage for which below food/water/oxygen is consumed.
# Setting type: Int32
# Default value: 9
Threshold = 9
```

## (Cheat) Auto Harvest

Automatically harvest grown algae or food from their machines and deposit them into designated containers.

To deposit **Algae**, name any number of containers as `*Algae1Seed` (the `*` is mandatory).

To deposit food, use the following default naming convention:

- **Eggplant** - `*Vegetable0Growable`
- **Squash** - `*Vegetable1Growable`
- **Beans** - `*Vegetable2Growable`
- **Mushroom** - `*Vegetable3Growable`

The naming is case insensitive.

It is possible to change these aliases via configuration. If customized, the `*` is no longer needed. The mod defaults to the naming convention above to remain compatible with previous versions of itself.

### Configuration

`akarnokd.theplanetcraftermods.cheatautoharvest.cfg`

```
[General]

## Enable auto harvesting for algae.
# Setting type: Boolean
# Default value: true
HarvestAlgae = true

## Enable auto harvesting for food.
# Setting type: Boolean
# Default value: true
HarvestFood = true

## The container name to put algae into.
# Setting type: String
# Default value: *Algae1Seed
AliasAlgae = *Algae1Seed

## The container name to put eggplant into.
# Setting type: String
# Default value: *Vegetable0Growable
AliasEggplant = *Vegetable0Growable

## The container name to put squash into.
# Setting type: String
# Default value: *Vegetable1Growable
AliasSquash = *Vegetable1Growable

## The container name to put beans into.
# Setting type: String
# Default value: *Vegetable2Growable
AliasBeans = *Vegetable2Growable

## The container name to put mushroom into.
# Setting type: String
# Default value: *Vegetable3Growable
AliasMushroom = *Vegetable3Growable
```

## (Cheat) Auto Launch Rockets

Rockets crafted via the launchpad are automatically launched.

### Configuration

`akarnokd.theplanetcraftermods.cheatautolaunchrocket.cfg`

```

[General]

## Is the mod enabled?
# Setting type: Boolean
# Default value: true
Enabled = true

## Enable debugging with detailed logs (chatty!).
# Setting type: Boolean
# Default value: false
DebugMode = false
```

## (Cheat) Auto Sequence DNA

Automatically sequences DNA in the Sequencer or Incubator by collecting ingredients
from marked container(s), starting the sequencing process, then depositing the product
into marked container(s).

One marks a container by changing its text field to something specific. By default, the
following naming convention is used (can be changed in the config file):

On the recipe side:
- `*Larvae` - where the various common, uncommon and rare larvae will be searched for.
- `*Mutagen` - where the *Mutagen* ingredient is searched for.
- `*Fertilizer` - where the *Fertilizer* ingredient is searched for.
- `*TreeRoot` - where the *Tree Root* ingredient is searched for.
- `*FlowerSeed` - where the various *Flower Seed* ingredient is searched for.

On the product side:
- `*Butterfly` - where to deposit the created *Butterfly larvae* (all kinds).
- `*Bee` - where to deposit the created *Bee*s.
- `*Silk` - where to deposit the created *Silk Worm*s.
- `*TreeSeed` - where to deposit the created *Tree Seed*s (all kinds).

(Note. Unlike other similar mods, you don't need to start the naming with the star `*` character. The defaults shown are just a convention I use.)

You can name as many containers like this as you want. If a source container does not contain an item,
it will search the next container. If a destination container is full, it will search for the next container.

The *Sequencer* and *Incubator* both require *Mutagen* and you can name different or the same containers where
they would both get their ingredients from.

### Configuration

`akarnokd.theplanetcraftermods.cheatautosequencedna.cfg`

```
[General]

## Enable debugging with detailed logs (chatty!).
# Setting type: Boolean
# Default value: false
DebugMode = false

[Incubator]

## Should the Incubator auto sequence?
# Setting type: Boolean
# Default value: true
Enabled = true

## The name of the container(s) where to look for fertilizer.
# Setting type: String
# Default value: *Fertilizer
Fertilizer = *Fertilizer

## The name of the container(s) where to look for mutagen.
# Setting type: String
# Default value: *Mutagen
Mutagen = *Mutagen

## The name of the container(s) where to look for larvae (common, uncommon, rare).
# Setting type: String
# Default value: *Larvae
Larvae = *Larvae

## The name of the container(s) where to deposit the spawned butterflies.
# Setting type: String
# Default value: *Butterfly
Butterfly = *Butterfly

## The name of the container(s) where to deposit the spawned bees.
# Setting type: String
# Default value: *Bee
Bee = *Bee

## The name of the container(s) where to deposit the spawned silk worms.
# Setting type: String
# Default value: *Silk
Silk = *Silk

[Sequencer]

## Should the Tree-sequencer auto sequence?
# Setting type: Boolean
# Default value: true
Enabled = true

## The name of the container(s) where to look for fertilizer.
# Setting type: String
# Default value: *Mutagen
Mutagen = *Mutagen

## The name of the container(s) where to look for Tree Root.
# Setting type: String
# Default value: *TreeRoot
TreeRoot = *TreeRoot

## The name of the container(s) where to look for Flower Seeds (all kinds).
# Setting type: String
# Default value: *FlowerSeed
FlowerSeed = *FlowerSeed

## The name of the container(s) where to deposit the spawned tree seeds.
# Setting type: String
# Default value: *TreeSeed
TreeSeed = *TreeSeed


```

## (Cheat) Photomode Hide Water

Press <kbd>Shift+F2</kbd> to toggle photomode and hide water as well.

This is marked as cheat because allows picking up objects near the water edge
where they can't be picked up normally.

### Configuration

None.

## (Cheat) Highlight Nearby Resources

Press <kbd>X</kbd> to highlight nearby resources.
Press <kbd>Shift+X</kbd> to highlight and cycle forward through the set of resources configured.
Press <kbd>Ctrl+X</kbd> to highlight and cycle backward through the set of resources configured.

### Configuration

`akarnokd.theplanetcraftermods.cheatnearbyresourceshighlight.cfg`

```
[General]

## Specifies how far to look for resources.
# Setting type: Int32
# Default value: 30
Radius = 30

## Specifies how high the resource image to stretch.
# Setting type: Int32
# Default value: 1
StretchY = 1

## List of comma-separated resource ids to look for.
# Setting type: String
# Default value: Cobalt,Silicon,Iron,ice,Magnesium,Titanium,Aluminium,Uranim,Iridium,Alloy,Zeolite,Osmium,Sulfur,PulsarQuartz,PulsarShard
ResourceSet = Cobalt,Silicon,Iron,ice,Magnesium,Titanium,Aluminium,Uranim,Iridium,Alloy,Zeolite,Osmium,Sulfur,PulsarQuartz,PulsarShard

## Key used for cycling resources from the set
# Setting type: String
# Default value: X
CycleResourceKey = X

## List of comma-separated larve ids to look for.
# Setting type: String
# Default value: LarvaeBase1,LarvaeBase2,LarvaeBase3,Butterfly11Larvae,Butterfly12Larvae,Butterfly13Larvae,Butterfly14Larvae,Butterfly15Larvae
LarvaeSet = LarvaeBase1,LarvaeBase2,LarvaeBase3,Butterfly11Larvae,Butterfly12Larvae,Butterfly13Larvae,Butterfly14Larvae,Butterfly15Larvae

## If nonzero, a thin white bar will appear and point to the resource
# Setting type: Single
# Default value: 5
LineIndicatorLength = 5

## How long the resource indicators should remain visible, in seconds.
# Setting type: Single
# Default value: 15
TimeToLive = 15

```

## (Cheat) Inventory Capacity Override

:warning: **Discontinued.**

This is a very basic override of game inventories, existing and new alike. It tries to not break certain containers
with capacity 1 or 3. Note that the game is not really setup to handle large inventories that don't fit on the screen.
This mod makes no attempts at remedying this shortcoming.

### Configuration

`akarnokd.theplanetcraftermods.cheatinventorycapacity.cfg`

```
[General]

## The overridden default inventory capacity.
# Setting type: Int32
# Default value: 250
Capacity = 250

## Is this mod enabled?
# Setting type: Boolean
# Default value: true
Enabled = false
```

## (Cheat) Machines Deposit Into Remote Containers

For this mod to work, you have to rename your containers. 

For the default naming convention, for example,
to make machines deposit Iron, rename your container(s) to something that includes
`*Iron`. For Uranium, rename them to `*Uranim` (remark: this is a misspelling in the vanilla game which will probably never be fixed as it would break saves). Note the `*` in front of the identifiers.
Identifiers can be any case. 

You can combine multiple resources by mentioning them together: `*Iron *Cobalt`.

Typical identifiers are: 
-`Cobalt`,`Silicon`,`Iron`,`ice`,
`Magnesium`,`Titanium`,`Aluminium`,`Uranim`,
`Iridium`,`Alloy`,`Zeolite`,`Osmium`,
`Sulfur`, `PulsarQuartz`

You can also make the water and methane extractors deposit remotely by naming containers:

- `*WaterBottle1`, `*OxygenCapsule1`, `*MethanCapsule1`

With Insects & Waterfalls update, the mod also works with Silk generators:

- `*Silk`

You can override the default naming convention via the `Aliases` configuration option by listing the resource id and the target naming:

`Aliases=Iron:A,Cobalt:B,Uranim:U`

The identifiers are case sensitive, the target names are case insensitive. You can have the same alias for multiple resources. With overrides, there is no need for the `*` prefix.

You can have as many containers as you like, but they will be filled in non-deterministically.
If there are no renamed containers or all renamed containers are full, the machines
will deposit the resource into their own container, as would they without this mod.

If the mod **Ore Extractor Tweaks** by *Lathrey* is present, its ore generator functionality is integrated with this mod. Specifically, if `configOnlyExtractDetectedOre` is true *and* a machine mines a common ore *and* there is no target inventory for it, the ore is not deposited anywhere.

Note also that machines are slow to mine resources.

### Configuration

`akarnokd.theplanetcraftermods.cheatmachineremotedeposit.cfg`

```
[General]
## A comma separated list of resourceId:aliasForId, for example, Iron:A,Cobalt:B,Uranim:C
# Setting type: String
# Default value: 
Aliases = 
```

## (Cheat) Teleport to Nearest Minable

Locates the nearest **minable resource** or **grabable larvae** (configurable).

- Press <kbd>F8</kbd> to teleport to the nearest **minable resource** or **grabable larvae**. 
- Press <kbd>Shift+F8</kbd> to teleport to the nearest minable resource/larvae and mine/grab it instantly. 
- Press <kbd>CTRL+F8</kbd> to mine/grab the nearest resource/larvae without moving the character. 
- Press <kbd>V</kbd> to toggle automatic mining/grabbing in a certain radius (configurable).

Note that some resources are out of bounds and are not normally player-reachable. You may also
fall to your death so be careful on permadeath!

:warning: Does not currently support Multiplayer-Client mode.

Remark: `Uranim` is a misspelling in the vanilla game which will probably never be fixed as it would break saves.

### Configuration

`akarnokd.theplanetcraftermods.cheatteleportnearestminable.cfg`

```
[General]

## List of comma-separated resource ids to look for.
# Setting type: String
# Default value: Cobalt,Silicon,Iron,ice,Magnesium,Titanium,Aluminium,Uranim,Iridium,Alloy,Zeolite,Osmium,Sulfur,PulsarQuartz,PulsarShard
ResourceSet = Cobalt,Silicon,Iron,ice,Magnesium,Titanium,Aluminium,Uranim,Iridium,Alloy,Zeolite,Osmium,Sulfur,PulsarQuartz,PulsarShard

## List of comma-separated larvae ids to look for.
# Setting type: String
# Default value: LarvaeBase1,LarvaeBase2,LarvaeBase3,Butterfly11Larvae,Butterfly12Larvae,Butterfly13Larvae,Butterfly141Larvae,Butterfly15Larvae
LarvaeSet = LarvaeBase1,LarvaeBase2,LarvaeBase3,Butterfly11Larvae,Butterfly12Larvae,Butterfly13Larvae,Butterfly141Larvae,Butterfly15Larvae

## Press this key (without modifiers) to enable automatic mining/grabbing in a radius.
# Setting type: String
# Default value: V
ToggleAutomatic = V

## The automatic mining/grabbing radius.
# Setting type: Single
# Default value: 90
Radius = 90

## The delay between automatic checks in seconds
# Setting type: Single
# Default value: 5
Delay = 5
```

## (Cheat) Minimap

Display a minimap on the lower left side of the screen.

Press <kbd>N</kbd> to show/hide the minimap.
Press <kbd>Shift+N</kbd> or <kbd>Mouse 4</kbd> to zoom in.
Press <kbd>Ctrl+N</kbd> or <kbd>Mouse 5</kbd> to zoom out.
Press <kbd>Alt+N</kbd> to show/hide/autoscan chests.

Notes
- Uses two static maps: barren and lush, where lush is currently set to show after 200 MTi.
- Currently, this was the best map that I could find and also wouldn't be huge.
- Can't do much about the rotating square, Unity has some UI rendering quirks.
- The current map is from https://map.fistshake.net/PlanetCrafter/ by **I crash at random** on the Steam Guides page https://steamcommunity.com/sharedfiles/filedetails/?id=2786757809


### Configuration

`akarnokd.theplanetcraftermods.cheatminimap.cfg`

```
[General]

## The minimap panel size
# Setting type: Int32
# Default value: 400
MapSize = 400

## Panel position from the bottom of the screen
# Setting type: Int32
# Default value: 350
MapBottom = 350

## Panel position from the left of the screen
# Setting type: Int32
# Default value: 0
MapLeft = 150

## The zoom level
# Setting type: Int32
# Default value: 4
ZoomLevel = 4

## The key to press to toggle the minimap
# Setting type: String
# Default value: N
ToggleKey = N

## Which mouse button to use for zooming in (0-none, 1-left, 2-right, 3-middle, 4-forward, 5-back)
# Setting type: Int32
# Default value: 4
ZoomInMouseButton = 4

## Which mouse button to use for zooming out (0-none, 1-left, 2-right, 3-middle, 4-forward, 5-back)
# Setting type: Int32
# Default value: 5
ZoomOutMouseButton = 5

## If nonzero and the minimap is visible, the minimap periodically scans for chests every N seconds. Toggle with Alt+N
# Setting type: Int32
# Default value: 5
AutoScanForChests = 5

## If negative, the map rotates on screen. If Positive, the map is fixed to that rotation in degrees (0..360).
# Setting type: Int32
# Default value: -1
FixedRotation = -1
```

## (Cheat) Inventory Stacking

Items in inventories now stack. The stack count is displayed on the middle of the item.

Use <kbd>Shift-Left Click</kbd> to move a particular stack of items.

:warning: The game is not meant to be working with stacks of items and I might not have
found all places where this can be bad. Backup your saves!

### Configuration

`akarnokd.theplanetcraftermods.cheatinventorystacking.cfg`

```
[General]

## The stack size of all item types in the inventory
# Setting type: Int32
# Default value: 10
StackSize = 10

## The font size for the stack amount
# Setting type: Int32
# Default value: 25
FontSize = 25
```

## (Perf) Load Inventories Faster

:warning: **Discontinued, now part of the vanilla game.**

This speeds up loading the game when there are lots of containers or (modded) containers have a lot of items.

### Configuration

None.

## (Fix) International Loading

:warning: **Discontinued, now fixed in the vanilla game.**

The game saves the beacon color information in a localized manner that crashes the game on a different windows locale. This mod fixes this by patching the color parsing so it accepts comma and colon as decimal separator.

### Configuration

None.

## (Fix) Unbrick Save

The mod prevents the game from crashing in case the save contains an unplaceable object (often added by 3rd party mods).

Current fixes:
- None.

Previous fixes
- Remove objects that can't or shouldn't be built as the game has no visual assets for them. **Fixed in game version 0.4.014**
- Prevent the load screen from crashing when a save is truncated (these are beyond repair). **Fixed in game version 0.4.014**

### Configuration

None.

## (Fix) Unofficial Patches

A mod that hosts the unofficial patches for the game. Eventually, these patches may end up becoming vanilla fixes.

Current fixes:
- Scroll the File List screen from whereever the mouse is currently at.


### Configuration

None.

## (Feat) Space Cows

Place a Grass Spreader *(2 Water, 1 Magnesium, 1 Aluminium, 1 Lirma Seed)* and a **Space Cow** will appear.

Every 2 minutes, the Space Cow will produce 1 *Water*, 1 *Astrofood* and 1 *Methane Capsule*. 
Open her "inventory" and take them out. She won't produce more until then.

In addition, she will also add 60 grams to the *Animals* component of the Terraformation Index.

Why does it have a helmet? She dislikes your atmosphere.

:information_source: Since a Space Cow is not a machine or a grower, the various auto-gather/auto-deposit mods won't work.

### Configuration

`akarnokd.theplanetcraftermods.featspacecows.cfg`

```
[General]

## Is the mod enabled?
# Setting type: Boolean
# Default value: true
Enabled = true

## Enable debugging with detailed logs (chatty!).
# Setting type: Boolean
# Default value: false
DebugMode = false
```



## (Perf) Reduce Save Size

This mods the save process and removes attributes with default values from the `WorldObject`s, reducing
the save size. These attributes are automatically restored when the game loads.

The save remains compatible with the vanilla game so it will still work without this mod (but will be
full size again).

### Configuration

None.

## (Save) Auto Backup

When saving the game, this mod will automatically make a backup copy (optionally compressed) in a specified directory.
You can also control how many and how old backup saves to keep in this directory per world.

Start the game once so you get the default config file `BepInEx\config\akarnokd.theplanetcraftermods.saveautobackup.cfg`.
Quit, then open this file and set `OutputPath` to an **existing directory**. Example

```
OutputPath = c:\Temp\ThePlanetCrafterBackup\
```

Leave `OutputPath` empty to disable the backup process.

Files are saved based on the name of your world plus a timestamp:

- `Survival-9_backup_20220523_115024_255.json.gz`
- `Survival-9_backup_20220523_115024_255.json`

### Configuration

`akarnokd.theplanetcraftermods.saveautobackup.cfg`

```
[General]

## The path where the backups will be placed if not empty. Make sure this path exists!
# Setting type: String
# Default value: 
# c:\Temp\ThePlanetCrafterBackup\
OutputPath = 

## Compress the backups with GZIP?
# Setting type: Boolean
# Default value: true
GZIP = true

## If zero, all previous backups are retained. If positive, only that number of backups per world is kept and the old ones will be deleted
# Setting type: Int32
# Default value: 0
KeepCount = 0

## If zero, all previous backups are retained. If positive, backups older than this number of days will be deleted. Age is determined from the file name's timestamp part
# Setting type: Int32
# Default value: 0
KeepAge = 0

## If true, the backup handling is done asynchronously so the game doesn't hang during the process.
# Setting type: Boolean
# Default value: true
Async = true
```

## (Save) Auto Save

Saves the game automatically. You can configure the save period via the config file (default 5 minutes). You can use fractions such as
`0.5` to save every 30 seconds.

### Configuration

`akarnokd.theplanetcraftermods.saveautosave.cfg`

```
[General]

## Save delay in minutes. Set to 0 to disable.
# Setting type: Single
# Default value: 5
SaveDelay = 5
```

## (UI) Customize Inventory Sort Order

Specify the order of items when clicking on the sort all button in inventories.

### Configuration

`akarnokd.theplanetcraftermods.uicustominventorysortall.cfg`

```
[General]

## List of comma-separated resource ids to look for in order.
# Setting type: String
# Default value: OxygenCapsule1,WaterBottle1,astrofood
Preference = OxygenCapsule1,WaterBottle1,astrofood
```

## (UI) Prevent Accidental Deconstruct

When deconstructing, hold the accessibility key (default CTRL) too to prevent accidental deconstruction with a plain
left click.

The accessibility key is a vanilla feature, configurable in the game's settings menu.

### Configuration

`akarnokd.theplanetcraftermods.uideconstructpreventaccidental.cfg`

```
[General]

## Is the mod enabled?
# Setting type: Boolean
# Default value: true
Enabled = true
```


## (UI) Don't Close Craft Window

When crafting an item, <kbd>Right Click</kbd> to not close the crafting window.

Since vanilla **0.4.014**, there is an accessibility key (<kbd>CTRL</kbd> by default) which does the same as this mod.
However, it does not update the tooltip currently, but this mod does fix that.

### Configuration

None.

## (UI) Grower Grab Vegetable Only

:warning: **Discontinued. The vanilla game now grabs the vegetable only.**

When looking at a grown vegetable in a Grower, hold <kbd>Shift</kbd> while clicking
the vegetable itself to not take the seed, so it can immediately grow the next vegetable.

### Configuration

None.

## (UI) Hide Beacons in Photomode

:warning: **Discontinued. Fixed in the vanilla game.**

When using the photomode (<kbd>F2</kbd>), this mod will hide the user placed and colored
beacons.

### Configuration

None.

## (UI) Hotbar

This mod adds 9 slots to the bottom of the screen where you can pin buildable objects from the Constuction screen <kbd>Q</kbd>.

On the construction screen, hold the <kbd>1</kbd>..<kbd>9</kbd> number keys while <kbd>Left clicking</kbd> on a buildable item.

On the normal screen (outside any UI), press <kbd>1</kbd>..<kbd>9</kbd> to build that item if you have enough resources for it.

If the mod [**(UI) Pin Recipe To Screen**](#ui-pin-recipe-to-screen) is also installed,
On the normal screen (outside any UI), press <kbd>Shift+1</kbd>..<kbd>Shift+9</kbd>
to pin/unpin the recipe to the item in the particular non-empty slot.

The color and numbers on the top right of the panels indicate how many of that item you can build.

- If the mod [**Craft From Containers**](https://www.nexusmods.com/planetcrafter/mods/9) by aedenthorn is installed and active (toggle via <kbd>Home</kbd> by default), nearby inventories are also considered when showing how many of the selected buildings one can build.

Multi-build is allowed by holding <kbd>CTRL</kbd> while clicking to build something over and over (vanilla feature as of 0.4.011, not affected by this mod).

### Configuration

`akarnokd.theplanetcraftermods.uihotbar.cfg`

```
[General]

## The size of each inventory slot
# Setting type: Int32
# Default value: 75
SlotSize = 75

## The font size of the slot index
# Setting type: Int32
# Default value: 20
FontSize = 20

## Placement of the panels relative to the bottom of the screen.
# Setting type: Int32
# Default value: 40
SlotBottom = 40
```

## (UI) Inventory Move Multiple Items

When transferring items between the player backpack and any container,
- Press <kbd>Middle Mouse</kbd> to transfer all items of the same type (i.e., all Iron)
- Press <kbd>Shift+Middle Mouse</kbd> to transfer a small amount of items of the same type (default 5)
- Press <kbd>Ctrl+Shift+Middle Mouse</kbd> to transfer a larger amount of items of the same type (default 50)

:information_source: The vanilla game now supports transferring all the same type of items via <kbd>CTRL</kbd>+<kbd>Left Mouse</kbd>.

### Configuration

`akarnokd.theplanetcraftermods.uiinventorymovemultiple.cfg`

```
[General]

## How many items to move when only a few to move.
# Setting type: Int32
# Default value: 5
MoveFewAmount = 5

## How many items to move when many to move.
# Setting type: Int32
# Default value: 50
MoveManyAmount = 50
```

## (UI) Overview Panel

Pressing the <kbd>F1</kbd> (configurable) shows an overview panel with the current status of the world, statistics and next unlocks.

### Configuration

`akarnokd.theplanetcraftermods.uioverviewpanel.cfg`

```
[General]

## Font size
# Setting type: Int32
# Default value: 19
FontSize = 19

## The keyboard key to toggle the panel (no modifiers)
# Setting type: String
# Default value: F1
Key = F1
```

## (UI) Show Consumable Counts

Next to the Health, Food and Water Gauges, display the number of consumables of each type
the player has in its inventory.

### Configuration

`akarnokd.theplanetcraftermods.uishowconsumablecount.cfg`

```
[General]

## The font size
# Setting type: Int32
# Default value: 20
FontSize = 20
```

## (UI) Show Container Content Info

When looking at a container before opening it, the tooltip at the bottom of the screen will show how many
items are in there, the capacity of the container and the very first item type.
(Pro tip: store different types of items in different containers)

Example: `Open Container [ 5 / 30 ] Cobalt`

### Configuration

None.

## (UI) Show Grab N Mine Count

When picking up items or mining ore, this mod will show a small information indicator (left side) for what you picked up
and how many of the same item is now in your inventory.

### Configuration

`akarnokd.theplanetcraftermods.uishowgrabnminecount.cfg`

```
[General]

## Is the visual notification enabled?
# Setting type: Boolean
# Default value: true
Enabled = true
```


## (UI) Show Player Inventory Counts

In the bottom left part of the screen, there are some numbers showing the player's position, status and
framerate. This mod will add the current number of inventory items, the inventory capacity and
how many items can be added to it.

Example: `800,0,100:4:60   <[  5  /  30  (  -25  )]>`

### Configuration

None.

## (UI) Show Player Tooltip Item Count

When in an inventory or build screen, in the tooltip of an item, show the number of items of the same
type in the player's backpack.

Example: `Cobalt x 5`

### Configuration

None.

## (UI) Show Rocket Counts

On the Terraformation information screen (one of the large screens), show the number of rockets used for
each type of terraformation effect: oxygen, heat, pressure, biomass, next to the current growth speed.

Example: ` 2 x -----    6000.00 nPa/s`

On the Launch Platform's crafting screen, the number of rockets are shown above each rocket type.

### Configuration

`akarnokd.theplanetcraftermods.uishowrocketcount.cfg`

```
[General]

## The font size of the counter text on the craft screen
# Setting type: Int32
# Default value: 20
FontSize = 20
```

## (UI) Show MultiTool Mode

Shows the current multitool mode as text and icon on the 2D hud. Useful when running the game on lower resolution and the tool's 3D image is cut off.

### Configuration

`akarnokd.theplanetcraftermods.uishowmultitoolmode.cfg`

```
[General]

## Show the current mode as text?
# Setting type: Boolean
# Default value: true
ShowText = true

## Show the current mode as icon?
# Setting type: Boolean
# Default value: true
ShowIcon = true

## The size of the font used
# Setting type: Int32
# Default value: 15
FontSize = 15

## The icon size
# Setting type: Int32
# Default value: 100
IconSize = 100

## The width of the text background
# Setting type: Int32
# Default value: 200
TextWidth = 200

## How transparent the text/icon background should be.
# Setting type: Int32
# Default value: 80
TransparencyPercent = 80

## Position of the text from the bottom of the screen
# Setting type: Int32
# Default value: 30
Bottom = 30

## Position of the text from the right of the screen
# Setting type: Int32
# Default value: 10
Right = 10
```

## (UI) Pin Recipe to Screen

On the various craft screens, use <kbd>Middle click</kbd> to pin or unpin a craftable recipe to the screen.

To unpin all recipes, press <kbd>C</kbd>.

In the panel, the curly parenthesis indicates how many of that item is in the player's inventory.
The `< 2 >` indicates how many of the recipe can be crafted from the given inventory.

Note that pinned recipes can't be saved currently as it requires save modding.

### Configuration

`akarnokd.theplanetcraftermods.uipinrecipe.cfg`

```cs
[General]

## The size of the font used
# Setting type: Int32
# Default value: 25
FontSize = 25

## The width of the recipe panel
# Setting type: Int32
# Default value: 850
PanelWidth = 850

## Panel position from the top of the screen.
# Setting type: Int32
# Default value: 150
PanelTop = 150

## The key to press to clear all pinned recipes
# Setting type: String
# Default value: C
ClearKey = C
```

## (UI) Craft Equipment Inplace

When crafting upgrades to equimpent currently equipped, the newer equipment
will be replaced inplace. This avoids loosing backpack capacity or equipment capacity
for the duration of a traditional crafting step.

Note that the UI will indicate you are missing the equipment as an ingredient but
the crafting action will succeed if the rest of the materials are in your backpack.

:warning: Please make a backup of your save before attempting to use this mod, just in case.

### Configuration

None.

## (UI) Save When Quitting

Automatically saves the game when clicking the "Exit to main menu" button.

### Configuration

`akarnokd.theplanetcraftermods.saveonquit.cfg`

```
[General]

## Is the mod enabled?
# Setting type: Boolean
# Default value: true
Enabled = true
```

## (UI) Sort Saves

Allow sorting the save file list by time or name via clicking on buttons `[ <- ]` and `[ -> ]` or with <kbd>Left arrow</kbd> and <kbd>Right arrow</kbd> on the keyboard.

### Configuration

`akarnokd.theplanetcraftermods.uisortsaves.cfg`

```
[General]

## Sorting mode: 0=default, 1=newest, 2=oldest, 3=name ascending, 4=name descending
# Setting type: Int32
# Default value: 1
SortMode = 1

## The font size used
# Setting type: Int32
# Default value: 20
FontSize = 20
```

## (UI) Teleporter Scroll Targets

:warning: **Discontinued. The vanilla game now has a scrollbar on the teleporter screen.**

This mod allows scrolling the teleporter targets on screen by adding up and down buttons or via <kbd>Mouse scroll</kbd>. You can configure the number of targets shown at once.

### Config

`akarnokd.theplanetcraftermods.uiteleporterscroll.cfg`

```
[General]

## Maximum number of targets to show at once.
# Setting type: Int32
# Default value: 6
MaxTargets = 6
```

## (UI) Hungarian Translation

Patches in labels and enables switching to Hungarian ("Magyar") in the game's options screen. Note that some labels do not change when switching to Hungarian the first time. This is a bug in the vanilla game's UI and can be resolved by restarting the game.

The translation contains partly my own work, partly the translations (already accepted or still pending) provided by the community on https://www.localizor.com/the-planet-crafter/translate?language=5&key=297111 . Some consistency-adjustments were made.

:hungary:

Magyar nyelvűvé változtatja a játékot. A játék beállítások (Options) képernyőjén lévő nyelvi opciók közül a "Magyar" bejegyzést kell kiválasztani. Sajnos néhány felirat nem változik magyarrá az első nyelvváltás alkalmával. Ez egy hiba az eredeti játékban és a játék teljes újraindításával orvosolható.

A fordítás részben saját munka, részben a https://www.localizor.com/the-planet-crafter/translate?language=5&key=297111 weboldalon a közösség által
még nem vagy már elfogadott fordításokat tartalmazza. Néhány fordítás egy picit át lett alakítva a következetesség és konzisztencia érdekében.

## (UI) Italian Translation

Patches in labels and enables switching to Italian ("Italiano") in the game's options screen. Note that some labels do not change when switching to Italian the first time. This is a bug in the vanilla game's UI and can be resolved by restarting the game.

The translation was kindly provided by [Lorenza](https://github.com/LorenzaMX) (Discord: 𝕷𝖔𝖗𝖊𝖓𝖟𝖆#8158).

:information_source: If you find a problem with the translation, please provide such feedback in **English** as I don't speak Italian myself.

:it:

Patch nelle etichette e abilita il passaggio all'italiano ("Italiano") nella schermata delle opzioni del gioco. Si noti che alcune etichette non cambiano quando si passa all'italiano per la prima volta. Questo è un bug nell'interfaccia utente del gioco vanilla e può essere risolto riavviando il gioco.

La traduzione è stata gentilmente fornita da [Lorenza](https://github.com/LorenzaMX) (Discord: 𝕷𝖔𝖗𝖊𝖓𝖟𝖆#8158).


### Configuration

Only diagnostic options. Not relevant for the player.

## (UI) Polish Translation

Patches in labels and enables switching to Polish ("Polskie") in the game's options screen. Note that some labels do not change when switching to Polish the first time. This is a bug in the vanilla game's UI and can be resolved by restarting the game.

The translation was kindly provided by XXXX (Discord: XXX).

:information_source: If you find a problem with the translation, please provide such feedback in **English** as I don't speak Polish myself.

:pl:

TBD

### Configuration

Only diagnostic options. Not relevant for the player.

## (UI) Menu Shortcut Keys

Adds (configurable) keyboard shortcuts to the player's backpack screen, container screens (chests) and certain machine screens (to be expanded later).

The available shortcuts are displayed at the bottom of the screen.

Currently, the following shortcuts are supported:

- Backpack screen
  - Sort backpack (default <kbd>G</kbd>)
  - Sort equipment (default <kbd>T</kbd>)
- Construction screen
  - Toggle tier filter (default <kbd>F</kbd>). (Reminder: there is a new microchip that hides low tier machines if equipped. This key toggles this feature without the need to remove the chip).
- Container screens
  - Take All (default <kbd>R</kbd>) (Not all inventories allow this).
  - Sort backpack (default <kbd>G</kbd>)
  - Sort equipment (default <kbd>T</kbd>)
- Sequencer and Incubator
  - Sort backpack (default <kbd>G</kbd>)


### Configuration

`akarnokd.theplanetcraftermods.uimenushortcutkeys.cfg`

```
[General]

## The font size
# Setting type: Int32
# Default value: 20
FontSize = 20

## Toggle the tier-filter microchip's effect in the build screen
# Setting type: String
# Default value: F
BuildToggleFilter = <Keyboard>/F

## Take everything from the currently open container
# Setting type: String
# Default value: R
ContainerTakeAll = <Keyboard>/R

## Sort the player's inventory
# Setting type: String
# Default value: G
SortPlayerInventory = <Keyboard>/G

## Sort the other inventory
# Setting type: String
# Default value: T
SortOtherInventory = <Keyboard>/T
```

## (Feat) Command Console

When pressing <kbd>Enter</kbd> (configurable), a command window is shown where you can type in commands.

Only accessible if no other ingame dialogs are open.

Type in `/help` to see a list of commands. Type `/help [name]` to show a short description of that command. Most commands give you an usage example if run without parameters.

Notable commands:
- `/tp` - teleport
- `/spawn` - add an item to your inventory

### Configuration

`akarnokd.theplanetcraftermods.featcommandconsole.cfg`

```
[General]

## Enable this mod
# Setting type: Boolean
# Default value: true
Enabled = true

## Enable the detailed logging of this mod
# Setting type: Boolean
# Default value: false
DebugMode = true

## Key to open the console
# Setting type: String
# Default value: <Keyboard>/enter
ToggleKey = <Keyboard>/enter

## Console window's position relative to the top of the screen.
# Setting type: Int32
# Default value: 200
ConsoleTop = 100

## Console window's position relative to the left of the screen.
# Setting type: Int32
# Default value: 300
ConsoleLeft = 400

## Console window's position relative to the right of the screen.
# Setting type: Int32
# Default value: 200
ConsoleRight = 200

## Console window's position relative to the bottom of the screen.
# Setting type: Int32
# Default value: 200
ConsoleBottom = 200

## The font size in the console
# Setting type: Int32
# Default value: 20
FontSize = 20
```

## (Feat) Multiplayer

[See the wiki](https://github.com/akarnokd/ThePlanetCrafterMods/wiki/%28Feat%29-Multiplayer)


## (Feat) Technician's Exile

After reaching 1.1 MTi, soon you'll get some company. Follow the in-game clues in this light expansion of the game's world.

:warning: This is a new territory for me so I suggest making a backup of your save. Also if you build at a certain location of the map, this mod may not work correctly.

### Configuration

None.

## (Lib) Support Mods with Load n Save

This mod alters the loading and saving of the game by parsing/appending custom information based on
registered callbacks. These callbacks can be registered by other plugins and thus they can use this
plugin for save-specific persistency.

Here is an example plugin that utilizes this plugin:

https://github.com/akarnokd/ThePlanetCrafterMods/blob/main/ExampleModLoadSaveSupportSoft/Plugin.cs

### Developer notes

#### Dependency setup

To add a (soft) dependency to this plugin in your own plugin, use the `BepInDependency` annotation
with the guid (`akarnokd.theplanetcraftermods.libmodloadsavesupport`) of this plugin:

```cs
[BepInPlugin(guid, "(Example) Soft Dependency on ModLoadSaveSupport", "1.0.0.0")]
[BepInDependency(libModLoadSaveSupportGuid, BepInDependency.DependencyFlags.SoftDependency)]
public class Plugin : BaseUnityPlugin
{
    const string libModLoadSaveSupportGuid = "akarnokd.theplanetcraftermods.libmodloadsavesupport";

    const string guid = "akarnokd.theplanetcraftermods.examplemodloadsavesupportsoft";
}
```

This way, BepInEx knows to load your plugin after this plugin.

#### Registering callbacks

This plugin uses callbacks to get what to save or notify about what has been loaded for a plugin.

First, locate this plugin via its guid:

```cs
using BepInEx.Bootstrap;

if (Chainloader.PluginInfos.TryGetValue(libModLoadSaveSupportGuid, 
        out BepInEx.PluginInfo pi))
{
}
```

If found, locate the `RegisterLoadSave` method on its instance:

```cs
// public IDisposable RegisterLoadSave(string guid, Action<string> onLoad, Func<string> onSave)

MethodInfo mi = pi.Instance.GetType().GetMethod("RegisterLoadSave",
                   new Type[] { 
                       typeof(string), 
                       typeof(Action<string>), 
                       typeof(Func<string>) 
                   }
);

```

Then, invoke it with your plugin id and the delegates to a load and a save function:

```cs
this.handle = (IDisposable)mi.Invoke(pi.Instance, new object[] { 
    guid, new Action<string>(OnLoad), new Func<string>(OnSave) 
});

//...

IDisposable handle;

void OnLoad(string content) {

}
string OnSave() {

}
```

The handle is there to remove the registration if needed.

```cs
void OnDestroy()
{
    handle?.Dispose();
    handle = null;
}
```

:warning: Please make sure the string you return does not contain the `@` or `|` characters as these are treated by the vanilla game
and this mod as separators.

#### Loading Lifecycle

This plugin will deliver the custom save data (if any) after the `SessionController.Start` of the game
returns control. This way, every vanilla game data should be initialized.

Note that there is no guaranteed order of loading data for different registered plugins.