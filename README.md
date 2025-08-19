# Deploying-CryptoApp-to-AWSEKS-Using-AWSCodePipeline
Deploying a Crypto App to AWS EKS Using AWS CodePipeline, Docker, Terraform, Amazon ECR &amp; S3 Artifact

# PROJECT OVERVIEW
In this project, we will deploy a `Flask-based Crypto Application` using a fully automated CI/CD pipeline on `AWS EKS`. The application is written in Python and features a basic login page. Upon successful login, the user is redirected to a product page where they can purchase crypto tokens and crypto-based products.


## `Step 1:` Writing the Dockerfile for Local Testing

Before jumping into the deployment pipeline, it is important to containerize the application and test it locally. Below is the Dockerfile that we use to build the Flask app.
### Dockerfile

```
# Use an official Python runtime as a parent image
FROM public.ecr.aws/docker/library/python:3.11-bullseye

# Set the working directory in the container
WORKDIR /usr/src/app

# Copy the current directory contents into the container at /usr/src/app
COPY . .

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Make port 5000 available to the world outside this container
EXPOSE 5000

# Define environment variable
ENV FLASK_APP=app.py
ENV FLASK_RUN_HOST=0.0.0.0

# Run flask application
CMD ["flask", "run"]

```

## `Step 2:` Build and Run the Application Locally with Docker

Open your terminal, navigate to the root directory of your project, and run the following commands:
### Build the Docker Image
```
docker build -t crypto-app .
```
### Run the Docker Container
```
docker run -d --name crypto-app -p 8080:5000 crypto-app
```
### Verify Application Locally by opening your browser and navigate to the link bellow. You should see the login page of the crypto application.
```
http://localhost:8080/
```
![Alt text](images/login-page.png)






































![Alt text](Ansible-ubuntu-controller-1.png)

### Write a playbook with four (4) plays:
* Play1: Deploy apache on ubuntu clients
* Play2: Deploy apache on amazon clients
* Play3: Deploy git on amazon linux clients
* Play4: Deploy git on ubuntu clients

# STEPS BY STEPS PROCESS 

### 1. Launched 3 amazon linux 2 and 2 ubuntu server:

![image](https://github.com/Fokoue22/ANSIBLE-Project-on-AWS/assets/117523566/652c366e-9281-4c62-ab97-9560917463e8)


### 2. Installed ansible on linux-ansible-controller:

![image](https://github.com/Fokoue22/ANSIBLE-Project-on-AWS/assets/117523566/b44759ac-f49a-4102-acee-deaae6d83818)


### 3. Verified ansible is installed in linux-ansible-controller. And generated ssh key-pair. Copied the public key to all 4 nodes:

<img width="512" alt="image" src="https://github.com/Fokoue22/ANSIBLE-Project-on-AWS/assets/117523566/088d1bbd-a60b-441e-9b36-99c90b0a2390">


### 4. Updated “hosts” file in ansible-controller.

![image](https://github.com/Fokoue22/ANSIBLE-Project-on-AWS/assets/117523566/ae396a32-ee5a-4d9a-af68-18d0a6fb98ff)


### 5. Test the connectivity in-between the controller and nodes:

<img width="590" alt="image" src="https://github.com/Fokoue22/ANSIBLE-Project-on-AWS/assets/117523566/dffc2ab1-b43b-4a9e-bb38-ba771cc1cbd0">

![image](https://github.com/Fokoue22/ANSIBLE-Project-on-AWS/assets/117523566/a0f79a1a-2dd3-410c-bdde-452a0f8c9c46)


### 6. Run ansible-hw-playbook.yml file

![image](https://github.com/Fokoue22/ANSIBLE-Project-on-AWS/assets/117523566/e7502d8e-7abf-4fb0-b97c-775c844cd65d)

![image](https://github.com/Fokoue22/ANSIBLE-Project-on-AWS/assets/117523566/2557550e-851e-4ef5-accf-98254a3a55b4)


### 7. Connect to linux-node1 i.e. “ansible-linux-node1” and verify that index.html file is written in /var/www/html

![image](https://github.com/Fokoue22/ANSIBLE-Project-on-AWS/assets/117523566/a0ab4ddc-f45f-4797-b57e-50ded432d027)


### 8. Connect to ubuntu-node1 i.e. “ansible-node1” and verify that index.html file is written in /var/www/html

![image](https://github.com/Fokoue22/ANSIBLE-Project-on-AWS/assets/117523566/a73aef8d-0195-45e5-b497-4cde2b51104b)


### 9. Verify GIT is installed in both linux and ubuntu nodes:
![image](https://github.com/Fokoue22/ANSIBLE-Project-on-AWS/assets/117523566/8c53e5b4-d676-4d7e-bee9-9435f725447c)

![image](https://github.com/Fokoue22/ANSIBLE-Project-on-AWS/assets/117523566/390358c6-d5c5-4ec5-9521-8346ec8e6aa7)




## Author
FOKOUE THOMAS