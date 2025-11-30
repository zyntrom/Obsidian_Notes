## Express.js (Backend Framework)

### Basic Server

```js
const express =require("express");
const PORT =5000;
const app =express();

app.use(express.json());

app.get("/",(req,res)=>{
	res.json({"message":"Hello"});
})

app.listen(PORT,()=>{
	console.log("Server Running at port: "+PORT+" http://localhost:"+PORT);
})
```

## Basic Folder Structure

### index.js

```js
const express =require("express");
const PORT =5000;
const app =express();
const homeRouter= require("./routes/homeRouter.js");
app.use(express.json());

app.use("/home",homeRouter);

app.listen(PORT,()=>{
	console.log("Server Running at port: "+PORT+" http://localhost:"+PORT);
})
```

### homeRouter.js

```js
const express = require("express")
const router = express.Router();

const {getHome}= require("../controllers/homeController.js");

router.get("/",getHome);

module.exports =router;
```

### homeController.js

```js
 exports.getHome= (req,res)=>{
	 res.json({"message":"hello"});
 };
```
