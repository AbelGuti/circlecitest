# Dependencies

### Install Docker
* https://docs.docker.com/install/#support
* Install Docker CE
* Test successful installation:  `docker --version`

### Install Docker-Compose
* https://docs.docker.com/compose/install/
* Install Docker-Compose tool
* Test successful installation:  `docker-compose --version`

### Install and configure the aws-cli
* https://aws.amazon.com/cli/?nc1=h_ls
* Install and configure your aws-cli
* Test successful installation:  `docker --version`

# Bringing it up

1. Clone this repository in your workstation

2. Run the following command to download the environments variables and the frontend application files (dont forget the ".").

```
aws s3 sync s3://tpc-local-development . 
```
- Be sure that you have the `/efs` directory and the `.env.develop.local` file at the same directory level than your code is.

3. Inside of your code directory, run the following command

```
docker-compose build
```
- This will create all your containers so it will take a while the first time that you run this command in your machine because it needs to download some docker images first.

4. (Optional) Try to run this command

```
docker images
```

- After that you should see the images that were downloaded from the previous command.

5. Now lets start our application. First at all, be sure that is nothing running in the ports 3306, 6379 and 8080 in your local computer. Then procede running this

```
docker-compose up
```

- This will start your docker-compose infrastructure, you also can run this command like a background just adding the `-d` flag like This

```
docker-compose up -d
```

6. (Optional) You can verify by your self if the containers are running with this command

```
docker ps
```

- Running this command you should see 3 containers running, one mysql, one redis and the tomcat container.

7. Go to your browser and access to http://localhost:8080/ping,html. If you get a 200 http code all went good.
