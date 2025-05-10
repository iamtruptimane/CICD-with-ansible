# Jenkins Declarative CICD Pipeline using AWS Cloud and Docker Hub

## **Introduction to configuring Jenkins Declarative Pipeline with AWS Cloud integration.**

![](https://miro.medium.com/v2/resize:fit:700/1*zUoT-sTzQhSdsKyJoAzVZg.png)

## **Jenkins Declarative Pipeline:**

Jenkins is an open-source automation server that helps automate various aspects of software development, including building, testing, and deploying applications. The Declarative Pipeline is a more structured and opinionated way to define your build and deployment pipelines as code. It provides a simpler syntax and enforces best practices, making it easier to create, understand, and maintain pipelines.

## **Integration with AWS Cloud:**

Integrating Jenkins Declarative Pipeline with AWS Cloud allows you to automate the deployment of your applications and infrastructure on Amazon Web Services (AWS).

## **Benefits of Jenkins Declarative Pipeline with AWS Cloud:**

- **Automation:** Jenkins automates the deployment process, reducing manual intervention and potential errors.
- **Versioned Pipelines:** Pipeline configurations are stored as code (Jenkinsfile), allowing versioning, collaboration, and auditability.
- **Scalability:** AWS Cloud offers scalable infrastructure, allowing you to deploy applications as needed.
- **Consistency:** Declarative Pipelines enforce a consistent structure and best practices, making pipelines easier to understand and maintain.
- **Flexibility:** You can customize your pipeline stages to fit your specific application deployment requirements.

## **Project description:**

1. The project aims to automate the building, testing and deployment process of web application using GitHub, Jenkins, Docker and AWS.
2. The pipeline will include stages such as check out code from GitHub, building, creating docker image, pushing image to docker hub, deployment on EC2 server.

## **Use the following:**

1. **Java**: Required for Jenkins installation.
2. **Git**: As a version control system for the program.
3. **Jenkins**: To create the build pipeline.
4. **Docker**: To build and create docker image.
5. **DockerHub**: To store docker image.
6. **AWS EC2**: To deploy the application.

## **Step 1: Create AWS EC2 Instance.**

![](https://miro.medium.com/v2/resize:fit:700/1*dSMpjXRu5_AmN58WtVOWtQ.png)

![](https://miro.medium.com/v2/resize:fit:700/1*MFoS3phFz4bTyA6In_77Qg.png)

EC2 Instance is Created

![](https://miro.medium.com/v2/resize:fit:700/1*hYsRmyVFKyAtbg0-O2hotA.png)

Connect to EC2 Instance

![](https://miro.medium.com/v2/resize:fit:700/1*k-lwkO-LKgojBghwxA1b3Q.png)

Connected to EC2 Instance

## **Step 2: Update the Server**

> sudo apt update
> 
> 
> git clone [https://github.com/SudheerBarakers/Django-Notes-App.git](https://github.com/SudheerBarakers/Django-Notes-App.git)
> 
> cd Django-Notes-App
> 
> sudo apt install git docker.io -y
> 
> sudo usermod -aG docker ubuntu
> 
> sudo reboot
> 

![](https://miro.medium.com/v2/resize:fit:700/1*JJ8BblL_iFWl5y1FJwIA8Q.png)

![](https://miro.medium.com/v2/resize:fit:700/1*5ChTMaXVM6VWP4IUzG_z9g.png)

![](https://miro.medium.com/v2/resize:fit:700/1*QPTz1FqK2hquz_v1TA7c1Q.png)

## **Step 3: Shell Script to install Java and Jenkins on EC2 Server**

![](https://miro.medium.com/v2/resize:fit:700/1*eC_JimwmzwZyzj1bvTk1cw.png)

![](https://miro.medium.com/v2/resize:fit:700/1*7GhF8GlIKnJx7yGu87YoBw.png)

After running the script

![](https://miro.medium.com/v2/resize:fit:700/1*F0o6y30uVomPB2pLHJYhGQ.png)

Edit inbound rules under security to open port number 8080 to access Jenkins.

![](https://miro.medium.com/v2/resize:fit:700/1*UjajZtSLyK7QXI5H99rCOg.png)

![](https://miro.medium.com/v2/resize:fit:700/1*o9UVE-PypymsTAGqIcusQQ.png)

![](https://miro.medium.com/v2/resize:fit:700/1*ierl-EPRRBxVd2mBwql09g.png)

## **Step 3: Dockerfile**

Create a Dockerfile with the following content:

![](https://miro.medium.com/v2/resize:fit:700/1*hoOQLNtzhjxiEQb-7_AssQ.png)

Dockerfile

## **Build the Docker image by running:**

> docker build -t sudheerbaraker/my-note-app:latest .
> 
> 
> docker images
> 

![](https://miro.medium.com/v2/resize:fit:700/1*Ujf0lUwzjD7dI9O9MIMYLQ.png)

## **Step 4: Creating a Declarative Pipeline**

![](https://miro.medium.com/v2/resize:fit:700/1*NLLz1OA3dzbzfXZzgut0Wg.png)

Create a New Job

![](https://miro.medium.com/v2/resize:fit:700/1*HnIf2YJZdjpYui0FGjYgzw.png)

Give Project Repo

![](https://miro.medium.com/v2/resize:fit:700/1*aMltlpCeqfyb8ybqP6ce7Q.png)

For Automatic build from GitHub

In the “Pipeline” section, choose “Pipeline Script” and add the following script:

![](https://miro.medium.com/v2/resize:fit:700/1*b09dJIaAJtWQrzNNS8hEPw.png)

# **Before building, make sure to follow these additional steps:**

Add DockerHub credentials in the global credentials section with the ID as “dockerhub” along with the username and password.

![](https://miro.medium.com/v2/resize:fit:700/1*9P3n9-66kVJS77pFhRn6Dw.png)

Once everything is set up, you can manually trigger the pipeline by clicking the **build button** in the Jenkins interface.

![](https://miro.medium.com/v2/resize:fit:700/1*qQbUT-As6RRt508TQcuvgg.png)

After successful build, docker image is created and pushed to docker hub.

![](https://miro.medium.com/v2/resize:fit:700/1*45PEnXCx8ZLW70kyWxuSgA.png)

Docker Image created

![](https://miro.medium.com/v2/resize:fit:700/1*EGH7L0OT6gjMR69LfhnrOg.png)

Pushed Image to Docker Hub

Note App is Succefully deployed.

![](https://miro.medium.com/v2/resize:fit:700/1*m8yEz5qxIg1EoNkHHHauKw.png)

Congratulations! Note App is now deployed and ready to use. Enjoy the benefits of automation and continuous integration.

# **Bonus Step: Full Automation with Webhooks**

To achieve full automation, configure webhooks so that any changes pushed to the GitHub repository will trigger the Jenkins pipeline and initiate the deployment process automatically.

🔹 Further Simplification with “Pipeline Script from SCM”

To make your pipeline more effective and easier to modify, you can use “Pipeline Script from SCM.” This approach allows you to provide a GitHub repository link containing the **Jenkinsfile**. By adopting this method, any developer in your team with proper permissions can review and modify the Jenkinsfile, simplifying the pipeline management process.

## **Jenkinsfile**

![](https://miro.medium.com/v2/resize:fit:700/1*ltaJzAf5SvtX1qlJeSUiDw.png)

![](https://miro.medium.com/v2/resize:fit:700/1*vozIQCG4Br8idctr3-LSRA.png)

Pipeline Script from SCM

![](https://miro.medium.com/v2/resize:fit:700/1*rZzIt_RlJsEcXZMNVXvqKg.png)

Webhook Configuration

```
Auto-trigger Jenkins pipeline using webhook

New commit: changed the content in project
```

After new commit in the code, build will start automatically.

![](https://miro.medium.com/v2/resize:fit:700/1*MBMuvqNR2MS63lJWGNciwg.png)

Build Success

![](https://miro.medium.com/v2/resize:fit:700/1*m8yEz5qxIg1EoNkHHHauKw.png)

# **Conclusion**

In this blog, we explored the step-by-step process of configuring a Jenkins declarative pipeline using AWS Cloud. By following the outlined instructions, you can automate your development workflow, enhance collaboration, and achieve continuous integration.

## **Let’s summarize the key points covered:**

1️. We started by setting up an EC2 server with the necessary ports enabled, allowing us to establish a secure connection.

2. After connecting to the server, we updated the server, installed Git, and Docker, and cloned the project repository.

3️. Dockerfile was created to define the Docker image configuration, and we built the image using the Docker build command.

4️. Java JDK and Jenkins were installed using a shell script, granting Jenkins access to build and run Docker images.

5️. We accessed Jenkins through the browser, installed the required plugins, and created a declarative pipeline to automate the CI/CD process.

6️. The pipeline consisted of stages such as cloning the code, building the image, pushing it to Docker Hub, and deploying the container.

7️. We discussed additional steps, including adding DockerHub credentials and triggering the pipeline with webhooks.

8️. Lastly, we highlighted the benefits of using “Pipeline Script from SCM” to simplify pipeline modifications and encourage team collaboration.

By implementing this Jenkins declarative pipeline configuration, you can streamline your software development process, reduce manual efforts, and achieve faster and more reliable deployments.