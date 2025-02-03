What was the process before CI?
-
- In the SDLC process, developers used to do infrequent checkins to source code repo which used to result in infrequent build(code integration) of code. When they used to check in, they would realise there're too many conflicts in code and resolving them is time consuming.
- After code check in in SCR, build and release engineer used to integrate the code (build) and deploy on QA/test server after which QA would do the sanity check on the application.
- If bugs were found during sanity check, they were communicated to developers via mail which was then Feedback Loop. If no bugs found, code would be released to production
- **Drawbacks**
  - No constant feedback from dev as we need to wait for deployment and testing to find bugs if any
  - Bug fixing was costly. If test fails, locating and fixing bug was very time consuming as dev has to update entire code base to check and fix the bug resulting in slow SD process

How CI was to the rescue of traditional SDLC process?
-
- Here in CI, developers does ferquent check ins in SCR. As soon as they commit the code, it gets build, test and deploy automatically by jenkins
- If bugs or issues are found, developers are notified immediately to get constant feedback as every commit is tested here.
- **Benefits**
  - Constant feedback is given to dev
  - Effective bug fixing as developers look for code in last commit only not the whole codebase
  - SD process is fast

Explain CI and CD
-
**_Continuous Integration_**
- It is a development practice where developers integrate the code into shared repository frequently, preferably several times a day. Each integration is verified by auto build and test
- Using CI we can detect errors quickly and locate them more easily

**_Continuous Delivery/Deployment_**
- C-del and C-dep are developed as best practices for keeping the application deployable at any point or pushing our main codebase automatically to prod
- C-del is to keep code deployable. Our application needs to have all configirations ready to be pushed to prod. This takes only specific commits to deploy
- C-dep is close to CI and keeps application deployable at any point. It refers to releasing app to test or prod environment if latest version passes all automated tests. Unlike c-del it deploys all commits
- In c-del deploy to prod is manual whereas in c-dep its automated.

- **Benefits**
  - It reduces risk of bugs and defects by early detection
  - As developers share the code here, collaboration between teams is increases
  - Faster iterations as gap between production app and development work is small
  - Faster feedback on business decisions
  - It resuces overhead time and effort

- **CI/CD Principles**
  - Maintain single source code repo
  - Automate the build
  - Make build self testing
  - Keep the build fast
  - Test in preprod
  - Automate deployment

- **CI Practices**
  - Developer checkout the code in private workspace and commit to the remote repo
  - CI server monitors the repo and checks out changes when they occur (SCM polling)
  - CI server builds and runs unit tests and integration test
  - CI server releases deployable artifacts for testing with version
  - Success/failure report is generated
  - Continue to integrate and test the project continuously
