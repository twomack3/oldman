## Product Review of Gyroscope by GyroscopeSoftware
### GyroscopeSoftware a small company started by Adam Fletcher (CEO) and Jonathan Mortensen (Chief Science Officer)
### Review of Gyroscope
Gyroscope represents a game testing tool that not only tests the interface of your game from a player stand point in the game but uses AI learning to play it as a more advanced gamer would as they learn the game.
* This product has 5 main features:

  1.  The AI can learn about individual players and tailor its action recommendations to the individual player and this 'tailoring' evolves during game plays, the AI get better.
  
  2.  This product got written in C# and uses standard interfaces to send commands (game action triggers) to the game.
  * Game controller inputs
  * Ads (boo, hiss)
  * In-App purchases
  * Random number generators
  * Enemy difficulty calibration
  * Boss encounter frequency
  3.  Installs in Unity as a standard asset that you to list your actions (Test case steps)
  4.  Collects all event data required
  5.  Executes experiments behind the scenes and acts on what it learns (adaptive or learning AI)
  6.  Tracks game Key Performance Indicators
  
Used in conjunction with a browser automation tool like Selenium-WebDriver developers have a way to test their game on multiple devices and platforms and tie the results back to specific test cases and bug reports.
  
I think one of the most important parts of this testing software exists in the proprietary AI code. or as developer calls it an 'algorithm of algorithms'.  The developers can define an “observation space” the information the AI can understand.  By defining the “observation space” and the use of standard interfaces developers can test for specific action and see how the player reacts to the actions and rewords or if enough time exists let the AI determine the “observation space”.  If the AI created “observation space” differs from the expected “observation space” then an analysis as to why needs to get performed.
  
By installing as Unity standard asset developers using Unity now have the ability to run these type of AI learning tests at  every step of the development cycle for quicker determination of how changes effect game play interactions.
  
Because this software can perform thousands of test in a cloud environment such as "Google Cloud Platform" and automated data collection of events from the AI, only data analysis tools provide a practical method of analyzing the results of the test.  This stands in contrast to more conventional testing tools such as Selenium-WebDriver which can tie to a specific test case or suite and log results accordingly.
  
The AI can 'create and execute' (weird button presses, no own would do that...) experiments and report on what i 'learns', this may get classified as an documented feature or bug.
  
By tracking developer defined Key Performance Indicators (KPIs) the developer can see how the effects of changes and time on KPIs.
  
### Conclusion
When coupled with a web-based automation tool such as Selenium-WebDriver game developers have a suite of tools that not only allow them to test specific things and track specific bugs in the micro but also in the all together macro environment.  The AI provides an unbiased way to test the game.  The article on the web [How We Built an AI to Play Street Fighter II — Can you beat it?](https://medium.com/gyroscopesoftware/how-we-built-an-ai-to-play-street-fighter-ii-can-you-beat-it-9542ba43f02b) shows how the people at Gyroscope used their software test and develop better AIs for the game Street Fighter II.

You can find more about Gyroscope and their software from their website at [Gyrosope.com](https://games.gyroscope.cc).
