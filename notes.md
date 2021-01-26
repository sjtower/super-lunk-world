# Level generation observations

1. generic.lvl contains things like shops and kali altars. This file is used in conjuction with the other level files
1. two-room or fewer crashes
1. size of 4-1 with all original tiles can still crash
1. at least one `\.side` room is required
1. `\.path_normal` is not always, but often required
1. Dwelling seems to require both `\.pen_room` and `\.shop`
1. Can safely remove all idol and coffin rooms
1. 2-2 is more stable but still crashes occasionally
1. 3-3 seems stable, no crashes
1. cannot erase contents of generic.lvl
1. It seems like we need to keep all "sections" in generic.lvl, EG `\.altar`, `\.vault`. It seems like IF the level can contain these sections, they are loaded and will crash if not found.
1. QUESTION: They can be replaced with anything you want, they just have to be there?
1. We can trim down `dwelling.lvl` to one room per section
1. Try set size to 5-5 and set `1` for `\-machine_bigroom_chance 1`, `\-machine_wideroom_chance 1`, `\-machine_tallroom_chance 1`
1. Some worlds require a `machine_rewardroom_chance` > 0, and a valid room defined in the `\.machine_rewardroom` section
1. All worlds except 1 require `\.coffin_unlockable	` section
1. `\.coffin_player_vertical` & `\.coffin_player` are not required and can be removed

## Level generation notes

### Sections (not exhaustive)

1. `\.entrance`
1. `\.entrance_drop`
1. `\.exit`
1. `\.exit_notop`
1. `\.side`
1. `\.path_normal`
1. `\.path_notop`
1. `\.path_drop`
1. `\.path_drop_notop`
1. `\.idol_top`
1. `\.idol`
1. `\.machine_bigroom_path`
1. `\.machine_bigroom_side`
1. `\.machine_wideroom_path`
1. `\.machine_wideroom_side`
1. `\.machine_tallroom_path`
1. `\.machine_tallroom_side`
1. `\.machine_tallroom_path`

### Notes on sections/rooms
1. Spelunky 2 does not seem to care if the rooms defined in sections can connect. It seems to operate on assuming that all required pieces for a level are present. Namely, you can go left/right, and you can drop down to a lower screen.
1. "path" rooms are open on the left and right. They can also be open at the top and bottom.
1. "drop" rooms are open on the bottom
1. "notop" rooms are open on the top
1. combinations occur here, so "path_drop_notop" is open on the sides (path), top (notop), and bottom (drop)
1. "side" rooms are placed at outside the main path of a level as mostly dead ends, but can open into other rooms.
1. drop_notop rooms will have "side" rooms on either side, because the main path will go top -> bottom
1. It seems like the required path is never past a "side" room, or past a special room (idol, shop, kali, etc.)
1. "machine" big,wide, & tall rooms function much like regular rooms
1. You can control the chance of these spawning. With a large level, you can force most rooms to be big
1. machine tall rooms are generally open left/right, but have a floor in the middle
1. machine big rooms are generally open on all sides
1. In order to have layer 2 rooms, you need all layer 2 sections in `generic.lvl`
1. Crates and treasure can automatically appear if you have a natural corner in the level
1. Seems like switches and doors are only usable in certain levels (tidepool, vlad's, COG, Eggplant)

### Notes on Traps and Enemies

#### Spikes
1. Can only be placed on dirt, will break upon spawning if placed on minewood, stone, pagoda, platforms etc.

#### Upside-down Spikes
1. can be placed anywhere
1. Spring trap can be placed on top

#### Big Spear Trap
1. takes up two tiles, starts from leftmost tile

#### Log trap
1. Log is 5 tiles tall and two tiles wide
1. There must be 6 tiles minimum between the log (T) and the idol (I)

#### spring trap
1. does not work if placed under a anything but an empty space

#### lava
1. can be pushed through kitty-corner openings via PBs
1. 1 square of lava can cover ~4 tiles in lava
1. lava only burns bushes when on top of bush - bush next to lava survives. We can use this like a bush fuse delay

#### water
1. does not interact with conveyors

#### Falling Platforms
1. small objects can fit under the FP, such as lava or rocks. This way you can set up a path that items can go through but not the player 
1. You can place a FP near the ceiling and it won't be able to be stepped on or grabbed in any way

#### switches / gates
1. Will only work in levels where they are present in vanilla (Tidepool, CoG, Eggplant)
1. Will crash if push block placed on top of gate
1. Will crash if two gates spawn at different heights in the same room
1. Sorceress lasers will trigger switches
1. Mummy locusts will not trigger switches

#### Crush Blocks
1. will slow down in water
1. You cannot push a PB on to a moving CB because the PB will bounce upon landing and fall off the CB.
1. Big crush blocks are 2x2 tiles big. Spawn location can vary - placement conforms to surrounding blocks?

#### Quicksand
1. if platform is placed below quicksand, player cannot dop below it

#### Elevators
1. you can push elevator if it lands on a PB/TNT

### Enemies

1. Imp: You can spawn an imp without their cauldron if you spawn them in a 1-tile high space.
1. UFO: its range is 5 tiles for back & forth routine
1. Giant Frog: requires a back layer with connected door

# Things to test
1. Entrance/exit on machine big/wide/tall rooms?
1. will oldhunter kill vlad anywhere? Or do we have to meet him somewhere first? Same level?
1. can we use `\.setroom#-#` in any lvl? A - no 
1. `\!purge` ? Multiple `\.setroom` rooms?
1. Will Yang say anything if we put him at an entrance?
1. can I place note? Will it replace crystal idol?

## Audio/Visual ideas
1. reskin dog and hampster to be cat variations
1. recolor terrain to emphasize modded content
1. repack the sound bank - include SMW romhack music


# Overlunky

1. If you spawn a door from camp, you will respawn at that level on death/restart

### cannot spawn directly
1. hornedlizard
1. firebug
1. mole
1. monkey
1. bat 

#Misc

1. strings files need to be the same number of lines or the game will crash
1. you do not need to preserve %ls present in the original string


### Room counts

#### Jungle

1. Path: 18
1. Top: 11
1. Drop: 11
1. Top/Drop: 6
1. Big: 2
1. Wide: 10
1. Tall: 3

#### Tidepool

1. Path: 20
1. Top: 11
1. Drop: 13
1. Top/Drop: 6
1. Big: 3
1. Wide: 3
1. Tall: 5