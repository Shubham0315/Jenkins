- Jenkins Shared Libraries provide a way to define reusable code for jenkins pipeline. They help in modularizing pipeline logic, reducing duplication and maintain consistency across multiple projects
  - We can write pipeline logic once and use it across multiple jenkinsfile
  - Centralized management of pipeline scripts
 
![image](https://github.com/user-attachments/assets/58b7248c-f9a1-4e81-9a3e-82d37d347bca)

- vars/ :- contains globally accessible groovy scripts (custom pipeline scripts)
- src/ :- contains groovy classes that can be imported within vars/ script
- resources/ :- stores config files or templates
- README.md :- documentation for library

Configure Shared Lib
-
- Manage jenkins - configure system - global pipelines - add new library with name, Repository, default branch/tag,

- In jenkinsfile use @Library annotation

![image](https://github.com/user-attachments/assets/5377aac1-4b7f-420b-bdb3-27146df336e9)


