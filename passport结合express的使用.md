# passport结合express的使用  

路由中使用`passport.authenticate`  

```js
passport.authenticate('login', {
		successRedirect: '/home',
		failureRedirect: '/',
		failureFlash : true  
	})
```
## `passport.js`的认证流程  

1. form表单把数据通过http发送到服务器，通过路由，猝发函数`passport.authenticate` 
2. 执行passport-login里面的函数体,表单里面的用户填写的用户名和密码会被传进这个函数体。这一步主要的工作是进数据库根据用户填写的用户名找到到对应的密码，并这个密码和用户输入的密码进行比对。
	* 查询数据库异常，调用`done(err)`。
	* 查找不到用户，或者密码不匹配时，调用`done(null, false)`
	* 认证成功，让用户登录时，调用`done(null, user)`  




## 相关阅读文章  
* [Authenticating Node.js Applications With Passport](http://code.tutsplus.com/tutorials/authenticating-nodejs-applications-with-passport--cms-21619)  
* [Understanding passport.js authentication flow](http://toon.io/understanding-passportjs-authentication-flow/)