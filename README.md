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

 ![image](https://github.com/user-attachments/assets/62cf04dd-753c-46b6-8dfc-c5b283ba8a51)


  
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
    
    ![image](https://github.com/user-attachments/assets/3b5ec61a-c025-49fd-a788-363039b78e8d)




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
  
 ![image](https://github.com/user-attachments/assets/4d93d7c5-4b38-4405-88e9-bec8dcdf3ed6)




## 1.4 Push the code to your Github repository

After initializing your Git repository and adding your e-commerce website template, the next step is to push your code to a remote repository on GitHub. This step is crucial for version control and collaboration.


- Create a Remote Repository on GitHub: Log into your GitHub account and create a new repository named "MarketPeak_Ecommerce". Leave the 
  repository empty without initializing it with a README, gitignore, or license.


  ![image](https://github.com/user-attachments/assets/368fb42c-2dbd-4d12-88e7-d97315f345d6)



 

- Leave the repository empty without initializing it with a README, gitignore, or license.



  ![image](https://github.com/user-attachments/assets/cd7cfd01-eabb-487c-bce3-a90d11e95afb)

  


  
- ﻿﻿Link Your Local Repository to GitHub: In your terminal, within your project directory, add the remote repository URL to your local repository configuration.

   ```
    git remote add origin https://github.com/your-git-username/MarketPeak_Ecommerce.git

  ```
 Note: Make sure you replace "your-git-username" with your actual git username
-  Push Your Code: Upload your local repository content to GitHub.
  ```
    git branch -M main
    git push -u origin main

  ```
  
 ![image](https://github.com/user-attachments/assets/16a63266-1916-4267-a542-74104505753e)



  
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


    ![image](https://github.com/user-attachments/assets/9ccd8230-446f-4ff9-a5bc-d4cab59e1a80)



SSH Method:

- On your EC2 instance, generate SSH keypair using ssh-keygen.
  
  ![image](https://github.com/user-attachments/assets/bf49ac7e-b28c-499f-9cb8-79522e89e39a)




- Display and Copy your public key
  
  ```
       cat ~/.ssh/id_rsa.pub 
  ```
  ![image](https://github.com/user-attachments/assets/51258190-63e7-4ba8-9731-d4f567347a49)



Note: Your ssh public key will different
- Add the SSH public key to your GitHub
   click on the profile image of your git repository (top right hand side) => Settings => "ssh and gpg keys" => "new ssh key" => paste the copied ssh key => click "save key"

  ![image](https://github.com/user-attachments/assets/13405af2-5a65-47de-ba89-5946212ccec4)


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

  ![image](https://github.com/user-attachments/assets/4cfc0db7-7d94-4dea-aa0a-84358ecc2b06)


  
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

![image](https://github.com/user-attachments/assets/60e4014c-5122-45a4-afb5-13a2dec5aa3d)



The directory /var/www/html/ is a standard directory structure on Linux systems that host web content, particularly for the Apache HTTP Server.
When you install Apache on a Linux system, the installation process automatically creates this directory. It's designated as the default document root in Apache's configuration, meaning that Apache is set up to serve web files (such as HTML, CSS, and JavaScript files) located in this directory to visitors of your website.


- Reload httpd: Apply the changes by reloading the httpo service.

```
  sudo systemctl reload httpd

```

2.5. Access Website from Browser

- ﻿﻿With httpd configured and website files in place, MarketPeak Ecommerce platform is now live on the internet
- ﻿﻿Open a web browser and access the public IP of your EC2 instance to view the deployed

  ![image](https://github.com/user-attachments/assets/e179f11c-136d-4292-845c-9c78d2a3cefc)




## 3. Continuous Integration and Deployment Workflow
To ensure a smooth workflow for developing, testing, and deploying your e-commerce platform, follow this structured approach. It covers making changes in a development environment, utilizing version control with Git, and deploying updates to your production server on AWS.

Step 1: Developing New Features and Fixes

- Create a Development Branch: Begin your development work by creating a separate branch. This isolates new features and bug fixes from the stable version of your website.

  ```

  git branch development
  git checkout development

  ```

  ![image](https://github.com/user-attachments/assets/f2a0fe6e-0fa0-4f73-85f4-b65e43c12bde)



- Implement Changes: On the development branch, add your new features or bug fixes. This might include updating web pages, adding new products, or fixing known issues.


  ![image](https://github.com/user-attachments/assets/84874b40-70d2-40e2-a450-9686bfdc81a4)



Step 2: Version Control with Git

- Stage Your Changes: After making your changes, add them to the staging area in Git. This prepares the changes for a commit.


  ```
   git add .
  
  ```

  ![image](https://github.com/user-attachments/assets/90e01231-ba3e-4b17-bf03-4be74f06bfef)




- Commit Your Changes: Securely save your changes in th Include a descriptive message about the updates.



   ```

    git commit -m "Add new features or fix bugs"


  ```


  ![image](https://github.com/user-attachments/assets/1dcdc05f-8103-4dee-bdee-c1f4eaa43618)

  
  

- Push Changes to GitHub: Upload your development branch with the new changes to GitHub. This enables collaboration and version tracking.


  ```

    git push origin development


  ```

  ![image](https://github.com/user-attachments/assets/9b6f01a9-8aec-4428-9d1c-577c2c18301c)




Step 3: Pull Requests and Merging to the Main branch

- Create a Pull Request (PR): On GitHub, create a pull request to merge the development branch into the main branch. This process is crucial for code review and maintaining code quality.


  ![image](https://github.com/user-attachments/assets/de566bf5-b788-46d0-83c5-aa4044f767d1)



- Review and Merge the PR: Review the changes for any potential issues. Once satisfied, merge the pull request into the main branch, incorporating the new features or fixes into the production codebase.


  
  ```

    git checkout master
    git merge development

  ```


  ![image](https://github.com/user-attachments/assets/579addf4-d796-47f2-947c-cffa0c70be1c)


- Push the Merged Changes to GitHub: Ensure that your local main branch, now containing the updates, is pushed to the remote repository on GitHub.

  ```

      git push origin main

  ``` 


  ![image](https://github.com/user-attachments/assets/5b065cb2-a6a2-4d6c-9c21-c31657ed2a99)



Step 4: Deploying Updates to the Production Server


- Pull the Latest Changes on the Server: SSH into your AWS EC2 instance where the production website is hosted. Navigate into directory where you cloned the website and pull the latest changes from the main branch.

  ![image](https://github.com/user-attachments/assets/5a3bae12-5c2e-439f-b8e7-b78f5b5fbe23)



-  Now copy the changes to the httpd directory
 
```
  sudo cp -r ~/MarketPeak_Ecommerce/* /var/www/html/

``` 

-  Restart the Web Server (if necessary): Depending on the nature of the updates, you may need to restart the web server to apply the changes.

```

      sudo systemctl reload httpd

```

  ![image](https://github.com/user-attachments/assets/74369671-e10d-43d3-9f69-d2d7ec7643cb)



Step 5: Testing the New Changes

- Access the Website: Open a web browser and navigate to the public IP address of your EC2 instance. Test the new features or fixes to ensure they work as expected in the live environment.
  From the Image above, We can see that the modification of "Gerald Oti interior" we made on the index.html file of the title section has now reflected on the webpage.

This workflow emphasizes best practices in software development and deployment, including branch management, code review through pull requests, and continuous integration/ deployment strategies. By following these steps, you maintain a stable and up-to-date production environment for your e-commerce application.

