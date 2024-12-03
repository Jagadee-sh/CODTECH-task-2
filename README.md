# CODTECH-task-2
NAME:jagadeesh maddi
COMPANY:CODTECH it solutions
ID:CT6WDS2607
DURATION:nov 30 to jan 15


Here’s a guide to setting up a CI/CD pipeline with Jenkins for automating the build, test, and deployment processes of a simple application.


---

Step 1: Install and Configure Jenkins

1.1 Install Jenkins

1. Install Jenkins on Linux:

sudo apt update
sudo apt install openjdk-11-jdk -y
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt update
sudo apt install jenkins -y


2. Start Jenkins:

sudo systemctl start jenkins
sudo systemctl enable jenkins


3. Access Jenkins:
Open your browser and navigate to http://<server-ip>:8080. Use the initial password from /var/lib/jenkins/secrets/initialAdminPassword.


4. Install Plugins:
During setup, choose the suggested plugins or manually select required plugins like:

Git

Pipeline

Docker Pipeline

SSH Agent





---

1.2 Configure Jenkins

1. Create Credentials:

Navigate to Manage Jenkins > Manage Credentials.

Add credentials for:

Git: Repository credentials.

Docker: Username and access token.

SSH: Key for deployment servers.




2. Install Docker: Ensure Docker is installed on the Jenkins server if your pipeline uses Docker:

sudo apt install docker.io -y
sudo usermod -aG docker jenkins




---

Step 2: Create a Jenkins Pipeline

2.1 Application Structure

Use the earlier Flask application as the example app, assuming it is stored in a GitHub repository.




2.2 Jenkinsfile

The Jenkinsfile defines the CI/CD pipeline and is stored in the root of your repository.
#print the code that is in the repositoty


Step 3: Set Up Jenkins Job

1. Create a Pipeline Job:

Go to Jenkins Dashboard > New Item > Pipeline.

Name the job and select "Pipeline."



2. Configure the Job:

Pipeline Definition: Select "Pipeline script from SCM."

SCM: Choose Git and provide the repository URL.

Credentials: Add your Git credentials if required.

Branch: Specify the branch to build (e.g., main).



3. Save and Build:

Click "Save" and then "Build Now."





---

Step 4: Validate the Pipeline

1. Pipeline Stages:

Checkout Code: Verifies the repository checkout.

Build Docker Image: Builds the Docker image.

Test Application: Runs the application and tests the endpoint.

Push to Docker Hub: Pushes the image to Docker Hub.

Deploy to Server: Deploys the updated application to the production server.



2. Monitor Logs: View build logs in Jenkins for debugging.




---

Best Practices

1. Automate Testing: Add unit tests and include them in the pipeline.


2. Error Notifications: Use Jenkins plugins to send alerts on failures.


3. Environment Separation: Use different pipelines for development, testing, and production environments.


4. Secure Credentials: Use Jenkins credentials to manage sensitive information securely.


5. Scalability: Integrate with Kubernetes for container orchestration if needed.




---

This pipeline automates the entire CI/CD process, from code checkout to deployment, ensuring fast and reliable delivery. Let me know if you need further assistance with any part!

