###1.Install the node dependencies###

```npm install```

###2.Start the application###

```npm start```


###3.Config database###

all the database configurations are inside src/config/dbconfig.js.

```
"use strict";

const dbConfig = {
    "default": "mongodb",

    "mongodb": {
    	DATABASE: "media"
    },

	"mysql": {
		HOST: "172.28.128.3",
		USER: "root",
		PASSWORD: "roowpw",
		DATABASE: "eshop"
	}
}

export {dbConfig};

```

###4.Define the route.###

you can find all the routes definitions inside src/routes folder, let's say you want to get something from /test, and you want test controller and test method to deal with this request, you can add the following code to setRoute method:

```
	this.app.get("/test",  (req, res) => {
		that.response({
			controller: "test",
			action: "test"
		}, req, res);
	});

```

you can define diffent request method like post, put, delete:

```
	this.app.post("/test",  (req, res) => {
		that.response({
			controller: "test",
			action: "test"
		}, req, res);
	});

	this.app.put("/test",  (req, res) => {
		that.response({
			controller: "test",
			action: "test"
		}, req, res);
	});

	this.app.delete("/test",  (req, res) => {
		that.response({
			controller: "test",
			action: "test"
		}, req, res);
	});

```

###5.Create controller###

let's say you want to create controller which is called "test", you can run the following command.
```
node createController.js test
```

it will generate "test" controller under src/controllers/.

###6.Create model###

let's say you want to create model which is called "test", you can run the following command.

```
node createModel.js test
```
it will generate "test" model under src/models/.

###7. how to use mongodb node driver###

before run the application, you need run mongodb first:

```
mongod --dbpath data/db
```

you can find all the details about the driver [here](https://mongodb.github.io/node-mongodb-native/api-articles/nodekoarticle1.html "title")

###8. unit test ###
```
npm test
```

all the test filses should be put inside "spec".

the name of the test file must be *[S]spec.js.

###7. How to use search api?###

the path of the api is:
```	
/search
```
here is the example of request header:
```
POST /search HTTP/1.1
Host: localhost:3000
Cache-Control: no-cache

{ "q":"test", "action":"nextPageToken", "actionValue":"CBQQAQ" }
```
if you want to see the next page of search result, you can send following json:

```
{
	"q":"test",
    "action":"nextPageToken",
    "actionValue":"CBQQAQ"
}
```
if you want to see tne previouse page of search result, you can dend following json:

```
{
	"q":"test",
    "action":"prevPageToken",
    "actionValue":"CCgQAA"
}
```

you can get the token value from the api respone:

```
 "kind": "youtube#searchListResponse",
    "etag": "\"0Fu6lI6VPLdRMlQU3wwNcowdAUs/2FOWlSS7DAFMRd_gZUxEo_eoUxQ\"",
    "nextPageToken": "CCgQAA",
    "prevPageToken": "CBQQAQ",
    "regionCode": "GB",
    "pageInfo": {
        "totalResults": 1000000,
        "resultsPerPage": 20
    },
```




