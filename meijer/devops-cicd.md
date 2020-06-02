# DevOps and CI/CD
Simply put, DevOps and CI/CD (continuous integration and continuous delivery/deployment) is the practice of automating the building, testing, and deployment of code. 

## **DevOps**  
DevOps is a software development approach used by companies to drastically decrease development lifecycles and quickly push out new features, resulting in higher customer satisfaction. The lifecycle of DevOps contains four steps:
1. Version Control
    - maintaining older versions of code (git already does this)
2. Continuous Integration
    - continuous compilation and validation of code, constant code reviews and QA checks, unit testing.
3. Continuous Delivery
    - deploying new features and build to test servers, getting feedback for user acceptance / satisfaction
4. Continuous Deployment
    - deploying features into production server for release to the public

There is a constant feedback loop as applications go through these 4 stages of lifecycles. This way, many bugs are found and fixed immediately, which minimizes the impact of slowing down the constantly moving pipeline.

## **CI/CD**  
Continuous Integration and Deployment is a similar pipeline process aimed at moving code efficiently from developer to customer. If a company were to develop a complicated web application, this process would be necessary:

1. The cycle beings with **version control**, with a continuous feedback loop that updates the version control after all updates.
2. The app now goes to the **build phase**, where code is written and features are added. The code can be merged with other branches of the repo and compiled.
3. Next comes **unit testing**, where the new features are heavily tested. Many bugs are caught during this phase of development, and the feedback loop to version control saves all updated versions.
4. After comes the **deploy phase**, where the new changes are staged into a test server. The new features can be seen with the entire application. 
5. The **auto test** phase is a all-inclusive testing phase to make sure the new features don't break existing features present in the application. 
6. Finally, if all steps are passed, the code is allowed to be **deployed** to production. 

> if an error occurs in any given step, the pipeline will halt and developers will work on fixing the bug. the new code is saved into version control, and the cycle restarts.

This loop ensures that the code is of utmost quality and bugs are virtually non existent. These pipelines are important because of their speed and how quickly feedback gets back to developers. Furthermore, much of the testing is handled automatically, leaving more time for developers to fix bugs instead of creating manual tests. 

## **Helpful Guides**

Quick 100 second explanation on devops found [here](https://www.youtube.com/watch?v=scEDHsr3APg).  
In-depth explanation with diagrams and flowcharts found [here](https://dzone.com/articles/learn-how-to-setup-a-cicd-pipeline-from-scratch#:~:text=A%20CI%2FCD%20Pipeline%20implementation,testing%2C%20and%20deployment%20of%20applications.).