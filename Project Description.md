# SIMPLE TO-DO APPLICATION ON MERN WEB STACK
In this project, you are tasked to implement a web solution based on MERN stack in AWS Cloud.

1. MERN Web stack consists of following components:
2. MongoDB: A document-based, No-SQL database used to store application data in a form of documents.
3. ExpressJS: A server side Web Application framework for Node.js.
4. ReactJS: A frontend framework developed by Facebook. It is based on JavaScript, used to build User Interface (UI) components.
5. Node.js: A JavaScript runtime environment. It is used to run JavaScript on a machine rather than in a browser.


## Step 1 – Backend configuration
Update ubuntu
*sudo apt update*

img

Upgrade ubuntu
*sudo apt upgrade*

img

Lets get the location of Node.js software from Ubuntu repositories.
*curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -*

img

Install Node.js on the server
*sudo apt-get install -y nodejs*

img

Verify the node installation with these commands 
*node -v* & *npm -v*

img

##### Application Code Setup

Create a new directory for your To-Do project:
*mkdir Todo*
Run the command below to verify that the Todo directory is created with ls command
ls

img

Change the current directory to Todo directory and use the command *npm init* to initialise your project, so that a new file named package.json will be created.

