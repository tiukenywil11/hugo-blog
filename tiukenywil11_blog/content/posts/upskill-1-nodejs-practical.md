---
title: "Upskill 1 (Nodejs): Practical"
date: 2022-05-07T11:41:55+08:00
tags: ["upskill", "full stack", "nodejs", "expressjs", "swagger", "javascript", "github"]
description: "Upskill 1: Practical research on backend Javascript framework NodeJS"
author: "Kenywil Tiu"
---
# Introduction
  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; I have done some research on NodeJS, and some crash course practical developement. I personally think I learn better by coding step by step, so for this blog I'll follow and break down this Youtube Video called ["NodeJS Swagger API Documentation Tutorial Using Swagger JSDoc"](https://youtu.be/S8kmHtQeflo) By Maksim Ivanov.
  
# Steps

## Prerequisite
- Github account
- Git
- NodeJS
- VSCode


## Github setup
1. Created a repository [here](https://github.com/tiukenywil11/node-express-swagger-crud) by using GitHub's website UI.
2. Cloned to my local machine by using the following code
```bash
git clone https://github.com/tiukenywil11/node-express-swagger-crud.git
```
3. Navigated in and opened the directory on VSCode.
```bash
cd node-express-swagger-crud
code . 
```

## Initialize project
1. Initialize Node project.
```bash
npm init
```
2. Just used default configurations.
3. Install dependencies
- express: Used as server.
- lowdb: Used to store data.
- morgan: Output the logs.
- nanoid: Create unique ids.
- cors: To setup cross origins policy.
- swagger-jsdoc: JS docs syntax.
- swagger-ui-express: To serve as swagger ui specifications
```bash
npm install express lowdb@1.0.0 morgan nanoid cors swagger-jsdoc swagger-ui-express
```

## Create the server
1. Create and append 'index.js'.
```bash
touch index.js
```
- Import the required libraries
```javascript
const express = require("express");
const cors = require("cors");
const morgan = require("morgan");
const low = require("lowdb");
```
- Initialize port to get from the environment variable, or set it to '4000'.
```javascript
const PORT = process.env.PORT || 4000;
```	
- Link data to the file *'db.json'*
```javascript
const FileSync = require("lowdb/adapters/FileSync");

const adapter = new FileSync("db.json");
const db = low(adapter);
```
- Add default characters to db.
```javascript
db.defaults({ books: []}).write()
```
- Initilialize ExpressJS.
```javascript
const app = express();
```
- Set ExpressJS DB.
```javascript
app.db = db;
```
- Initialize CORS, ExpressJS JSON library, and Morgan.
```javascript
app.use(cors());
app.use(express.json());
app.use(morgan("dev"));
```
- Create server listener.
```javascript
app.listen(PORT, () => console.log(`The service is running on port ${PORT}`));
```
2. Test the server.
```bash
node index.js
```
- Should show the following message.
```bash
The service is running on port 4000
```
- Accessing via `http://localhost:4000/` would show the following message.
```bash
Cannot GET /
```
![server-screen](/img/upskill-1-practical/1_server-screen.png)
  
**Error encountered:**  
- lowdb 3.0.0 (ERR_REQUIRE_ESM). 
	- Reason: Version incompatible with node^16.13.1
	- Solution: Downgraded to lowdb^1.0.0 

3. Committed changes in the repository.
```
git add .
git commit -m "Part 1: Creating a server"
git push
```
- [First Commit](https://github.com/tiukenywil11/node-express-swagger-crud/commit/bb43052d8d8287f9f4a4d3001141c715ec35b967): Working node-express server.

## Create Routes
1. Create 'routes' directory.
```bash
mkdir routes
```
2. Create and append'routes/books.js' file.
```bash
touch routes/books.js
```
- Import the required libraries.
```javascript
const express = require("express");
const router = express.Router();
const { nanoid } = require("nanoid");
```
- Initilialize ID length.
```javascript
const idLength = 8;
```
- Define books route.
	- Note: 'app.db' is initialized on 'index.js'
- Create 'GET' books array.
```javascript
router.get("/", (req, res) => {
	const books = req.app.db.get("books");
	// sends a response which are 'books'
	res.send(books);
})
```
- Create 'GET' for a single entry.
```javascript
router.get("/:id", (req, res) => {
	const book = req.app.db.get("books").find({ id: req.params.id }).value();
	res.send(book);
})
```
- Create 'POST' to add to the book array.
```javascript
router.post("/", (req, res) => {
	try {
		const book = {
			id: nanoid(idLength),
			// This should be expounded on real projects.
			...req.body
		};
		req.app.db.get("books").push(book).write();
	} catch(error) {
		return res.status(500).send(error);
	}
})
```	
- Create 'PUT' to append an entry.
```javascript
router.put("/:id", (req, res) => {
	try {
		req.app.db.get("books").find({ id: req.params.id }).assign(req.body).write();		
		res.send(req.app.db.get("books").find({ id:request.params.id }));
	} catch(error) {
		return res.status(500).send(error);
	}
})
```	
- Create 'DELETE' to remove an entry.
```javascript
router.delete("/:id", (req, res) => {
	req.app.db.get("books").remove({ id: req.params.id }).write();
	res.sendStatus(200);
})
```	
- Export the routes.
```javascript
module.exports = router;
```
3. Add routes to 'index.js'.
- Import booksRouter. Ideally placed together with other imports.
```javascript
const booksRouter = require('./routes/books');
```
- Initialize books router. Should be placed before 'app.listen'
```javascript
app.use("/books",booksRouter);
```
4. Added test data to 'db.json' for a quick test.
```json
{
  "books": [
    {
      "id": "123456",
      "name": "Book",
    }
  ]
}
```
5. Test the server.
```bash
node index.js
```
- Should show the following message.
```bash
The service is running on port 4000
```
- Accessing via `http://localhost:4000/` would show the following message.
```bash
Cannot GET /
```
![server-screen](/img/upskill-1-practical/1_server-screen.png)
- Accessing via `http://localhost:4000/books` would show the following message.
```bash
[{"id":"123456"}]
```
![server-screen-2](/img/upskill-1-practical/2_server-screen.png)

5. Committed changes in the repository.
```bash
git add .
git commit -m "Part 2: Create routes"
git push
```
- [Second Commit](https://github.com/tiukenywil11/node-express-swagger-crud/commit/2894acd86532b43cc63f8435a1d2cd9447d9d86f): Routes are connected to 'index.js', test with GET successful.
  
## Adding SwaggerUI
1. Append 'index.js'.
- Import swagger. Ideally placed together with other imports.
```javascript
const swaggerUI = require("swagger-ui-express");
const swaggerJsDoc = require("swagger-jsdoc");
```
- Create options for swagger, placed under 'db.defaults'
```javascript
const options = {
	definition: {
		openapi: "3.0.0",
		info: {
			title: "Library API",
			version: "1.0.0",
			description: "A simple Express Library API"
		},
		servers: [{
			url: "http://localhost:4000"
		}],
	},
	apis: ["./routes/*.js"],
};
```
- Initialize swagger js docs, under swagger options.
```javascript
const specs = swaggerJsDoc(options);
```
- Use the API docs, placed after instantiation of express to variable app.
```javascript
app.use("/api-docs", swaggerUI.serve, swaggerUI.setup(specs));
```

2. Test the server.
```bash
node index.js
```
- Should show the following message.
```bash
The service is running on port 4000
```
- Accessing via `http://localhost:4000/api-docs` would show the following.
![server-screen-3](/img/upskill-1-practical/3_server-screen.png)
3. Committed changes in the repository.
```bash
git add .
git commit -m "Part 3: Added base Swagger"
git push
```
- [Third Commit](https://github.com/tiukenywil11/node-express-swagger-crud/commit/462341d548a051d32534028393842021bbbc196d): Added base Swagger JS.

## Adding Schemas for books  
Additional Swagger resource regarding component specification can be found [here](https://swagger.io/docs/specification/components/)

1. Append'routes/books.js' file.
- Add swagger definition after initializing ID length.
```javascript
/**
 * @swagger
 * components:
 *   schemas:
 *     Book:
 *       type: object
 *       required:
 *         - title
 *         - author
 *       properties:
 *         id:
 *           type: string
 *           description: The auto-generated id of the book
 *         title:
 *           type: string
 *           description: The book title
 *         author:
 *           type: string
 *           description: The book author
 *       example:
 *         id: 123456
 *         title: Book
 *         author: Aut H. Or
 */
```
**Error encountered:**
- Swagger 'component' not showing. 
	- Reason: Javascript option `apis: ["*./routes/*.js"]` on 'index.js' is a typo.
	- Solution: Appended to the following `apis: ["./routes/*.js"],`
**Notes:**
- Also appended 'db.json' test data from:
```json
{
  "books": [
    {
      "id": "123456",
      "name": "book",
    }
  ]
}
```
to the following:
```json
{
  "books": [
    {
      "id": "12345678",
      "title": "Book",
      "author": "Aut H. Or"
    }
  ]
}
```
- Accessing via `http://localhost:4000/api-docs` would show the following.
![server-screen-4](/img/upskill-1-practical/4_swagger-screen-1.png)
![server-screen-5](/img/upskill-1-practical/5_swagger-screen-2.png)
- Create a swagger tag, to grpup all 'books'/
```javascript
 /**
  * @swagger
  * tags:
  *   name: Books
  *   description: The books managing API
  */
```
- Accessing via `http://localhost:4000/api-docs` would show the following.
![server-screen-6](/img/upskill-1-practical/6_swagger-screen-3.png)
-  Add Swagger for 'GET' route. Placed above the 'router.get'.
```javascript
/**
 * @swagger
 * /books:
 *   get:
 *     summary: Returns the list of all the books
 *     tags: [Books]
 *     responses:
 *       200:
 *         description: The list of the books
 *         content:
 *           application/json:
 *             schema:
 *               type: array
 *               items:
 *                 $ref: '#/components/schemas/Book'
 */
```
- Accessing via `http://localhost:4000/api-docs` would show the following. You can also click "Try it out", to test the API endpoint.
	- These images are similar to the other routes.
![server-screen-7](/img/upskill-1-practical/7_swagger-screen-4.png)
![server-screen-8](/img/upskill-1-practical/8_swagger-screen-5.png)
-  Add Swagger for 'GET' for a single entry. Placed above the 'router.get' that gets a single entry.
```javascript
/**
 * @swagger
 * /books/{id}:
 *   get:
 *     summary: Get the book by id
 *     tags: [Books]
 *     parameters:
 *       - in: path
 *         name: id
 *         schema:
 *           type: string
 *         required: true
 *         description: The book id
 *     responses:
 *       200:
 *         description: The book description by id
 *         contens:
 *           application/json:
 *             schema:
 *               $ref: '#/components/schemas/Book'
 *       404:
 *         description: The book was not found
 */
```
- Add error 404 for 'GET' for single entry. This is placed inside router.get, and after book variable is initialized.
```javascript
if(!book) {
	res.sendStatus(404);
}
```
- **Error Encountered:**
	- 'GET' with {:id} not returning the a value: 
	- Reason: Wrong variable is passed backed to`res.send(books);`
	- Solution: Appended to the following `res.send(book);`
- Add Swagger for 'POST' route. Placed above the 'router.post' function.
```javascript
/**
 * @swagger
 * /books:
 *   post:
 *     summary: Create a new book
 *     tags: [Books]
 *     requestBody:
 *       required: true
 *       content:
 *         application/json:
 *           schema:
 *             $ref: '#/components/schemas/Book'
 *     responses:
 *       200:
 *         description: The book was successfully created
 *         content:
 *           application/json:
 *             schema:
 *               $ref: '#/components/schemas/Book'
 *       500:
 *         description: Some server error
 */
```
- Add a respond snippet for 'POST' route, after 'req.app.db.get' snippet.
```javascript
res.send(book);
```
- Add Swagger for 'PUT' route, Placed above the 'router.put' function.
```javascript
/**
 * @swagger
 * /books/{id}:
 *  put:
 *    summary: Update the book by the id
 *    tags: [Books]
 *    parameters:
 *      - in: path
 *        name: id
 *        schema:
 *          type: string
 *        required: true
 *        description: The book id
 *    requestBody:
 *      required: true
 *      content:
 *        application/json:
 *          schema:
 *            $ref: '#/components/schemas/Book'
 *    responses:
 *      200:
 *        description: The book was updated
 *        content:
 *          application/json:
 *            schema:
 *              $ref: '#/components/schemas/Book'
 *      404:
 *        description: The book was not found
 *      500:
 *        description: Some error happened
 */
```
- Add Swagger for 'DELETE' route, Placed above the 'router.delete' function.  
- **Error encountered:**
	- router.delete is not working properly. 
	- Reason: The router for delete had the wrong syntax `router.put` on 'books.js'.
	- Solution: Appended to the following `router.delete`
```javascript
/**
 * @swagger
 * /books/{id}:
 *   delete:
 *     summary: Remove the book by id
 *     tags: [Books]
 *     parameters:
 *       - in: path
 *         name: id
 *         schema:
 *           type: string
 *         required: true
 *         description: The book id
 * 
 *     responses:
 *       200:
 *         description: The book was deleted
 *       404:
 *         description: The book was not found
 */
```
5. Test the server.
```bash
node index.js
```
- Should show the following message.
```bash
The service is running on port 4000
```
- Accessing via `http://localhost:4000/` would show the following message.
```bash
Cannot GET /
```
- Accessing via `http://localhost:4000/api-docs` would show the following. You can also click "Try it out" for each request type, to test the API endpoint.
![server-screen-9](/img/upskill-1-practical/9_swagger-screen-6.png)
3. Committed changes in the repository.
```bash
git add .
git commit -m "Part 4: Added Swagger for the rest, final working demo"
git push
```
- [Fourth Commit](https://github.com/tiukenywil11/node-express-swagger-crud/commit/d543cde0cae32342791c557fe3486a2fa1b6e7dd): Added the rest of the Swagger definitions, working demo.  
  
# Outro

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Encountered a few errors while doing this demo, mainly due to careless syntax errors, but aside from that I think Swagger library is pretty convenient, and can be used to complement Postman for testing APIs. You can find the final Github repo [here](https://github.com/tiukenywil11/node-express-swagger-crud). I plan on trying to implement a containerize version of this if I get the time to, will update this post if I do.
  
**Read More:**  
[NodeJS: Research]({{< ref "upskill-1-nodejs.md" >}})  
