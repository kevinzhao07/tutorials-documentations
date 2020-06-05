# Microservice Architecture
Microservice Architecture is a style of structure for an application that is highly testable and deployable, even with a large scale application. Characteristics of MSA include slowly developing projects piece by piece and tending to be more towards a DevOps and continuous testing. The opposite would be a _monolithic_ archictecture, where applications are built entirely in one piece as a single autonomous unit. This made fixing small bugs and testing portions of code a lot more difficult, as small changes would require the costly redeployment of the entire piece of software. 

## **Notable Differences**
Microservices allow an application to be split into smaller and manageable services, that can each be independently tested and deployed. Each section requires no understanding of the others, helping to catch bugs and hazards quickly. 

#### **More Info**
A more detailed description is found [here](https://smartbear.com/solutions/microservices/).

# What is an API?
An API allows users to communicate with and accept information from other programs. We use APIs without even knowing it: when we go on any travel site and punch in our information and available dates, a list of cheap flight tickets and hotel reservations pop up. How did this website, which is not related to any airline or hotel get all this information within the matter of milliseconds? Well this is where the **API** comes in. What's happened behind the scenes is that the information that you've given the travel site is packaged and sent to airline and hotel company APIs. The information that you gave is in a specific configuration that makes sense to company APIs, which return the information you may be looking for. This travel site simply compiles all the information it has received (this data is configured to dates and prices **you** have specified), adds some CSS, and gives it to you. 

Having an API eliminates the need to have every program that wants to analyze flights and hotels search the company's database itself. By using an API, any program can simply request some specified data, and it will be given to them quickly.

**Here is a real life, easier to understand example.**  

You are at a restaurant with a menu in front of you. You want to order something, communicate it to the chef, who will then bring your order back to you. 
> you have this database and want a specific section of it. how will you get the information you want?

The waiter is the missing link that takes your order, goes to the chef, and tells him what to do. Afterwards, it delivers your order back to you.
> the api is the missing link. it takes your request, goes to the system, and tells it what to do. Afterwards, it delivers the system's response back to you. 

# Scripts in Postman
Postman is used to create, test, and use APIs seamlessly in any project. Scripts in Postman especially help with automating test suites, pass data between parameters, and more. The timeline of using Postman scripts go like this:
1. **Pre-request Script** is generated before a request is sent to a server
2. **Request**: the request to the API is set
3. **Response**: the response from the API comes back
4. **Test Script** executes after a request is sent

Quick Tutorial [here](https://www.guru99.com/postman-tutorial.html).