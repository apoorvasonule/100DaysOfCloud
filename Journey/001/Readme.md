<img width="497" alt="image" src="https://user-images.githubusercontent.com/75572990/230887318-8e3cdc2e-b187-4a64-b260-28ec316354d3.png">

# Create Azure Function to do arithmetic operations

## Introduction

Create an Azure Function with a language of your choice to do arithmetic operations on 2 numbers supplied as input and return the result.
I am using **Python** for this practical.

## Prerequisite

-Azure Subscription

-knowledge about Azure fundamentals and Azure Functions (Resource for study provided below)


## Cloud Research

-To do this pratical, i needed to study about azure functions. 
      First, I asked chatGPT about Azure functions to get a basic information about it. These are the key points after reading it:
      
      1. Azure Function is **serverless** compute service
      2. Used to run **event-driven** applications
      3. Only pay for the time function is in running stat
      4. we can write Azure function in many languages such as C++, Java, Python, Javascript and many more
      5. Integration option with other azure resources.

-Link for Azure Function Documentation by Microsoft: https://learn.microsoft.com/en-us/azure/azure-functions/ . This link provides detailed information about Azure Function such as introduction, how to get started with it, quick samples of code and exercises and many tutorials.


<img width="943" alt="image" src="https://user-images.githubusercontent.com/75572990/230867769-ad393ae1-f81f-4eda-99b9-cad39d09f2c2.png">



## Try yourself

Follow this step by step guide 

### Step 1 — Create Azure Function
-Search for Azure Function in search bar. Select Azure Function App and fill in information as show in picture below and hit Review + create.

<img width="395" alt="image" src="https://user-images.githubusercontent.com/75572990/230879243-acb5134c-3f54-4179-99a7-ec5ba2164281.png">

### Step 2 — Create Azure Function using given templates
-Click on Azure function app you just created and go through the overview of function app.
-In left menu, Under Functions, select functions.
-Click +Create 
-Select development environment as **Develop in portal** and select template as **HTTP trigger** and hit create.

<img width="565" alt="image" src="https://user-images.githubusercontent.com/75572990/230880734-309d39cd-d109-4d82-9d71-ca2c136dfd86.png">

-Once the function is created, click Code + Test and copy paste this code there
```
import logging
import json
import azure.functions as func

def main(req: func.HttpRequest) -> func.HttpResponse:
    req_body = req.get_json()
    operation = req_body.get('operation')
    numbers = req_body.get('numbers')
    result = 0
    
    if operation == 'add':
        for num in numbers:
            result += num
    elif operation == 'subtract':
        for num in numbers:
            result -= num
    elif operation == 'multiply':
        result = 1
        for num in numbers:
            result *= num
    elif operation == 'divide':
        result = numbers[0]
        for i in range(1, len(numbers)):
            result /= numbers[i]
    else:
        return func.HttpResponse(
            "Invalid operation specified",
            status_code=400
        )

    return func.HttpResponse(
        json.dumps({"result": result}),
        status_code=200
    )
 ```      


### Step 3 — Test the Code
-Click Test/Run and in Body section, Paste this and hit Run.
```
{
    "operation": "add",
    "numbers": [2, 3, 5]
}
```
After this you should get results like this

<img width="217" alt="image" src="https://user-images.githubusercontent.com/75572990/230884139-8340fcdd-80c9-440c-bf73-d2fea438f31a.png">



## Social Proof
https://www.linkedin.com/feed/update/urn:li:share:7051143274413117441/
