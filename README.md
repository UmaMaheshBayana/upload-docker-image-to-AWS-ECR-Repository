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
1) login to your AWS console and search for ECR(Elastic Container Registry) and open.
2) click on **get started** and Give your docker image name in the empty text box and save.
3) Repository Name will be created with repository details.
4) Select the repository and click on **view push commands**



<img width="154" alt="GFG" src="https://user-images.githubusercontent.com/108786040/181249656-c4bf039b-c396-4569-89ac-6dd4dc1b3475.jpg">





