# Jenkins

- Jenkins is an open source automation server/tool to automate our tasks of software development like building, deploy, testing.

Features of Jenkins
-
- Continuous integration and Continuous delivery (CICD)
- Easy installation
- Easy configuration as we get easy interface on browser and we can make tasks on frontend
- Plugins based arrchitecture. Like if our project is python based just download python related plugins for project to run
- Extensible and versatile
- Easy to distribute work across multiple machines

What is CICD
-
- It is a method of frequently delivering apps to customers by introducing automation into the stages of app development
- If we automate all the steps of SDLC, we can provide many small changes to customers in short time. So CICD is used to avoid delay by manual changes. So using CICD we can increase efficiency
- We can implement CICD using jenkins
- In CI, building, testing and merging is done. We write code in branches, then test that code, if test is good we merge that code into main branch for prod.
- In C-del, the change which is ready for delivery after CI, we can release it to repository. In C-dep, we make the code live to customer by auto deploying on prod.

Lab Setup for Jenkins
-
- We'll install jenkins and practice. In our setup, on Linux OS we'll install jenkins using VMs.


Jenkins Installation
- 


Jenkins Dashboard Overview
-
- Whatever autonation tasks we do in jenkins is in the form of jobs. For this we can do **New Item** or **Create a Job**
- Also there is option of **set up agent** or **configure a cloud** for distributed builds. Distributed build is a jenkins setup where we use agents on different servers so that if there is more load or there are multiple jobs which we work on gets distributed among these servers/agents.

![image](https://github.com/user-attachments/assets/db8327f7-6995-4251-84ab-fd73b3fad0c0)

- There is option of "**Manage Jenkins**" where we can find all the settings related to jenkins
  - **_Plugins_** :- If we need to perform some task related to ansible for which we need that plugin, go to _available plugin_ option and download it. Plugins are used to connect servers and perform tasks.
  - **_Users_** :- Different users can perform different tasks according to access they have
 
Creating first Jenkins Job
-
- We can create Freestyle Job so that we can configure it by ourself

![image](https://github.com/user-attachments/assets/4a2f64b5-1b65-43ab-9fdc-3dae2dbb05b3)

- Inside this job we see "Build Step" option means what we want to execute inside our job. We can do execute shell

![image](https://github.com/user-attachments/assets/78e77b08-bb6a-4cea-be07-be0517a542c8)
