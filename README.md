# AWS Lambda Function + DynamoDB

SDET/QE Perspective. Practical use case for Lambda. How to integrate λ with API GW.

![image](https://user-images.githubusercontent.com/70295997/207719183-58f6cd6f-da34-4abe-97fe-f1c07e533013.png)

__DynamoDB:__
- very flexible NoSQL DB
- key-value pair format of documentation
- highly scalable - single digit millisecond performance  at any scale
- fully managed, multi region, multi master, durable DB with built-in security, backup, restore, and in-memory caching for internet-scale apps
- can handle > 10 trilliom requests per day and support peaks of > 20 million per second
- a lot of companies/clients use it - Lyft, AirBnB, Redfin, enterprise apps like Capital One, Samsung, Toyota, plus many gaming companies
- can use for Mobile, Web, Gaming, ad tech, IoT that need low latency data access at any scale
- perfect example where Lambda Function can be used

_Steps:_
1. Go to the AWS Management Console.
2. Login as a root user.
3. Select DynamoDB storage service.
4. Create a table.
5. Process data in this particular DB
6. Post/enter data in this DB using a POST API call.

![image](https://user-images.githubusercontent.com/70295997/207703935-2f118085-8a54-453c-9681-94887a7e2182.png)

<img src="https://user-images.githubusercontent.com/70295997/207983354-2b18e179-5d0b-426c-9522-746c9f178bce.png" width=900>
<img src="https://user-images.githubusercontent.com/70295997/207708225-a9fcebe3-11d8-4054-8d97-a4df66fad249.png" width=900>
<img src="https://user-images.githubusercontent.com/70295997/207710878-74e52caf-722c-43ab-b232-7fbd45e581eb.png" width=900>

After the table is created, I can view its structure. No need to predefine the Schema structure. It's an advantage of NoSQL.

![image](https://user-images.githubusercontent.com/70295997/207709809-4530a271-80f7-4234-9247-97950912a2a1.png)
![image](https://user-images.githubusercontent.com/70295997/207710286-f5e87adf-1069-4ca4-bd38-3ccb849f59c8.png)

Now I have to create the API Gateway (GW). To grant access to the outside world, I create a Public API.

<img src="https://user-images.githubusercontent.com/70295997/207742678-71aa7b41-0a26-4edc-8193-89111a12e0a2.png" width=700>
<img src="https://user-images.githubusercontent.com/70295997/207741330-d3404790-fe2e-46da-9d0c-2152ce953755.png" width=700>

In the Amazon API GW, a REST API refers to a collection of resources and methods that can be invoked through HTTPS endpoints.

![image](https://user-images.githubusercontent.com/70295997/207759968-15bc606c-3741-4d39-aa36-c1ec23838f50.png)
![image](https://user-images.githubusercontent.com/70295997/207760391-204c8f31-568a-468b-b76d-65c678c11b47.png)
![image](https://user-images.githubusercontent.com/70295997/207760614-a71cbc45-03e5-4e9b-b4b3-0bf6649d5807.png)
![image](https://user-images.githubusercontent.com/70295997/207760740-2da87862-fb25-4144-9013-a784da64cac5.png)
![image](https://user-images.githubusercontent.com/70295997/207760878-8355597d-fe65-40f7-977e-4dae761f825b.png)
![image](https://user-images.githubusercontent.com/70295997/207761014-b6c27afd-aa02-4209-a5bf-7a68ee750d18.png)
![image](https://user-images.githubusercontent.com/70295997/207761760-c48d14b6-302c-442c-9edb-5fe805f35063.png)

Go back to the API GW and pass the name of this particular Lambda Function.

![image](https://user-images.githubusercontent.com/70295997/207762274-f73e153d-e557-4663-bd83-d24424cf2682.png)
![Screenshot_20221214_071324](https://user-images.githubusercontent.com/70295997/207764131-60e6f80d-a8eb-418f-8bbb-72db1d79da67.png)
![image](https://user-images.githubusercontent.com/70295997/207765482-514fcc0b-0c3f-4d2b-886f-55ad3aa1e903.png)
![image](https://user-images.githubusercontent.com/70295997/207765841-ce4b7883-e696-4906-9602-ab8787ddccdd.png)
![image](https://user-images.githubusercontent.com/70295997/207951005-8ad4fc60-cc7d-4082-ada4-77c976f1ee22.png)

Currently, λ is not interacting with DynamoDB. I have to integrate λ and DynamoDB. Write code in such a way that I can make a connection to the database. I use [Boto3](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/dynamodb.html) (AWS SDK for Python) for integration with the λ function. Boto3 is a low-lelel DynamoDB client.

I use the [_put_item()_](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/dynamodb.html#DynamoDB.Client.put_item) query method from the Boto3 service APIs documentation.
![image](https://user-images.githubusercontent.com/70295997/207941167-3195bbe7-423b-432a-a560-0e0535ec41e0.png)

Create a connection with DB by creating an object of DynamoDB. Follow the steps in the [Quick Start](https://boto3.amazonaws.com/v1/documentation/api/latest/guide/quickstart.html#using-boto3) guide:

![image](https://user-images.githubusercontent.com/70295997/207942365-519364ef-635c-44db-a1e2-0ba9150413e4.png)

Proceed to the AddEmployee Lambda Function and edit the _lambda_function.py_ file as follows:

        import boto3

        dynamodb = boto3.resource('dynamodb')
        table = dynamodb.Table('Employee')

        def lambda_handler(event, context):
                table.put_item(Item=event)
            return
                {
                "status code": 200,
                "message": "Employee is created successfully"
                }

Click 'Deploy' to get the deployment package successfully saved. 

![image](https://user-images.githubusercontent.com/70295997/207948358-abd92db3-48ec-4132-bd6e-3eddb713436f.png)

Now, test it from the API GW. Pass the following load to the Request Body:

        {
            "Employee_ID": 101,
            "Name": "Abby",
            "Age": 25
        }

![image](https://user-images.githubusercontent.com/70295997/207949807-ae348286-ca79-4172-836e-3c7e87e04cda.png)

I get the _AccessDeniedException_ error message, because I have no access to the Employee table.

![image](https://user-images.githubusercontent.com/70295997/207962221-f909784a-af66-4f14-9e87-88dc42697433.png)

I have to grant permission/access when creating the AddEmployee function. Currenly, I have no permissions. Go to Lambda Function > Configuration > Permissions and edit the Execution Role.

![image](https://user-images.githubusercontent.com/70295997/207965657-ddaa958f-9c2d-4201-86bd-b98c072f2a18.png)

Select option 'Create a new role from AWS policy templates' and proceed to the IAM Console to create a role.

![image](https://user-images.githubusercontent.com/70295997/207966866-eb085f52-7a75-419c-92a2-5221f382f60d.png)

![image](https://user-images.githubusercontent.com/70295997/207968042-d8ce80c3-acb1-4749-b1f8-761c76bad70f.png)

Select the AdministratorAccess Policy, populate the Tags if applicable, and proceed to the Review.

![image](https://user-images.githubusercontent.com/70295997/207970690-32be1106-4f17-4ba4-a686-3b6736ce1d9f.png)

Create the _lambda_admin_role_ and verify it displays under IAM > Roles.

![image](https://user-images.githubusercontent.com/70295997/207971197-ea0dbbf7-38b8-4ab1-aa47-de6fd3ed690d.png)

Go back to _Lambda > Functions > AddEmployee > Edit basic settings_ and select option 'Use an existing role'.

![image](https://user-images.githubusercontent.com/70295997/207974779-00114215-a23c-49c2-96c2-b845557b58b1.png)


...







