# MobiledgeX_Hello_World

This demo application shows how to serve a simple HTML file via a NodeJS http server called "http-server" and can be found here: https://www.npmjs.com/package/http-server. Note that the Node http-server server defaults to port 8080. 

Step 1 -- Install NodeJS and Git -- https://nodejs.org/en/download/ && https://githowto.com/

Step 2 -- Open a terminal window and create a temporary directory (call it anything you want)

Step 3 -- Download the sample code with Git (make sure you are in your temp directory) and then CD into the directory after downloading the github repository -- Type the following command into your terminal:
```
git clone https://github.com/skydvr01/Docker_NodeJS_Hello_World.git
```
Step 5 -- Verify that the same files you see on the Github repository webpage are the same files you see in the local directory. Your local directory should look like this: 
```
ls
```

Step 4 -- Install the necessary NodeJS dependencies (http-server module in this case) by typing the following:
```
npm install
```

Step 4 -- Type "npm start" -- This will start the http-server server 
```
npm start
```
Step 5 -- Press "Command" button and click the link provided. You should see this <show image> in a new browser window. Congrats! You started a webserver and served up index.html! 

Step 6 -- Build the docker image (don't forget the period at the end of this command!).
```
docker image build -t test:1.0 .
```
Step 7 -- Run the docker image you just created
```
docker container run --publish 8090:8000 --detach test:1.0
```
* "publish 8090:8000" -- This tells docker to forward traffic incoming on the host’s port 8090 (your computer), to the container’s port 8000 (containers have their own private set of ports, so if we want to reach one from the network, we have to forward traffic to it in this way; otherwise, firewall rules will prevent all network traffic from reaching your container, as a default security posture).
* "detach" --Tells Docker to run this container in the background so that you don't have to open a new terminal window
Step 8 -- Type "localhost:8090" into a new browser window and you should see [this](https://drive.google.com/file/d/14t0eEVYtIQVjNQ90StxgV-cC_DAqfBey/view?usp=sharing). Congrats! You have just dockerized a webpage and served it up via NodeJS!

Step 9 -- Log into https://console.mobiledgex.net/. If you do not have an account or are not provided one, please speak to the event organizer or email support@. 

Step 10 -- Open a terminal and type the following command. This should list the docker image you just created from the steps above. 
```
docker image ls
```

Step 11 -- Log into the MobiledgeX Platform.
```
docker login -u <your_user_name__remember_it_is_not_your_email> docker.mobiledgex.com
```

Step 12 -- 
```
docker tag
```

Step 13 -- Push your image to the MobiledgeX Docker Repository.
```
docker push
```
Step 14 -- Log out of your MobiledgeX session
```
docker logout
```

Step 15 -- Log into or pull up the MobiledgeX console https://console.mobiledgex.net/.

Step 16 -- https://sites.google.com/mobiledgex.com/doc/getting-started/how-to-deploy-container?authuser=0




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
