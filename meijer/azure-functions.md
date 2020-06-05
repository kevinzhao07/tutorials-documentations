# Azure Functions
Explained online,  

**Azure Functions allows splitting an API into several independent functions following a microservice architecture.**

Azure functions allow for _serverless computing_, which lets users upload code, define trigger events, and activate those trigger requests. They are not meant to handle large complete software programs, but more bite size manageable code that aims to test or implement a certain feature. Examples of using an Azure Function include:
- have events that trigger specific functions in a cloud environment
- message traffic and timer triggers

By chaining together multiple functions, a more complicated API can be made. 

### **Serverless Computing**
Azure falls into the category of serverless computing, the idea of hosting backend code without worrying about infrastructure and how servers are set up. Simply, backend code is uploaded to a vendor who takes care of setting up server space, and a user who has access to the frontend code can request information from the backend databases. 

### **Resources**

Expalnation of a quick function creation [here](https://youtu.be/nCExarOuPAw).
- John makes a function in Azure in JS
- retrieves the function link, and tests on postman (API)
- passing into the API a parameter `name`, he gets back `"hello john!"`
- the testing is complete, and the functions works as intended.

What can functions be used for? [documentation](https://docs.microsoft.com/en-us/azure/azure-functions/functions-overview).  

Usage of Azure Functions (testing on postman/etc) [here](https://dzone.com/articles/introduction-to-azure-functions).

[1 hour] explanation of Azure Functions [here](https://www.youtube.com/watch?v=zIfxkub7CLY).

# Creating an Azure Function
Some high level defintion: a **function** is an app that simply does ONE thing. This ties in with the concept of microservices, where there are multiple functions that specify in their own task. They do work that they know how to do well, and pass on the rest to another function. This is why microservice architectures are referred to as a _pipeline_. Another benefit of this is not needing to scale up the entire project if one section is going to have a lot more traffic. Each function is independent from another and you can scale functions out as needed. 

Here are some steps to creating an Azure Function to work with. I'll use Visual Studio 2019 with the Azure extensions installed. They already have many built in features that allow anyone to create and run their azure functions almost immediately. This will make a test API on a localhost, where you can test with postman or just by modifying the URL.

We can `Create a New Project` and select `Azure Functions`. When we hit create, we will see another pop up. Make sure you are using the latest version of Azure (you can check on the top right). There will be a list of triggers that you can select for your Azure function, defined below:

- `Blob Trigger`: listens for whenever a file gets written into "blob storage" and will execute its function accordingly. One example of this is a web application that allows profile pictures. If one were to add 4/5 MB files, they wouldn't be web friendly. Instead, an Azure Function can listen to these files being uploaded and save smaller instances of those images to be used in the web application. This is all done automatically because the trigger that invokes these functions comes from the uplaoding of files.   

- `Cosmos DB Trigger`: database trigger that listens to when things are added/modified to a database. For example, if a user submits a form to join this program, a Azure function can be triggered to send an email to verify that it was them. Cosmos DB also has the ability to scale to massive sizes. 

- `Queue Trigger`: executes Azure functions while listening to an updating queue. An example of this would be an ordering system, where a user may place their order, their order number and values are placed in a queue with hundreds of other orders, and an Azure function would create tickets and information to ship these orders out in the order of the given queue. If you were to order something but afterwards you are alerted it is out of stock, it simply means someone towards the front of the queue also ordered the same item and got it before you. 

- `HTTP Trigger`: executes when you have an HTTP request. This is a really small API that have a few functionalities. Webhook is the communication between computers that call out to a URL. 

VS also allows these functions to be run on our local machine without pushing it to Azure in the cloud. With such a small testing application, there is no reason to push it to Azure for now. We can just press run on our local machine, where it will give us a localhost link. 

## Expalantion of starting code
```cs
namespace testapp1
{
    public static class Function2
    {
        
        // name of our function that we will call when we upload it to Azure
        [FunctionName("Function2")]

        // tells you what type of function this is: we know it is a HttpTrigger with authorization level "function" (rather than admin/anon). we allow "get" and "post" requests to access our url.
        // route refers to the url: {route}/api/{function_name}
        // the HTTPRequest is passed in as parameter "req" and there exists a logger "log". 
        public static async Task<IActionResult> Run(
            [HttpTrigger(AuthorizationLevel.Function, "get", "post", Route = null)] HttpRequest req,
            ILogger log)
        {
            // logs what happened. string can be modified
            log.LogInformation("C# HTTP trigger function processed a request.");

            // expected parameter for a 'get' request
            string name = req.Query["name"];

            string requestBody = await new StreamReader(req.Body).ReadToEndAsync();
            dynamic data = JsonConvert.DeserializeObject(requestBody);
            name = name ?? data?.name;

            // if name is not supplied, give a generic message. else return good morning + {name}.
            string responseMessage = string.IsNullOrEmpty(name)
                ? "yo dawg u gotta put a {name} in mane."
                : $"Good Morning my good lad, {name}. ";

            return new OkObjectResult(responseMessage);
        }
    }
}
```