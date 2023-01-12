Proj description 
Link to Dockerfile:
https://hub.docker.com/repository/docker/fromgreensky/userservice
https://hub.docker.com/repository/docker/fromgreensky/rabbitmq
https://hub.docker.com/repository/docker/fromgreensky/postservice

To install and run RabbitMq, you need to run these commands on the command line: docker pull rabbitmq:3-management

docker run --rm -it --hostname my-rabbit -p 15672:15672 -p 5672:5672 rabbitmq:3-management

Now by going to http://localhost:15672 , using username "guest" and password "guest", we have created Exchange with name "user" of type "Fanout" and two queues "user.postservice" and "user.otherservice ".

image

Now, after launching Debug from Multiple Startup Projects, we can see 2 services:

image

image

We will add a new user and product description to both services.

image

image

We can see a successful execution:

image

Work progress:

Let's create a Docker image for each application. Let's look at the current images, we will notice that there is also a rabbitmq image:

image

Let's expand Deployment for UserService:

image

Let's create a Service for UserService:

image

Similarly for PostService:

image

Services successfully created:

image
