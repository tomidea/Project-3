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

Run the command ls to confirm that you have package.json file created.
img


### INSTALL EXPRESSJS
To use express, install it using npm:
*npm install express*
img

Now create a file index.js with the command below
*touch index.js*
Run ls to confirm that your index.js file is successfully created
img

Install the dotenv module
*npm install dotenv*
img

Open the index.js file with the command below
*vim index.js*
img

Now it is time to start our server to see if it works.
*node index.js*
img

Open port 5000 in EC2 Security Groups
img

Lets try to access our server’s Public IP or Public DNS name followed by port 5000: http://'PublicIP-or-PublicDNS':5000
img

##### Routes
There are three actions that our To-Do application needs to be able to do:
1. Create a new task
2. Display list of all tasks
3. Delete a completed task
Each task will be associated with some particular endpoint and will use different standard HTTP request methods: POST, GET, DELETE.
For each task, we need to create routes that will define various endpoints that the To-do app will depend on. So let us create a folder routes
*mkdir routes*
Change directory to routes folder
*cd routes*
Now, create a file api.js with the command below
*touch api.js*
img
Open the file with this command vim api.js and paste the code below
img


## MODELS
The app is going to make use of Mongodb which is a NoSQL database, we need to create a model. A model is at the heart of JavaScript based applications, and it is what makes it interactive.
To create a Schema and a model, install mongoose which is a Node.js package that makes working with mongodb easier. Change directory back Todo folder with cd .. and install Mongoose
*npm install mongoose*
img

Create a new folder  models :
*mkdir models*
Change directory into the newly created ‘models’ folder with
*cd models*
Inside the models folder, create a file and name it todo.js
*touch todo.js*
Open the file created with *vim todo.js* then paste the code below in the file:
img

In Routes directory, open api.js with vim api.js, delete the code inside with :%d command and paste there code below into it then save and exit
img


## MONGODB DATABASE
We need a database where we will store our data. For this we will make use of mLab. mLab provides MongoDB database as a service solution (DBaaS.
In the index.js file, we specified process.env to access environment variables, but we have not yet created this file. So we need to do that now.
Create a file in your Todo directory and name it .env.
touch .env
vi .env
Add the connection string to access the database in it, just as below:

*DB = 'mongodb+srv://<username>:<password>@<network-address>/<dbname>?retryWrites=true&w=majority'*
img  
Now we need to update the index.js to reflect the use of .env so that Node.js can connect to the database.
Simply delete existing content in the file, and update it with the entire code below.
  img
 
  
Start your server using the command:
*node index.js*
img
  
 ##### Testing Backend Code without Frontend using RESTful API
  In this project, I will use Postman to test our API. Create a POST request to the API http://'PublicIP-or-PublicDNS':5000/api/todos. This request sends a new task to our To-Do list so the application could store it in the database.
  img
  img
  img
  
  ## STEP 2 – FRONTEND CREATION
  In the same root directory as our backend code, which is the Todo directory, run:
*npx create-react-app client*
  img
 This will create a new folder in our Todo directory called client, where you will add all the react code.
  img
  
  ##### Running a React App

Before testing the react app, there are some dependencies that need to be installed.

Install concurrently. It is used to run more than one command simultaneously from the same terminal window.
*npm install concurrently --save-dev*
  img
Install nodemon. It is used to run and monitor the server. If there is any change in the server code, nodemon will restart it automatically and load the new changes.
*npm install nodemon --save-dev*
  img
In Todo folder open the package.json file. Change the highlighted part of the below screenshot and replace with the code below.
  "scripts": {
"start": "node index.js",
"start-watch": "nodemon index.js",
"dev": "concurrently \"npm run start-watch\" \"cd client && npm start\""
},
  img
  
##### Configure Proxy in package.json
Change directory to ‘client’
*cd client*
Open the package.json file
*vi package.json*
Add the key value pair in the package.json file "proxy": "http://localhost:5000".
  img

Run this command in the Todo directory:
*npm run dev*
 open the application on port: 3000
  img
  
  
 ##### Creating your React Components
  From your Todo directory run
  *cd client*
  move to the src directory
*cd src*
Inside your src folder create another folder called components
*mkdir components*
  Move into the components directory with
*cd components*
Inside ‘components’ directory create three files Input.js, ListTodo.js and Todo.js.
*touch Input.js ListTodo.js Todo.js*
Open Input.js file
*vi Input.js*
Copy and paste the following
  img
 Move to the client folder and Install Axios
  *npm install axios*
Go to ‘components’ directory
*cd src/components*
After that open your ListTodo.js *vi ListTodo.js* and paste the code below
  img
  Then in your Todo.js file you write the following code
  img
  In src folder open App.js and paste the code below:
  img
  Open App.css and paste the code below:
  img
  open index.css and paste the code below:
  img
  
  Go to Todo directory and run *npm run dev*
  img
  

