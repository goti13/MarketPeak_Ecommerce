# E-Commerce Platform Deployment with Git, Linux, and AWS

## Scenario

You are assigned to develop an e-commerce website for a new online marketplace named "MarketPeak." 
This platform will feature product listings, a shopping cart, and user authentication. 
Your objective is to utilize Git for version control, develop the platform in a Linux environment, and deploy it on an AWS EC2 instance. 
A suitable website template is found [here](https://www.tooplate.com/) to kickstart this development journey.


## Tasks

## 1.0 Implement Version Control with Git

## 1.1. Initialize Git Repository

- Begin by creating a project directory named "Market_Peak_Ecommerce"
- ﻿﻿Inside this directory, initialize a Git repository to manage your version control.
  ```
    mkdir MarketPeak_Ecommerce 
    cd MarketPeak_Ecommerce
    git init
  
  ```

  <img width="637" alt="image" src="https://github.com/user-attachments/assets/815d99a6-9ce5-48d1-823c-bf625e8a0276">

  
## 1.2. Obtain and Prepare the E-Commerce Website Template

Instead of developing the website from scratch, I’ll use a pre-existing e-commerce website template. This approach allow me to focus on the deployment and operational aspects, rather than on web development. The actual web development is done by web/ software developers on the project.

- ﻿﻿Download a Website Template: Visit [Tooplate](https://www.tooplate.com/) or any other free template resource, and download a suitable e-commerce website template. Look for templates that are ready to use and require minimal adjustments.
- ﻿﻿It is recommended you download the specific [template](https://www.tooplate.com/view/2133-moso-interior)
- ﻿﻿Prepare the Website Template: Extract the downloaded template into your home directory. Copy all the contents of the extracted folder "2133_moso_interior" into the the project folder "MarketPeak_Ecommerce" and delete the extracted folder afterwards.

    ```
      unzip ~/Downloads/2133_moso_interior.zip -d ~/ > /dev/null 2>&1
      cp -r ~/2133_moso_interior/* ~/test/MarketPeak_Ecommerce/
      rm -r ~/2133_moso_interior/
      
    ```
    
    <img width="637" alt="image" src="https://github.com/user-attachments/assets/e5f327da-32a0-4831-b310-376812181cb8">



- ﻿﻿Customize the Template (Optional): If desired and you have basic web development skills, you can make minor customizations to the template to tailor it to "MarketPeak" This might include updating logos, changing color schemes, or modifying text to better fit the marketplace's brand identity.

## 1.3. Stage and Commit the Template to Git

- ﻿﻿Add your website files to the Git repository.
- ﻿﻿Set your Git global configuration with your username and email.
-  ﻿﻿Commit your changes with a clear, descriptive message.

  ```
    git add .
    git config --global user. name "YourUsername"
    git config --global user.email "youremail@example.com"
    git commit -m "Initial commit with basic e-commerce site structure"

  ```
  
  <img width="932" alt="image" src="https://github.com/user-attachments/assets/3995a443-066d-45b7-9e3b-607f2829cbdc">


## 1.4 Push the code to your Github repository

After initializing your Git repository and adding your e-commerce website template, the next step is to push your code to a remote repository on GitHub. This step is crucial for version control and collaboration.


- Create a Remote Repository on GitHub: Log into your GitHub account and create a new repository named "MarketPeak_Ecommerce". Leave the 
  repository empty without initializing it with a README, gitignore, or license.


  <img width="292" alt="image" src="https://github.com/user-attachments/assets/9ed4ce87-9062-44af-b580-bf7ac935bb93">


 

- Leave the repository empty without initializing it with a README, gitignore, or license.



  <img width="641" alt="image" src="https://github.com/user-attachments/assets/eace259f-2f6d-4ca1-8069-ef56e12a54b4">
  


  
- ﻿﻿Link Your Local Repository to GitHub: In your terminal, within your project directory, add the remote repository URL to your local repository configuration.

   ```
    git remote add origin https://github.com/goti13MarketPeak_Ecommerce.git

  ```
 Note: Make sure you replace "your-git-username" with your actual git username
-  Push Your Code: Upload your local repository content to GitHub.
  ```
    git branch -M main
    git push -u origin main

  ```
  
 <img width="843" alt="image" src="https://github.com/user-attachments/assets/ebda504a-2414-4320-88eb-a0a9d15a2d5a">


  
  This command pushes your commits from your local main branch to the remote repository on GitHub, enabling you to store your project in the cloud and share it with others.

## 2.0 AWS Deployment

To deploy "MarketPeak_Ecommerce" platform, you'll start by setting up an Amazon EC2 instance:

2.1. Set Up an AWS EC2 Instance

- ﻿﻿Log in to the AWS Management Console.
- ﻿﻿Launch an EC2 instance using an Amazon Linux AMI.
- ﻿﻿Connect to the instance using SSH.

2.2. Clone the repository on the Linux Server
Before deploying your e-commerce platform, you need to clone the GitHub repository to your AWS EC2 instance. This process involves authenticating with GitHub and choosing between two primary methods of cloning a repository: SSH and HTTPS. To see the ssh or http link to clone your repository

1. ﻿﻿﻿Navigate to your repository in github console
2. ﻿﻿﻿Select the code as highlighted in the image below.
   <img width="672" alt="tPeak_Ecommerce" src="https://github.com/user-attachments/assets/86ae49a3-fbb8-4451-bd5d-a00919a800e1">


SSH Method:

- On your EC2 instance, generate SSH keypair using ssh-keygen.
  
  <img width="634" alt="image" src="https://github.com/user-attachments/assets/7e10dc80-0c96-4062-91b2-cfa6e3d25640">



- Display and Copy your public key
  
  ```
       cat ~/.ssh/id_rsa.pub 
  ```
  <img width="562" alt="image" src="https://github.com/user-attachments/assets/81f7cea7-dfa5-4202-8c17-e1f1c3fcec02">


Note: Your ssh public key will different
- Add the SSH public key to your GitHub
   click on the profile image of your git repository (top right hand side) => Settings => "ssh and gpg keys" => "new ssh key" => paste the copied ssh key => click "save key"
   <img width="969" alt="Pasted Graphic 12" src="https://github.com/user-attachments/assets/96e5b027-ae13-4f2e-aee0-f37d739011e5">

- Install git

  ```
      sudo yum install git -y

  ```
   Use the SSH clone URL to clone the repository:
   ```
    git clone git@github.com:yoursername/MarketPeak_Ecommerce.git

   ```


HTTPS Method:
For repositories that you plan to clone without setting up SSH keys, use the HTTPS URL. GitHub will prompt for your username and password:
 
  ```
  git clone https://github.com/yourusername/MarketPeak_Ecommerce.git

  ```

  <img width="648" alt="image" src="https://github.com/user-attachments/assets/6c5caf61-5a6b-4a6b-91f5-ae4ff29969ae">

  
2.3. Install a Web Server on EC2

Apache HTTP Server (httpd) is a widely used web server that serves HTML files and content over the internet. Installing it on Linux EC2 server allows you to host MarketPeak E-commerce site:
- Install Apache web server on the EC2 instance. Note that httpd is the software name for Apache on systems using yum package manager

```
sudo yum update -y
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd

```

This first updates the linux server and then installs httpd (Apache), starts the web server, and ensures it automatically starts on server boot.

2.4. Configure httpd for Website

To serve the website from the EC2 instance, configure httpd to point to the directory on the Linux server where the website code files are stored. Usually in /var/www/html.
- Prepare the Web Directory: Clear the default httpd web directory and copy MarketPeak Ecommerce website files to it.

```
  sudo rm -rf /var/www/html/*
  sudo cp -r ~/MarketPeak_Ecommerce/* /var/www/html/

```

<img width="757" alt="image" src="https://github.com/user-attachments/assets/1f42f78b-6b04-4d80-9924-cb4ca6be6321">


The directory /var/www/html/ is a standard directory structure on Linux systems that host web content, particularly for the Apache HTTP Server.
When you install Apache on a Linux system, the installation process automatically creates this directory. It's designated as the default document root in Apache's configuration, meaning that Apache is set up to serve web files (such as HTML, CSS, and JavaScript files) located in this directory to visitors of your website.


- Reload httpd: Apply the changes by reloading the httpo service.

```
  sudo systemctl reload httpd

```

2.5. Access Website from Browser

- ﻿﻿With httpd configured and website files in place, MarketPeak Ecommerce platform is now live on the internet
- ﻿﻿Open a web browser and access the public IP of your EC2 instance to view the deployed

  <img width="900" alt="image" src="https://github.com/user-attachments/assets/06a1c587-524c-4e3e-a174-ed5446827ca5">



## 3. Continuous Integration and Deployment Workflow
To ensure a smooth workflow for developing, testing, and deploying your e-commerce platform, follow this structured approach. It covers making changes in a development environment, utilizing version control with Git, and deploying updates to your production server on AWS.

Step 1: Developing New Features and Fixes

- Create a Development Branch: Begin your development work by creating a separate branch. This isolates new features and bug fixes from the stable version of your website.

  ```

  git branch development
  git checkout development

  ```

  <img width="424" alt="image" src="https://github.com/user-attachments/assets/972af215-19d1-472a-b7dd-c0b42c8d39c3">


- Implement Changes: On the development branch, add your new features or bug fixes. This might include updating web pages, adding new products, or fixing known issues.


  <img width="821" alt="image" src="https://github.com/user-attachments/assets/682cec9f-b6f0-460e-88a4-6712432f03cc">


Step 2: Version Control with Git

- Stage Your Changes: After making your changes, add them to the staging area in Git. This prepares the changes for a commit.


  ```
   git add .
  
  ```

  <img width="656" alt="image" src="https://github.com/user-attachments/assets/af0d0f27-c676-406a-828c-3d90da5e209f">



- Commit Your Changes: Securely save your changes in th Include a descriptive message about the updates.



   ```

    git commit -m "Add new features or fix bugs"


  ```


  <img width="422" alt="image" src="https://github.com/user-attachments/assets/8f4c183c-ccaf-43c5-85a8-a4de25399e63">
  
  

- Push Changes to GitHub: Upload your development branch with the new changes to GitHub. This enables collaboration and version tracking.


  ```

    git push origin development


  ```

  ![image](https://github.com/user-attachments/assets/bd7a607c-7f22-446a-a743-0e7d4a1adc9a)



Step 3: Pull Requests and Merging to the Main branch

- Create a Pull Request (PR): On GitHub, create a pull request to merge the development branch into the main branch. This process is crucial for code review and maintaining code quality.


  <img width="708" alt="image" src="https://github.com/user-attachments/assets/4cf1cde0-3c49-478c-a7f2-466dbcf1772f">


  <img width="854" alt="image" src="https://github.com/user-attachments/assets/d8bb7d49-179b-483f-9c88-7ed0a65fee90">




- Review and Merge the PR: Review the changes for any potential issues. Once satisfied, merge the pull request into the main branch, incorporating the new features or fixes into the production codebase.


  
  ```

    git checkout master
    git merge development

  ```


  <img width="432" alt="image" src="https://github.com/user-attachments/assets/4d95a353-fa43-4962-b521-17c7bd59b799">

- Push the Merged Changes to GitHub: Ensure that your local main branch, now containing the updates, is pushed to the remote repository on GitHub.

  ```

      git push origin main

  ``` 

  <img width="489" alt="image" src="https://github.com/user-attachments/assets/7d710a82-031d-408d-8317-baabe2f63379">


Step 4: Deploying Updates to the Production Server


- Pull the Latest Changes on the Server: SSH into your AWS EC2 instance where the production website is hosted. Navigate into directory where you cloned the website and pull the latest changes from the main branch.

  <img width="561" alt="image" src="https://github.com/user-attachments/assets/48af553e-cabf-4bb0-98f3-454cf67126f4">


-  Now copy the changes to the httpd directory
 
```
  sudo cp -r ~/MarketPeak_Ecommerce/* /var/www/html/

``` 

-  Restart the Web Server (if necessary): Depending on the nature of the updates, you may need to restart the web server to apply the changes.

```

      sudo systemctl reload httpd

```

  <img width="988" alt="image" src="https://github.com/user-attachments/assets/1c5b3acc-b1f5-45b1-8b96-c2cd32d4d562">


Step 5: Testing the New Changes

- Access the Website: Open a web browser and navigate to the public IP address of your EC2 instance. Test the new features or fixes to ensure they work as expected in the live environment.

This workflow emphasizes best practices in software development and deployment, including branch management, code review through pull requests, and continuous integration/ deployment strategies. By     following these steps, you maintain a stable and up-to-date production environment for your e-commerce

