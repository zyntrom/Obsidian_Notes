## Register and Login

### authController.js

```js
const User =require("../models/User");
const bcrypt =require("bcrypt");

const generateToken = require("../utils/generateToken");

exports.register= async (req,res)=>{
	try{
		const {name,email,password}=req.body;
		const hashedPassword =await bcrypt.hash(password,10);
		const user= await User.create({
			name,
			email,
			password:hashedPassword
		})
		res.json({
			success:true,
			data:{
				name:user.name,
				email:user.email
			}
		})
	}catch(err){
		res.status(500).json({
			message:err.message
		})
	}
}

exports.login= async (req,res)=>{
	try{
		const {email,password}=req.body;
		const user = await User.findOne({email});
		if(!user){
			return res.status(404).json({
				message:"user Not found"
			})
		}
		const isMatch =await bcrypt.compare(password,user.password);
		if(!isMatch){
			return res.status(400).json({
				message:"wrong password"
			})
		}
		const token =generateToken(user._id);
		res.json({
			success:true,
			token,
			user:{
				id:user._id,
				name:user.name,
				email:user.email
			}
		})
	}catch(err){
		res.status(500).json({
			message:err.message
		})
	}
}

```

### authRouter.js

```js
const router = require("express").Router();
const auth = require("../middlewares/authMiddleware");
const { register,login } =require("../controllers/authController");

router.post("/register",register);
router.post("/login",login);


module.exports =router;
```

## Middleware

```js
const jwt = require("jsonwebtoken");

module.exports = (req,res,next)=>{
	const header = req.header("Authorization");
	if(!header || head.startWith("Bearer")){
		return res.status(401).json({
			message:"No Token Provided"
		})
	}
	const token =header.split(" ")[1];
	try{
		const decoded=jwt.verify(token,process.env.JWT_SECRET);
		req.user=decoded.id;
		next();
	}catch(err){
		res.status(401).json({
			message:"Invalid token"
		})
	}
}
```