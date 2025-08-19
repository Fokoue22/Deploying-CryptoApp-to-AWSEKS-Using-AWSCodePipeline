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
![Alt text](images/steps2-image.png)

### Verify Application Locally by opening your browser and navigate to the link bellow. You should see the login page of the crypto application.
```
http://localhost:8080/
```
![Alt text](images/login-page.png)


## Author
FOKOUE THOMAS