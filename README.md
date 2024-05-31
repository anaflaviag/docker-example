## Explaining the Dockerfile

Explaining line by line.

1 - FROM - Create a new build stage from a base image.

3 - WORKDIR - Change working directory - Specifies in which directory you want your application and where the next commands will be executed.

5 - COPY - Copy files and directories - This is copying all the files and pasting them into the /app directory.

7 - RUN - Execute build commands. 

9 - EXPOSE - Describe which ports your application is listening on - aka exposing to the “outside world”/being accessible outside the container. Used for documentation purposes only.

11 - CMD - Specify default commands - This is running server.js with the node command. The previous commands are executed when the image is created, but this one is only executed when the container is started. The syntax is an array with strings.

You can find more references [here](https://docs.docker.com/reference/dockerfile/)


## Building and running

- You can only run images that are already built;
- ```docker build .``` command to build the docker file found in the directory where you run it;
- After building the image, the generated id appears at the end, but you can also check the image id using the ```docker images``` command;
- When we use the ```docker run``` command, running instances are being created as containers based on the image;
- With the id generated you can start a container based on the image with the command ```docker run ID-HERE```, but as in this example the container has a port to be accessed outside of it, that port need to be published on the container and you do it adding the -p flag on the command and then the ports, resulting in ```docker run -p 8080:80 ID-HERE``` (you are publishing on local port 8080 the container's internal port 80);
- With the container running on the published port, you'll be able to test your application [here](http://localhost:8080/);
- ```docker ps``` to find the container that is running and ```docker stop CONTAINER-NAME``` to stop it. Adding the -a flag in the container listing command shows all containers that docker has created, resulting in ```docker ps -a```.