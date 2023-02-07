Proj description 

According to business logic, we created an application in which the customer can post his purchases with a description and review of whether it is worth buying this item.

![image](https://user-images.githubusercontent.com/93725278/217241124-378ecf96-ba90-44f0-820e-f1c90e17d863.png)


The first service is responsible for the user's data and the product he wants to talk about, and the second service directly for the description and title of this post.

As a customer, we used the Swagger tool to help us support API virtualization along with management and monitoring. Open API specification Swagger creates complex and automatically generated documentation and shares the REST API specification.

Also used was RabbitMQ, a general-purpose message broker that supports protocols including MQTT, AMQP, and STOMP. It can handle high-throughput use cases such as online payment processing. In this lab, RabbitMq acts as a message broker between microservices. When adding or changing information in the database in one of the microservices, we see updated changes in the console.

Link to Dockerfile:
https://hub.docker.com/repository/docker/fromgreensky/userservice
https://hub.docker.com/repository/docker/fromgreensky/rabbitmq
https://hub.docker.com/repository/docker/fromgreensky/postservice

To install and run RabbitMq, you need to run these commands on the command line: docker pull rabbitmq:3-management

docker run --rm -it --hostname my-rabbit -p 15672:15672 -p 5672:5672 rabbitmq:3-management

Now by going to http://localhost:15672 , using username "guest" and password "guest", we have created Exchange with name "user" of type "Fanout" and two queues "user.postservice" and "user.otherservice ".

![image](https://user-images.githubusercontent.com/93725278/212052113-1f3e04e5-df01-4af7-86de-4adaff9dbbea.png)

Now, after launching Debug from Multiple Startup Projects, we can see 2 services:

![image](https://user-images.githubusercontent.com/93725278/212024181-be85b86e-71d5-4154-9a29-1c132eebf6bf.png)

![image](https://user-images.githubusercontent.com/93725278/212052004-17ce432f-023a-4c9a-b3bf-78b47bbcdcaa.png)

We will add a new user and product description to both services.

![image](https://user-images.githubusercontent.com/93725278/212052154-81b4971f-acb5-4efe-9640-e8a0b3544b96.png)

![image](https://user-images.githubusercontent.com/93725278/212052181-10705193-2576-4347-ab74-ed2f40cf1c10.png)

We can see a successful execution:

![image](https://user-images.githubusercontent.com/93725278/212052219-500fe4ac-7ca7-40da-992f-dcafb712afe0.png)

Work progress:

Let's create a Docker image for each application. Let's look at the current images, we will notice that there is also a rabbitmq image:

![image](https://user-images.githubusercontent.com/93725278/212052266-bac5754f-e0ca-4fe0-bb73-1c2a46f070ff.png)

Let's expand Deployment for UserService:

![image](https://user-images.githubusercontent.com/93725278/212052324-228ef4a3-2d78-4a18-a58e-2306c4e57a4d.png)

Let's create a Service for UserService:

![image](https://user-images.githubusercontent.com/93725278/212052436-966d154e-aa39-47d8-9361-c1fd23e6cdcd.png)

Similarly for PostService:

![image](https://user-images.githubusercontent.com/93725278/212052373-27c6a206-d19d-4e36-bcc5-3bf3807891bd.png)
![image](https://user-images.githubusercontent.com/93725278/212052472-8133775e-b5f4-4a57-a8f6-80e5913194ab.png)


Services successfully created:
![image](https://user-images.githubusercontent.com/93725278/212052533-a0081c19-1b9b-4138-ad93-3a072e3ff5dd.png)

