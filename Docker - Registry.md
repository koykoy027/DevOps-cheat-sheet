# How to push and pull in Docker Hub
  
### Push the image
1. Ensure you have already created a repository in your Docker Hub.
2. Sign in to Docker Hub using the `docker login -u <USERNAME>` command.
3. You'll need to tag your local images with the correct repository and tag them before pushing them to Docker Hub using `docker tag`.
```
docker tag <image>:<tag> <USERNAME>/<REPOSITORY_NAME>:<NEW-IMAGE-TAG>

# Sample
docker tag nginx:alpine javillanueva/repository:nginx-alpine
```

4. Push the images to Docker Hub
```
docker push <USERNAME>/<REPOSITORY_NAME>:<NEW-IMAGE-TAG>

# Sample
docker push javillanueva/repository:nginx-alpine
```

### Run the image on a new instance
5. Pull the image
```
docker pull <CONTAINER_NAME:TAG>

# Sample
docker pull javillanueva/repository:nginx-alpine
```

6. In the terminal, start your freshly pushed app
```
docker run -dp 0.0.0.0:80:80 javillanueva/repository:nginx-alpine
```

> reference [here](https://docs.docker.com/get-started/workshop/04_sharing_app/)
