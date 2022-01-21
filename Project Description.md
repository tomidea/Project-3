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

<img width="272" alt="package json" src="https://user-images.githubusercontent.com/51254648/150437880-48c19659-def1-4662-9043-f871adf3faff.png">



### INSTALL EXPRESSJS
To use express, install it using npm:
*npm install express*

<img width="605" alt="install npm express" src="https://user-images.githubusercontent.com/51254648/150437886-65313d32-919b-4fc8-ad24-66b0f6fbfc81.png">


Now create a file index.js with the command below
*touch index.js*
Run ls to confirm that your index.js file is successfully created

<img width="395" alt="create indexjs" src="https://user-images.githubusercontent.com/51254648/150437891-8a847254-e434-49e1-9df5-d300d379c4dd.png">


Install the dotenv module
*npm install dotenv*

<img width="363" alt="install dotenv" src="https://user-images.githubusercontent.com/51254648/150437893-b3b4c382-9adc-453f-8982-817fddd19883.png">


Open the index.js file with the command below
*vim index.js*
 
 <img width="661" alt="indexjs cmd" src="https://user-images.githubusercontent.com/51254648/150437895-93341d05-ac5e-4b97-8993-7143b026cc52.png">

Now it is time to start our server to see if it works.
*node index.js*

<img width="347" alt="server running 5000" src="https://user-images.githubusercontent.com/51254648/150437898-6e7f73db-98ab-458a-a5b3-dd3ab8392791.png">


Open port 5000 in EC2 Security Groups

<img width="1137" alt="create inbound rule" src="https://user-images.githubusercontent.com/51254648/150437900-cba0f40e-308f-411c-bad3-e37c3194b32a.png">


Lets try to access our server’s Public IP or Public DNS name followed by port 5000: http://'PublicIP-or-PublicDNS':5000

<img width="1280" alt="welcome to express" src="https://user-images.githubusercontent.com/51254648/150437902-702e2d69-6317-41da-933a-a709dbab672b.png">


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

<img width="359" alt="routes todo api" src="https://user-images.githubusercontent.com/51254648/150437904-4d90616e-c1f8-4786-8abf-84a736e28b86.png">

Open the file with this command vim api.js and paste the code below

<img width="369" alt="apijs code" src="https://user-images.githubusercontent.com/51254648/150437907-4de5a249-0003-4ff0-88ac-797e55cf8f4c.png">



## MODELS
The app is going to make use of Mongodb which is a NoSQL database, we need to create a model. A model is at the heart of JavaScript based applications, and it is what makes it interactive.
To create a Schema and a model, install mongoose which is a Node.js package that makes working with mongodb easier. Change directory back Todo folder with cd .. and install Mongoose
*npm install mongoose*

<img width="376" alt="install mongose" src="https://user-images.githubusercontent.com/51254648/150437911-67fe6c79-4a2a-4cc3-90d5-7a345e20a7a4.png">


Create a new folder  models :
*mkdir models*
Change directory into the newly created ‘models’ folder with
*cd models*
Inside the models folder, create a file and name it todo.js
*touch todo.js*
Open the file created with *vim todo.js* then paste the code below in the file:

<img width="373" alt="todojs code" src="https://user-images.githubusercontent.com/51254648/150437913-0225b79f-c872-473d-9c6d-3d4ef2d21faa.png">


In Routes directory, open api.js with vim api.js, delete the code inside with :%d command and paste there code below into it then save and exit

<img width="605" alt="new apijscode" src="https://user-images.githubusercontent.com/51254648/150437915-f4d4cfc5-bc0a-4379-97e2-52e12f3df6c9.png">

Open Input.js file and paste the code below into it

<img width="659" alt="new indexjs code" src="https://user-images.githubusercontent.com/51254648/150437917-2d15a000-3ceb-4cbb-9187-5629948c967b.png">

