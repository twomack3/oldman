# Case Study Heroku
1.  Offered Technologies
    1.  Heroku Pipelines
    2.  Heroku CI
    3.  Review Apps
    4.  GitHub Integration
    5.  Release Phase
    6.  Heroku ChatOps
2.  Testing Environment Integration
3.  Use in a Game Developing Scenerio
## Heroku Technology Offerings
Heroku has created technologies to support the concept of continous integration or development.  The ability to make and test changes and mergem into a viable project.  This supports the agile methodologies and I find especially suited to Scrum techniques.
### Heroku Pipelines
According to the Heroku web site, Heroku defines a pipeline as a group of Heroku apps that share a common code base.  Each app in a pipeline represents one of the following steps in a continuous delivery workflow:
* Review - The developer creates a pull request and Heroku creates a 'review app' to allow the testing of the change.
* Development - The developer makes and test changes, when ready the code gets merged with the master branch.
* Staging - After merging with the master branch the 'slug' (compressed and pre-packaged copies of your application optimized for distribution to the Dyno manager) gets 'promoted' from the Review or Development stage to the 'Staging' stage.  After further acceptance testing it gets 'promoted' to Production
* Production - The production environment and deployment.  See [Heroku documentation for Heroku Pipeline](https://devcenter.heroku.com/articles/pipelines) for more details.
### Heroku CI
The Heroku CI a low-configuration test runner that integrates easily with Heroku Pipelines (and so complements Review apps, existing Heroku apps, and our GitHub integrations) that integrates with GitHub, [Heroku documentation for Heroku CI](https://devcenter.heroku.com/articles/heroku-ci).
### Review Apps
Integrated with GitHub to run and code in a pull request as a disposable app on Heroku.  Stake holders can access this app to review the application under development, make suggestions, discuss and manage changes to the code that will later get merged with the code base.  This app also allows for integration tests in the Heroku app as a GitHub branch, [Heroku documentation for Heroku Review Apps](https://devcenter.heroku.com/articles/github-integration-review-apps).  I concur with the Heroku recommendation of only enable Review apps on the development or staging version of the application in order to avoid possible data leaks in the production environment.
### GitHub Integration or GitHub Sync
This product can run tests and if they changes pass can promote the 'slug' after integration with the GitHub, [Heroku documentation GitHub Integration](https://devcenter.heroku.com/articles/github-integration).
### Release Phase
This should get run as a step in 'promoting' a release candidate to production.  This run tests and will failure will cancel the release until the the reason for the failure (code, environment, internet connection) get corrected.  This will help ensure stability and quality of the released product, [Heroku documentation Heroku Release Phase](https://devcenter.heroku.com/articles/release-phase).
### Heroku ChatOps
Heroku ChatOps uses Heroku Pipelines and the 'team communicationstite' Slack to provide the following additional features over a normal Heroku deployment: Heroku will check the required status checks on GitHub to ensure that only code that passed the tests gets deployed, Heroku will notify GitHub that you have deployed your code so that your pull requests will have a record of successful or failed deploys, [Heroku documentation Heroku ChatOps](https://devcenter.heroku.com/articles/chatops).
## Testing Environment Integration
In my opinion Heroku Pipelines offers greatest value when integrated with the game development environments of: Development, QA Environment, Staging and Production.  This assumes the use of GitHub as the version control repository.  I would follow the Heroku recommendation the following stages: review --> staging --> production.  With the use of the Review Apps product the combination of the Development and QA Environment into the Heroku review stage makes perfect sense.  The ability to run automated testing during the 'promoting' of an app to the next stage represents one of the major strengths these technologies offer.

The idea of continous integration fits Agile methodologies and after the establishment of a base (result of first or second scrums).  Adding the app into a Heroku Pipeline and as a GitHup 'master' (could exist as a 'place holder' with no functionality other than it loads and exits) provides a starting point.  The developer or developers making forks by pull requests from the master, as required by the current scrum, when using the Heroku CI and Review Apps triggers the Review Apps functions which provides tracking, discussion and documentation of the changes.  This corresponds to the functions of Development and QA Environment testing environments.

The merging of the completed and tested fork into the master in the GitHub - Heroku environment can start more automated testing before allowing the merge and promotion to the Staging test environment.  Again the use of the auto documentation features assists in tracking, review and modification (if needed) of the application, I feel this corresponds to moving to the Staging test environment used for user validation, training, and a holding area for the product.  As mentioned above Review Apps should not get run when promoting to the production environment.  This promotion should use the Heroku Release Phase and probably the Heroku ChatOps application services during promotion to maintain quality of the product.

Use of the services provided by GitHub and Heroku will help ensure only viable - runnable application get promoted/moved into production.  Heroku Release Phase will stop the move if the build fails to pass the associated tests.
## Use in a Game Developing Scenerio
The use of the GitHug - Heroku environments and application in the creation of the game Time Waster by OldFarts Inc. using Agile - Scrum methodologies.

Scrum 01 - Define game concept and create files, set up project, teams, pipeline and master on GitHub and Heroku sites for the project.

Scrum 02 - Create forks one to develop base scenes and levels, load/splash, game setup, levels, game over and help, another to create player prototypes and movement.  With the use of Heroku Review apps document changes required made and tested in the combined Development and QA Environment upon completion merge the completed and tested code into the master, this will move the master to staging with automated documentation and testing.

Scrums 03 - 05 - Use results of previous scrum to determine new features to add and changes to make to the master.  Create pull requests as required and have Development and QA Environment testing environments for the changes while testing can start and continue on the master in the staging stage.  Use the all documentation to help develop the backlog for upcoming scrums.

Scrums 06 - 08 - Concentrate testing on master in the Staging 'stage' of the pipeline and use the all documentation to help develop the backlog for upcoming scrums.

Scrum 09 - Testing for user acceptance and release of the great game Time Waster.. Use documentation for bugs and features not fixed or implemented, fix all errors that prevent Release App from moving candidate to production.

Celebrate and rake in the cash from the game.
