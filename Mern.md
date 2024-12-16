>    #   **THE MERN STACK**
___
**The Mern Stack combines the followings:** 
>  * **MONGO DATABASE**
>  * **EXPRESS JS**
>  * **REACT**
>  * **NODE JS**

___
___

>  The First thing to do is starting up an Instance on AWS
![](assets/2024-11-22-17-31-12.png)
>   * **Security Group of the Instance allows**
>   *  **SSH ON PORT 22**
>   *  **HTTP ON PORT 80**
>   *  **HTTPS ON PORT 443**
>   *  **CUSTOM PORT 5000**
>   *  **CUSTOM PORT 3000**
>  ![alt text](sg1.png)

>  ## THE LINUX OS
>  **The Operating System in use is the **LINUX** used via a Window Terminal computer**

>  **This shows the SSH CONNECTION**
![](assets/2024-11-22-17-49-45.png)
>  **I update the OS using
> * **sudo apt update**
> * **sudo apt upgrade**
___
___
> **THE NODE.JS AND NODE PACKAGE MANAGER(npm)**
> * A confirmation that NODE AND ITS MANAGER(NPM) is successfully installed
> ![alt text](v.png)
> **Directory named TODO is created**
> ![alt text](TODO.png)
> **npm init** **is used to initialiase the TODO FOLDER**
![alt text](npm_init.png)
> * **PACKAGE.JSON is Present**
> #### EXPRESS.JS is installed using the ***npm install express***
> **index.js file is created empty and later opened using:**   ***vi index.js***
![alt text](index_vi.png)
> **Tested using:** ***node index.js***
![](port5000.png)
![alt text](we.png)
> **A new directory is created named ROUTES**
> **I change into the Directory then created a file named API.JS and opened using vim editor and write in necessary codes**
> * **mkdir Routes**
> * **cd Routes**
> * **touch api.js**
> * **vi api.js**
> ![alt text](api.js_confi.png)
##### I created a directory named ***MODELS*** and also install **mongoose** using:
* *mkdir models*
* *npm install mongoose*

within the model directory i created a file named it **todo.js** open the file and write in some codes

>> ***const mongoose = require('mongoose');
const Schema = mongoose.Schema;***

>> ***//create schema for todo
const TodoSchema = new Schema({
action: {
type: String,
required: [true, 'The todo text field is required']
}
})***

>> ***//create model for todo
const Todo = mongoose.model('todo', TodoSchema);***

>> ***module.exports = Todo;****

#### I modify the existing code in api.js to allow functionality

>> ***const express = require ('express');
const router = express.Router();
const Todo = require('../models/todo');***

>> **router.get('/todos', (req, res, next) => {***

 >> **//this will return all the data, exposing only the id and action field to the client
Todo.find({}, 'action')
.then(data => res.json(data))
.catch(next)
});***

 >> ***router.post('/todos', (req, res, next) => {
if(req.body.action){
Todo.create(req.body)
.then(data => res.json(data))
.catch(next)
}else {
res.json({
error: "The input field is empty"
})
}
});***

>> ***router.delete('/todos/:id', (req, res, next) => {
Todo.findOneAndDelete({"_id": req.params.id})
.then(data => res.json(data))
.catch(next)
})***

>> ***module.exports = router;***

> ## THE MONGODB
> **I registered via this link https://www.mongodb.com/products/try-free/platform/atlas-signup-from-mlab**

followed the prompt, later I created a cluster and a database and user
I allowed access from anywhere 
![alt text](db_access.png)
I process my database connection 
![alt text](db_connect1.png)
![alt text](db_code_copy.png)
then created an .env file through which i connected DATABASE
![alt text](vi.env.png)
I successfully connected my DATABASE
![alt text](13_kill_p_DB_test.png)
>#### **I downloaded a  postman  api**
I run an api post request 
![alt text](post_request.png)
and later run a get request
![c:\Users\USER\Pictures\get_request.png](get_request.png) they both show successfully
___
___ 
###  **THE FRONT END**
In the same root directory as My backend code, which is the Todo directory, I run:
 >> ***npx create-react-app client***; to create my front end app and a folder named **client** where all front end blocks of codes are
![alt text](react_client_install-1.PNG)

In  the Todo directory, I install legacy-peer-deps. it solves dependency tree conflict using:

>> * **npm install legacy-peer-deps**

In  the Todo directory, I Install concurrently. It is used to run more than one command simultaneously from the same terminal window. I use:
>> * **npm install concurrently --save-dev**

In the Todo directory, I Install nodemon. It is used to run and monitor the server. If there is any change in the server code, nodemon will restart it automatically and load the new changes. I use:
>> * **npm install nodemon --save-dev**

![](assets/2024-12-16-15-35-49.png)
**In Todo folder I open the package.json file using vim package.json and fill it with this.**

**I  change directory into the client folder and open the package.json file to add:**
>> * "proxy": "http://localhost:5000" **so the application can run on localhost** 

**Then I changed directory into **client** and later to sub-directory named **src** where I created a directory named **components** and changed directory into it**
**Within I created files named:
> * Input.js
> * ListTodo.js
> * Todo.js
![](assets/2024-12-16-16-20-46.png)
**I opened the Input.js via vim and paste code and confirmation**
![alt text](com_input.PNG)
**I confirmed that of ListTodo.js also:**
![alt text](listtodo.PNG)
**I also confirmed the Todo.js file**
![alt text](todo.js_conf.png)
**Changing directory into src folder, already created and opened the ***App.js****  and fill it with codes. this is about front end design**
![alt text](app_js.PNG)
**I did the same for the **App.css** and fill in the codes**
![alt text](App_css.PNG)
**The last blocks of code**
![alt text](ind_css.PNG)
**I run the command to bring up my built Application**
>> * npm run dev
**IT WORKS**  ![alt text](final_todo.PNG)