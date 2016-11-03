Instructions:

- Add your answers inline to the markdown file.
- Use your own words.
- Come up with an answer from memory. Write it down, even if the answer is "I don't know."
- Then, we will go over the answers in class. Write down your revised answer below your original answer.
- There are two intermissions. We will go over the answers to the previous parts during those times.
- Finally, submit all of your answers in a file to canvas. This is so Lloyd and I can get a sense of your understanding.

---
### Part 1: Servers - 20 minutes

1. What is a server? What does a server do?

A server is a program that serves a client.

2. What is Node.js?

Node.js is a platform that can run a server.

3. What is express?

Express is an npm to create a server.

4. What is a client? What does a client do?

A client is a front-end program that gets data from the server

5. How do the server and the client communicate?

Through HTTP

6. Debugging:
- 6a. How do you view server logs?
In node.js

- 6b. How do you view client logs?
In the browser

---
### Part 2: HTTP Requests - 15 minutes

1. What is an HTTP Request?
A request from a browser for a file from the server

2. GET Requests
- 2a. What is a GET request?
A request for data from the server

- 2b. When do you use GET requests?
If you want to load a page or file

- 2c. How do you send data in a GET request?
with response.

3. POST Requests
- 3a. What is a POST request?
A request to send data provided by a user

- 3b. When do you use POST requests?
To send an email or search a page

- 3c. How do you send data in a POST request?
app.post('/path', (request, response) {
	});

---

### Intermission

---
### Part 3: Ajax - 15 minutes

1. Ajax
- 1a. What is Ajax?
Asynchronous JavaScript and XML

- 1b. When should you use Ajax?
When you want to use data from the server but don't want to load a new page

2. Given the following code snippet:

```js
console.log("A");
$('#map').click(function(event) {
	console.log("B");
	var coordinates = convertMouseCoordinatesToGeoCoordinates(event);

	console.log("C");
	$.get('/map', { lat: coordinates.x, lon: coordinates.y }, function(response, status) {
		console.log("D");
		mapDisplay.update(response);
	});

	console.log("E");
});
console.log("F");
```

- 2a. Describe what seems to be happening.
If you click on a button with id map, it shows the geo coordinates of the place you clicked on

- 2b. In what order is `A` through `F` printed?
AFBCDE

- 2c. Describe the events that happen between each letter. When does the server get hit?
At $.get(...

---

### Intermission

---
### Part 4: Jade - 20 minutes

1. Jade
- 1a. What is Jade?

A template for HTML

- 1b. Why should we use Jade?

Because it makes it easier to write and change multiple pages with one template

2. Explain the difference between 'server side' JavaScript and 'client side' JavaScript.

Server side JavaScript is meant to instruct the server, client side JavaScript is
meant to program the behaviour of the website as it is shown to the user.

3. Given this example `index.jade` file:

```js

doctype html
html
	head
		script(src='boop.js')
		script.
			var x = 1;
	body
		- var y = 2;
		h2= z + y

```

- 3a. Is `x` executed server side or client side? Does the client ever see `x`?
Client side. No.

- 3b. Is `y` executed server side or client side? Does the client ever see `y`?
Client side. No..

- 3c. Is `z` executed server side or client side? Does the client ever see `z`?
Client side. Yes

- 3d. When is `boop.js` executed? Does the client ever see `boop.js`?
When the page is rendered. No.

---
### Part 5: Request Lifecycle - 15 minutes

5. Given the following code snippet in an express application:

```js

app.get('/home', function (request, response) {
	response.render('index', { z: 3 } );
});

```

- 5a. List the complete order of events, starting from the browser making a `GET` request to `/home`. Assume that `index` refers to the Jade file in Part 4. Be sure to describe when each JavaScript statement (`x`, `y`, `z`, and `boop.js`) gets executed.

-path /home is requested from the server
-index.pug is rendered as response
-boop.js is executed
-x is executed
-y is executed
-z is executed as 3

- 5b. What is displayed on the page?
5

- 5c. What is visible from 'view page source'?
The code
