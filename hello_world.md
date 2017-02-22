# Step 2: Hello World!

This next step requires opening the shell so we can type commands into PASE on IBM i.  Below is the button you need to press to open the shell (aka terminal).

![image alt text](image_5.png)

Node.js has already been installed in your Litmis Space so we won't be going over those details here.  With that said it is necessary to verify the installation which can be done with the below command from the Shell (aka terminal).

```sh
% node -v
v6.9.1
```

As you can see we are running version 4.4.6 of Node.js which is the current version as of this writing.

Sometimes the best way to learn something is to get a quick "win".  In an effort to not disrupt the balance of language introduction we’re going to create a hello world application.

First create a new directory to hold this new application, cd (change directory) into it, and touch app.js to create it.

```
% mkdir hello
% cd hello 
% touch app.js
```

Now go back to your Litmis Spaces page and click the editor button, as shown below.

![image alt text](image_6.png)

This will open a new browser tab with the browser-based editor, as shown below.  **NOTE:** To see newly created files like hello/app.js you will need to right click on the root folder and select "Refresh".

![image alt text](image_7.png)

Before we edit app.js we need to obtain some system information; specifically the port our web application will be listening to for inbound requests.  Go to your [Spaces page](https://spaces.litmis.com/workspaces) and select the information button to obtain the port that is dedicated to your user profile, as shown below.

![image alt text](image_8.png)

Then in the pop-up window you should see the below section where the ports are delineated.

![image alt text](image_9.png)

Now go to the browser-based editor and paste *(Ctrl+Shift+V) *the following into the newly created app.js file.  You may need to right click in the directory tree to refresh the list.  

**NOTE:** Make sure to change the below port of 60263 to the one obtained in the previous step. Also, make sure to save your source by using Ctrl+S or menu File->Save.

```js
var http = require('http')
var port = 60263

http.createServer(function(req, res) {
  res.writeHead(200, {'Content-Type': 'text/plain'})
  res.end('Hello World**\n**')
}).listen(port, '0.0.0.0')

console.log('Server running at http://0.0.0.0:%d', port)
```

Now go back to your console and enter the following command to start your application.

```sh
% node app.js 

Server running at http://0.0.0.0:60263
```

As you can see it output the value we placed in the call to console.log(...).  Now open a new tab in your browser and enter spaces.litmis.com:<your port>. You should see the below screenshot.

![image alt text](image_10.png)

Wow!  That was simple!

For the fun of it let's add a log each time a request is made using the following line of code that is colored.

```js
var http = require('http')
var port = 60263
http.createServer(function(req, res) {
 res.writeHead(200, {'Content-Type': 'text/plain'})
 res.end('Hello World**\n**')
 console.log('Request came in at: ' + new Date())
}).listen(port, '0.0.0.0')

console.log('Server running at http://0.0.0.0:%d', port)
```

Now go back to your console and hit Ctrl+C to end the current application.  Then hit the up arrow to bring up the previous command and hit enter to run it again, as shown below.  Restarting the Node.js application is necessary so it can pick up the code changes.

```sh
% node app.js
Server running at http://0.0.0.0:60263
Request came in at: Mon Feb 22 2016 21:53:50 GMT+0000 (EST)
Request came in at: Mon Feb 22 2016 21:53:53 GMT+0000 (EST)
Request came in at: Mon Feb 22 2016 21:53:59 GMT+0000 (EST)
```

Refresh the hello world browser tab a few times and you should see additional log lines in the console with timestamps.