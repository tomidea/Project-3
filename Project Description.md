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

<img width="867" alt="apt updaate" src="https://user-images.githubusercontent.com/51254648/150159501-430e488a-8937-4eb4-beaf-874e0b58b972.png">

Upgrade ubuntu
*sudo apt upgrade*

<img width="1269" alt="apt upgrade" src="https://user-images.githubusercontent.com/51254648/150159520-52eca013-f10d-481b-a015-29a78f87d24a.png">

Lets get the location of Node.js software from Ubuntu repositories.
*curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -*

<img width="1220" alt="locate nodejs" src="https://user-images.githubusercontent.com/51254648/150159524-b1748f86-e77b-42ef-8edc-2115407b68a8.png">

Install Node.js on the server
*sudo apt-get install -y nodejs*

<img width="775" alt="Install nodejs" src="https://user-images.githubusercontent.com/51254648/150159528-071804a8-c10d-4983-98d4-88d5d774a1e4.png">

Verify the node installation with these commands 
*node -v* & *npm -v*

<img width="257" alt="verify node" src="https://user-images.githubusercontent.com/51254648/150159530-87d19a58-5ca8-4a20-8b18-3e0e5442afe3.png">




##### Application Code Setup

Create a new directory for your To-Do project:
*mkdir Todo*
Run the command below to verify that the Todo directory is created with ls command
ls

<img width="264" alt="Create Todo dir" src="https://user-images.githubusercontent.com/51254648/150159532-04482223-65c5-4e5f-ac24-7069f4cf3e0f.png">

Change the current directory to Todo directory and use the command *npm init* to initialise your project, so that a new file named package.json will be created.

<img width="582" alt="init project" src="https://user-images.githubusercontent.com/51254648/150159535-70dfc326-6608-4f97-9a42-b630c54c28a7.png">
