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

<img src="https://user-images.githubusercontent.com/70295997/207708326-4ea30952-3bad-4a7e-9333-6d10ce0b215a.png" width=900>
<img src="https://user-images.githubusercontent.com/70295997/207708225-a9fcebe3-11d8-4054-8d97-a4df66fad249.png" width=900>
<img src="https://user-images.githubusercontent.com/70295997/207710878-74e52caf-722c-43ab-b232-7fbd45e581eb.png" width=900>


After the table is created, I can view its structure. No need to predefine the Schema structure. It's an advantage of NoSQL.

![image](https://user-images.githubusercontent.com/70295997/207709809-4530a271-80f7-4234-9247-97950912a2a1.png)
![image](https://user-images.githubusercontent.com/70295997/207710286-f5e87adf-1069-4ca4-bd38-3ccb849f59c8.png)

Now I have to create the API Gateway (GW). To grant access to the outside world, I create a Public API.

<img src="https://user-images.githubusercontent.com/70295997/207742678-71aa7b41-0a26-4edc-8193-89111a12e0a2.png" width=700>
<img src="https://user-images.githubusercontent.com/70295997/207741330-d3404790-fe2e-46da-9d0c-2152ce953755.png" width=700>

In the Amazon API GW, a REST API refers to a collection of resources and methods that can be envoked through HTTPS endpoints.

![image](https://user-images.githubusercontent.com/70295997/207742125-0f11d5b9-071b-48d0-8d38-0b97aafb252a.png)

![image](https://user-images.githubusercontent.com/70295997/207743101-7f9300a3-fc04-453e-9b2b-4c3244960581.png)
![image](https://user-images.githubusercontent.com/70295997/207743306-f80361fc-077d-4f41-abc2-c174044f90f6.png)
![image](https://user-images.githubusercontent.com/70295997/207743500-65aaf9ac-d309-4bbf-8494-6253a24da523.png)
![image](https://user-images.githubusercontent.com/70295997/207743573-644d29b2-7793-4bae-b1b9-e3617b5825c5.png)
![image](https://user-images.githubusercontent.com/70295997/207743657-09d4840b-be1f-4055-8cb3-232817c71363.png)
![image](https://user-images.githubusercontent.com/70295997/207743846-2606af2b-da8f-4f54-9bb7-9f632096fd6e.png)
![image](https://user-images.githubusercontent.com/70295997/207744149-ab6b5e55-d155-4ee5-816a-49c43733e9a8.png)
![image](https://user-images.githubusercontent.com/70295997/207744435-a304f7b1-f92e-4396-a36c-a1c5c23b7fe2.png)
![image](https://user-images.githubusercontent.com/70295997/207744536-137ea29a-34bf-4c45-81b6-a75c0a1eaddf.png)
![image](https://user-images.githubusercontent.com/70295997/207744636-43f02246-82dd-4e88-b943-bf0ea9d1c797.png)
![image](https://user-images.githubusercontent.com/70295997/207745030-9b74e467-b725-4213-98ec-48b01a62e474.png)
![Screenshot_20221214_043927](https://user-images.githubusercontent.com/70295997/207746277-5aa52e28-9852-4b9e-b9d7-29ab2fb4814d.png)
![Screenshot_20221214_043648](https://user-images.githubusercontent.com/70295997/207746158-5e32c8b6-ece0-4678-981e-d5a4c4c271f2.png)
![image](https://user-images.githubusercontent.com/70295997/207745434-466bb909-38f8-42dc-aad9-8d4fee7fd5e7.png)
![image](https://user-images.githubusercontent.com/70295997/207745531-7f32207b-82bb-499c-80bb-83500c26c7de.png)










