
# Test Plan for: Fireball by international hobo

## Summary Information
From the Frireball game design document (GDD): "Fireball is a budget game for PS2. The player controls a ball of fire, and traverses a landscape made of blocks of different materials. As the player sets fire to these blocks, they grow hotter, and can set fire to more and more different types of blocks. The fireball the player controls can also rise up in height and the hotter the player gets, the higher they can jump in this fashion.

On each field (level) the player has an ultimate goal of igniting the torch (brazier) and thus clearing the field – but the torch is generally positioned at a high point and out of reach. The player must use a combination of platform skills and dynamic environmental features (for instance, by burning the supports under the torch down to the ground) in order to clear the field.

Simple, clean cut graphics and controls combine to give an easy to learn but engaging play experience"

### Environment/User Community
According the GDD This game will come in two different version aimed at two different markets.  The Fireball game will target the casual gamer or impulse buyer, while the Hidama will target the hard core gamern with its unique game play.

### Test Objectives:
Test the subsystems against the GDD stated desired player experience of:
1.  Effortless play coming from a simple control scheme.
2.  Unique experience – the only game to be based around setting fires.
3.  Varied solutions to the mini-puzzles as the player works out the best places to start fires.
4.  Exploration of small environments.
Test the following subsystems:
1.  Avatar which controls the player's ability to move around the landscape
2.  Temperature which controls the the ignitions of blocks in the world abnd how the fire spreads between blocks
3.  Gravity which concerns the collapse of objects and blocks as result for the fires.

### Testing will occur on a PS2 gaming console with standard configuration
### Testing the Avatar subsystem
The player will get represented by a glowing ball fire (GDD) and it will have the follwoing abilities:
1.  Move around the environment. The player turns left and right, and pushes forward to move (relative controls).
2.  Jump up to a (relative) height determined by the heat of the ball. The player will rise rapidly up to their maximum (relative) height, and then slowly descend.
3.  Burning blocks occurs when the player has enough heat to ignite a block and pushes into it for a short time..
4.  Slamming happens after the the player has jumped and causes the fireball to crash down on the first surface beneath it.  This will quickly starrt fires in a wide area slightly hotter than the player’s default temperature.
#### Testing the movement controls as defined in the GDD.
|Test Suite     |Button    |Function                                               |
|---------------|:--------:|-------------------------------------------------------|
|Basic Controls |X(0)   |Jump: The fireball jumps up to its maximum height, then begins to drift slowly down towards the ground.|
|Basic Controls |O(1) or [](2)|Slam: Crash down to ground rapidly and then explode, igniting nearby blocks. If already on the ground, just explodes. |
|Basic Controls | ^(3) |Jump and Top Down View: The fireball jumps, but the camera view tilts to give a top down view. Press again to cancel top down view. (Toggles top down view). |
|Basic Controls | > (Pause)| Pause/Map |
|Basic Controls | (reset) | Hold for 0.5 seconds to begin the current field again |
|Advanced Controls | L1 |Roll Left: Move Sideways to Left i.e. strafe left |
|Advanced Controls | R1 |Roll Right: Move Sideways to Right i.e. strafe right |
|Advanced Controls | L2 |Turn Left: Turn 90 degrees left |
|Advanced Controls | R2 |Turn Right: Turn 90 degrees right |
#### Test the Jump profile
|Action       |Expected result                                                        |
|-------------|---------------------------------------------------------------------------------------------------------------------|
|Start at any height| The ground (0 height) or on a platform (>0 height). 
|Press Jump to begin | The fireball goes up in the air by +x units as a function of current temperature. Jump with Triangle, gives a top down view| 
|Drifting begins| The player descends at the rate of about 1 unit per second. The Triangle to toggle between a top down view and a regular view|
|Pick Target |The shadow of the fireball shows the impact point (target). The shadow of the fireball always shows precisely where the player will land if they press Slam |
|Slam by pressing the correct control| The fireball descends almost instantly to the shadow-point and explodes – possibly igniting everything at this point. The slam fires have a temperature one higher than the avatar’s current temperature|
#### Test Slam profile
Whenever the player slams, they raise every block in a 3 unit spherical radius of the point of impact (or point of explosion if they were on the ground) up to one higher than their current temperature. (The colour of the explosion effect should correspond to the higher temperature). 
If this temperature is high enough to ignite a block, the block begins burning. 
### Testing the Temperature subsystem
### Testing the Gravity subsytem
### Testing Goal conditions
### Testing Chains
### Testing Block System
All game should consist of one or more of the folling block types with the following charasteristics:
Note 
No block may ever be at a heat level higher than that shown in its Burn column or Melt column (whichever is higher). 

|Block Type| Block Colour |Melt Burn | Burn Time | Ignition Time |
|:--------:|:--------:|:--------:|:--------:|:--------:|
|1: Leaf| Green| No |1: Yellow Hot |10 seconds |0.1 seconds| 
|2: Wood| Brown| No |2: Orange Hot |15 seconds |1 second| 
|3: Coal| Black| No |3: Red Hot |60 seconds |1 second| 
|4: Plastic| Pink| 2: Orange Hot |3: Red Hot |15 seconds |1 second| 
|5: Metal| Blue| 4: Blue Hot |5: White Hot |90 seconds |1 second| 
|6: Stone| Grey| 5: White Hot |No| –| –| 
|7: Fire| Red |No |No |– |– |

The following table shows the tints of blocks when they are melted or burning: 

|Block Type |Block Colour |Melted Texture |Meted Tint |Burning Texture |Burning Tint |
|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|
|Leaf |Green |– |– |Burning Leaves |Yellow |
|Wood |Brown |– |– |Burning Wood |Orange |
|Coal |Black |– |– |Hot Coals |Red |
|Plastic |Orange |Molten Plastic |Orange |Burning Plastic |Red |
|Metal |Blue |Molten Metal |Blue |White-hot |Metal |White |
|Stone |Grey |Lava |White |– |– |
 
## For more information on the Fireball game click [here](https://www.gamasutra.com/view/feature/130127/design_document_play_with_fire.php)
