# sit323-2025-prac5d

## Overview
This project demonstrates the deployment of a simple microservice to Google Cloud's Artifact Registry.

## Prerequisites
- Google Cloud SDK
- Docker
- Node.js
- Git
- Visual Studio (for editing)

## Steps
1. **Create Google Cloud Artifact Registry Repository using terminal or through GCC itself**
    **TERMINAL**
   - Use the `gcloud` command to create a Docker repository.
   - Command:
     ```bash
     gcloud artifacts repositories create microservice --repository-format=docker --location=australia-southeast2
     ```

     **WEBSITE**
     - Log in to your Google Cloud account.
    - Navigate to **Artifact Registry**.
    - Click **Create Repository**.
    - Set the **Repository name** (e.g., `microservice`).
    - Set the **Location** to `australia-southeast2`.
    - Select **Docker** as the format and click **Create**.


2. **Authenticate with Google Cloud Artifact Registry**
   - Use the following command to authenticate Docker with Google Cloud:
     ```bash
     gcloud auth configure-docker australia-southeast2-docker.pkg.dev
     ```

3. **Build the Docker Image**
   - Navigate to the project directory and run:
        docker build -t my-microservice .
    

4. **Tag and Push the Docker Image**
   - Tag the image:
     ```bash
     docker tag my-microservice:v1 australia-southeast2-docker.pkg.dev/sit323-25t1-shailen-b727fe1/microservice/my-microservice:v1
     ```
   - Push to Google Cloud:
     ```bash
     docker push australia-southeast2-docker.pkg.dev/sit323-25t1-shailen-b727fe1/microservice/my-microservice:v1
     ```

5. **Run the Docker Container**
   - To check if the image is running:
     ```bash
     docker run -d -p 3000:3000 australia-southeast2-docker.pkg.dev/sit323-25t1-shailen-b727fe1/microservice/my-microservice:v1
     ```

## Conclusion
The microservice is successfully deployed to Google Cloud's Artifact Registry. It runs on port 3000 and can be accessed locally.
