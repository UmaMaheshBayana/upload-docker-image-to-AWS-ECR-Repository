# UPLOAD DOCKER IMAGE TO AWS ECR

**STEP-1**

Connect to AWS EC2 machine.

**STEP-2**

Install docker on you EC2 linux machine

```curl -fsSL https://get.docker.com -o get-docker.sh```

```sh get-docker.sh```

```exit```

Login Again

```sudo usermod -aG docker $USER```

To check the Docker Containers

```docker ps -a```

If you get permission denied execute the below command

```sudo chmod 666 /var/run/docker.sock```

Command to check Docker images

```docker images```

**STEP-3**
1) login to your AWS console and search for ECR(Elastic Container Registory) and open.
2) click on **get started** and Give your docker image name in the empty text box and save.
3) Repository Name will be created with repository details.

**STEP-4**

**Create IAM authentications to access AWS EC2 machine to ECR repository**

1) Login to aws account and create a IAM user in IAM service

2) Give Admin full access policy to the user 

3) Download the Access key and Secret key form there.

4) Create IAM role with EC2 policy and attach to the particular instance

5) Install awscli on the EC2 machine.

```sudo apt-get install awscli -y```

6) configure Access Key and Secret Key.

```aws configure```

7) Enter download Acces Key, Secret Key, Region, Language. By this IAM authentication will be saved to upload docker image to ECR.

**STEP-5**

**UPLOAD DOCKER IMAGE TO ECR CREATED**

1) login to your AWS console and search for ECR(Elastic Container Registory) and open the repositorys.
2) Here select the repository cerated and click on view push commands.
3) Retrieve an authentication token and authenticate your Docker client to your registry.
4) Check authentication token which we will use for uploding docker image.

```aws ecr get-login --region ap-south-1```

5) Copy the authentication token and past in the above cmd. 

```docker login -u AWS -p $TOKEN  -e none https://$REPOSITORYID.dkr.ecr.ap-south-1.amazonaws.com```

6) Build your Docker image using the following command. For information on building a Docker file from scratch see the instructions here . You can skip this step if your image is already built:

```docker build -t $IMAGE```

7) After the build completes, tag your image so you can push the image to this repository:

```docker tag $IMAGE:latest $REPOSITORYID.dkr.ecr.ap-south-1.amazonaws.com/mongo:latest```

8) Run the following command to push this image to your newly created AWS repository:

```docker push $REPOSITORYID.dkr.ecr.ap-south-1.amazonaws.com/$IMAGE:latest```

<img width="154" alt="GFG" src="https://user-images.githubusercontent.com/108786040/181249656-c4bf039b-c396-4569-89ac-6dd4dc1b3475.jpg">





