# MobiledgeX_Hello_World

This demo application walks through the following
* Step 1 -- How to create a base level NodeJS http server that serves up a bare bones index.html and view from local browser
* Step 2 -- How to "dockerize" the webserver and view from local browser
* Step 3 -- How to deploy the "dockerized container" to the MobiledgeX platform and view from local browser

Couple of requirements:
* This tutorial was developed for Mac OSX
* The Node http-server server defaults to port 8080

## Step 1 -- Create a Basic Web Server and View from Local Browser

Step 1a -- Install NodeJS and Git -- https://nodejs.org/en/download/ && https://githowto.com/

Step 1b -- Open a terminal window and create a temporary directory (call it anything you want)

Step 1c -- Download the sample code with Git (make sure you are in your temp directory) and then CD into the directory after downloading the github repository -- Type the following command into your terminal:
```
git clone https://github.com/skydvr01/Docker_NodeJS_Hello_World.git
```
Step 1d -- Verify that the same files you see on the Github repository webpage are the same files you see in the local directory. Your local directory should look like this: 
```
ls
```

Step 1e -- Install the necessary NodeJS dependencies (http-server module in this case) by typing the following:
```
npm install
```

Step 1f -- Type "npm start" -- This will start the http-server server.  
```
npm start
```

Step 1g -- Press "Command" button and click the link provided. You should see this <show image> in a new browser window. Congratulations! You started a webserver and served up index.html! 

## Step 2 -- Dockerize Your Website and View from Local Browser

Step 2a -- Build the docker image (don't forget the period at the end of this command!).
```
docker image build -t test:1.0 .
```
Step 2b -- Run the docker image you just created
```
docker container run --publish 8090:8000 --detach test:1.0
```
* "publish 8090:8000" -- This tells docker to forward traffic incoming on the host’s port 8090 (your computer), to the container’s port 8000 (containers have their own private set of ports, so if we want to reach one from the network, we have to forward traffic to it in this way; otherwise, firewall rules will prevent all network traffic from reaching your container, as a default security posture).
* "detach" --Tells Docker to run this container in the background so that you don't have to open a new terminal window
Step 2c -- Type "localhost:8090" into a new browser window and you should see [this](https://drive.google.com/file/d/14t0eEVYtIQVjNQ90StxgV-cC_DAqfBey/view?usp=sharing). Congrats! You have just dockerized a webpage and served it up via NodeJS!

## Deploy the "dockerized container" to the MobiledgeX platform and View from Local Browser
Step 3a -- Log into https://console.mobiledgex.net/. If you do not have an account or are not provided one, please speak to the event organizer or email support@. 

Step 3b -- Open a terminal and type the following command. This should list the docker image you just created from the steps above. 
```
docker image ls
```

Step 3c -- Log into the MobiledgeX Platform.
```
docker login -u <your_user_name__remember_it_is_not_your_email> docker.mobiledgex.com
```

Step 3d -- "Tag" your image with a simple name that you can reference later.
```
docker tag <(your application name):(version number)> docker.mobiledgex.net/<your organization name from earlier>/images/<application name>:<version>
```

Step 3e -- Push your image to the MobiledgeX Docker Repository.
```
docker push docker.mobiledgex.net/<your organization name from earlier>/images/<application name>:<version>
```
Step 3f -- Log out of your MobiledgeX session
```
docker logout docker.mobiledgex.net
```

Step 3g -- Log into or pull up the MobiledgeX console https://console.mobiledgex.net/.

Step 16 -- https://sites.google.com/mobiledgex.com/doc/getting-started/how-to-deploy-container?authuser=0

Help Tip -- TRACE ID -- If you experience issues or your Docker Container does not deploy, we will ask you to let us know the "trace ID" number. To find your "trace id" number, look on the left nav for for "audit log", click on "audit log," new data should populate the three boxes within the right nav panel, find the box marked "raw viewer," scroll down to the bottom and you should see a JSON field called "trace id." Check out [this video](https://drive.google.com/open?id=1ypz_QiEbFUUhHGGqDty-DTdLCqlTUvVs) to see where to click in more detail. 

Bonus Points -- Type the following command to validate via the command line that your docker image is up and running without leaving the terminal. Your output should look like [this](https://drive.google.com/file/d/1BRLBm2D0MlPs3AWSyEK5kW--nZWOlktI/view?usp=sharing).
```
curl http://localhost:8090/
```

## Good to know Docker Commands

List all running docker containers. Output will be similar to [this]().
```
docker ps
```
Kill a specfic container. Output will be similar to [this]().
```
docker kill <containter ID>
```
List all images currently on your local machine. Output will be similar to [this](https://drive.google.com/file/d/1IfIiM2-WpjfYzUFH9NJV1ljBK-crwcu0/view?usp=sharing). Docker [documentation link](https://docs.docker.com/v17.12/edge/engine/reference/commandline/image_ls/). Relevant [stackoverflow link](https://stackoverflow.com/questions/30543409/how-to-check-if-a-docker-image-with-a-specific-tag-exist-locally)
```
docker images
```
