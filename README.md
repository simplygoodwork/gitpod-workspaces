# gitpod-workspaces
Docker images for use with Gitpod to provide a stable Craft development environment

## Create or update an image

To alter these you need to build a Docker image and upload it to Docker Hub. you’re going to need the following:
* A Docker Hub account.
* A running instance of the Docker engine.

### Prepare the Image

Create a new directory containing the Dockerfile and any associated files
- gitpod-8.0
    - client.cnf
    - Dockerfile
    - mysql.cnf

### Connect local terminal to Docker Hub account

We have to log into our Docker Hub account to push the new image. To successfully log into Docker Hub from the command line, you must first create an access token. Log in to Docker Hub and click your profile image. From the popup menu, select Account Settings. On the resulting page, click Security in the left navigation and then click New Access Token and follow the prompts and copy the access key.

```
docker login -u USER
```
 
Where USER is your Docker Hub username. You will be prompted for your Docker Hub password, where you’ll use the access token you just generated.

### How to build your image

It’s time to build our image. We’re going to name the image gitpod-test (note the period at the end). The `-m` flag increases memory

```
docker build -t gitpod-test . -m 4g
```

When the build completes, you’ll have a new image, named `gitpod-test`.

### How to tag and push the image

We’re going to tag our new image with `:latest` and then push it to Docker Hub.

```
docker image tag gitpod-test USER/gitpod-test:latest
```

Where USER is your Docker Hub username.
 
Now that the image is tagged, we can push it to Docker Hub with:

```
docker image push USER/gitpod-test:latest
```

When the push completes, you should find the image in your Docker Hub repository. And that’s all there is to building a Docker image and pushing it to your Docker Hub repository.

If there are permissions errors, may need to be run using sudo

### Examples

For PHP 8.0 simplygoodwork gitpod...
```
docker build -t gitpod-8.0 . -m 4g
docker image tag gitpod-8.0 simplygoodwork/gitpod-8.0:latest
docker image push simplygoodwork/gitpod-8.0:latest
```

For PHP 7.4 simplygoodwork gitpod...
```
docker build -t gitpod-7.4 .
docker image tag gitpod-7.4 simplygoodwork/gitpod-7.4:latest
docker image push simplygoodwork/gitpod-7.4:latest
```

### Free up local disk space

After all that you might want to free up some disk space.

```
docker system prune -a
```
