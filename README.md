# AWS Lambda Function + DynamoDB

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

<img src="https://user-images.githubusercontent.com/70295997/207708326-4ea30952-3bad-4a7e-9333-6d10ce0b215a.png" width=900>
<img src="https://user-images.githubusercontent.com/70295997/207708225-a9fcebe3-11d8-4054-8d97-a4df66fad249.png" width=900>
<img src="https://user-images.githubusercontent.com/70295997/207710878-74e52caf-722c-43ab-b232-7fbd45e581eb.png" width=900>


After the table is created, I can view its structure. No need to predefine the Schema structure.
![image](https://user-images.githubusercontent.com/70295997/207709809-4530a271-80f7-4234-9247-97950912a2a1.png)
![image](https://user-images.githubusercontent.com/70295997/207710286-f5e87adf-1069-4ca4-bd38-3ccb849f59c8.png)