## MONGODB DATABASE
We need a database where we will store our data. For this we will make use of mLab. mLab provides MongoDB database as a service solution (DBaaS.
In the index.js file, we specified process.env to access environment variables, but we have not yet created this file. So we need to do that now.
Create a file in your Todo directory and name it .env.
touch .env
vi .env
Add the connection string to access the database in it, just as below:

*DB = 'mongodb+srv://<username>:<password>@<network-address>/<dbname>?retryWrites=true&w=majority'*

  <img width="767" alt="connection string" src="https://user-images.githubusercontent.com/51254648/150437921-3cc292a4-13b5-4b34-99ca-05397521cf84.png">

Now we need to update the index.js to reflect the use of .env so that Node.js can connect to the database.
Simply delete existing content in the file, and update it with the entire code below.
 
const express = require('express');
const bodyParser = require('body-parser');
const mongoose = require('mongoose');
const routes = require('./routes/api');
const path = require('path');
require('dotenv').config();

const app = express();

const port = process.env.PORT || 5000;

//connect to the database
mongoose.connect(process.env.DB, { useNewUrlParser: true, useUnifiedTopology: true })
.then(() => console.log(`Database connected successfully`))
.catch(err => console.log(err));

//since mongoose promise is depreciated, we overide it with node's promise
mongoose.Promise = global.Promise;

app.use((req, res, next) => {
res.header("Access-Control-Allow-Origin", "\*");
res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");
next();
});

app.use(bodyParser.json());

app.use('/api', routes);

app.use((err, req, res, next) => {
console.log(err);
next();
});

app.listen(port, () => {
console.log(`Server running on port ${port}`)
});
 
  
Start your server using the command:
*node index.js*

 <img width="323" alt="db connect successful" src="https://user-images.githubusercontent.com/51254648/150437923-dfd95b95-4f14-4585-8fe4-e8f7c6deb510.png">

  
 ##### Testing Backend Code without Frontend using RESTful API
  In this project, I will use Postman to test our API. Create a POST request to the API http://'PublicIP-or-PublicDNS':5000/api/todos. This request sends a new task to our To-Do list so the application could store it in the database.
 
  <img width="852" alt="post " src="https://user-images.githubusercontent.com/51254648/150437925-d15af7ce-3d9f-4ceb-81bb-64a8a6dca598.png">

 <img width="862" alt="Get" src="https://user-images.githubusercontent.com/51254648/150437927-a59819d6-a958-484d-a5ea-87103430d065.png">

  <img width="845" alt="Delete" src="https://user-images.githubusercontent.com/51254648/150437931-b628f43b-7b28-4460-8e07-9a028b988634.png">

  
  ## STEP 2 – FRONTEND CREATION
  In the same root directory as our backend code, which is the Todo directory, run:
*npx create-react-app client*
 
  <img width="659" alt="create client" src="https://user-images.githubusercontent.com/51254648/150437934-68b47265-9d8b-46d8-bdfa-aa4ed6805a63.png">

 This will create a new folder in our Todo directory called client, where you will add all the react code.
  

  
  ##### Running a React App

Before testing the react app, there are some dependencies that need to be installed.

Install concurrently. It is used to run more than one command simultaneously from the same terminal window.
*npm install concurrently --save-dev*
  
  <img width="582" alt="install concurently" src="https://user-images.githubusercontent.com/51254648/150437936-ce77b5f2-b065-4ba2-b5e2-338fb622c8bf.png">

Install nodemon. It is used to run and monitor the server. If there is any change in the server code, nodemon will restart it automatically and load the new changes.
*npm install nodemon --save-dev*
  
  <img width="1239" alt="install no demon" src="https://user-images.githubusercontent.com/51254648/150437939-5c8c3f62-4970-422e-a8a9-950e23fd973e.png">

In Todo folder open the package.json file. Change the highlighted part of the below screenshot and replace with the code below.
  "scripts": {
"start": "node index.js",
"start-watch": "nodemon index.js",
"dev": "concurrently \"npm run start-watch\" \"cd client && npm start\""
},

  <img width="562" alt="package json code" src="https://user-images.githubusercontent.com/51254648/150437944-2dc9fca8-8c60-414f-b82c-ee6ae74182b2.png">
  
  
##### Configure Proxy in package.json
Change directory to ‘client’
*cd client*
Open the package.json file
*vi package.json*
Add the key value pair in the package.json file "proxy": "http://localhost:5000".
 
  <img width="387" alt="proxy packagejson" src="https://user-images.githubusercontent.com/51254648/150437943-bbb9f124-7e96-47cd-87da-f44dbaf91e2c.png">


Run this command in the Todo directory:
*npm run dev*
 open the application on port: 3000
  
  <img width="1257" alt="react page" src="https://user-images.githubusercontent.com/51254648/150437949-2de58171-287b-4ad0-9ac7-e9bb40687479.png">

  
  
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
 
  <img width="518" alt="inputjs code" src="https://user-images.githubusercontent.com/51254648/150437953-a7c802c0-895d-4792-b91a-fe5faa543015.png">

 Move to the client folder and Install Axios
  *npm install axios*

  <img width="1280" alt="Npm install axios" src="https://user-images.githubusercontent.com/51254648/150437959-bc0b997c-4be6-4c66-9c8e-9049589c7aef.png">
  
Go to ‘components’ directory
*cd src/components*
After that open your ListTodo.js *vi ListTodo.js* and paste the code below
 
  <img width="560" alt="Listtodojjs code" src="https://user-images.githubusercontent.com/51254648/150437962-538810bb-dd37-4b27-9696-f79204ac3851.png">

  Then in your Todo.js file you write the following code
  
  <img width="513" alt="Todo code" src="https://user-images.githubusercontent.com/51254648/150437964-0d060445-1d82-4371-acc4-cfe025c55d66.png">

  In src folder open App.js and paste the code below:
  
  <img width="280" alt="new appjs code" src="https://user-images.githubusercontent.com/51254648/150437968-2377767c-a9be-496e-b554-c7d981f712cb.png">

  Open App.css and paste the code below:
  
  <img width="381" alt="new appcss code" src="https://user-images.githubusercontent.com/51254648/150437970-a066e46a-da33-4ba2-9418-d66287375b9c.png">

  open index.css and paste the code below:
  
  <img width="573" alt="new indexcss code" src="https://user-images.githubusercontent.com/51254648/150437972-a6aac5f6-dd3c-4b35-b265-2bc811fd34df.png">

  
  Go to Todo directory and run *npm run dev*
  <img width="1264" alt="Todo app" src="https://user-images.githubusercontent.com/51254648/150437975-bfbecf2f-5cad-4380-8e2d-915ef29e32c0.png">

  


  
<img width="1264" alt="Todo app" src="https://user-images.githubusercontent.com/51254648/150437975-bfbecf2f-5cad-4380-8e2d-915ef29e32c0.png">
