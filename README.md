##  Node on docker

[Tutorial](https://nodejs.org/en/docs/guides/nodejs-docker-webapp/)

[Pushing to gcloud](https://cloud.google.com/container-registry/docs/pushing-and-pulling?hl=en_US)

### Requirements:

 - [gcloud](https://cloud.google.com/sdk/docs/)
     - after install run:

        ` gcloud init `
     - configure auth with docker:

        ` gcloud auth configure-docker `

### Step by step:
1. Create package.json
2. Run `npm install`
3. Create server.js
4. Create Dockerfile
5. Create .dockerignore
6. Running docker
    * [BUILD] -t flag lets tagging the image so it's easier to find using 'docker images'

    	`	docker build -t manutheking199/node-web-app . `

    * [RUN] -d runs the container in detached mode, -p redirect publicPort:privatePort

    	` docker run -p 49160:8080 -d manutheking1991/node-web-app `
    * [COMMANDS]
        - `docker ps` &rarr; List the current running containers
        - `docker logs <container id>` &rarr; Redirects the output of the selected id
        - ` docker exec -it <container id> /bin/bash ` &rarr; SSHs to the container


### Push container to gcloud:
1. Define the hostname like `[HOSTNAME]/[PROJECT-ID]/[IMAGE]`
    - HOSTNAME: Where the image container will be stored: eu.grc.io
    - PROJECT_ID: here will be container-project
    - IMAGE: Anything you like

    `eu.gcr.io/container-project/node-container`
2. Tag the local image:
    - If tag is omitted it will use 'latest'

    `docker tag [local-continer-id] eu.gcr.io/container-project/node-container:[TAG]`

3. Push the image:
    - As well as tagging, if you specified a TAG, append it here too

    `docker push eu.gcr.io/container-project/node-container:[TAG]`

4. We can check the new container either on gcloud console or via CLI:

    `gcloud container images list-tags eu.gcr.io/container-project/node-container`

5. Pulling images from registry:
    - You can use the TAG:

    `docker pull eu.gcr.io/container-project/node-container:[TAG]`
    - Or the IMAGE_DIGEST (Listed on the previous step):

    `docker pull eu.gcr.io/container-project/node-container@[IMAGE_DIGEST]` 
