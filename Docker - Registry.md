# How to push and pull Docker registry
  
### Push the image
1. Ensure you have already created a repository in your Docker Hub.
2. Sign in to Docker Hub using the `docker login -u <USERNAME>` command.
3. You'll need to tag your local images with the correct repository and tag them before pushing them to Docker Hub using `docker tag`.
```
# skeleton
docker tag <image>:<tag> <USERNAME>/<REPOSITORY_NAME>:<NEW-IMAGE-TAG>

# sample
docker tag nginx:alpine <javillanueva/repository:nginx-alpine
```

4. Push the images to Docker Hub
```
# skeleton
docker push <USERNAME>/<REPOSITORY_NAME>:<NEW-IMAGE-TAG>

# sample
docker push javillanueva/repository:nginx-alpine
```

### Run the image on a new instance
- 

> reference [here](https://docs.docker.com/get-started/workshop/04_sharing_app/)