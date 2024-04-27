# Sample Node.js application
Demo containerizing a NodeJs application, pushing docker image on dockerhub and also running it as a docker container.This is a To-Do list app where we can create list of items,also check them or delete once it is done.Create EC2 instance with linux AMI,keypair,security groups.

1. The main file of our application would be index.js. Make a directory (mkdir),change your working directory to it (cd /your/dir), Install docker on you ec2 instance, install git ,git clone you repo in ec2 user to get your files.Create and build the Docker image with vi Dockerfile command.
2. Explanation of Dockerfile Structure:
    FROM: Selecting the base image (e.g., node:14) for the Docker container.
    WORKDIR: Setting the working directory inside the container where the application code will be located (/app).
    COPY: Copying application files (e.g., package.json, index.js) into the container.
    RUN: Installing Node.js dependencies using npm install inside the container.
    EXPOSE: Specifying the port (3000, for example) on which the Node.js application will run.
    CMD: Defining the command (node index.js) to start the Node.js application inside the container.

Click on Save and close the Editor window.
Return to terminal in the instance window and type the command given below, the Dockerfile and Index.js file should be in the same location.
Run the below command ,

3. Build the Docker image (-t) to name your image -- docker build -t mynodeapp .
4. Run the Docker image -- docker run -d -p 3000:3000 mynodeapp
5. 88d912664b9bb99cab5e53aa7000ba3e4c052249a43ad660e8c9fcc119d3f319, The -p flag maps a port running inside the container to your host, -d is detached mode. In this case, you're mapping the app running on port 3000 inside the container to port 3000 on your host(allow port in your ec2 security group). Note that if port 5001 is already being used by another application on your host, you might need to replace 3000 with another value, such as 5002. Also we have allowed the port where app listens in the index.js file.

6. Check docker image -- docker images

7. Displays a list of currently running Docker containers along with relevant details. -- docker ps
8. To view all containers (including stopped ones) -- docker ps -a
   to only display container IDs for scripting purposes -- docker ps -q

9. Navigate to http://your public ip:3000 in a browser to see the results.
10. Check the log output of the container -- docker logs

11. Tag your image and Push to a central registry(If you don't have a Docker ID, head over to https://hub.docker.com to create one) to add your image to docker hub.
other developers and operators can use the docker pull command to deploy your image to other environments. Remember: Docker images contain all the dependencies that they need to run an application within the image. This is useful because you no longer need to worry about environment drift (version differences) when you rely on dependencies that are installed on every environment you deploy to. You also don't need to follow more steps to provision these environments. Just one step: install docker, and that's it.
