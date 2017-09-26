# Game Title: PLEX - Story mode
#### Test Case Number:
#### Game Build Version Number:
#### Test Case Summary:
### Test Environment:
#### Developemnt - Functional
#### QA - Smoke
#### QA - New Features
#### QA - Regression
#### Staging - User Validation/Play Test
#### Staging - Training
#### Staging - Final Beta
### OS: Windows 98/XP/NT, Linux

## Game Engine
### Loads and starts when the game.
### Locks out other writes to the main game buffer.
### Initialize all of the other drivers.
### Handled user input.
### Display Game Images

## New Game
### Initialize game variables, drivers and start game.
### Character selection.
### Load puzzels for character and level.

## Save Game
### Write valid file for use in later games.
### Over write existing game files else create requred files.
### All data saved and retreived for later game play.

## Load Game
### Load existing game files, else start New Game.

## Play Driver

REQ 1: Only works it story mode.

Rationale: You can’t pause the game in online mode, its constantly running whether the user is there or not.

REQ 2: Pause the game.

Rationale: Keep things from happening while the user is gone.

REQ 3: Resume the game if it has been paused.

Rationale: The user has returned, the game can continue like it was before.

## Menu Driver

REQ 1: Load the appropriate menu when asked.

Rationale: This way the game will always show the correct menu at the right time.

REQ 1: Keep track of where the selector is.

Rationale: This way the game knows what option is being picked from which menu.

## Game Logic

REQ 1: In charge of ALL the game logic, game boards, and game play variables.

Rationale: Logic is separate from graphics so it can be changed easily. In games the graphic never change, only the logic behind them does.

## Graphic Driver

REQ 1: Load all of the game graphics.

Rationale: Game graphics will be ready to go before the user starts playing the game to decrease loading times.

REQ 2: Return graphics to the engine buffer.

Rationale: The engine will be in charge of requesting the appropriate graphics so that they don’t overwrite what’s already on the buffer.

## Music Driver

REQ 1: Load all of the game music.

Rationale: Game music will be ready to go before the user starts playing the game to decrease loading times.

REQ 2: Play music.

Rationale: Will always play the most current music selection.

REQ 3: Stop music.

Rationale: Stop whatever music is currently playing.

REQ 4: Mute music.

Rationale: Turn off the volume for whatever music is playing.

REQ 5: Play music.

Rationale: Will always play the most current music.

REQ 6: Adjust volume if music is playing and not muted.

Rationale: User can turn volume up or down at any time.

## Timer

REQ 1: Start the timer when the game is started.

Rationale: Timer should always be running.

REQ 2: Restart timer.

Rationale: So time can be measured against some pre-determined start point.

## Database Connection Requirements

REQ 1: Only works in build mode.

Rationale: You don’t have to be online in story mode.

REQ 2: Connect to the database.

Rationale: Must be able to connect in order for people to play in build mode.

REQ 3: Return query results in string format.

Rationale: Must be able to return a string result from a query.

REQ 4: Return query results in integer/boolean format.

Rationale: Must be able to return a integer result from a query.

## Database Timeout Driver Requirements

REQ 1: Only works in build mode.

Rationale: You don’t have to be online in story mode.

REQ 2: Check to see how much time has passed since the user last entered some kind of input and log them out if that time surpasses x seconds.

Rationale: Free up database resources by kicking out idle users.



## Non-Functional

REQ 1: PLEX will come with a HTML and CHM instruction manual.

Rationale: The user must be able to understand how to navigate and work the game otherwise they won’t bother playing.

REQ 2: PLEX graphics should be cartoons and appeal to people of all ages, but especially to teenager and pre-teens.

Rationale: This way PLEX will attract an audience who wants to play the game, especially people from the targeted age group.

## Test if Implemented
### Chat feature in build mode.
### Play videos.
#### Load information about movies.
#### Play movie.
#### Pause movie.
#### Stop/skip movie.

### Test Data - Bugs found and recorded
    [Bugs, and Issues]

#### Status:

#### Remarks:

#### Tester By:
#### Test Date:
