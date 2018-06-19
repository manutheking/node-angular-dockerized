
## Node on docker

[Tutorial](https://nodejs.org/en/docs/guides/nodejs-docker-webapp/)

### Requirements:

 - [gcloud](https://cloud.google.com/sdk/docs/)
     - after install run:

        ```gcloud init
        ```
     - configure auth with docker:

        ```gcloud auth configure-docker
        ```

### Step by step:
1. Create package.json
2. Run ```npm install```
3. Create server.js
4. Create Dockerfile
5. Create .dockerignore
6. Running docker
    * [BUILD] -t flag lets tagging the image so it's easier to find using 'docker images'

    ```docker build -t manutheking199/node-web-app .
    ```

    * [RUN] -d runs the container in detached mode, -p redirect publicPort:privatePort

    ```docker run -p 49160:8080 -d manutheking1991/node-web-app
    ```
    * [COMMANDS]
        - docker ps &rarr; List the current running containers
        - docker logs <container id> &rarr; Redirects the output of the selected id
        - docker exec -it <container id> /bin/bash &rarr; SSHs to the container
        -
