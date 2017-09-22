# Case Study Heroku
1.  Offered Technologies
    1.  Heroku Pipelines
    2.  Heroku CI
    3.  Review Apps
    4.  GitHub Integration
    5.  Release Phase
    6.  Heroku ChatOps
2.  Testing Environment Integration
3.  Use in Developing a Game
## Heroku Technology Offerings
Heroku has created technologies to support the concept of continous integration or development.  The ability to make and test changes and mergem into a viable project.  This supports the agile methodologies and I find especially suited to Scrum techniques.
### Heroku Pipelines
According to the Heroku web site, Heroku defines a pipeline as a group of Heroku apps that share a common code base.  Each app in a pipeline represents one of the following steps in a continuous delivery workflow:
* Review - The developer creates a pull request and Heroku creates a 'review app' to allow the testing of the change.
* Development - The developer makes and test changes, when ready the code gets merged with the master branch.
* Staging - After merging with the master branch the 'slug' (compressed and pre-packaged copies of your application optimized for distribution to the Dyno manager) gets 'promoted' from the Review or Development stage to the 'Staging' stage.  After further acceptance testing it gets 'promoted' to Production
* Production - The production environment and deployment.  See [Heroku documentation](https://devcenter.heroku.com/articles/pipelines). for more details.
### Heroku CI
The Heroku CI a low-configuration test runner that integrates easily with Heroku Pipelines (and so complements Review apps, existing Heroku apps, and our GitHub integrations) that integrates with GitHub, [Heroku documentation](https://devcenter.heroku.com/articles/heroku-ci).
### Review Apps
Integrated with GitHub to run and code in a pull request as a disposable app on Heroku.  Stake holders can access this app tho reiew the app in question, make suggestions, discuss and manage changes to the code that will later get merged with the code base.  This app also allows for integration tests in the Heroku app as a GitHub branch,  [Heroku documentation](https://devcenter.heroku.com/articles/github-integration-review-apps).  I concur with the Heroku recommendation of only enable Review apps on the devlopment or staging version of teh application in order to avoid possible data leaks in the production environment.
### GitHub Integration or GitHub Sync
This product can run tests and if they changes pass can promote the 'slug' after integration withthe GitHub, [Heroku documentation](https://devcenter.heroku.com/articles/github-integration).
### Release Phase
This should get run as the a step in 'promoting' a release candidate to production.  This run tests and will failure will cancel the release until the the reason for the failure (code, environment, internet connection) get corrected.  Thsi will help ensure stability and quality of the released product, [Heroku documentation](https://devcenter.heroku.com/articles/release-phase).
### Heroku ChatOps
Heroku ChatOps uses Heroku Pipelines and the 'team communicationstite' Slack to provide the following additional features over a normal Heroku deployment: Heroku will check the required status checks on GitHub to ensure that only code that passed the tests gets deployed, Heroku will notify GitHub that you have deployed your code so that your pull requests will have a record of successful or failed deploys, [Heroku documentation](https://devcenter.heroku.com/articles/chatops).
