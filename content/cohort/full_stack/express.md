---
id: express
aliases: []
tags: []
---

# HTTP
- Ecmascript : documentation of how JS will work
- web browser engines
    - V8
    - spidermonkey
- compilers
    - Node js
    - Bun

- HTTP server : has frontend and backend
- HTTP protocol : way computer communicates
----
1. browser parses the URL
2. does DNS lookup
3. establishes a connection

----
`https://chat.openai.com/backend-api/conversation`
Protocol-URL-Route
- HTTP request
    header
        cookie
        authorization
    body
    method
- HTTP response
    header
    body
    status code
        - 200
        - 403
        - 404
        - 500
- DNS resolution : registering URL to IP

# Express
- basic http server

Protocols
```javascript
const express = require("express");
const app = express();
const users = [{
    name:"Victon",
    kidneys: [{
        healthy:false
    }]
}];
app.use(express.json());
app.get("/",function(req,res){
    const johnKidneys = users[0].kidneys;
    const numberOfKidneys= johnKidneys.length;
    let numberOfHealthyKidneys = 0;
    for (let i=0;i<johnKidneys.length;i++){
        if (johnKidneys[i].healthy){
            numberOfHealthyKidneys = numberOfHealthyKidneys + 1;
        }
    }
    const numberOfUnhealthyKidneys = numberOfKidneys - numberOfHealthyKidneys;
    res.json({
        numberOfKidneys,
        numberOfHealthyKidneys,
        numberOfUnhealthyKidneys,
    })
})
app.post("/",function(req,res){
    const isHealthy = res.body.isHealthy;
    users[0].kidneys.push({
        healthy:isHealthy
    })
    res.json({
        msg:"done!"
    })
})
//411
app.put("/",function(req,res){
    for (let i=0;i<users[0].kidneys.length;i++){
        users[0].kidneys[i].healthy = true;
    }
    res.json({});
})
//removing all the unhealthy kidneys
app.delete("/",function(req,res){
    if(isThereAtLeastOneUnhealthyKidney()){
        const newKidneys = [];
        for (let i=0;i<users[0].kidneys.length;i++){
            if (users[0].kidneys[i].healthy){
                newKidneys.push({
                    healthy: true;
                })
            }
        }
        users[0].kidneys = newKidneys;
        res.json({msg:"done"})
    } else {
        res.status(411).json({
            msg:"You have no bad kidneys"
        })
    }
})
function isThereAtLeastOneUnhealthyKidney(){
    let atleastOneUnhealthyKidney = false;
    for(let i=0; i<users[0].kidneys.length;i++){
        if(!users[0].kidneys[i].healthy){
            atleastOneUnhealthyKidney = true;
        }
    }
    return atleastOneUnhealthyKidney
}
app.listen(3000);
```

BODY
```javascript
const express = require('express')
const bodyParser = require("body-parser");
const port = 3000
const app = express()
app.use(bodyParser.json());
app.post('/backend',function(req,res){
    const message = req.body.message;
    console.log(message);
    res.json({
        output: "2+2=4"
    })
})
app.listen(port,()=>{
    console.log(`Listening to port ${port}`)
})
```

QUERY

```javascript
const express = require('express')
const bodyParser = require("body-parser");
const port = 3000
const app = express()
app.use(express.json());
app.post('/backend',function(req,res){
    const message = req.query.message;
    console.log(message);
    res.json({
        output: "2+2=4"
    })
})
app.listen(port,()=>{
    console.log(`Listening to port ${port}`)
})
```

HEADERS
```javascript
const express = require('express')
const bodyParser = require("body-parser");
const port = 3000
const app = express()
app.use(express.json());
app.post('/backend',function(req,res){
    const message = req.query.message;
    console.log(message);
    console.log(req.headers.authorization);
    res.json({
        output: "2+2=4"
    })
})
app.listen(port,()=>{
    console.log(`Listening to port ${port}`)
})
```

STATUS
```javascript
const express = require('express')
const bodyParser = require("body-parser");
const port = 3000
const app = express()
app.get('/',(req,res)=>{
    console.log(res.headers);
    setTimeout(function(){
        res.status(401).send("Hi!")
    },1000)
})
app.listen(port, ()=>{})
```

READ-FILE
```javascript
const express =  require("express");
const fs = require("fs");
const app = express();

app.get("/files/:fileName",function(err,data){
    const name = req.params.fileName;
    console.log(name);
    fs.readFile(name,"utf-8",function(err,data){
        res.json({
            data;
        });
    })
});
app.listen(3000);
```

ERROR
```javascript
const express = require ("express");
const app = express();
app.get("/",function(req,res){
    throw new Error("asdfaadf");
})
app.listen(3000);
```
