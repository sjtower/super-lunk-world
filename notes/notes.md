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
1. The room engine does not like solids arranged diagonally, IE:
    X0
    0X 
    X = solid 0 = air
    The engine will fill in one of the air blocks with dirt. You can get around this by placing something like a platform or bones in the air spot.

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
1. You can combine room sections that are defined in other files. For example, if you define a `.shop` section,
    it will combine with the `\.shop` defined in `generic.lvl` and rooms can be pulled from either section
    
### Items and Damsels
1. when trying to leave through an exit door with no floor, the damsel will jump out of your hands at the door and fall

### Notes on specific worlds and levels
1. 1-4
    1. normal entrance must be in 0-2 somewhere
    1. shortcut entrance can be anywhere
1. 4-1, 4-3: Tusks entrance will appear on the path
1. 5:
    1. height can be increased, but bottomlewss pit will always spawn at the same depth
    1. you can spawn liquids, but if any liquid drops off the bottom of the screen, the game will crash
1. 6-2: Ushabti room is required (hallofushabti) and cannot be entirely filled in with dirt.
    1. cannot be sized 1-1
    1. entrance can be covered with dirt
    1. Error displayed if more or less than 100 ushabti's are generated (won't crash)
    1. Increasing the size of the level without altering the ushabti rooms will throw above error
    1. 4 / 4 = 15 normal rooms @ 6 ushabti and one entrance @ 10 ushabti = 100 ushabti 
    1. ushabti room will fill whole level, can figure out how to avoid error with math
        1, EG: 6 / 6 room would be 5 normal rooms @ 2 ushabti each (70 total ushabti) and one entrance with 30 ushabti
    1. hallofushabti takes priority for room size
    1. ushabti dual entrance has 10 ushabtis by default. There are 5 ushabti rooms with 6 ushabti each 
    1. cannot seem to generate big, tall, or wide rooms
1. 6-3: Pleasure Palace entrance can spawn anywhere on or off the path along with treasure room entrance 

### Notes on Traps and Enemies

#### Spikes
1. Can only be placed on dirt, will break upon spawning if placed on minewood, stone, pagoda, platforms etc.

#### Powder Keg (TNT)
1. Will explode if it touches a lit torch (hanging on the wall or thrown by the player)
1. Will explode if dropped any distance
1. Will not explode if placed on top of a PB and pushed over a ledge

#### Upside-down Spikes
1. can be placed anywhere
1. Spring trap can be placed on top

#### Big Spear Trap
1. takes up two tiles, starts from leftmost tile

#### Log trap
1. Log is 5 tiles tall and two tiles wide
1. There must be 6 tiles minimum between the log (T) and the idol (I)
1. The log is held up with special tiles. Normally they surround the top of the log trap, and are destroyed when the player picks up the idol.
    1. Crashes can occur if you cut the corners from the log tiles. It seems like auto fill-in is the issue. 

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
1. will slow down in water and lava
1. will trigger when there is exactly 5 tiles between the player and the crush block 
1. You cannot push a PB on to a moving CB because the PB will bounce upon landing and fall off the CB.
1. Big crush blocks are 2x2 tiles big. Spawn location can vary - placement conforms to surrounding blocks?

#### Quicksand
1. if platform is placed below quicksand, player cannot dop below it

#### Honey
1. can be pushed by crush blocks, push blocks, etc. Even on the ceiling!

#### Elevators
1. you can push elevator if it lands on a PB/TNT

#### Force Fields
1. can block the generator block with TNT, and TNT will not explode

#### Horizontal forcefields
1. cannot spawn directly, only in Tiamat's lair
1. will pass through bone blocks

#### Pipes
1. Blocking a downward opening pipe with a platform will soft-lock the player

#### Vines
1. growable vines can grow through thin ice

### Enemies

1. Imp: You can spawn an imp without their cauldron if you spawn them in a 1-tile high space.
1. UFO: its range is 5 tiles for back & forth routine
1. Olmite:
    1. Will spawn in random stacks of 1-4
    1. Can limit height by placing blocks over the Olmite
    1. If you want one Olmite only, put them on a falling platform with a solid block above
1. Giant Frog: requires a back layer with connected door
1. Quillback
    1. will roll at you when 4-10 blocks away, will jump at you until 4 blocks away, must be looking at you
    1. You can use conveyor belts to control which way he is looking
    1. Conveyor belts will slow/speed him
    1. Honey will slow him significantly
    1. Normally, Quillback's roll will continue as long as he drops in height and destroys some floor?
    1. Won't reset his rolling attack if he doesn't destroy anything
    1. If rolls into a 4-wide hole with unbreakable blocks on both walls, he will bounce/climb all the way up after hitting a wall
    1. not effected by spring traps
1. Olmec:
    1. room 0-0 is unused - use `coffin_unlockable` instead
    1. olmec seems to spawn in vanilla location regardless of placement in the level
    1. You cannot spawn any cavemen 
1. Tiamat:
    1. Does not have a physical hitbox, so things like falling blocks/log trap/TNT will not affect her

# Things to test
1. Entrance/exit on machine big/wide/tall rooms? = NO
1. will oldhunter kill vlad anywhere? Or do we have to meet him somewhere first? Same level? = NO
1. can we use `\.setroom#-#` in any lvl? = NO 
1. `\!purge` ? Multiple `\.setroom` rooms?
1. Will Yang say anything if we put him at an entrance? = NO
1. can I place note? Will it replace crystal idol? = NO

1. can growing climbing poles only spawn in tidepool?

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
1. Falling platforms now trigger when a PB is on them & when another FP hits it
1. sequal: Can your next mod be named "Oliver's Twist"?
    super big path that you need to ride a boulder and get of at certain points

# Setups
1. If you want a corpse on bramble, place FP with pots/rocks on top around the enemy so they won't damage jump away
1. an enemy on a FP will survive a fall into spikes, use to set up single-tile jumps.
    1. sometimes the enemy dies, you can use robots which will not die

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

#### Neo Babylon
1. Path: 21
1. Top: 10
1. Drop: 10
1. Top/Drop: 9
1. Big: 3
1. Wide: 4
1. Tall: 3
