What was the process before CI?
-
- In the SDLC process, developers used to do infrequent checkins to source code repo which used to result in infrequent build(code integration) of code. When they used to check in, they would realise there're too many conflicts in code and resolving them is time consuming.
- After code check in in SCR, build and release engineer used to integrate the code (build) and deploy on QA/test server after which QA would do the sanity check on the application.
- If bugs were found during sanity check, they were communicated to developers via mail which was then Feedback Loop. If no bugs found, code would be released to production
- **Drawbacks**
  - No constant feedback from dev as we need to wait for deployment and testing to find bugs if any
  - Bug fixing was costly. If test fails, locating and fixing bug was very time consuming as dev has to update entire code base to check and fix the bug resulting in slow SD process

-------------------------------------------------------------------------------------------------------------------------------------------------

How CI was to the rescue of traditional SDLC process?
-
- Here in CI, developers does ferquent check ins in SCR. As soon as they commit the code, it gets build, test and deploy automatically by jenkins
- If bugs or issues are found, developers are notified immediately to get constant feedback as every commit is tested here.
- **Benefits**
  - Constant feedback is given to dev
  - Effective bug fixing as developers look for code in last commit only not the whole codebase
  - SD process is fast
-------------------------------------------------------------------------------------------------------------------------------------------------

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
 
-------------------------------------------------------------------------------------------------------------------------------------------------

What is Jenkins and how it is used for CICD?
-
- Jenkins is an open-source automation server that helps developers build, test and deploy software efficiently. It is widely used in DevOps for CI/CD. It usually executes set of predefined steps
  e.g :- Compile Source code - Build JAR - Deploy to Websphere - Run test cases
- Execution for steps here can be time/event based.
- It allows to continuously deliver our application by providing powerful ways to define build pipelines. Also allows to monitor execution of steps and allows to stop process if any of the step fails. Can also send notifications for success/failure
- Jenkins by supporting all SDLC process automates build and tests at rapid rate,
- **Workflow** 
  - Code commit to SCR
  - Jenkins detect change and triggers build
  - Code is compiled, tested and packaged
  - If test pass, jenkins deploy application to staging or prod
  - Feedback is sent to developers for success/failure

- Jenkins achieve the CI with the help of plugins and improves SDLC process
- **_Features of Jenkins_**
  - **CICD** :- Automates code deployment and integration, reducing manual effort
  - **Plugin support** :- Plugins are the interfaces which allows jenkins to talk to other tools. Jenkins offers vast ecosystem of plugins to integrate with Git, docker, K8S, ansible
  - **Pipeline as code** :- Jenkins support scripted and declarative pipelines for better automation and version control
  - **Distributed builds** :- Jenkins can distribute workloads across multiple machines to improve efficiency

-------------------------------------------------------------------------------------------------------------------------------------------------
 
Explain Jenkins Distributed architecture
-
- Jenkins follow master slave architecture to distribute workloads efficiently.
- Beyond threshold, one jenkins instance is not enough to run all your jobs. So master-slave architecture allows jenkins to scale, handle multiple jobs simultaneously, by delegating tasks to multiple agents

- **_Jenkins Master (Controller)_**
  - Master node is central component responsible for managing jenkins config, scheduling build jobs, assigning jobs to agents, monitoring agents and build execution.
  - It doesnt execute builds itself in large-scale setup
  - Master instance is responsible for managing slaves

- **_Jenkins Slave (Agent)_**
  - It handles all requests from master. Slaves can be on different OS
  - Executes build jobs assigned by master
  - Runs tests, compiles code and pckage apps
  - Reports job status back to master

- **Workflow**
  - Chnages are pushed to repo by dev
  - Jenkins master detects changes and triggers pipeline job as per webhook or SCM polling
  - Master assigns job to agents based on labels, workload and job config
  - Agent executes build - Compiles code, run tests and deploy artifacts
  - Agents send results back to master using logs

- **_Jenkins Master-Slave communication_**
  - **SSH** :- For linux based agents
  - **Docker containers**
  - **K8S Agents** :- Dynamic scaling with cloud infrastructure

-------------------------------------------------------------------------------------------------------------------------------------------------
 
