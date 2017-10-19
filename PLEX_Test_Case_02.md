# Test Case 

## Test Details

* Test Case ID: PLEX 001
  * 001
* Test Case Name:PLEX Story mode
  * 001
* Component: Build Mode Game Engine component
  * Test the Game Engine when in Story - single mode - no server
* Test Case Designer:
  * Travis Womack
* Creation Date:
  * October 17, 2017
* Modified By:
  * T. Womack
* Modified Date:
  * October 18, 2017
* Requirements Covered:
  1. First thing to occur when game/application started
  2. Only the game engine can write to the main buffer
  3. Game engine will initialize all drivers necessary for user input
   a. Menu Driver - loads the correct menus at the appropriate time
   b. Graphics Driver displayes game on the user's display
   c. Music Driver starts, plays and stops the music and sdjusts volume as required
  4. Game engine will handle all user input
  5. Game engine will establish the required connection to the game server
  6. Game engine update the user's display as required
* Test Description/Purpose:
  * The tester perform the following steps/tests for each of the following OS: Windows 98
  1. Start the the application by starting/opening the installed executable file.
  2. Using a command/batch file attempt to write into the gaming files
  3. Test the game drivers
   a. Menu Drive the correct menu when asked
   b. Graphics Driver displayes game on the user's display
   c. Music Driver starts, plays and stops the music and sdjusts volume as required
  4. Make sure that the game correctly handels user input.
  5. Make sure the tester can see the results of their input on the display.
  This test will consider an 80% pass as successful
* Pre-Test Conditions:
  * This test requires one PC running Windows 98 

## Test Steps: 
| # | Description | Expected Result | Check (√) |
| --- | --- | --- | --- |
| 1 |Double Click the PLEX icon| Game started without errors, lockup or unintended exit | √|			
| 2 |Run batch file to write into game file |Attempt should give an error and not write | √|			
| 3 |Select the menus |verify selected menu loads correctly | √|			
| 4 |Graphics |Does the display have the correct colors, fonts and resolution |√ |
| 5 |Turn off and on the music |The usic turns off and on as desired | √|
| 6 |Change the music volume|Volume changed as expected| failed |
| 7 |Test the display |Does the game display correctly | √|					
| 8 |Enter correct key combinations |Does the display show the correct data | √|			
| 9 |Enter incorrect key combinations |Did the game handle the error condition without crashing | √|	
| 10 |Move mouse to various fields|Did the fields get selected as expected| √ |

## Overall Test Status:
This test passed wityh an 90% success. the test could not change the music volume only turn it on or off
Submitted bug report # 312 & 313 submmitted on this problem Unable to turn off music
Submitted suggestion on UI redesign for Music controls too confusing for tester


## Run History:
| # |	Run Date |	Run By |	Results |
| --- | --- | --- | --- |
| 1 | Oct 17, 2017 | T. Womack| Unable to turn off music or turn down music|			
| 2 | Oct 17, 2017 | I. Testsalot | Cannot turn down music - failed this test, bug report 215 submitted|			
| 3 | Oct 18, 2017| T. Womack| Figured out UI still cannot turn down music - failed this test, bug report 216 submitted|	
