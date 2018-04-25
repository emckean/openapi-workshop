# OpenAPI Workshop
April 25, 2018 	
Galvanize

## Overview

In this workshop we will:

* learn about the OpenAPI spec version 3
* create an API with LoopBack
* export a Swagger 2.0 spec
* convert it to a Swagger 3.0 spec
* generate client code with Bluemix
* create some interactive docs
* do automated testing of your API

## Prerequisites

* Please sign up for a FREE IBM Cloud account: [https://ibm.biz/BdZaNJ](https://ibm.biz/BdZaNJ)
* You should have installed: 
	* 	Node (v 6 or higher, recommend 8 or higher) -- check with `node -v`
	*  npm (should be installed with Node) -- check with `npm -v`
	[Need help installing Node or npm? Check out [this post](http://blog.teamtreehouse.com/install-node-js-npm-mac) for Mac users; [here](https://nodejs.org/en/download/) are the install pages for other OSes] 
	*  the LoopBack cli: `npm install -g loopback-cli`
	*  the Bluemix cli: [https://clis.ng.bluemix.net/ui/home.html] (https://clis.ng.bluemix.net/ui/home.html)

## Create a LoopBack app

* `lb app $appname`*  `lb datasource` (ask for the connection string info)!* lb model	 * jeopardyQuestion		 * question - string – required		 * answer - string – required		 * category - string - required
* start your app with `node .`

* add remote methods:  
	* 	in the file: `models/jeopardyQuestion.js`		 * copy code from [http://ibm.biz/OAI-workshop-remote](http://ibm.biz/OAI-workshop-remote) * don’t forget to restart!

## Export an OpenAPI specification

* `lb export-api-def --o jeopardyAPI.yml`

## Create a client

* log in to the `bx` cli: `bx login`
* you may have to set your target org and space if you have more than one: see them with `cf target` and set them with `bx target -o ORG -s SPACE`
* generate a client with `bx sdk generate -f jeopardyQuestion.yml --js` 

## Create Docs
* install the redoc module: `npm install redoc --save`
* export a .json version of your swaggerfile: `lb export-api-def --json -o ./client/swagger.json`* add file serving in `server/middleware.json` (inside `files : {}`): 	````
	"loopback#static": {      		"params": "$!../client"    	}
	````
* make your redoc.html file (you can copy-paste from this gist: [http://ibm.biz/OAI-workshop-docs](http://ibm.biz/OAI-workshop-docs))
* open `redoc.html` in your browser

## Set Up Automated Testing
For this workshop, we're using Assertible, which is free. You can login with your Github account, if you have one. 

* to your `jeopardyAPI.yml` file, add a `host` object as the second line: `host: jma.mybluemix.net`
* import your `jeopardyAPI.yml` file
* delete the PUT/POST/DELETE endpoints

## Convert your spec to OpenAPI 3.0

For this workshop, we'll use the Mermade online converter: [https://mermade.org.uk/openapi-converter](https://mermade.org.uk/openapi-converter)

## Resources
* OAI Resources: [http://ibm.biz/OAI-LDC](http://ibm.biz/OAI-LDC)* Create REST APIs using LoopBack [http://ibm.biz/loopbackpattern](http://ibm.biz/loopbackpattern)
* LoopBack docs: [loopback.io](https://loopback.io)* LoopBackJS Google group: [https://groups.google.com/forum/#!forum/loopbackjs](https://groups.google.com/forum/#!forum/loopbackjs)* StackOverflow tag:[http://stackoverflow.com/questions/tagged/loopback](http://stackoverflow.com/questions/tagged/loopback)* IBM Code [https://developer.ibm.com/code/](https://developer.ibm.com/code/)
*  Other documentation options in this blog post from Pronovix: [https://pronovix.com/blog/free-and-open-source-api-documentation-tools](https://pronovix.com/blog/free-and-open-source-api-documentation-tools)	