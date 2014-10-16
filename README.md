invent
==============
#### start your own invention.
--------------

This is a tool to jumpstart your nodejs development in conjuntion with mongodb.
Similar to the express-generator, this is a vagrant generator. 

So you want to do some application development via vagrant as your environment control, first install some dependancies to get you going:
	
	$ vagrant plugin install vagrant-omnibus
	$ vagrant plugin install vagrant-berkshelf

install this module via: 

    $ npm install -g invent
    
Use via:

    $ invent my_app

You can now serve applications out of 192.168.111.111

How it works

* Copies over template files for package.json and the Vagrantfile
* Downloads Trusty 64 from Ubuntu Cloud Images
* Downloads and uncompresses required chef cookbooks

Requires

    Vagrant Version 1.6.2
    VirtualBox Version 4.3.12

Installs 
* nodejs 0.10.31
* npm 1.4.23
* mongodb @latest

--------------

##### Example webserver
* Vagrant ssh into the box - `$ vagrant ssh`
* Create a file app.js

    
    /* app.js */
    var http = require('http');
    var server = http.createServer(function (request, response) {
      response.writeHead(200, {"Content-Type": "text/plain"});
      response.end("Start your own invention\n");
    });
    server.listen(80);
    console.log("Server running at http://127.0.0.1:80/");
   
* From the guest machine, run the app - `sudo node app.js` 
* From the host machine, visit `192.168.111.111`
