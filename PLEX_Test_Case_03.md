# Test Case 

## Test Details

* Test Case ID: PLEX 003
  * 003
* Test Case Name:PLEX Server for Build mode
  * 003
* Component: Build Mode Game Engine component
  * Test the Game Engine server side used to support the Game played in Build mode
* Test Case Designer:
  * Travis Womack
* Creation Date:
  * October 19, 2017
* Modified By:
  * T. Womack
* Modified Date:
  * October 19, 2017
* Requirements Covered:
  1. Provide secure connection to a 5 or more concurrent connections
  2. Severice requests from 5 with no loss in response time
  3. Proved secure file storage for teh game files
  4. Provide user name - password security
  5. Provide storage for puzzels and game files
* Test Description/Purpose:
  1. Start the server application by starting/opening the installed executable file.
  2. First time user must enter a profile: User name, password and character
  3. User must enter a user name and password to access the server and Build versiion.
  4. User can play the Build version of the game with his correct character.
  This test will consider an 80% pass as successful
* Pre-Test Conditions:
  * Intel Celeron 1300MHz with a 256KB cache or better sever running either NT or Linux OS.
  * Five client PCs one each running the following OSs: Windows 98. Windows XP, Windows NT, Ubuto Linux and Red Hat Linux
## Test Steps: 
| # | Description | Expected Result | Check (√) |
| --- | --- | --- | --- |
| 1 | Start Server PLEX application| Loads with our error - allows connections| |			
| 2 | User creates profile on Windows 98| Profile created with errors or lag| |			
| 3 | User creates profile on Windows XP| Profile created with errors or lag| |			
| 4 | User creates profile on Windows NT| Profile created with errors or lag| |			
| 5 | User creates profile on Ubuto Linux Profile created with errors or lag| |			
| 6 | User creates profile on Red Hat Linux| Profile created with errors or lag| |			
| 7 | All Users login at the same time| Logins allowed with out lag| |			
| 8 | User uses invalid password| Login fails| |			
| 9 | User attempts login without a profile| Login fails| |			
| 10 | All user play game at different levels| Game plays normally with no down grading of response time| |
| 11 | All Users quit the game and restart| Require User name and password before allowing game play| |			

## Overall Test Status:
This test case failed due to the inability of the Windows 98 PC to maintain connection during game play or login after quiting the game (no logout) and restarting.

Bug reports submitted:
1. S-145, S-146, S-147 Windows 98 login takes over 8 secinds to complete all other completed in under 3 seconds
2. S-148, S-149, S-150 Windows 98 PC dropped donnection during game play
3. S-151, S-152, S_153 Windows 98 PC could not login after quitting and logging back in - "Only one user with account allowed, access denied."error
## Run History:
| # |	Run Date |	Run By |	Results |
| --- | --- | --- | --- |
| 1 | Oct 19, 2017| T. Womack| Failed - Bug reports: S-145, S-146 and S-147|			
| 2 | Oct 19, 2017| I. Testalot| Failed - Bug reports:S-148, S-149 and S-150|			
| 3 | Oct 19, 2017| Waffal Testers| Failed - Bug reports:S-151, S-152 and S_153|	
