---
id: middlewares
aliases: []
tags: []
---
# middlewares
The logic to perform checks and validation

**middleware as a function**

```js
const express = require("express");
const app = express();

function userMiddleware(req,res,next){
    if(usename != "Victon" && password != "fail"){
        res.status(403).json({
           msg:"Incorrect inputs",
        });
    } else {
        next();
    }
};
function kidneyMiddleware(req,res,next){
    if(kidneyId != 1 && kidneyID != 2){
        res.status(403).json({
            msg:"Incorrect inputs"
        })
    } else {
        next();
    }
};
app.get("/health-checkup",userMiddleware,kidneyMiddleware,function(req,res){
    //logic
    res.send("your heart is healthy");
});
app.listen(3000);
```
**USE**

```js
const express = require("express");
const app = express();
numberOfRequests = 0;
function calculateRequests(req,res,next){
    numberOfRequests++;
    console.log(numberOfRequests);
    next();
}
app.use(calculateRequestes); //middlewares
app.use(express.json()); //middlewares
app.get("/health-checkup",function(req,res){
    //logic
    res.send("your heart is healthy");
});
//global-catches: error handling middlewares
app.send(err,req,res,next){
    res.json({
        msg:"Something messed up"
    })
}
app.listen(3000);
```

# ZOD
```js
const zod = require("zod");
const express = require("express");
const app = express();
function validateInput(obj){}
    const schema = zod.object({
        email: zod.string().email().endsWith("@google.com"),
        password: zod.string().min(8)
    })
    const response = schema.safeParse(obj);
    console.log(response.errors)
    console.log(response);
}
validateInput({
    email:"abcds@gmail.com",
    password:"adfasedew"
});
app.post("/login",function(req,res){
    const response = validateInput(req.body)
    if(!response.success){
        res.json({
            msg:"your input are invalid"
        })
        return;
    }
})
app.listen(3000);
//coercion for primitive
//const schema = z.coerce.string();
```
---
- Zod infer
```ts
const signupInput = z.ooject({
  username = z.string(),
  password = z.string(),
})
type SignUpParams = z.infer<typeof signupInput>
```

Mupliple middlewares
---
```js
const express = require("express");
const app = express();
const middlewares = [express.json,userValidaton,kidneyValidation];
app.get("/",...middlewares,function(req,res){

})
app.listen(3000);
```
# Fetch API
```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset = "utf-8">
        <meta name = "viewport", content = "with-devicw-with">
        <title>new page</title>
        <link href = "style.css", rel ="stylesheet", type = "text/css"" \>
    </head>
    <body>
        <script>
        async function getAnimalData(){
            const response = await fetch("https://fakerapi.it/api/v1/persons");
            const finalData = await response.json();
            document.getElementById('userData').innerHTML = JSON.stringif(finalData)
            }
        </script>
        <div id="userData"></div>
        <button onclick = 'getAnimalData()'>Click Me!</button>
    </body>
</html>
```
---
```js
function main(){
  fetch("https://sum-server.100xdevs.com/todos",{
    method:"POST",
    body:{
      username:"victon",
      password:"13456"
    },
    headers:{
      "Authorization":"Bearer 123"
    }
  })
    .then(async (response)=>{
      const json = await response.json();
      console.log(json.todos.length);
    })
}
main();
```
# axios API
For mehods that can send a body their sescond argument is a body
```js
const axios = require("axios");
async function main(){
  const response = await axios.post("https://sum-server.100xdevs.com/todos",{
    username:"Viction",
    password:"243546"
    },
    {
      headers:{
        Authorization:Bearer 123",
      }
    }
  );
  console.log(response.data.todos.length);
}
```
---
```js
const axios = require("axios");
async function main(){
  const response = await axios(
    {
      url: "https://sum-server.100xdevs.com/todos",
      method: "POST",
      headers:{
        Authorization:Bearer 123",
      },
      data:{
        username:"Viction",
        password:"243546"
      },
    }
  );
  console.log(response.data.todos.length);
}
```
# Authentication
### JWT (JSON Web Token)
long text that has three parts
```js

const express = require('express');
const jwt = require("jsonwebtoken");
const jwtPassword = "123456";

const app = express();

const ALL_USERS = {
    {
        username:"victon@gmail.com",
        password:"123",
        name:"Avi",
    },
    {
        username:"rampriya@gmail.com",
        password:"123321",
        name:"Ramya Rampriya",
    },
    {
        username:"prashasti@gmail.com",
        password:"123321",
        name:"Prashas",
    },
};
function userExists(username,password){
    let userExists = false;
    for (let i=0; i<ALL_USERS.length;i++){
        if(ALL_USERS[i].username==username&&ALL_USERS[i].password==password){
            userExists = true;
        }
    }
    return userExists;
}
app.post("/signin",function(req,res){
    const username = req.body.uesrname;
    const password = req.body.password;

    if(!userExists(username, password)){
        return res.status(403).json({
            msg: "User doesn't exists in our db",
        });
    }

    var token = jwt.sign({username: username}, "shhhh");
    return res.json({
        token,
    });
    // to set expiration to a token
    //jwt.sign({expiresAt:new Date().getTime() = 3600})
});

app.get("/users",function(req,res){
    const token = req.headers.authorization;
    // fetch localstorage
    //fetch("asd.com",{headers:{Authorization:"Bearer"+localStorage.getItem("token")}})
    try{
        const decoded = jwt.verify (token,jwtPassword);
        const username = decoded.username;
        res.json({
        //returns list of users other other than this username
            users:ALL_USERS.filter(function(value){
                if (value.username==username){
                    return false;
                } else {
                    return true;
                }
            })
        })
    } catch(err){
        return res.status(403).json({
            msg: "Invalid user",
        });
    }
});

app.listen(3000);
```
# mongoose online
```js
const express = require('express');
const mongoose = require('mongoose');
const app = express();
app.use(express.json())
mongoose.connect('URL');
cosnt User = mongoose.model('Users',{name:String,email:String,password:String});
app.post('/signin',function(req,res){
    const username = req.body.username;
    const password = req.body.password;
    const name = req.body.name;
    const existingUser  = await User.findOne({email:username});
    if(existingUser){
        return res.status(403).send('Username already exists')
    }
    // await User.create({name:name,email:username,password:password})
    const user = new User({
        name:name,
        email:username,
        password:password,
    });
    user.save();
    res.json({
        msg:'User created successfully'
    })
})
app.listen(3000);
```