Explain Jenkins dashboard and its configurations
- 
- Jenkins dashboard is the central hub where we can configure, monitor and manage jenkins jobs, nodes, executors, builds, plugins

Jenkins Jobs
-
- Jenkins Job represent single task or process in jenkins. It could be build, test, deployment or any automated task
- To create job, go to "New Item". Choose job type from Freestyle, pipeline, multi-branch pipeline, maven project,etc
      
![image](https://github.com/user-attachments/assets/0f421fa6-f3fe-4fbd-acac-2258565fcf37)
![image](https://github.com/user-attachments/assets/77c65eb3-686d-4c61-b4cd-3f6bea4b2b4b)

- To configure job, go to configure option

![image](https://github.com/user-attachments/assets/cc7fcd71-dc09-4bc9-a4b3-cf6095e77d1a)

  - In configure we can do settings such as :-
    - **Source Code management** :- Integrate with VCS like Git,SVN
    - **Build triggers** :- Define when the jobs should run (On commit, scheduled, manual trigger)
    - **Build steps** :- Specify commands or scripts to be executed during build (run shell commands, etc)
    - **Post build actions** :- To define actions that happen after build completion. Includes sending notifications, archiving artifacts, trigger other jobs
   
![image](https://github.com/user-attachments/assets/b2971198-79c9-43b3-841a-d9d1099e0856)
![image](https://github.com/user-attachments/assets/292f03d0-fbb3-462b-8a05-0b7fe4233187)
![image](https://github.com/user-attachments/assets/48cb8f36-36e9-4ec7-a8b3-75fcc60e343a)

Jenkins Nodes
-
- Nodes are machines where jenkins runs jobs. The jenkins master runs on the main server, while additional machines are slaved to distribute build workload
- To configure jenkins nodes
  - Go to manage jenkins --> add new node --> Configure node (Define remote dir, usage, launch method, availability)
 
![image](https://github.com/user-attachments/assets/d9ccf8d3-c721-4284-8df9-b8cfc9509e1f)
![image](https://github.com/user-attachments/assets/227f24f9-5ee1-4fab-beb7-a06c89561cf8)

Jenkins Executors
- Executors are computational resources available on node (master or slave) that actually run jenkins job. A node can have one or more executors which allows parallel execution of multiple tasks
- To configure executors
  - When adding node, define no of executors
  - On each node we can specify how many executors are available. (4 executors means node can run 4 jobs at a time)
  - We also can set resources like CPU, memory to handle specified no of executors

Jenkins Builds
-
- Build represents specific execution of jenkins job. Its where all tasks defined in job take place
- On jenkins we can see list of jobs inside which we can see history of builds

![image](https://github.com/user-attachments/assets/a6e18486-36eb-4c93-ad8f-0e89467c14fb)

- Each build has :-
  - **Status** :- to check the success/failure
  - **Console output** :- Detailed logs of build. Useful for debugging issues
  - **Artifacts** :- Files generated by build saved for later use

- Build configuration :- Under manage jenkins - configure system, we can configure global settings for builds such as default directories, security settings

- Trigger Builds :- This can be done manually (Build now) or autonatically like:-
  - **SCM Triggers** :- Code commit resulting in build
  - **Scheduled Builds** :- Using cron syntax we can specify build timing
  - **Triggered by other jenkins jobs** :- Like post build action

 ![image](https://github.com/user-attachments/assets/a27fcd93-d355-45d3-bbe3-5be3e5b2bcf9)

Jenkins Plugins
-
- Plugins extend jenkins capabilities, enabling integration with various tools, systems and additional functionality like code quality analysis, notifications, version control. Used to integrate jenkins with other tools of SDLC
- To configure plugins :- Manage jenkins - Managa plugins - Install plugins from available tab

-------------------------------------------------------------------------------------------------------------------------------------------------

Explain Manage Jenkins 
-
1. **_Configure System_**
- In jenkins configure system page allows to set up and manage global settings for jenkins. These configurations define how jenkins behaves and interacts with tools, services and resources
  - **Home dir** :- location where all jenkins information is stored
  - **System message** :- To boradcast message to all users of jenkins instance which is displayed on dashboard
  - **No of executors** :- Max. no of jobs that we can run in parallel on single instance
  - **Quiet period** :- Duration is sec jenkins has to wait before starting new job
  - **SCM Checkout retry count** :- Jenkins while connecting to SCR, it specifies max no of retries jenkins should make if it fails
  - **Restrict project naming** :- To define all jobs should contain specific keywords
 
![image](https://github.com/user-attachments/assets/a6a57f5f-6050-4139-9376-5ca5e773ef60)

  - **Jenkins URL** :- Base URL jenkins uses to generate links in notifications, emails and web interface (http://localhost:8080/)
  - **Extended email Nofitications** :- To send emails with build status

2. **_Configure global security_**
- Using this we can ensure our jenkins instance is secure, especially when its accessible over network
- We can use Security Realm (Authentication) to define how jenkins will authenticate users. We can do this by any of below:-
  - **Jenkins own user DB** :- Allows to manage users and passwords directly in jenkins. We can manually add users and assign roles
  - **LDAP** :- Integrate with LDAP server to authenticate users

![image](https://github.com/user-attachments/assets/5e76d88b-b5e4-4f79-b289-43981a92430e)

- Authorization controls what users and groups can do with jenkins
  - **Matrix based security** :- Provides fine grained control over permissions. Assign specific permissions to diff users or groups
  - **Role based strategy** :- Allows assigning specific roles to different set of permissions
  - **Project based matrix authorization** :- We can define permissions for each project, providing more granular control over who can access which jobs
  - **Anyone can do anything**

![image](https://github.com/user-attachments/assets/5e83ddba-ab08-454d-aab4-1fbd713fb086)

- **Enable CSRF Protection (Cross site Request Forgery)**
  - Prevents malicious users from tricking authorized users into performing unintended actions

3. **_Manage Plugins_**
- To install, enable plugins

4. **_System Information_**
- Displays list of current java system prop and env variables

5. **_System Log_**
- To view Jenkins log files in real time to troubleshoot

![image](https://github.com/user-attachments/assets/bf945a63-6729-4de2-a0d8-62440e292333)

6. **_Load statistics_**
- Displays graphical data on how busy jenkins instance is in terms of no of concurrent builds and length of build queue which gives idea on how long our job need to wait before getting executed
- It provides idea if extra build nodes are required

7. **_Manage Nodes_**
- For jenkins distributed architecture we can setup nodes as per requirement

8. **_Manage Users_**
- Setup new users, delete or modify existing

![image](https://github.com/user-attachments/assets/253158e7-b073-4a9e-b101-aa3234b62262)

- **Build Executor status** :- If we've set 2 executors and run 3 jobs, 3rd job will be in queue till one of the first 2 gets completed
- **Build queue** :- Shows all build jobs which're triggered but are qaiting in queue to get executed

![image](https://github.com/user-attachments/assets/9b80d8af-d821-493c-9f44-f30cc6fb613e)

-------------------------------------------------------------------------------------------------------------------------------------------------

Explain user and role management in Jenkins
-
- Jenkins provides flexible user and role management system that ensures secured and controlled access to the system. It consists of 2 components

1. **_Security Realm (Authentication)_**
- It handles authentication, verifying user identity before granting access. Jenkins support multiple authentication methods
  - **Jenkins own user DB** :- Create users manually. Passwords asre stored internally
  - **LDAP** (Lightweight Directory Access Protocol) :- Integrates with corporate directory services. Users authenticate using their existing company credentials
  - **SSO and OAuth** :- Supports authetication via Google, Github. Useful for large organizations with SSO user management (Charter)
  - **External authentication (via plugins)** :- Integrates with security providers like SAML, OpenID, Crowd

2. **_Authorization (Access Control)_**
- After authentication, jenkins defines what users can do through authorization strategies
  - **Anyone can do anything** :- Security risk for sensitive environments
  - **Logged in users can do anything** :- Only authenticated users have full control. Anonymous users have no access
  - **Matrix based security (for enterprises)** :- Fine grained permissions at user/group level like read, configure, delete
  - **Role based strategy (Best for large teams)** :- Provides role with predefined permissions. Assigns users/groups to roles based on responsibilities. Requires "Role based auth strategy plugin"
 
- Implementing RBAC in Jenkins
  - Install Role based Auth strategy plugin
  - **Enable role based strategy** :- Manage jenkins - Configure global security - Role based auth
  - **Define roles** :- Manage and assign roles - Assign roles
  - **Assign users/groups to roles** :- Add users to respective roles under assign roles

-------------------------------------------------------------------------------------------------------------------------------------------------

Explain role based strategy for users in jenkins
-
- In project based matrix, if we've 100's of users, it will be difficult to manage access of all
- Role based auth strategy allows admins to define roles with specific permissions and assign them to users and groups. It provides fine grained access control making it ideal for large teams managing multiple projects

- **To enable RBAC** :-
  - Install plugin named Role based auth strategy, then restart jenkins
  - Enable role based security :- Configure global security - Authorization - Role based strategy

- **_Types of roles in Jenkins_** :-
  - **Global Roles (System level permissions)** :- Admin (full access over jenkins), developer (can configure jobs but not modify settings), Viewer (Read only)
  - **Project roles (Job level permissions)** :- Build manager (trigger builds and manage jobs), test engineer (execute test but not configure jobs), read only (only view job status)
  - **Agent (node) roles (For build executors)** :- Node admin (configure and manage nodes), node user (run builds but not modify configs)
 
To configure RBAC
- **Define roles** :- Manage and assign roles - Manage roles - Create roles under global roles - Check permission for each role
- **Assign users to roles** :- Manage and assign roles - Assign roles - Enter username or group under global roles and assign roles

![image](https://github.com/user-attachments/assets/f703ef2b-9855-4f56-aee6-b39c51f004eb)

-------------------------------------------------------------------------------------------------------------------------------------------------

Explain jenkins job configurations 
-
- Jenkins jobs define automation workflow for building, testing and deploying apps. When configuring job, various settings determine how jenkins interact with source code, trigger builds, execute tasks, and handles post build actions

General Section
-
- **Project name and description** :- decription to define purpose of job
- **Discard old builds** :- Limits history of builds to save. Either for no of days or no of builds we can keep based on log rotation strategy

![image](https://github.com/user-attachments/assets/13aa9038-5541-462b-8125-24b7ba08a81b)

- **GitHub project URL**
- **Parameterized** :- Defines input parameters for dynamic builds. We can try "branch name"

![image](https://github.com/user-attachments/assets/cdc5c600-0088-412a-8a99-e9879ded335b)

- **Throttle builds** :- To maintain time interval between consecutive run of a job. In below SS. we can run build once in an hour

![image](https://github.com/user-attachments/assets/7487477b-1987-4c43-a909-ebf65e0bd3a1)

- **Execute concurrent builds** :- Allows to run multiple builds in parallel  

Source Code Management
-
- Used to configure job's connection to source code repo
- Supported SCM options :- Git, SVN
- **Repository URL** :- To define git repo location
- **Credentials** :- Used for authentication (SSH key, tokens)
- **Branch specifier** :- Branch to build
- **Polling SCM** :- Enables auto detetction of code changes

![image](https://github.com/user-attachments/assets/d31cab35-5e37-49cc-87f1-6f36a20f5689)

Build Triggers
-
- Defines when and how job should be triggered
- **Trigger build remotely (via WEBHOOK/API Token)** :- Used for CICD integrations (e.g., H/5 * * * * for every 5 minutes).
- **Poll SCM** :- Checks for changes in repository at regular intervals and trigger acc to it
- **Build after other projects are built** :- Triggers job after other is done
- **Schedule** :- Uses cron syntax to schedule builds (e.g., @daily, 0 12 * * * for noon builds)
- **Github webhook** :- Trigger build when code is pushed to github

![image](https://github.com/user-attachments/assets/f6cedb3b-0206-4a3e-9785-91bef111fcf6)

Build Environment
-
- Configures runtime environment before executing build
- **Delete workspace before build starts** :- Ensures clean workspace
- **Use secret text or files** :- Injects credentials securely
- **Provide env variables** :- to use in script
- **Run build steps in parallel** :- execution for faster builds
- **Terminate build if its stuck**
- **Add timestamp to console output**

![image](https://github.com/user-attachments/assets/70bf2a05-6cc2-4b3b-b6cd-9c0780a353d3)

Build Steps
-
- Define actual execution tasks for job
- **Execute shell** :- Run shell commands
- **Execute windows batch command**
- **Invoke ant/gradle/maven** :- Trigger builds for java projects
- **Docker build and publish** :- Builds and pushes docker images
- **Run tests** :- Executes test cases

![image](https://github.com/user-attachments/assets/ffc1afdc-3001-460a-8547-8d47b0579cdd)

Post Build Actions
-
- Defines actions to take place after build process is complete
- **Archive artifacts** :- stores output for later use
- **Send email notifications** :- about failure/success of build
- **Trigger another job** :- Runs dependent jobs automatically
- **Deploy to server**
- **Publish to docker registry** :- push images

![image](https://github.com/user-attachments/assets/97834ed1-dc35-475d-b50f-fdc91086a858)

-------------------------------------------------------------------------------------------------------------------------------------------------

Explain integartion of jenkins with Github using poll SCM
-
- Integrating jenkins with Github using poll SCM allows jenkins to auto trigger builds when it detects changes in git repo at scheduled intervals. It is useful when webhooks cannot be used or when jenkins needs to check for changes periodically
- Prerequisites :- Jenkins, git plugin, github repo, git installed on jenkins server

- Enable Poll SCM in build triggers
  - Go to Build triggers - Poll SCM - Enter cron expression (H/5 * * * * or H/30 * * * *)
  - Make changes in git repo and check whether our job runs every 5 mins as per cron expression set

![image](https://github.com/user-attachments/assets/e3527fdc-1940-4c09-9beb-beaa33d1a26b)

- If jenkins is not detecting POLL SCM Changes :-
  - Ensure correct GitHub creds and repo URL
  - Run git ls-remote on jenkins to check repo access
  - Manually trigger build to check connectivity

-------------------------------------------------------------------------------------------------------------------------------------------------

Explain job chaining in jenkins
-
- Job chaining in jenkins refers to process of triggering multiple jobs in sequential or parallel manner. This approach is useful for CICD pipelines where different jobs handle distinct stages of SDLC like compile, unit test, integration test, deploy

- Upstream and downstream jobs :- US job means job that triggers another job and DS job means job that is triggered by upstream job
  - Job a --> Job B --> Job C (A triggers B and B triggers C)
 
Methods for Job Chaining
-
1. **Build other projects (Freestyle jobs)**
- Go to configure - Post build actions - Build other projects - Enter downstream job to build after this gets complete

2. **Parameterized Trigger Plugin (For passing variables)**
- Post build actions - Trigger parameterized build on other projects - Specify downstream job - Add parameters to pas (Branch, version)

![image](https://github.com/user-attachments/assets/3d184618-8165-48c2-99c9-8c9e8abd683e)

3. **Build pipeline Plugin**
- Install "Build pipeline Plugin"
- Go to Build pipeline view
- Configure job flow :- Build - Test- Deploy

4. **Pipeline script**
- Here inside script we can define stages and jobs inside those stages. So the jobs will run in sequence of the stages

-------------------------------------------------------------------------------------------------------------------------------------------------

Explain jenkins integration with github using webhooks
-
- Integraing jenkins with Github webhooks allows jenkins to automatically trigger a build whenever there is a change in GitHub repo.
- This is more efficient than Poll SCM as jenkins does not need to check for changes periodically, instead github notifies jenkins instantly when push event occurs.

- **Prerequisites** :- Jenkins, Git plugin, Github repo, Github Personal Access Token

- Configure Jenkins to accept webhooks :- Manage Jenkins - Configure system - Enable GitHub webhooks
- Create jenkins job :- Freestyle - SCM fill
- Enable build triggers for webhooks :- Build triggers - GitHub hook trigger for GITScm polling
- Create webhook in Github :- Open GitHub repo - Settings - Webhooks - Add webhooks - Payload URL (http://JenkinsURL:8080/github-webhook) - Content type(application/json) - Add webhook
- Test Webhook integration :-   Make commit in Github - Check jenkins job (triggered automatically) - Verify webhook -
  - Steps to verify :- GitHub - Settings - Webhooks - delivery logs - Response code 200 means jenkins received webhook successfully
