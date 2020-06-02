# Gitflow Idea Map
Gitflow is a workflow design idea that encourages simultaneous development of functions and ideas from many people working on a project. From gitflow maps presented on the internet, there seems to be a consensus of five sections that are simultaneously being worked on:
1. master
2. hotfixes
3. release branches
4. develop
5. feature branches

## **Each Branch Definition and Use**
**Master (Main Branch)**   
The master branch is the overall git repository for the entire project. This repo alone houses the entire project and is never a version that is currently being worked on. Pull requests to the master are very infrequent and are only accepted for complete version overhauls and big updates. This may represent a new milestone achieved with the project.
> think about the master like a game. new updates come out sparingly and only when they are 100% complete without bugs. 

**Hotfixes**  
Hopefully a section that is not commonly used, hotfixes are for resolving severe bugs that are caught after deploying or pushing to master. Though there is a quality check right before pushing to master, some huge bugs that have slipped past. Those are pulled into hotfixes, quickly fixed, and pushed back to master. Though not a completely new version, it is necessary to fix current bugs instead of wait until the next update release.
> after releasing a new version of a game, it seems as if level ups are not working as they're supposed to. it is quickly fixed and re-released days later.

**Release Branches**  
Updates that happen to the release branches have just come off the develop track and are not always ready for release to the public. They will contain a few new features that are set to be released for the upcoming version, but are prone to bugs and can quickly move back to the develop phase. 
> 2 of 3 main features have been added to a game when developers find a bug. it is quickly moved back to develop to solve this issue. After all 3 features are added and no bugs are found, a new version is ready to be released and a PR to master is made. 

**Develop (Main Branch)**
Most of the work will happen here in the develop phase, where devs are working towards fulfilling the requirements of the current version. This may include adding all necessary features and fixing bugs that are going to be released in the upcoming update. 
> devs are hard at work adding new cars and powerups to game v2.0.

**Feature Branches**
These branches are for features that are going to be added not in the upcoming update, but future updates afterwards. These usually have a lower priority but still allows for devs to cross develop and test different features across a multitude of versions.
> a new login feature will be added in the next 2 or 3 updates, but devs have already started planning on how this would look like. 

## **Usage**
Gitflow diagrams and commands found [here](https://danielkummer.github.io/git-flow-cheatsheet/).  
Successful model and correct usage found [here](https://nvie.com/posts/a-successful-git-branching-model/).