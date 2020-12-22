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
1. Seems like switches and doors are only usable in certain levels

### Notes on Traps

#### Log trap
1. Log is 5 tiles tall and two tiles wide
1. There must be 6 tiles minimum between the log (T) and the idol (I)


# Things to test
1. Entrance/exit on machine big/wide/tall rooms?
1. will oldhunter kill vlad anywhere? Or do we have to meet him somewhere first? Same level?
1. can we use `\.setroom#-#` in any lvl? A - no 
1. `\!purge` ? Multiple `\.setroom` rooms?
1. Will Yang say anything if we put him at an entrance?
1. can I place note? Will it replace crystal idol?

# Room Ideas
##Dwelling
1. ~~jump on snakes over spikes~~
1. ~~high horned lizard jump (can't spawn lizards :( )~~
1. overhang ledge coyote jump (AKA stupid jump) (jump up past an overhanding ledge, 1 tile)
1. ~~push block puzzle~~
1. ~~arrow trap puzzle/dodge room~~
1. idol room
1. ~~imp jump~~
1. parachute level
1. key escort (volcana can guarantee a key?)
1. ~~look at tall push block puzzle - can we force direction?~~
1. can we trigger from below with death waffle / ufo? ~~Or just UFO?~~
1. multiple log traps in one room (?)
1. ~~Normal platforms over spikes drop~~
1. ~~Falling platform arrow dodge~~
1. ~~Drop on caveman, avoid arrows~~
1. ~~Run jump to send push block down to arrows~~
1. ~~Long spike pit with bones~~
1. ~~Drop rocks into arrows, preserve bone blocks~~
1. ~~Toss at caveman with key~~
1. ~~bunch of bones, don't break them all!~~
1. ~~Grab falling platform, require jump away right when it falls~~
1. ~~throw rock, let out imp, jump on imp~~
1. Falling platform next to push block, have to push a little then jump
1. run under some falling platforms you have to trigger

## Quillback escort
1. require Quillback to get through a bedrock encased exit tunnel
1. push down TNT
1. TNT on crush blocks - send up

##Jungle / Volcana - prefer traps/enemies of these two levels
1. ~~Climbing puzzles with trees~~
1. ~~trap gauntlet - path~~
1. ~~kill imp, drop magma man on falling platform~~
1. don't hit the door switch (can't do in jungle))
1. ~~imp escort~~
1. bow/arrow stand puzzle
1. robot escort with push block / falling platforms / door&switch
1. precise mine excavation
1. throw mine excavation? caveman/yeti?
1. throw rock at door switch / key
1. reflect throw via robots to hit switch
1. jump thru lava elevator
1. lava conveyor loop 
1. PB conveyor / FP / elevator puzzle
1. Don't wake caveman! next to mines/lava
1. monkeys?
1. save caveman / robot with PBs
1. wake hermit crab to hit switch
1. Thin ice to force delay - spikes, spears, lasers, whip away lava
1. mine on FP puzzle/timing
1. lava elevator with trees on either / one side / vines
1. snakes on bramble
1. tiki guys / witchdoctor in spikes
1. choose correct FP -> robot explosion
1. mosquito jump room
1. water fountain / just water gates to extinguish flame
1. push blocks into lava, into side of lava. Can lava burn bushes?
1. throw rock on robot
1. ride giant spiders over bramble
1. ~~ride tusk through spikes~~
1. don't hit any robot!
1. ride lavamander through lava
1. start on bush bridge with lit torch above
1. trees on bushes? Do they break when burned?
1. PB bush burn puzzle
1. witch doctor gauntlet
1. Don't burn any bushes! avoid imp, require player carry torch
1. climb tree, avoid spikes/spears
1. mine bridge/jumps - prevent running with honey? thin ice?
1. whip lava onto bush
1. wide trap gauntlet w/ key
1. put pot on FP -> conveyor -> to trigger tusk
1. layer 2 lava lock - open back door
1. layer 1/2 maze
1. bring crush block down and ride
1. delicate TNT traversal
1. TNT + PB puzzle
1. PB to block spear trap (thin ice?)
1. mine escort? laser traps, lava
1. push TNT through laser traps / imps
1. bones + TNT
1. throw mine at laser trap / lava elevator
1. double leaf bridge with witch doctors

#Olmec
1. Giddyup! Ride olmec through the level! dodge laval, upper-deckers. Don't get crushed!

#Temple / Tidepool
1. give Vlad's cape
1. death waffle guantlet
1. crush block gauntlet / you get a PB for defense / required
1. ice block spring spikes
1. giant frog excavation
1. pipe puzzle, plumbus puzzle

##Neo Babylon
1. mech escort / excavation
1. plasma cannon precise excavation

## Audio/Visual ideas
1. reskin dog and hampster to be cat variations
1. recolor terrain to emphasize modded content
1. repack the sound bank - include SMW romhack music


# Overlunky

1. If you spawn a door from camp, you will respawn at that level on death/restart

## Spwan notes

1. You can spawn an imp without their cauldron if you spawn them in a 1-tile high space.

### cannot spawn directly
1. hornedlizard
1. firebug
1. mole
1. monkey
1. bat 

#Misc

1. strings files need to be the same number of lines or the game will crash
1. you do not need to preserve %ls present in the original string

