<img src="https://i.imgur.com/IKHxRMa.png">

# Intro to Single-Page Applications (SPAs) and the MERN-Stack

## Learning Objectives

|Students Will Be Able To:|
|---|
| Explain the difference between a SPA and a traditional multi-page web application |
| Identify the three development concepts that make SPAs possible |
| Structure a MERN-Stack Project |

## Road Map

1. Intro to SPAs
2. Intro to the MERN-Stack
3. This Unit's Reference App: **SEI CAFE**
4. Building a MERN-Stack's Infrastructure
5. Setting Up the **mern-infrastructure** Project
6. Configure React for Full-stack Development
7. Essential Questions
8. Further Study

## 1. Intro to SPAs

### Review - What is a Single-Page App?

We've mentioned them previously - **what are they?**

<img src="https://i.imgur.com/m01TbLF.png">

In a traditional multi-page web app, if we click a link, submit data via a form, or type in the address bar and press [enter], **what happens?**

In a SPA, we still want to be able to access different functionality by clicking links, submitting data to the server, etc., however, we want the UI to update without triggering a full-page refresh.

There are three development concepts that make SPAs possible:

1. AJAX Communications between client and server
2. Client-Side Routing
3. Client-Side Rendering

### Concept 1: Client/Server Communication via AJAX

As you've seen, the `fetch` API, as well as utilities such as Axios & jQuery's AJAX methods can be used to send HTTP requests to a server using JavaScript instead of using forms and links in the page.

With AJAX, the server responds to an HTTP request with an HTTP response that usually contains a JSON payload in the response body.

Because the request was sent via code, and the response handled via code, the browser won't reload the page!

### Concept 2: Client-Side Routing

When the users have interacted by clicking links and submitting forms in the traditional multi-page web apps we've built thus far, the server has responded with a new HTML document that the browser proceeds to replace the current page with.

In a SPA, we still need a way to switch to different "pages" of functionality (see diagram above) - but without replacing the entire HTML document that's currently loaded in the browser...

**Client-side routing** is what enables users of a SPA to navigate to different "pages" without triggering a full-page refresh. 

The users will still be clicking navigation "links" that cause the browser's address bar to change.

However, the client-side router intercepts the changes to the path by tapping into the browser's [History API](https://developer.mozilla.org/en-US/docs/Web/API/History_API). 

By using the History API, the client-side router can manipulate the path in the address bar without triggering an HTTP request.

> 👀 We will continue to define server-side routes, however, the vast majority of those routes will be API-type routes that are accessed via AJAX calls, perform CRUD and return data as JSON to the browser.

Feel free to checkout the Further Study section to learn more about the History API and Hash URIs.

### Concept 3: Client-Side Rendering

So, assume a user clicks an **Add Comment** button in a SPA and expects to see the new comment show up in the list of comments...

This is a SPA, so you don't want the button to cause a full-page refresh!

In SPAs, you would send an AJAX request containing the data for the new comment to the server.

The server would update the database respond with JSON data - probably containing the current comments in an array.

However, to make the comment show up in the UI, it needs to be updated using JavaScript - a process we call **client-side rendering**.

<details>
<summary>
Guess who the undisputed client-side rendering champion is...
</summary>
<hr>

The **React** Library - of course!

<hr>
</details>

### ❓ Review Questions - SPAs (1 min)

<details>
<summary>
(1) What's the most significant difference between a traditional multi-page web app and a single-page app?
</summary>
<hr>

**A SPA avoids full-page reloads.**

A SPA loads the `index.html` once and then has its DOM modified via client-side rendering. 

<hr>
</details>

<details>
<summary>
(2) What three development concepts enable the creation of comprehensive single-page applications?
</summary>
<hr>

- AJAX Communications between client and server
- Client-Side Routing
- Client-Side Rendering

<hr>
</details>

## 2. Intro to the MERN-Stack

A technology stack, also called a solutions stack, is a group of development tools/services used to build an application.

For example, the LAMP-Stack is a mature technology stack that uses:
- Linux
- Apache (web server)
- MySQL and
- PHP (web development programming language)

In the last unit, our stack consisted of:
- Python
- Django and 
- PostgreSQL

There are a few tech stacks that use MongoDB, Express & Node as their backend solutions.

Then, one of the following front-end technologies is added to go full-stack:

- [React](https://reactjs.org/) which results in the MERN-Stack
- [Angular](https://angular.io/) which results in the MEAN-Stack
- [Vue.js](https://vuejs.org/) which results in the MEVN-Stack

The MERN-Stack is by far the most popular tech stack currently and will remain so into the foreseeable future.

### Architecture of the MERN-Stack

The following depicts the overall architecture of a MERN-Stack app:

<img src="https://i.imgur.com/m87p4kN.png">

The flow is as follows:

1. When the user browses to the app's URL, the Express server always delivers the static **public/index.html** page.

    > 👀 There will be no EJS templates on the server - just the static index.html.  In fact, there's no reason to install the EJS template engine!

2. When the browser loads **index.html**, it will request the JS that is the React app (outlined in blue).

3. The code in the React app's **index.js** module runs, which causes the React app to render for the first time. During this initial rendering, the client-side routing library renders components based upon the URL in the address bar.

4. After the React app has been loaded, all subsequent HTTP communications between the client and server will be via AJAX in order to avoid the page from being reloaded.

5. Certain components may want to CRUD data on the server. However, we won't litter components with the code responsible for CRUD. Instead, as a best practice, that code will be organized into **service/API** modules.

6. On the server, a single non-API "traditional" route will be defined with the purpose of delivering the static **index.html** file. We will refer to this route as the "catch all" route since it will match all `GET` requests that do not match any of the "API" routes...

7. Other than the single "catch all" route just mentioned, all other routes on the server will be defined to respond to AJAX requests with JSON. By convention, the endpoints of these routes with be prefaced with `/api`, e.g., `/api/cats`, `/api/login`, etc.

Now that we know a bit about the MERN-Stack, let's take a look at the reference app we'll build together this unit...

## 3. This Unit's Reference App: **SEI CAFE**

As you know, it's important to practice the individual skills we learn for a given technology by bringing them together to build a real-world working application.

This unit's reference app is a MERN-Stack online food ordering app called [SEI CAFE](https://sei-cafe.herokuapp.com/).

Be sure to sign-up:

<img src="https://i.imgur.com/ShSz0xE.png">

and place an orders!

<img src="https://i.imgur.com/ZSsDUqk.png">

## 4. Building a MERN-Stack's Infrastructure

We'll begin by building out the infrastructure (boilerplate) that most real-world MERN-Stack apps starts with, including client-side routing and authentication.

After the infrastructure code is complete, we'll save the project to a separate repo that can be cloned to launch future MERN-Stack projects, including your capstone project at the end of this unit!

### How to Structure a MERN-Stack Project

Up until this point, we've taken for granted that full-stack apps, like your Express and Django projects, were single, integrated projects.

However, developing a MERN-stack project involves complexities such as tooling such as [webpack](https://webpack.js.org/), React's development server, etc.

Additionally, there are concerns during both **development and production** that have to be addressed...

#### During Development

A React project uses a development server that compiles and serves the React app to the browser at `localhost:3000`.

<details>
<summary>
❓ There's a conflict between React's development server and the Express applications we've built previously - what is it?
</summary>
<hr>

**They both run on port `3000` by default** and only a single process can run on a given port.

<hr>
</details>

Luckily, the React team recognized this conflict and has a solution which we'll see in a bit.

#### Production Environment Concerns

As we develop our React app locally, we're writing source code that React's dev server builds and runs automatically.  However, this is not production ready code because it has extra debugging logic, etc.

In a moment will see how to **build** the React app locally.

However, this locally built code is typically git ignored thus it's important to ensure that whatever hosting service you deploy to is configured to **build** the React app in the cloud each time the code is deployed.

Luckily for us, since 2019, Heroku automatically builds the React apps each time they are deployed.

In addition to ensuring that the hosting service builds the React app, we will also need to code the Express app to serve the built production code.

### Possible MERN-Stack Project Structures

There are two general architectures we could pursue:

1. Maintain **two** separate projects, one for the React app, the other for the Express backend.
2. Integrate the codebase for both the React frontend and the Express backend.

| Architecture | Pros | Cons |
| --- | --- | --- |
| Separate Projects | <ul><li>Better for when the backend services multiple frontend projects (web, native mobile, desktop).</li></ul> | <ul><li>Must manage two projects and git repos.</li><li>Must deploy those two projects separately.</li><li>The React project will require code and/or configuration to access the correct backend during development (localhost) and production (could be anywhere).</li><li>Must implement CORS.</li></ul> |
| Single Project | <ul><li>A single integrated project.</li><li>None of the above Cons.</li></ul> | <ul><li>Not the best project structure to re-use the same backend project to service multiple frontend projects, e.g., Web/Mobile/Desktop</li></ul> |

The single, integrated project approach looks to be a no-brainer. But, what does the structure of a single project look like?

Again, two options:

1. Start with an Express app, then generate the React app within it (naming it `client` or something similar). This approach will result in nested **package.json** files and **node_modules** folders requiring you to "know where you are" when installing additional Node modules. Also with this approach, Heroku will not "see" the React app and will not build it automatically.
2. Start with a React app, then add an Express **server.js** and other server related folders/files as necessary. This approach results in a single **package.json** file and **node_modules** folder.

The second option is "cleaner" and less error prone, so we'll opt for that approach.

Let's start building!

## 5. Setting Up the `mern-infrastructure` Project

Here's the plan:

- Generate the React app
- Build the React app's production code
- Code the skeleton Express app
- Define the "catch all" route in the Express backend
- Test the Express server

Let's do this!

### Generate the React App

The best way to create a React project is by using the `create-react-app` script provided by the React team:

```
cd ~/code
npx create-react-app mern-infrastructure
```

> 👀 A new folder will be created named **mern-infrastructure**. If you would like to generate a project in the future within an existing folder, you can use `.` in place of the project name.

Creating a new React app takes some time because `create-react-app` automatically installs the Node modules - and there's a ton of them!

> 👀 It's best to ignore all severity vulnerabilities.  There's been much written about how create-react-app is simply tooling and that we should ignore npm's overreactions.

Let's briefly review the outputted message:

```
Created git commit.

Success! Created mern-infrastructure at /Users/<your username>/code/mern-infrastructure
Inside that directory, you can run several commands:

  npm start
    Starts the development server.

  npm run build
    Bundles the app into static files for production.

  npm test
    Starts the test runner.

  npm run eject
    Removes this tool and copies build dependencies, configuration files
    and scripts into the app directory. If you do this, you can’t go back!

We suggest that you begin by typing:

  cd mern-infrastructure
  npm start

Happy hacking!
```

Now we can:

```
cd mern-infrastructure
```

Open the project in VS Code:
```
code .
```
Open an integrated terminal in VS Code:
```
control + backtick
```
CRA has already initialized a repo, so let's connect to the code-along repo that you can sync with it as needed:
```
git remote add origin https://git.generalassemb.ly/sei-blended-learning/mern-infrastructure.git
git fetch --all
```
Spin up React's built-in development server:
```
npm start
```
which automatically opens the app in a browser tab at `localhost:3000`:

<img src="https://i.imgur.com/4ouH8bS.png" height="400">


The React development server automatically builds and reloads the app in the browser whenever changes are saved.

Within VS Code, we'll find a Node project's usual **package.json**, **node_modules**, etc.

The React project's source code lives within the **src** folder:

<img src="https://i.imgur.com/d9T3Vqw.png" height="400">

### Build the React App's Production Code

We will soon be coding the Express server to serve the production React app.

Thus, we need to build the React app's code locally into production code at least once so that the Express server does not raise an error.

The `create-react-app` CLI includes tooling and a **build** script in **package.json** that, when run, compiles the the code in the **src** and **public** folders of the React project into production code - placing it into a folder named **build**.

Let's run the build script:

```
npm run build
```

> 👀 npm requires us to use the `run` command for scripts other than `start` and `test`.
 
After building, examining our project's structure reveals a new **build** folder containing production ready static assets including **index.html**, **static/css** & **static/js** folders, etc.  If this React app was a frontend only app, the assets in the build folder would be ready to deploy to any static hosting service.

This **build** folder of production-ready goodness is ready to be served up by an Express backend...

### Code the Skeleton Express App

Now with the React app up and running, we can start to code the Express backend.

We _could_ use Express generator if we save the existing React-oriented **package.json** file and merge it with the Express dependencies.

Instead we're going to code our own Express app from scratch because we won't need much middleware, etc. due to the fact that the Express backend simply needs to:

- Deliver the **production-ready** **index.html**, which will in turn request the **production-ready** scripts, etc.
- Respond to AJAX requests, performing any necessary CRUD, and finally respond with JSON.

#### Install the Modules for the Express Server

There's no problem with the Express project happily sharing that same **package.json** that `create-react-app` created.

For now, we're only going to install a minimal number of modules for the Express app:

```
npm i express morgan serve-favicon
```

Again, we don't need a view engine because our server will be either serving static assets (index.html, CSS, JS, images, etc.) or responding to AJAX requests with JSON. There will be no EJS templates!

Later, we'll install additional modules, e.g., `mongoose`, `dotenv`, etc.

#### Create and Code the Express App (**server.js**)

Let's code our Express server:

1. Ensure that you're still in the root folder of the React project.

2. `touch server.js`

3. At the top of **server.js**, let's do all the familiar stuff::

	```js
	const express = require('express');
	const path = require('path');
	const favicon = require('serve-favicon');
	const logger = require('morgan');
	
	const app = express();
	
	app.use(logger('dev'));
	app.use(express.json());
	```

    <details>
    <summary>
    ❓ Why don't we need to mount the <code>express.urlencoded()</code> middleware also?
    </summary>
    <hr>

    **Because `express.urlencoded` middleware is used to process data submitted by a form - and we don't submit forms in a SPA.**

    <hr>
    </details>

4. Mount and configure the `serve-favicon` & `static` middleware so that they serve from the **build** (production) folder:

	```js
	app.use(express.json());
	
	// Configure both serve-favicon & static middleware
	// to serve from the production 'build' folder
	app.use(favicon(path.join(__dirname, 'build', 'favicon.ico')));
	app.use(express.static(path.join(__dirname, 'build')));
	```

5. Set the port for development to use `3001` so that React's dev server can continue to use `3000` and finally, tell the Express app to listen for incoming requests:

	```js
	// Configure to use port 3001 instead of 3000 during
	// development to avoid collision with React's dev server
	const port = process.env.PORT || 3001;
	
	app.listen(port, function() {
	  console.log(`Express app running on port ${port}`)
	});
	```

### Define the "Catch All" Route

A single "catch all" route is required to serve the **index.html** when any non-AJAX "API" request is received by the Express app:

```js
app.use(express.static(path.join(__dirname, 'build')));

// Put API routes here, before the "catch all" route

// The following "catch all" route (note the *) is necessary
// to return the index.html on all non-AJAX requests
app.get('/*', function(req, res) {
  res.sendFile(path.join(__dirname, 'build', 'index.html'));
});
```

> 👀 Since this route is a "catch all" that matches every `GET` request, be sure to mount API or other routes before it!

Now the "catch all" route will serve the **index.html** whenever:

- A user types a path into the address bar and presses enter.
- The user refreshes the browser.
- A person clicks a link to the app provided via email, slacked, included on another web page, etc.

For example, let's say you provide a friend with a link to your app's dashboard functionality like the following:
```
https://amazingapp.com/dashboard
```

When clicked, the server will receive `GET /dashboard` request, but won't that be a problem because the `/dashboard` path is meant to be a client-side route?

Nope, no problem at all because the "catch-all" route will send the **index.html** page to the browser.

Then, after **index.html** loads in the browser, the React app's client-side routing will render components based upon the `/dashboard` path in the address bar - and all is well!

### Test the Express Server

We should now be able to test the Express server.

However, we can no longer just type `nodemon` because just typing `nodemon` will run the command in the `start` script in **package.json** and that script is being used to start the React development server instead.

Therefore, in our MERN-Stack development environment, it's important to start the Express server by typing:

```
nodemon server
```

As expected, the Express server will run on port 3001 instead of 3000 (which is where the React dev server runs).

Browsing to `localhost:3001` will display the built production React app!

<details>
<summary>
❓ What command must be run to update the React app's production code?
</summary>
<hr>

**`npm run build`**

<hr>
</details>

## 6. Configure React for MERN-Stack Development

Note how we're viewing the React app without the React development server running, again, this is because we are viewing the production code that's in the **build** folder, not the code as it exists in the **src** folder.

So, when you are developing and nothing seems to be updating in the browser - be sure to verify that you are browsing at `localhost:3000`!

### Running Both Express & React During Development

To develop a MERN-Stack app, you'll need **two separate** Terminal sessions for running:

1. The Express backend (which is better to start first)
    <details>
    <summary>
    ❓ If we don't already have the Express server running, we start it with what command?
    </summary>
    <hr>

    ```
    nodemon server
    ```

    <hr>
    </details>

2. React's development server

    <details><summary>❓ What's the command to start React's dev server in the second Terminal?</summary>
    <p>

    ```
    npm start
    ```

    </p>
    </details>

Now, browse to `localhost:3000`, **not** `3001`!

So far, so good, just one more configuration issue...

### Ensuring that the React Dev Server Sends AJAX Calls to the Express Server

Let's think ahead to when we begin to make AJAX requests from the React app to our server using code like this:

```js
return fetch('/api/orders/history').then(res => res.json());
```

<details>
<summary>
❓ Which host/server will that fetch request be sent to?
</summary>
<hr>

**The same host as shown in the address bar:<br>`localhost:3000`**

<hr>
</details>

<details>
<summary>
❓ Where do we need the fetch requests be sent to during development?
</summary>
<hr>

**The Express server that's listening for AJAX requests at:<br>`localhost:3001` !**

<hr>
</details>

Luckily, the React team has created an easy fix for this dilemma. The React development server allows us to configure a "proxy" which specifies the host to forward API/AJAX calls to.

The fix is to add a `"proxy"` property in the  **package.json** (be sure that it's a "top-level" property):

```
  "browserslist": {
    "production": [
      ">0.2%",
      "not dead",
      "not op_mini all"
    ],
    "development": [
      "last 1 chrome version",
      "last 1 firefox version",
      "last 1 safari version"
    ]
  },
  "proxy": "http://localhost:3001"
}
```

> 👀 The React dev server will NOT automatically restart when changes are made to the package.json file.

Now the React development server will forward all AJAX calls, such as `fetch('/api/todos')`, to `localhost:3001` instead of `localhost:3000`.

BTW, this is only an issue **during development** - the deployed app will be just fine thanks to the way we structured the app as a single project.

#### Welcome to the MERN-Stack!

<details>
<summary>
👀 Do you need to sync your code?
</summary>
<hr>

**`git reset --hard origin/sync-1-finish-intro`**

<hr>
</details>

## 7. ❓ Essential Questions (2 mins)

<details>
<summary>
(1) What folder holds a React app's production-ready code?
</summary>
<hr>

**The `build` folder**

<hr>
</details>

<details>
<summary>
(2) What's the responsibility of the "catch all" route defined in the Express app?
</summary>
<hr>

Send back the **index.html** page for all non-API/AJAX requests.

<hr>
</details>

<details>
<summary>
(3) True or False: API routes will need to be defined in the Express app so that the React app can CRUD data, etc. on the server.
</summary>
<hr>

**True**

<hr>
</details>

<details>
<summary>
(4) True or False: The React app should use a "service/api" module to communicate with the backend's API routes via AJAX.
</summary>
<hr>

**True**.  We don't want to "litter" the React components with a bunch of AJAX code.

<hr>
</details>

## 8. Further Study

### HTML5's History API

Using HTML5's [History API](https://developer.mozilla.org/en-US/docs/Web/API/History), an application in the browser is able to manipulate the browser's current URL using JS and without triggering a server request.

Client-side router software can use the History API to perform client-side routing to load different "screens" of functionality and perform other magic without a causing a request to be sent to the server, thus there's no full-page refresh.

This approach works wonderfully when the client router is in charge and is the only thing manipulating the URL in the address bar. However, what about when a user enters a URL manually, or a link external to the client app is clicked? These cases require a small bit of configuration on the server - a simple "catch all" route that handles all requests that don't match requests for static assets, API routes, etc. The catch all route will then return the **index.html** and all is well.

Later in this unit you'll be introduced to the popular [React Router](https://github.com/ReactTraining/react-router), which uses the History API to perform client-side routing in React SPAs.

### Browser Hash Navigation

The HTML specification includes what is known as **Hash URIs**.

Hash URIs include a "hash" (`#`) in the URI, for example:<br>[https://facebook.github.io/react/docs/react-dom.html#reference](https://facebook.github.io/react/docs/react-dom.html#reference)  

If we browse to the above link, we will see that it takes us directly to the "Reference" section on the page.

Hovering over other titles/sub-titles on the page reveals other links that have their href's set to a value prefaced with a "#", for example:

```html
<a class="hash-link" href="#unmountcomponentatnode">#</a>
```

Notice that when we can click on these links, the address bar changes, but the browser does **not** make an HTTP request.

Today's client-side routers lean toward using the History API over Hash URIs due mainly to the fact that the URL's are "prettier" without the hash.

## References

[React Docs](https://facebook.github.io/react/)




<img src="https://i.imgur.com/IKHxRMa.png">

# MERN-Stack Infrastructure - Part 1

## Learning Objectives

|Students Will Be Able To:|
|---|
| Organize the React Frontend and Express Server Code |
| Implement Environment Variables Using the `dotenv` Module |
| Connect to a MongoDB Using Mongoose |

## Road Map

1. Setup
2. The 7-Part Plan for `mern-infrastructure`
3. Tidy Up the React App Generated by `create-react-app` (CRA)
4. Add Folders Used to Organize React Components
5. Add Folders to Organize the Express Server Code
6. Install and use `dotenv` to process a **.env** file
7. Install `mongoose` and Connect to a Database
8. Add an "external" **crud-helper.js** Module Used for Testing Models, etc.

## 1. Setup

This lesson continues to build-out the `mern-infrastructure` project right where the _Intro to Single-Page Applications (SPAs) and the MERN-Stack_ lesson left off.

Move into your **~/code** folder:
```
cd ~/code
```
Open the project in VS Code:
```
code .
```

### Start the Express Backend

Open an integrated Terminal in VS code (`control + backtick`).

Start the Express server:
```
nodemon server
```

### Start the React Development Server

Open a second integrated Terminal in VS code (`control + backtick`).

Start the React Development server:
```
npm run start
```

<details>
<summary>
👀 Do you need to sync your code?
</summary>
<hr>

**`git reset --hard origin/sync-2-part-1-starter`**

<hr>
</details>

## 2. The 7-Part Plan for `mern-infrastructure`

Over the next several lessons, we'll continue building out `mern-infrastructure` by implementing the boilerplate that's a part of any MERN-Stack app of significance.

Along the way, we will sprinkle in just a tad of SEI CAFE specific content when it makes sense to do so.

Here's the Plan:

**Part 1 - Project Setup:**
1. Tidy up the React app generated by `create-react-app` (CRA)
2. Add folders used to organize React components
3. Add folders to organize the Express server code
4. Install and use `dotenv` to process a **.env** file
5. Install `mongoose` and connect to a database
6. Add an "external" **crud-helper.js** module used for testing models, etc.

**Part 2 - Client-Side Routing:**
1. Set up `user` state
2. Add skeleton page-level components
3. Conditionally render based on the `user` state 
4. Intro to client-side routing using React Router
5. Implement client-side routing
6. Implement a typical navigation bar

**Part 3 - Implement Token-Based Auth:**
1. The process of adding a feature to a MERN-Stack app
2. Code the `<SignUpForm>` component as a class component
3. Add service & API modules on the client

**Part 4 - Implement Token-Based Auth (continued):**
1. Review of `fetch`
2. Review of handling promises with `async`/`await`
3. Make the AJAX request to sign-up
4. Define the server-side route for signing-up
5. Define the **controllers/api/users.js** module
6. Mock the `create` (sign-up) controller action

**Part 5 - Implement Token-Based Auth (continued):**
1. Discuss token-based authentication
2. Add the `User` model
3. Implement the `create` (sign-up) controller action

**Part 6 - Implement Token-Based Auth (continued):**
1. Save the token in the browser's local storage
2. Update the `user` state
3. Implement logging out
4. Implement logging in

**Part 7 - Implement Token-Based Auth (continued):**
1. Send the token with AJAX requests
2. Check the token on the server and add a `user` property to `req`
3. Implement middleware to protect server-side routes
4. Save MERN-Stack infrastructure to a new GH repo

Then, once all of the above infrastructure is in place, we'll save it to a separate GitHub repo for the purpose of being able to start new MERN-Stack projects by simply cloning it at anytime in the future!

## 3. Tidy Up the React App Generated by `create-react-app` (CRA)

Let's tidy up the generated React app by deleting some files we don't need at this time.

<details><summary>❓ Which JS file is the entry point of the React app?</summary>
<p>

**src/index.js**

</p>
</details>

### src/index.js

We're not going to be concerned with reporting the performance of this app, so we can optionally remove the `reportWebVitals()` call and the import.  Feel free to leave it if you wish and read the link for more info when you have time.

While in **index.js**, take note that it imports **index.css** which holds our application-wide styles.

Also as we learned, this is where the top-level `<App>` component is rendered from.  Let's tidy up **App.js** now...

### src/App.js

For better Emmet support and to stay consistent with the way we will name our future components, let's rename **App.js** to **App.jsx**.

> It may be necessary to restart React's Dev Server to get the app to compile.

Now in **App.jsx** we're going to:

- Change the outer `<div>` to be a `<main>` React Element.
- Clear out all of the `<App>` components children.
- Add "App" as placeholder text.
- Remove the import of `logo`.
- Move the `export default` in front of the `function`

```jsx
import './App.css';

export default function App() {
  return (
    <main className="App">
      App
    </main>
  );
}
```

> Note that `import React from 'react';` is no longer necessary with the latest version of the library's JSX transform and build configuration.

Now we can remove the following unused files from the project:

- **App.test.js**
- **logo.svg**
- **reportWebVitals.js** (assuming you removed it from index.js)
- **setupTests.js**

Also, **if** you removed **reportWebVitals.js**, you can uninstall it from the **package.json** by running `npm uninstall web-vitals`.

### **public/index.html**

Let's not forget to update the `<title>` element in the `<head>` of **index.html**.

You'll find **index.html** in the **public** folder, along with a few other static assets such as **favicon.ico**.

Let's update the `<title>` element as follows:

```html
<title>MERN Infrastructure</title>
```

## 4. Add Folders Used to Organize React Components

A typical React app has a high number of modules and we'll want to create a folder structure that best organizes these modules.

### Dedicated Component Folders

In React apps, it's a best practice to create a dedicated folder for each component.

Yes, this will result in quite a few folders, however, real-world React components often have dedicated CSS and test modules in addition to the module for the component itself - so it makes sense to keep these modules together in their own folder.

Let's create a folder for our only component at this time:

```
mkdir src/App
```

> The folder should be named **exactly** as that of the component - without the file extension, of course.

Now let's move the App related modules into the new **App** folder:

```
mv src/App.* src/App
```

The above move will require us to fix the import within **index.js**, which we'll do a bit later because we're not done organizing yet...

### Folders for Organizing Page-Level and Non-Page Components

Because of the high number of components in a typical React app, we'll create two additional folders to use as a further level of organization:

- **src/pages**: This folder will hold the "page-level" components that implement the app's main functionality.  Page-level components are rendered for each client-side route.  For example, in the past where we might have rendered a **movies/show.ejs** template for a `GET /movies/:id` route, we now might want to render a **MovieDetailPage.jsx** component when at the `/movies/:id` client-side route instead. We'll move the `<App>` component into the src/pages folder as well.

- **src/components**: This folder will hold all other non-page-level components. These components may often be used/rendered by any number of other components. 

Let's create the above two folders:

```
mkdir src/components src/pages
```

Now let's move the `<App>` component's folder into **src/pages**:

```
mv src/App src/pages
```

### Update the Import in **index.js**

The previous restructuring requires an update to the way **App.jsx** is being imported within **index.js**:

```jsx
// index.js

import App from './pages/App/App';
```

> Note:  Again, it may be necessary to restart React's Dev Server to get the app to compile.

## 5. Add Folders to Organize the Express Server Code

While we're creating folders used to organize our code, let's create some for the Express app that you're familiar with:

```
mkdir config routes models controllers
```

We'll be using the above folders to organize our server-side code soon enough.

## 6. Install and use `dotenv` to process a **.env** file

As we've seen in the past, we need a way to access environment variables and secrets. 

We're going to use the `dotenv` module to read the `key=value` pairs in a **.env** file exactly like we did in Unit 2.

### Install and Run the `dotenv` Module

First the install:

```
npm i dotenv
```

Now let's add it to **server.js**:

```jsx
const logger = require('morgan');

// Always require and configure near the top 
require('dotenv').config();
```

### Create the **.env** File

Be sure to touch the **.env** file in the project root folder:

```
touch .env
```

Now we're setup to hold secrets such as the database connection string...

## 7. Install `mongoose` and Connect to a Database

As you'll remember, in Unit 2 we used the [Mongoose](https://mongoosejs.com/) library to interact with a MongoDB database.

Mongoose is also the go to in MERN-Stack apps.

First, we need to install it as usual:

```
npm i mongoose
```

### Create the **config/database.js** Module

Just like we did in Unit 2, we'll use a dedicated Node module to connect to the database:

```
touch config/database.js
```

This code might look familiar:

```js
const mongoose = require('mongoose');

mongoose.connect(process.env.DATABASE_URL);

const db = mongoose.connection;

db.on('connected', function () {
  console.log(`Connected to ${db.name} at ${db.host}:${db.port}`);
});
```

### Add the `DATABASE_URL` to the **.env**:

Go copy your Atlas connection string (`DATABASE_URL`) from the **.env** file of your Project 2 or mongoose-movies and paste it into the **.env** we created a moment ago:

```
DATABASE_URL=mongodb+srv://seistudent:thepassword@cluster0.alq0ver.mongodb.net/mongoose-movies?retryWrites=true&w=majority
```

Now update the the database name from whatever it currently is, e.g., `mongoose-movies` to something like `mern-infrastructure`.

```
DATABASE_URL=mongodb+srv://seistudent:thepassword@cluster0.alq0ver.mongodb.net/mern-infrastructure?retryWrites=true&w=majority
```

### Connect to the Database

We `require` **database.js** in **server.js** in order to connect to the database:

```js
require('dotenv').config();

// Connect to the database
require('./config/database');
```

> Be sure to require the config/database module after dotenv.

Looking good:

<img src="https://i.imgur.com/RhxQdTB.png">

## 8. Add an "external" **crud-helper.js** Module Used for Testing Models, etc.

We've previously used a Node REPL to perform CRUD and test our models by following [these instructions](https://gist.github.com/jim-clark/57b646abbb6c0ce09f9fa948eab6febc).

It's worth the short amount of time it takes to create a module we can load in a Node REPL any time we need to perform CRUD outside of our application.

The module is not run as part of the Express app - it's "external" to it.

Start by creating the module:

```
touch crud-helper.js
```

There's no models to require at this time, but we'll add them as we build out SEI CAFE:

```js
// Connect to the database
require('dotenv').config();
require('./config/database');

// Require the Mongoose models
// const User = require('./models/user');
// const Item = require('./models/item');
// const Category = require('./models/category');
// const Order = require('./models/order');

// Local variables will come in handy for holding retrieved documents
let user, item, category, order;
let users, items, categories, orders;
```

This is how we will use the **crud-helper.js** module in the future:

```
mern-infrastructure[main*] % node
Welcome to Node.js v18.11.0.
Type ".help" for more information.
> .load crud-helper.js
// Connect to the database
require('dotenv').config();
require('./config/database');
 
// Require the Mongoose models
// const User = require('./models/user');
// const Item = require('./models/item');
// const Category = require('./models/category');
// const Order = require('./models/order');
 
// Local variables will come in handy
let user, item, category, order;
let users, items, categories, orders;
 
{}
> Connected to mern-infrastructure at localhost:27017
```

Type `.exit` or `control + c` twice to exit the REPL.

It sure doesn't look like much yet - but it's a start!

<img src="https://i.imgur.com/yhORihu.png">

Congrats - we're off and running toward the MERN-Stack!

<details>
<summary>
👀 Do you need to sync your code?
</summary>
<hr>

**`git reset --hard origin/sync-2-part-1-finish`**

<hr>
</details>



<img src="https://i.imgur.com/IKHxRMa.png">

# MERN-Stack Infrastructure - Part 2

## Learning Objectives

|Students Will Be Able To:|
|---|
| Add `user` State to the MERN-Stack App |
| Selectively Render Components Using a Ternary Expression |
| Implement Client-Side Routing Using the React Router Library |
| Implement Basic Navigation in a MERN-Stack App |

## Road Map

1. Setup
2. The Plan - Part 2
3. Set Up `user` State
4. Add Skeleton Page-Level Components
5. Conditionally Render Based On the `user` State
6. Intro to Client-Side Routing Using React Router
7. Implement Client-Side Routing
8. Implement a Basic Navigation Bar
9. Further Study

## 1. Setup

This lesson continues to build-out the `mern-infrastructure` project right where the _MERN-Stack Infrastructure - Part 1_ lesson left off.

Move into your **~/code** folder:
```
cd ~/code
```
Open the project in VS Code:
```
code .
```

### Start the Express Backend

Open an integrated Terminal in VS code (`control + backtick`).

Start the Express server:
```
nodemon server
```

### Start the React Development Server

Open a second integrated Terminal in VS code (`control + backtick`).

Start the React Development server:
```
npm start
```

<details>
<summary>
👀 Do you need to sync your code?
</summary>
<hr>

**`git reset --hard origin/sync-2-part-2-starter`**

<hr>
</details>

## 2. The Plan - Part 2

In Part 2 we will implement client-side routing as we continue to learn how to build a MERN-Stack app by following a realistic workflow.

**Part 2 - Client-Side Routing:**
1. Set up `user` state
2. Add skeleton page-level components
3. Conditionally render based on the `user` state 
4. Intro client-side routing using React Router
5. Implement client-side routing
6. Implement a typical navigation bar

## 3. Set Up `user` State

Before we jump into the routing, let's set up some state that we can use to dynamically render different components depending upon two factors:

- Is there a logged in user?
- If the user is logged in, render different page-level components according to the path in the address bar.

The following diagrams the routing in SEI CAFE:

<img src="https://i.imgur.com/UwNRJYv.png">

Note that `<App>` is always rendered but only one of the other page-level components render.

### Is There a Logged In User?

A good place to start is to define the `user` state.

### 👉 You Do - Define the `user` State in **App.jsx** (2 mins)

1. Use the `useState` hook to define a state variable named `user`.
2. Initialize `user` to `null`. 
3. The setter function should be named according to convention.

> Hint: Don't forget to add the necessary import.

## 4. Add Skeleton Page-Level Components

Now that we have the `user` state, let's continue setting up routing by stubbing up those three page-level components above.

<details>
<summary>
❓ In which folder will we define these new page-level components?
</summary>
<hr>

**src/pages**

<hr>
</details>

### 👉 You Do - Stub up SEI CAFE's page-level components (5 mins)

1. Create the `<AuthPage>`, `<NewOrderPage>` and `<OrderHistoryPage>` components.
2. Be sure to follow best practices (each in their own folder, etc.) and naming conventions. 
3. Each component should simply render an `<h1>` with the name of the component as its content, e.g., `<h1>AuthPage</h1>`.

> Hint: Be productive by defining one component, then copy/paste its folder and rename everything.

## 5. Conditionally Render Based On the `user` State

We've already seen how to conditionally render components by using:

- Ternary expressions: Used to render one component or another.
- Logical (`&&`) expressions: Used to render a component or nothing.

Examining our routing diagram above, we can see that we are conditionally rendering based upon whether the state of `user` is `null` (user not logged in) or not `null` (user logged in).

Since we want to render either `<AuthPage>` or one of the other two (`<NewOrderPage>` or `<OrderHistoryPage>`), we'll opt for a ternary expression.

Until we start using React Router, we'll just render `<NewOrderPage>` if there's a user logged in.

Here's the refactor in **App.jsx**:

```jsx
return (
  <main className="App">
    { user ?
      <NewOrderPage />
      :
      <AuthPage />
    }
  </main>
);
```

You'll have an error if the components were not automatically imported. Let's ensure all three components are imported while we're at it:

```jsx
import './App.css';
// Import the following components
import AuthPage from '../AuthPage/AuthPage';
import NewOrderPage from '../NewOrderPage/NewOrderPage';
import OrderHistoryPage from '../OrderHistoryPage/OrderHistoryPage';
```

> 👀 `command/ctrl + D` comes in handy for using multiple cursors to edit.

The `<AuthPage>` should now be rendering as expected.

<img src="https://i.imgur.com/QvEh2m6.png">

Updating the hook's State to any truthy value will result in `<NewOrderPage>` rendering instead!

Now let's learn about how to use React Router to perform client-side routing...

## 6. Intro to Client-Side Routing Using React Router

The React library does not include routing functionality.

[React Router](https://reactrouter.com/) is the de facto client-side routing library for both React and [React Native](https://reactnative.dev/).

> 👀 React Router has recently been updated from version 5.x to 6.x which included breaking changes.  Be aware that the code in most of the tutorials, etc. out there that include React Router may not work any more. 

### Install React Router

Since it's a third-party library, React Router must be installed:

```
npm i react-router-dom
```

> 👀 `react-router-dom` is the web-based router used with React apps.  `react-router-native` is the library for React Native.

### How it Works - React Router Is Component-Based!

**React Router provides several components used to conditionally render our app's components based upon the path of the URL in the address bar**

Please read the above again because it's fundamental to understanding how React Router works.

### The `<BrowserRouter>` Component

[`<BrowserRouter>`](https://reactrouter.com/docs/en/v6/api#browserrouter) is the top-level React Router component that makes React Router work.

Only a single `<BrowserRouter>` needs to be rendered and any components that need to use routing features must be nested within it, thus, the convention is to wrap the `<App>` component.

<details><summary>❓ In which module will we need to wrap <code>&LT;App></code> with <code>&LT;BrowserRouter></code>?</summary>
<p>

**index.js**

</p>
</details> 

Check out how we can use an **alias** with the `as` keyword when importing:

```jsx
import App from './pages/App/App';
// Import the top-level BrowserRouter component
import { BrowserRouter as Router } from 'react-router-dom';
```

Now let's refactor so that `<App>` is rendered by `<Router>`:

```jsx
root.render(
  <React.StrictMode>
    <Router><App /></Router>
  </React.StrictMode>
);
```

Using React Developer Tools we can see that the `<BrowserRouter>` component renders a few other components in addition to our `<App>` component:

<img src="https://i.imgur.com/Je9AZYy.png">

> 👀 Those components named ending with `.Provider` are using React's [Context API](https://reactjs.org/docs/context.html) to provide info to  components down in the component hierarchy without having to pass that info as props. 

## 7. Implement Client-Side Routing

Because React Router is component-based, it can be used in **any** component to conditionally render other components.

However, most React apps only need to perform routing in the `<App>` component - let's see how...

### The `<Routes>` Component

Any component that wants to define client-side routes will first need to render a `<Routes>` component.

Because `<App>` is where we will define all client-side routes, let's import the `Routes` component there:

```jsx
import { useState } from 'react';
// Add the following import
import { Routes } from 'react-router-dom';
```

Now we can use `<Routes>` in `<App>` to wrap our future routes...

```jsx
return (
  <main className="App">
    { user ?
      <Routes>
        {/* Route components in here */}
      </Routes>
      :
      <AuthPage />
    }
  </main>
);
```

On to defining specific routes using the `<Route>` component...

### The `<Route>` Component

The [`<Route>`](https://reactrouter.com/docs/en/v6/api#routes-and-route) component is the main component used to conditionally render a component instance (referred to as an "element" by React Router).

**`<Route>` works by simply rendering the element (instance of a component) assigned to its `element` prop when its `path` prop matches the current URL (path) in the address bar!**

Let's add the `<Route>` component to our list imports:

```jsx
import { useState } from 'react';
// Add the following import
import { Routes, Route } from 'react-router-dom';
```

### Rendering Components According to the Path of the URL

Once again referring to the routing diagram for SEI CAFE shows that we want to render:

- `<NewOrderPage>` when we browse to `/orders/new`, and
- `<OrderHistoryPage>` when we browse to `/orders`

So, let's add a `<Route>` component and set both its `path` and `element` prop to conditionally render `<NewOrderPage>`:

```jsx
return (
  <main className="App">
    { user ?
      <Routes>
        <Route path="/orders/new" element={<NewOrderPage />} />
      </Routes>
      :
      <AuthPage />
    }
  </main>
);
```

As you can see, we've set the `path` prop to the URL/path that we plan to use for this route.

Additionally, the `element` prop is interesting in that it accepts an actual component instance:

```jsx
element={<NewOrderPage />}
```

instead of the previous way of providing the component itself:

```jsx
component={NewOrderPage}
```

The advantage of the new approach is that it's easier to pass props to the component being rendered.

### Temporarily Update `user` State for Testing Purposes 

To avoid having to continually update the `user` state using React Developer Tools, let's temporarily initialize `user` to an empty object instead of `null`:

```jsx
const [user, setUser] = useState({});
```

Now, thanks to the `<Route>` component we just added, changing the path of the URL to `/orders/new` will render the `<NewOrderPage>` component as expected:

<img src="https://i.imgur.com/JxQVTFx.png">

### 👉 You Do - Add Another `<Route>` (2 mins)

1. Add a new `<Route>` used to render `<OrderHistoryPage />` when the path of the URL is `/orders`

2. Test by changing the path of the URL back and forth between `/orders` and `/orders/new`.

## 8. Implement a Basic Navigation Bar

Although SEI CAFE does not utilize a typical navigation bar, we'll code one as part of the infrastructure since many MERN-Stack apps will utilize one.

### 👉 You Do - Stub up a `<NavBar>` component (3 mins)

1. Create a `<NavBar>` component within the `components` folder.
2. `<NavBar>` should render a `<nav>` React Element with the text "NavBar" as its only content for now.
3. Import `<NavBar>` in **App.jsx**

<hr>

<details>
<summary>
❓ We want <code>&LT;NavBar></code> to always display when there's a logged in user and before the page-level component, where would we add it to the JSX?
</summary>
<hr>

**Right before the `<Routes>`, requiring a React Fragment to wrap `<NavBar>` and `<Routes>`.**

<hr>
</details>

<br>

Yup, just like this:

```jsx
return (
  <main className="App">
    { user ?
      <>
        <NavBar />
        <Routes>
          <Route path="/orders/new" element={<NewOrderPage />} />
          <Route path="/orders" element={<OrderHistoryPage />} />
        </Routes>
      </>
      :
      <AuthPage />
    }
  </main>
);
```

Yes, it's necessary to add a React.Fragment (`<>`) to wrap the `<NavBar>` and `<Routes>` components.

Resulting in this for now:

<img src="https://i.imgur.com/ThY0xki.png">

<details>
<summary>
❓ Assuming we want <code>&LT;NavBar></code> to render at all times regardless of whether there's a logged in user or not, where would we add it to the JSX?
</summary>
<hr>

**Between `<main>` and the ternary expression.**

<hr>
</details>

### The `<Link>` Component

<details>
<summary>
❓ What HTML element did we use to change the URL in our previous web apps?
</summary>
<hr>

**The `<a>` hyperlink element.**

<hr>
</details> 

<details>
<summary>
❓ What happens if we use traditional HTML hyperlinks in a SPA?
</summary>
<hr>

**It would cause a page reload when performing the navigation.**

<hr>
</details> 

Luckily, React Router provides a [`<Link>`](https://reactrouter.com/docs/en/v6/api#link) component that renders hyperlinks that when clicked, change the URL client-side only without triggering an HTTP request.

Here's how we can use `<Link>` components in **NavBar.jsx** to change the route client-side:

```jsx
// Don't forget the import
import { Link } from 'react-router-dom';

export default function NavBar() {
  return (
    <nav>
      <Link to="/orders">Order History</Link>
      &nbsp; | &nbsp;
      <Link to="/orders/new">New Order</Link>
    </nav>
  );
}
```

Clicking any of the links performs client-side routing where React Router will:

- Update the path in the address bar without causing the page to reload
- Automatically trigger a re-render

<img src="https://i.imgur.com/R5aElPF.png">

Inspecting the elements on the page will reveal that indeed an `<a>` element is being emitted to the DOM when we use a `<Link>` component.  However, although they look like ordinary `<a>` elements, React intercepts their click event thus preventing an HTTP request from being sent.

> 👀 If you accidentally use an `<a>` tag, React will not intercept the click event and a page reload will occur 😞

Although we've learned most there is to know about client-side routing, we'll learn more in future lessons, including how to change client-side routes programmatically (via code).

#### Congrats on implementing client-side routing!

<details>
<summary>
👀 Do you need to sync your code?
</summary>
<hr>

**`git reset --hard origin/sync-2-part-2-finish`**

<hr>
</details>

## 9. Further Study

### Route Params - Client-Side

- Check out React Router's [`useParams`](https://reactrouter.com/docs/en/v6/hooks/use-params) hook that allows you to access route parameters similar to how we did in Express.

### Other Topics

- Use React Router's [`<NavLink>`](https://reactrouter.com/docs/en/v6/components/nav-link) component when you want to style hyperlinks dynamically based upon the current URL.

- Learn more about the [Context API](https://reactjs.org/docs/context.html) which is a way to provide info to child components without having to pass that info as props.



<img src="https://i.imgur.com/IKHxRMa.png">

# MERN-Stack Infrastructure - Part 3

## Learning Objectives

|Students Will Be Able To:|
|---|
| Follow a Process for Adding Functionality to a MERN-Stack App |
| Define a Component as a Class |
| Organize Non-React Code Into Service & API Modules |

## Road Map

- The Plan - Part 3
- Infrastructure - Part 3 of 7
- Further Study

## The Plan - Part 3

In Part 3 we will begin to implement the ever so important user authentication.

Along the way we'll also learn how to define a component as a class instead of a function and preview how we're going to organize non-React code into service & API modules.

**Part 3 - Begin Implementing Token-Based Auth:**
1. The process of adding a feature to a MERN-Stack app
2. Code the `<SignUpForm>` component as a class component
3. Add service & API modules for the client

## 1. The process of adding a feature to a MERN-Stack app

The **process** of adding a feature to a MERN-Stack SPA is similar to what we followed when adding a feature to our traditional web apps in Units 2 & 3 in that we typically:

1. Start with the UI/frontend... Render a component with an event prop designed to handle interaction from the user, e.g., `onClick`.
2. Stub up and assign an event handler function to the event prop.
3. In the event handler function, write code to accomplish the task at hand which could include any of the following:
    - Perform program logic, calculations, etc.
    - Update local state.
    - Invoke service methods to make AJAX requests to the server.
    - Invoke a method passed to it as a prop so that the component up the hierarchy can respond to the event by updating state, etc.
    - Etc.<br><br>Then, in the case that an AJAX request was made...

4. Define a route on the server that maps the AJAX request to a controller action.
5. Code the controller action to perform any necessary CRUD and send a JSON response back to the client.
6. Back in the event handler of the component, if necessary, update state using the JSON received from the server and optionally programmatically change routes.

Basically, adding functionality starts with code on the client, then the server, and coming back full-circle to the client.

### Update `user` Initialization

If we're going to start implementing auth, we'll need to change back the initialization of the `user` state to `null` because we need to see `<AuthPage>`:

```jsx
// App.jsx

export default function App() {
  // Initialize user to null
  const [user, setUser] = useState(null);
```

### As a visitor (AAV), I want to sign up as a user so that I can place new orders and view my previous orders.

To implement the functionality of signing-up, we'll begin client-side as described above by defining a component that will contain a form with an `onSubmit` event prop...

## 2. Code the `<SignUpForm>` Component as a Class Component

We'll be adding a `<SignUpForm>` component that will be rendered by `<AuthPage>`.

In the new `<SignUpForm>` component, as you saw in the _React Fundamentals - Handling Input and Events_ lesson, we'll need to manage state for the controlled inputs used to gather information from the user that wants to sign up.

However, instead of using a function component, we'll define `<SignUpForm>` as a class component which used to be the go to for defining components that needed to manage state prior to hooks being added to the React library.

#### 💪 Practice Exercise - Stub Up the Module for the `<SignUpForm>` Component (1 minute)

The naming conventions of the folders and files for class components is no different than that of function components.

- Create the folder and module for `<SignUpForm>` following the same conventions and best practices as always.

> Hint:  Be careful of typos (`SignUpForm` vs. `SignupForm`).

### Set Up `<SignUpForm>` as a Class Component

Class components in React typically inherit from the [`Component`](https://reactjs.org/docs/react-component.html) class defined in the React library, let's import it:

**note**: With the new feature improvements provided by React hooks([See React State module for React hooks review here](../../1-react/1.3-react-state.md))in React 16.8, the React team now recommends engineers to use functional components and React hooks instead of class components. See React team's comments on moving from class components to functional components here [React classes to hooks](https://reactjs.org/docs/hooks-faq.html#from-classes-to-hooks). It is important to still understand class components and to be able to use these, as many projects will still use the older class component patterns. You will see a mixture of class and functional components using hooks in this course.


```jsx
// SignUpForm.jsx

import { Component } from 'react';
```

> Check out the Further Study section to learn more about the `PureComponent` class available to inherit from as well.

This is how we stub up a class component:

```jsx
export default class SignUpForm extends Component {

  render() {
    return (
      <div>
        SignUpForm
      </div>
    );
  }
}
```

A class component **must** implement a `render` method responsible for returning the component's JSX - making the `render` method itself very much like a function component.

### Importing and Rendering a Class Component

There's no difference in how we import and render function and class components.

Let's import and render `<SignUpForm>` within **AuthPage.jsx** and do a minor refactor while we're at it:

```jsx
// AuthPage.jsx

import SignUpForm from '../../components/SignUpForm/SignUpForm';

export default function AuthPage() {
  return (
    <main>
      <h1>AuthPage</h1>
      <SignUpForm />
    </main>
  );
}
```

So, as you can see, we can't even tell if a component is defined as a function or class when we import and render it:

<img src="https://i.imgur.com/eklFYbq.png">

### Initializing a Class Component's State

Our `<SignUpForm>` is going to need the following state:

- `name`: Name of the user
- `email`: The email address of the user
- `password`: The user's password
- `confirm`: Used to confirm the password is entered correctly
- `error`: Used to display an error message if the sign up fails

Unlike with a function component that can define multiple pieces of state by using the `useState` hook multiple times, **a class component's state is always a single object assigned to a `state` property on the instance of the component**.

There are two ways to initialize the `state` property:

- Using the `constructor` method (the original approach).
- Using the newer [class fields](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/Public_class_fields) approach.

Of course, we'll use the **class fields** approach that all the cool kids are using, but here's how it would look if we initialized the state using the `constructor` method:

```jsx
export default class SignUpForm extends Component {
  // state is always an object with a property for each "piece" of state
  constructor() {
    this.state = {
      name: '',
      email: '',
      password: '',
      confirm: '',
      error: ''
    };
  }
```

The following is the **class field** approach we're going with:

```jsx
export default class SignUpForm extends Component {
  state = {
    name: '',
    email: '',
    password: '',
    confirm: '',
    error: ''
  };
```

> FYI:  Internally, the class field syntax is converted into the constructor method approach.

### `this` Keyword in a Class Component

When we use class components, it's important to realize that the components themselves are instances of the class instantiated by React the first time they are rendered.

<details><summary>❓ An instance of a class is an _______.</summary>
<p>

**object**

</p>
</details>

<details><summary>❓ An object's methods accesses other properties/methods of the object via the _______ keyword.</summary>
<p>

**`this`**

</p>
</details>

Unlike with function components, a class component accesses its props and methods using `this`, for example:

- `this.props`: Accesses the class component's `props` object, e.g., `this.props.someProp`.
- `this.state`: Accesses the class component's `state` object, e.g., `this.state.email`.
- `this.someMethod()`: Invokes a method defined in the class component or inherited by the superclass (`Component`) such as `this.setState()` used to update state.

### The Complete `render` Method of `<SignUpForm>`

Here's the completed code of the `render()` method that we'll copy/paste and discuss:

```jsx
render() {
  const disable = this.state.password !== this.state.confirm;
  return (
    <div>
      <div className="form-container">
        <form autoComplete="off" onSubmit={this.handleSubmit}>
          <label>Name</label>
          <input type="text" name="name" value={this.state.name} onChange={this.handleChange} required />
          <label>Email</label>
          <input type="email" name="email" value={this.state.email} onChange={this.handleChange} required />
          <label>Password</label>
          <input type="password" name="password" value={this.state.password} onChange={this.handleChange} required />
          <label>Confirm</label>
          <input type="password" name="confirm" value={this.state.confirm} onChange={this.handleChange} required />
          <button type="submit" disabled={disable}>SIGN UP</button>
        </form>
      </div>
      <p className="error-message">&nbsp;{this.state.error}</p>
    </div>
  );
}
```

The form is rendering but it's ugly and we can't type in the inputs yet because the `this.handleChange` method assigned to the `onChange` prop is not defined yet...

### Defining Event Handler Methods in a Class Component

The `handleChange()` method **can't** be defined using the usual syntax for defining an instance method of a class like that of the `render()` method.

The reason the usual syntax won't work is because the method will be invoked as a callback and thus will not have `this` bound to the component instance as necessary if we want to be able to access `this.props`, `this.setState()`, etc.

There are two solutions to ensure that a method has `this` correctly set to the component instance:

- Define the method as usual and use JavaScript's [`bind`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_objects/Function/bind) method in the `constructor` method to explicitly set the value of `this`.
- Use the **class field** syntax along with an arrow function when defining the method which by its very nature fixes the issue due to the way **class fields** are actually initialized in the `constructor` method.

> FYI:  The trouble with the binding of `this` in class components is definitely one of the main inspirations for React hooks!

So, here's how we use class field syntax to properly define methods used to handle events in class components:

```jsx
// The object passed to setState is merged with the current state object
handleChange = (evt) => {
  this.setState({
    [evt.target.name]: evt.target.value,
    error: ''
  });
};

render() {
  ...
}
```

The controlled inputs should now update their appropriate state!

Even the cool little line of code<br>`const disable = this.state.password !== this.state.confirm;`<br>combined with the `disabled` prop on the submit button should be working!

That code is pretty much what we learned in the _React Fundamentals - Handling Input and Events_ lesson except...

### Updating State in a Class Component

There's two key differences in how state is updated in class vs. function components:

- Class components always update state by invoking the inherited `setState()` method vs. invoking the setter function(s) returned by the `useState` hook in function components.
- [`setState()`](https://reactjs.org/docs/react-component.html#setstate) accepts an object as an arg and this object is **merged** into the existing state object. This differs with how a function component's setter function **replaces** that state with the value provided.

    > Note: `setState` also has a couple of other signatures - refer to the [docs](https://reactjs.org/docs/react-component.html#setstate) for more info.

### Handling the `onSubmit` Event

The `<form>` React Element in `<SignUpForm>` already has an event handler method assigned to its `onSubmit` prop.

#### 💪 Practice Exercise - Stub Up the `handleSubmit()` Method (2 minutes)

- Using the same class field syntax used when defining `handleChange()`, define a method named `handleSubmit()` above the `render()` method.
- As we learned during the _React Fundamentals - Handling Input and Events_ lesson, we need to prevent the form from being submitted to the server by including `evt.preventDefault();` as the first line of code.
- Baby step by adding this additional line of code `alert(JSON.stringify(this.state));`.

Check it out by typing in some info and submitting the form:

<img src="https://i.imgur.com/W0mWxOp.png">

### Add the CSS

Yeah, `<SignUpForm>` is pretty ugly, however, the JSX we added was thinking ahead in terms of styling because the `<form>` React Element has a `className="form-container"` prop.

**❓ The `form-container` CSS class is intended to be reused by multiple forms in the app, therefore it should be defined in the ________ module?**

The CSS for the SEI CAFE app is not trivial, so instead of adding CSS to **index.css** in bits and pieces, let's go ahead and add all the general purpose CSS up front:

```css
/* CSS Custom Properties */
:root {
  --white: #FFFFFF;
  --tan-1: #FBF9F6;
  --tan-2: #E7E2DD;
  --tan-3: #E2D9D1;
  --tan-4: #D3C1AE;
  --orange: #F67F00;
  --text-light: #968c84;
  --text-dark: #615954;
}

*, *:before, *:after {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen',
  'Ubuntu', 'Cantarell', 'Fira Sans', 'Droid Sans', 'Helvetica Neue',
  sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: var(--tan-4);
  padding: 2vmin;
  height: 100vh;
}

code {
  font-family: source-code-pro, Menlo, Monaco, Consolas, 'Courier New',
    monospace;
}

#root {
  height: 100%;
}

.align-ctr {
  text-align: center;
}

.align-rt {
  text-align: right;
}

.smaller {
  font-size: smaller;
}

.flex-ctr-ctr {
  display: flex;
  justify-content: center;
  align-items: center;
}

.flex-col {
  flex-direction: column;
}

.flex-j-end {
  justify-content: flex-end;
}

.scroll-y {
  overflow-y: scroll;
}

.section-heading {
  display: flex;
  justify-content: space-around;
  align-items: center;
  background-color: var(--tan-1);
  color: var(--text-dark);
  border: .1vmin solid var(--tan-3);
  border-radius: 1vmin;
  padding: .6vmin;
  text-align: center;
  font-size: 2vmin;
}

.form-container {
  padding: 3vmin;
  background-color: var(--tan-1);
  border: .1vmin solid var(--tan-3);
  border-radius: 1vmin;
}

p.error-message {
  color: var(--orange);
  text-align: center;
}

form {
  display: grid;
  grid-template-columns: 1fr 3fr;
  gap: 1.25vmin;
  color: var(--text-light);
}

label {
  font-size: 2vmin;
  display: flex;
  align-items: center;
}

input {
  padding: 1vmin;
  font-size: 2vmin;
  border: .1vmin solid var(--tan-3);
  border-radius: .5vmin;
  color: var(--text-dark);
  background-image: none !important; /* prevent lastpass */
  outline: none;
}

input:focus {
  border-color: var(--orange);
}

button, a.button {
  margin: 1vmin;
  padding: 1vmin;
  color: var(--white);
  background-color: var(--orange);
  font-size: 2vmin;
  font-weight: bold;
  text-decoration: none;
  text-align: center;
  border: .1vmin solid var(--tan-2);
  border-radius: .5vmin;
  outline: none;
  cursor: pointer;
}

button.btn-sm {
  font-size: 1.5vmin;
  padding: .6vmin .8vmin;
}

button.btn-xs {
  font-size: 1vmin;
  padding: .4vmin .5vmin;
}

button:disabled, form:invalid button[type="submit"] {
  cursor: not-allowed;
  background-color: var(--tan-4);
}

button[type="submit"] {
  grid-column: span 2;
  margin: 1vmin 0 0;
}
```

That's better!  But rest assured we'll continue to improve the layout and styling as we continue coding out `mern-infrastructure`/SEI CAFE.

<img src="https://i.imgur.com/CHNtKss.png">

Next lesson we'll continue writing the code in the `handleSubmit()` method to send the user's sign-up info to the server using an AJAX request.  

However, doing so in a way that's more likely to get you hired requires organizing such code within **service** & **API** modules...

## 3. Add Service & API Modules for the Client

In a MERN-Stack app there's bound to be application/business logic, AJAX/API requests, etc.

Although it would be possible to code this logic directly within components, there are downsides of doing so:

- Poor code organization. As you know, it's better to modularize related code into separate modules, e.g., the `config/database.js` module.  Organizing code into modules makes it easier to build an application because you'll more or less know where new code will go.  It's also easier to refactor and debug when code is organized into focused modules.
- Smaller, more readable components. Reading a line of code like `const user = await signUp(formData);` in a component is far better than having read through all of the code included in the `signUp()` "service" function.
- Not DRY and violates the "separation of concerns" principle.  For example, if we wanted to fetch the same data from more than one component, we'd be repeating ourselves. Service and API modules can often be used in multiple projects.

### Utilities, Services, APIs, oh my...

Some common ways to organize code into modules are:

- **Utility modules**: Modules that hold general purpose functions, for example, a `formatTime(seconds)` function.  These modules are reusable in multiple projects.
- **Service modules**: Service modules are where we can organize application specific logic such as functions for signing-up or logging in a user. Service modules often use and depend upon API modules...
- **API modules**: API modules are for abstracting logic that make network requests such as AJAX calls to the backend or third-party APIs. This abstraction makes it easier to refactor code to use different techniques, libraries, etc.  For example, we are going to be using `fetch` for our AJAX communications, however, refactoring to use a library such as Axios would be made easy thanks to the use of API modules.

### Create a **utilities** Folder

Let's create a **src/utilities** folder used to hold any utility, service or API modules that we need in the future:

```
mkdir src/utilities
```

### Create a **users-service.js** Module

We will use a **src/utilities/users-service.js** module to organize functions used to sign-up, log in, log out, etc.

```
touch src/utilities/users-service.js
```

Any component can import the functions exported from **users-service.js** as needed.

### Create a **users-api.js** Module

The **users-service.js** module will definitely need to make AJAX requests to the Express server.

As discussed earlier, network related code is better abstracted into its own modules.

Let's create an API module that will handle user-related communications with the server:

```
touch src/utilities/users-api.js
```

#### Congrats on getting started with implementing user authentication!

On to the lab!

## Further Study

- Class components can also inherit from [PureComponent](https://reactjs.org/docs/react-api.html#reactpurecomponent) that can provide a performance boost in some cases.





<img src="https://i.imgur.com/IKHxRMa.png">

# MERN-Stack Infrastructure - Part 4

## Learning Objectives

|Students Will Be Able To:|
|---|
| Call "Service" Methods from a Component |
| Make AJAX Requests From an "API" Module Using `fetch` |

## Road Map

- The Plan - Part 4
- Infrastructure - Part 4 of 7

## The Plan - Part 4

In Part 4 we will continue to implement user authentication.

FYI, user authentication requires implementing code that's typical of most features in a MERN-Stack app including: 

- Responding to user interaction by handling events.
- Making AJAX requests to the server.
- Updating state using JSON data returned from the server.

So, when we're finally done with part 7, implementing the main functionality of an app, e.g., placing new orders, will be more of the same!

**Part 4 - Implementing Token-Based Auth (continued):**
  1. Review of `fetch`
  2. Review of handling promises with `async`/`await`
  3. Make the AJAX request to sign-up
  4. Define the server-side route for signing-up
  5. Define the **controllers/api/users.js** module
  6. Mock up the `create` (sign-up) controller action

## 1. Review of `fetch`

Back in Unit 2, we installed and used `node-fetch` to make HTTP requests from the Express server to the GitHub API.

Our browsers have [`fetch`](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch) built-in!

We're going to work with `fetch` in the Console of Chrome's DevTools.

First, browse to the [JSONPlaceholder fake REST API](https://jsonplaceholder.typicode.com/).

> Note:  The JSONPlaceholder API will reject requests coming from other sites (it checks the headers in the request).

In the Console:

```
> let resPromise = fetch('https://jsonplaceholder.typicode.com/users');
< undefined
> resPromise
< Promise {<fulfilled>: Response}
```

As seen above, invoking the `fetch` function returns a [JS Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) that quickly resolves to a response object with properties pertaining to the results of the request. For example:

```
> resPromise.then(response => console.log(response.ok))
  true
< Promise {<fulfilled>: undefined}
```

The response's `ok` property returning `true` means that the request was successful, i.e., it has a [status code](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status) in the 200s.

That `Promise {<fulfilled>: undefined}` is displayed due to the fact that a promise's `then()` method **always** returns another promise.

### So Where's the Data?

The response object has a few methods for accessing the data sitting in the body of the HTTP response.

The [JSONPlaceholder API](https://jsonplaceholder.typicode.com/), like most APIs, responds with JSON data (`content-type: application/json` header).

If the response object has JSON data in its body, the `json()` method is used to retrieve the data:

```
> resPromise.then(res => res.json()).then(data => console.log(data));
< Promise {<pending>}
  (10) [{…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}]
```

As you can see, the `json()` method also returns a promise which resolves to the actual data.

We can use `fetch` to make HTTP requests using any HTTP method, include headers and include a data payload which we'll do in a bit when we make a `POST` request to send the sign-up data to the server.

## 2. Review of Handling Promises with `async`/`await`

Again, back when we consumed the GitHub API in Unit 2, we refactored the code from calling `then()` on promises to use [`async`/`await`](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Async_await).

Here was the `then()` based code we used in the GitHub API lesson:

```js
router.get('/', function(req, res, next) {
  const username = req.query.username;
  if (!username) return res.render('index', {userData: null});
  const options = {
    headers: {
      Authorization: `token ${token}`
    }
  };
  let userData;
  // This is a search for a user
  fetch(`${rootURL}users/${username}`, options)
    .then(res => res.json())
    .then(user => {
      userData = user;
      return fetch(userData.repos_url, options);
    })
    .then(res => res.json())
    .then(repos => {
      userData.repos = repos;
      res.render('index', { userData });
    });
});
```

and here was the refactored code using `async`/`await`:

```js
router.get('/', async function (req, res, next) {
  const username = req.query.username;
  if (!username) return res.render('index', { userData: null });
  const options = {
    headers: {
      Authorization: `token ${token}`
    }
  };
  // This is a search for a user
  const userData = await fetch(`${rootURL}users/${username}`, options).then(res => res.json());
  const repos = await fetch(userData.repos_url, options).then(res => res.json());
  userData.repos = repos;
  res.render('index', { userData });
});
```

Quite an improvement in terms of conciseness and readability.  Look how the `await` keyword "pauses" the code until the promise is resolved and causes the promise to return its resolved value allowing us to assign the value to variables as shown with `userData` and `repos` above.

However, in order to use the magical `await` keyword, we must preface its containing function with the `async` keyword - do you see it?

We'll certainly be using `async`/`await` to consume promises as we continue to code `mern-infrastructure`!

## 3. Make the AJAX Request to Sign-Up

Okay, so the state in `<SignUpForm>` is ready to be sent to the server!

As we've discussed, SPAs must communicate via AJAX and we're going to utilize the **users-service.js** and **users-api.js** modules to pull this off.

### Use a `try`/`catch` Block to Catch Errors When Using `async`/`await`

Let's start back in the `handleSubmit` method in **SignUpForm.jsx** by setting up a `try`/`catch` block required to handle errors when using `async`/`await`:

```jsx
handleSubmit = async (evt) => {
  // Prevent form from being submitted to the server
  evt.preventDefault();
  try {
    
  } catch {
    // An error occurred 
    this.setState({ error: 'Sign Up Failed - Try Again' });
  }
};
```

Look how cleanly we are handling a failed sign-up by simply setting the `error` state property!

### Ready the Sign Up Data Payload

<details><summary>❓ There are two extra properties on the <code>state</code> object we don't want to send to the server - what are they?</summary>
<p>

**The `state.error` and `state.confirm` properties.**

</p>
</details>

We never want to directly mutate the `state` object, so let's make a copy of it and delete those properties from it:

```jsx
handleSubmit = async (evt) => {
  // Prevent form from being submitted to the server
  evt.preventDefault();
try {
  // We don't want to send the 'error' or 'confirm' property,
  //  so let's make a copy of the state object, then delete them
  const formData = {...this.state};
  delete formData.error;
  delete formData.confirm;

} catch {
...
```

<details><summary>❓ Can you think of another way to create the <code>formData</code> object that excludes the <code>confirm</code> and <code>error</code> properties?</summary>
<p>

```js
const formData = {
  name: this.state.name,
  emai: this.state.email,
  password: this.state.password
};
// or
const {name, email, password} = this.state;
const formData = {name, email, password};
```

</p>
</details>

`formData` is now ready to send to the server. We'll follow the best practice of putting sign up related app logic in the **users-service.js** service module and network logic in the **users-api.js** API module we created last lesson.

### Follow the "Coding Flow"

Even though we don't yet have the following `signUp` service method being invoked, let's continue coding by following the flow from the component to the service method, then to the API/AJAX method...

```
SignUpForm.jsx <--> users-service.js <--> users-api.js <-Internet-> server.js (Express)
```

```jsx
// SignUpForm.jsx

...
try {
  ...
  delete formData.error;
  // The promise returned by the signUp service method 
  // will resolve to the user object included in the
  // payload of the JSON Web Token (JWT)
  const user = await signUp(formData);
  // Baby step!
  console.log(user)
} catch {
...
```

We need to import the non-existent `signUp` method:

```jsx
// SignUpForm.jsx

import { Component } from 'react';
// Add this import
import { signUp } from '../../utilities/users-service';
```

Now let's follow the flow and go code and export the `signUp` method in **users-service.js**:

```js
// users-service.js

export async function signUp(userData) {
  // Delegate the network request code to the users-api.js API module
  // which will ultimately return a JSON Web Token (JWT)
  const token = await usersAPI.signUp(userData);
  // Baby step by returning whatever is sent back by the server
  return token;
}
```

> Note: We have not used a try/catch block because any error will propagate up to the "consumer" of the service - in this case the consumer is the `handleSubmit` method in the `<SignUpForm>` component.

Let's import the **users-api.js** using a different approach so that you can learn more about ES2015 JS modules...

```jsx
// users-service.js

// Import all named exports attached to a usersAPI object
// This syntax can be helpful documenting where the methods come from 
import * as usersAPI from './users-api';
```

Okay, let's follow the flow and go code and export the `signUp` method in **users-api.js**:

```jsx
// users-api.js

// This is the base path of the Express route we'll define
const BASE_URL = '/api/users';

export async function signUp(userData) {
  // Fetch uses an options object as a second arg to make requests
  // other than basic GET requests, include data, headers, etc. 
  const res = await fetch(BASE_URL, {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    // Fetch requires data payloads to be stringified
    // and assigned to a body property on the options object
    body: JSON.stringify(userData)
  });
  // Check if request was successful
  if (res.ok) {
    // res.json() will resolve to the JWT
    return res.json();
  } else {
    throw new Error('Invalid Sign Up');
  }
}
```

> IMPORTANT:  The fetch method will not raise an error unless there's a network failure. This is why we need to check the `res.ok` property to see if the server returned a successful response (status code in the 200s).

Yes, that was a lot to follow.  Don't worry, you'll get used to coding the flow from component to service module to API module - hang in there!

Open the Network tab of Chrome's DevTools, then attempt to sign up.  Inspect the request!

<img src="https://i.imgur.com/NSTHblW.png">

<details><summary>❓ What does that <code>404</code> mean?</summary>
<p>

**There's no route defined on the server that matches the HTTP request.**

</p>
</details>

To the Express server code we go...

## 4. Define the Server-Side Route for Signing-Up

Now that the AJAX request is being made from the browser, we need a route defined on the server that matches that request!

### Create the Router Module

Just like in Unit 2, we'll use an Express router module to define routes for each data resource. However, we want to help other developers know that the router is designed to respond to AJAX requests with JSON instead of rendering a template or redirecting.

To do so, we'll namespace these routes by prefacing them with `/api`.  Additionally, we will create the route module within a `routes/api` folder:

```
mkdir routes/api
```

Now let's create the router module dedicated to our **users** data resource:

```
touch routes/api/users.js
```

> Note: This namespacing business may seem overkill until you realize that its possible to include a traditional web app that includes traditional routes/controllers/views right alongside the SPA/API code! For example, you might want to code a quick admin view that returns the status of the SPA - those routes & controllers would not be namespaced with `/api` and the controller actions would respond by rendering EJS templates that return HTML instead of JSON.

### Define the Route

Hopefully, this code looks somewhat familiar:

```js
// routes/api/users.js

const express = require('express');
const router = express.Router();
const usersCtrl = require('../../controllers/api/users');

// POST /api/users
router.post('/', usersCtrl.create);

module.exports = router;
```

### Mount the Router

With the router being exported, we now can mount it in **server.js**:

```js
// Put API routes here, before the "catch all" route
app.use('/api/users', require('./routes/api/users'));
```

> Note how we've eliminated a line of code by requiring the router module inline.

Mapping the route to the non-existent controller action/function expectedly makes the Express server unhappy...

## 5. Define the **controllers/api/users.js** Module

Just like the route module, we'll namespace our controller modules as well...

#### 💪 Practice Exercise - Stub Up the Controller Module and Action (3 minutes)

1. Make a **controllers/api** folder.
2. Create the **controllers/api/users.js** module.
3. Stub up and export the `create` controller action.

    > Hint: Remember how we used `module.exports` to export an object in Node modules?

## 6. Mock up the `create` (Sign-Up) Controller Action

Ultimately we will need to return a JSON Web Token (JWT) from the controller action after the user is added to the database.

We'll code the `User` model and see how we create the JWT in the next lesson. For now, let's baby step and return some JSON that we can verify back in the React app:

```js
module.exports = {
  create
};

function create(req, res) {
  // Baby step...
  res.json({
    user: {
      name: req.body.name,
      email: req.body.email
    }
  });
}
```

That should complete the flow from component to server and back!

Open the Console tab of Chrome's DevTools, then attempt to sign up.

Rejoice!

<img src="https://i.imgur.com/9qsfE1d.png">

As a reminder, what we returned from the server is being logged by this line of code in the `<SignUpForm>` component:

```jsx
...
const user = await signUp(formData);
// Baby step!
console.log(user)
...
```

#### Congrats! On to the lab!



<img src="https://i.imgur.com/IKHxRMa.png">

# MERN-Stack Infrastructure - Part 5

## Learning Objectives

|Students Will Be Able To:|
|---|
| Describe the Benefits of Token-Based Authentication |
| Create a JSON Web Token that Includes the User's Data |

## Road Map

- The Plan - Part 5
- Infrastructure - Part 5 of 7

## The Plan - Part 5

In Part 5 we will continue to implement user authentication.

**Part 5 - Implementing Token-Based Auth (continued):**
  1. Discuss token-based authentication
  2. Add the `User` model
  3. Implement the `create` (sign-up) controller action

## 1. Discuss Token-Based Authentication

### What is Token-Based Authentication?

Token-based authentication uses a string of characters, a token, to identify who a request sent to the server is coming from.

There are different types of token-based authentication, in fact, Unit 2's OAuth used tokens obtained by the OAuth provider.

A [JSON Web Token (JWT)](https://jwt.io/introduction/) is the most popular type of token used in SPAs because of the advantages it provides...

### Advantages of Token and JWT-Based Authentication

Since a token itself is used to identify the user to the web server, the web server does not need to maintain sessions which require server resources and thus not as scalable as token-based auth.

The stateless nature of token-based auth allows the implementation of single sign-on (SSO) - where the same token can be used to access several different applications, for example, Google Mail, Google Docs, etc.  

Also, since sessions require the use of cookies, session-based auth cannot be used outside of browser apps. Because token-based auth does not require sessions, it can be used in applications running outside of browsers such as desktop and native mobile apps (cookies are a browser feature).

A [JSON Web Token (JWT)](https://jwt.io/introduction/) can contain a data payload including any data we wish. Typically we include data about the user in the payload so there's no need to query the database (an expensive operation) for the user every time a request hits the server.  This is way more efficient than with session-based auth.

We will only have to query the database for the user document/record if we need to modify the user or obtain additional information from the user that is not included in the JWT!

### What's a JSON Web Token (JWT)?

A JSON Web Token is a single encoded (not encrypted) string. Encryption makes the data completely unreadable until it's decrypted using keys, whereas, encoding simply converts one data format to another.

Some facts about JWTs:

- The token can contain whatever custom data (called _claims_) we want to put in it.
- The token is cryptographically _signed_ by the server when it is created so that if the token is changed in any way, it is considered invalid.
- The token is encoded, but **not encrypted**.  It is encoded (converted) using a standard known as [base64url](https://en.wikipedia.org/wiki/Base64) encoding so that it can be serialized across the internet or even be included in a URL's _querystring_. It may seem that encoded data is "secret" - it's not as you'll soon see!

Here's how a JWT is structured:

<img src="https://i.imgur.com/IXByEPP.png">

There is a great website dedicated to JWTs that explains them in detail and provides a playground to create them:  [https://jwt.io/](https://jwt.io/)

Let's take a JWT from the website and demonstrate that the token can be easily decoded in the browser's console:

```js
> const jwt = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiYWRtaW4iOnRydWV9.TJVA95OrM7E2cBab30RMHrHDcEfxjoYZgeFONFh7HgQ';
> const payload = jwt.split('.')[1]  // only interested in the payload (claims)
> atob(payload)
< "{"sub":"1234567890","name":"John Doe","admin":true}"
```
> The `atob()` method decodes a base-64 encoded string and `btoa()` base-64 encodes data.

Because the data in a JWT can be easily read, it's important not to include sensitive/secret data such as Social Security Numbers, etc.

Okay, JWT-based auth is cool, let's see how we use them in a SPA...

### Typical Token-Based Flow in a SPA

The following depicts the typical flow of JWT-based auth in a SPA:

<img src="https://i.imgur.com/3quZxs4.png">

Additional clarification on the above steps:

- STEP 1: Applies to logging in and signing up.
- STEP 2: The JWT is created only after the login credentials have been validated, or the visitor signing up has been saved to the database.
- STEP 3: After the JWT has been received by the client, it needs to be persisted, usually in local storage, so that it can be sent in future requests as needed (STEP 4).
- STEP 4: We will be including the JWT with any request that needs to be authenticated on the server.
- STEP 5: We will write a tidy middleware function used to validate the token and add the user data to Express's `req` object - cool beans for sure!

## Add the `User` Model

We need a `User` model so that we can save the user to the DB when they sign up and retrieve the user from the DB to validate their credentials when they log in.

### Create the **models/user.js**

Remember, the naming convention for model modules is singular:

```
touch models/user.js 
```

Now let's add the typical boilerplate for the schema, then compile and export the model:

```js
const mongoose = require('mongoose');
const Schema = mongoose.Schema;

const userSchema = new Schema({

});

module.exports = mongoose.model('User', userSchema);
```

### Add the Properties for the `User` Model

We'll just add the minimum required for authentication:

```js
const userSchema = new Schema({
  name: {type: String, required: true},
  email: {
    type: String,
    unique: true,
    trim: true,
    lowercase: true,
    required: true
  },
  password: {
    type: String,
    trim: true,
    minLength: 3,
    required: true
  }
});
```

There's some nice validations and transformations in there, for example:

- `unique`: Although technically not a validator, `unique: true` creates a unique index in the database which will trigger an error if violated.
- `trim`: This transform causes Mongoose to trim spaces before and after the string before saving.
- `lowercase`: This transform causes Mongoose to convert the string to lowercase before saving.

### Be Cautious When Adding Additional Properties to the `User` Model

Feel free to add additional properties/attributes about the user in your projects.  However, **do not add properties used to embed related data or reference 1:M/M:M relationships!**. These properties should be added to the related models instead!

> IMPORTANT:  Keeping the User model lean is always a good practice. However, it's especially important with JWT-based authentication because the user document will be the data payload included in the JWT and you don't want the JWT to be bigger than it has to be!

### Add the Options for the `User` Model

Without looking at the code below...

<details><summary>❓ What's the option property we like to add to every schema?</summary>
<p>

**The `timestamps: true` property.**

</p>
</details>

Let's add it:

```js
...
  password: {
    type: String,
    trim: true,
    minLength: 3,
    required: true
  }
}, {
  timestamps: true
});
```

In addition to `timestamps`, let's add the `toJSON` option that is used to transform the document when it's serialized to JSON (converted to a string):

```js
...
}, {
  timestamps: true,
  // Even though it's hashed - don't serialize the password
  toJSON: {
    transform: function(doc, ret) {
      delete ret.password;
      return ret;
    }
  }
});
```

### Automatically Hashing the Password

We never want to store passwords as plain text, known as "clear text".

Instead, we need to hash the password anytime it has changed and store the hash instead.

Hashing is a one-way process which makes it **impossible** to revert back to the clear text password.

<details><summary>❓ If the hash cannot be un-hashed back to the original password, how will we be able to verify the user's clear text password when logging in?</summary>
<p>

**By hashing the password and comparing the two hashes** 😊

</p>
</details>

We _could_ write the code to hash the password in the controller function(s), but the better practice is to make the model itself responsible so that we never have to worry about it anytime a user's password is changed.

Let's add a Mongoose **pre-save hook** ([Mongoose middleware](https://mongoosejs.com/docs/middleware.html)) that will hash the password anytime the password has changed:

```js
// models/user.sj

...

userSchema.pre('save', async function(next) {
  // 'this' is the user doc
  if (!this.isModified('password')) return next();
  // update the password with the computed hash
  this.password = await bcrypt.hash(this.password, SALT_ROUNDS);
  return next();
});

module.exports = mongoose.model('User', userSchema);
```

The `SALT_ROUNDS` variable determines how much processing time it will take to perform the hash. Let's define it near the top of the module:

```js
// models/user.js
const mongoose = require('mongoose');
const Schema = mongoose.Schema;

const SALT_ROUNDS = 6;  // 6 is a reasonable value
```

Next, we need to install and require the [`bcrypt` library](https://www.npmjs.com/package/bcrypt) used to hash data.

> Note: The bcrypt library is available for virtually every programming language.

Be careful of the spelling...

```
npm i bcrypt
```

Add it to the top of the module:

```js
// models/user.js
const mongoose = require('mongoose');
const Schema = mongoose.Schema;
// Add the bcrypt library
const bcrypt = require('bcrypt');
```

Yay - we're done coding the `User` model!

Let's add it to **crud-helper.js** and test it out...

### Test Drive the User Model

First, let's uncomment the following two lines in **crud-helper.js**:

```js
const User = require('./models/user');
// const Item = require('./models/item');
// const Category = require('./models/category');
// const Order = require('./models/order');

// Local variables will come in handy
let user, item, category, order;
let users, items, categories, orders;
```

Feel free sit back and observe...

```
mern-infrastructure[master*] % node
Welcome to Node.js v15.2.0.
Type ".help" for more information.
> .load crud-helper.js
// Connect to the database
require('dotenv').config();
require('./config/database');
 
// Require the Mongoose models
const User = require('./models/user');
// const Item = require('./models/item');
// const Category = require('./models/category');
// const Order = require('./models/order');
 
// Local variables will come in handy
let user, item, category, order;
let users, items, categories, orders;
 
 
{}
> Connected to mern-infrastructure at localhost:27017

> User.create({
... name: 'Laura',
... email: 'laura@email.com',
... password: 'abcd'
... }).then(u => user = u)
Promise { <pending> }
> user
{
  _id: 6003389c334a04950d6dc0de,
  name: 'Laura',
  email: 'laura@email.com',
  password: '$2b$06$bU291F/dj37tJBgvdd3Hgu/a.CMKFHn/dOaP6IxDe.d3orRhOGrM2',
  createdAt: 2021-01-16T19:03:56.642Z,
  updatedAt: 2021-01-16T19:03:56.642Z,
  __v: 0
}
> JSON.stringify(user)
'{"_id":"6003389c334a04950d6dc0de","name":"Laura","email":"laura@email.com","createdAt":"2021-01-16T19:03:56.642Z","updatedAt":"2021-01-16T19:03:56.642Z","__v":0}'
> user.password = 'abcd1234'
'abcd1234'
> user.save()
Promise { <pending> }
> user
{
  _id: 6003389c334a04950d6dc0de,
  name: 'Laura',
  email: 'laura@email.com',
  password: '$2b$06$kA5M6FY2JvpuQUjjT6gRze5SztUUvuvl6i2P921YXlzioWohHKQVG',
  createdAt: 2021-01-16T19:03:56.642Z,
  updatedAt: 2021-01-16T19:05:37.618Z,
  __v: 0
}
> .exit
```

Now you can see why it's better to make the model responsible for the hashing instead of some controller somewhere!

Questions?

## 3. Implement the `create` (Sign-Up) Controller Action

Previously we baby stepped the `create` action in the users controller to simply send back a mocked user object when a user signed up.

Now it's time to get real and:

1. Add the user to the database.
2. Create the JWT.  We'll include a `user` property in the JWT's payload containing the user's document data.
3. Send the JWT to the client using `res.json()`

### Add the User to the Database

We need to require the `User` model before we can create users.

#### 💪 Practice Exercise (1 minute)

- Require the `User` model in **controllers/api/users.js**.

<hr>

<details><summary>❓ In the <code>create</code> controller action, how do we access the data sent by the client in the request? </summary>
<p>

**`req.body`**

</p>
</details>

As promised, we'll be using `async`/`await` with promises, so let's set up error handling in the following refactor:

```js
// controllers/api/users.js

function create(req, res) {
  try {
    // Add the user to the database
    const user = await User.create(req.body);
    
  } catch (err) {
    // Client will check for non-2xx status code 
    // 400 = Bad Request
    res.status(400).json(err);
  }
}
```

<details><summary>❓ The above code causes a syntax error in the Express server because we forgot to add something - what?</summary>
<p>

**Add `async` in front of `function` to make it an async function.**

</p>
</details>

Make that fix.

Now we're ready to create the JWT!

### Create the JWT

We're going to need to install another Node module for creating and verifying JWTs.

[https://jwt.io](https://jwt.io) lists libraries available for your programming language of choice.

The Node module we need to install and require is named `jsonwebtoken`.

#### 💪 Practice Exercise (1 minute)

1. Install the `jsonwebtoken` Node module.
2. Require the new module in the users controller but shorten the name of the variable to `jwt`.

<hr>

Creating a JWT requires a "secret" string used for "signing" the JWT. 

Let's define one in our **.env** file:

```
DATABASE_URL=mongodb://localhost/mern-infrastructure
SECRET=SEIRocks!
```

The `sign` method in the **jsonwebtoken** library is used to create JWTs.

Let's add a `createJWT` helper function at the bottom of **controllers/api/users.js** that we can use both when a user signs up and when they log in:

```js
/*-- Helper Functions --*/

function createJWT(user) {
  return jwt.sign(
    // data payload
    { user },
    process.env.SECRET,
    { expiresIn: '24h' }
  );
}
```

> Note: There are several ways to specify the expiration of the JWT. Check [the docs](https://www.npmjs.com/package/jsonwebtoken) for more info.

Cool. Now let's use the `createJWT` function in the `create` action and send back the newly created JWT:

```js
async function create(req, res) {
  try {
    // Add the user to the database
    const user = await User.create(req.body);
    // token will be a string
    const token = createJWT(user);
    // Yes, we can use res.json to send back just a string
    // The client code needs to take this into consideration
    res.json(token);
  } catch (err) {
    // Client will check for non-2xx status code 
    // 400 = Bad Request
    res.status(400).json(err);
  }
}
```

Now for the moment of truth - sign up and verify that the token string is logged to the Console:

<img src="https://i.imgur.com/MJdTTmV.png">

Remember the demo earlier when we decoded the payload of the JWT?  Check it out!

<img src="https://i.imgur.com/uaiERcy.png">

#### Congrats! On to the lab!



<img src="https://i.imgur.com/IKHxRMa.png">

# MERN-Stack Infrastructure - Part 6

## Learning Objectives

|Students Will Be Able To:|
|---|
| Use localStorage to Persist Data |
| Better Understand How to Implement Features in the MERN-Stack |

## Road Map

- The Plan - Part 6
- Infrastructure - Part 6 of 7

## The Plan - Part 6

In Part 6 we will continue to implement user authentication.

**Part 6 - Implementing Token-Based Auth (continued):**
  1. Save the token in the browser's local storage
  2. Update the `user` state
  3. Implement logging out
  4. Implement logging in

## 1. Save the Token in the Browser's Local Storage

In the previous lesson we created the JWT on the server when the visitor signed up.  We also verified that the token was being sent back to the browser by logging it out in the console.

Because we will need to send the JWT to the server with any AJAX request that requires the controller action to know who the user is, we need to save the token in the client.

We can't simply assign the token to a variable or put it on state because a page refresh would loose the token.

Instead, we'll utilize the browser's [localStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage) to persist the JWT. This also enables the user to be logged in automatically when they browse to the app! That is, as long as the JWT hasn't expired.

<details><summary>❓ Where in the code does it make the most sense to persist the token to local storage?</summary>
<p>

**The `signUp` method in the `users-service.js` module (when the token has been received from the server).**

</p>
</details>

Here's the refactor:

```js
export async function signUp(userData) {
...
    const token = await usersAPI.signUp(userData);
    // Persist the "token"
    localStorage.setItem('token', token);
...
```

> Note: Local Storage only stores and retrieves strings. When saving, the data will automatically be converted to a string, however, you will be responsible for using `JSON.parse()` to convert the string retrieved from local storage back into a number, boolean, array, object, etc.

Let's verify it's working by signing up again and checking out the Local Storage in DevTool's Application tab:

<img src="https://i.imgur.com/qcwKdLO.png">

<details><summary>❓ What did we save in the JWT's payload when we created it?</summary>
<p>

**The token's payload has a `user` property that contains the data from the user's MongoDB document!**

</p>
</details>

Time to put that payload to use...

## 2. Update the `user` State

We need to set/update the `user` state defined in the `<App>` component whenever:

- The React app is loaded or refreshed.
- A visitor signs up.
- A user logs in.
- The user logs out.

Let's start with when the app is loaded/refreshed...

### Setting the `user` State When the Page is Loaded or Refreshed

<details><summary>❓ In plain language, what logic should we implement to set the <code>user</code> state when the page loads/refreshes? Try to consider the three cases of token persistence in localStorage: Valid token exists; Expired token exists; and no token exists.</summary>
<p>

<ol><strong>
  <li>Retrieve the token from localStorage.</li>
  <li>If there isn't a token, set <code>user</code> to <code>null</code>.</li>
  <li>If there's an expired token, remove it from localStorage and set <code>user</code> to <code>null</code>.</li>
  <li>If the token hasn't expired, extract the <code>user</code> object from the payload use set the <code>user</code> state to that object.</li>
</strong></ol>

</p>
</details>

It makes sense to code much of the above logic in new `getToken()` and `getUser()` functions in **users-service.js**:

```js
// users-service.js

export function getToken() {
  // getItem returns null if there's no string
  const token = localStorage.getItem('token');
  if (!token) return null;
  // Obtain the payload of the token
  const payload = JSON.parse(atob(token.split('.')[1]));
  // A JWT's exp is expressed in seconds, not milliseconds, so convert
  if (payload.exp < Date.now() / 1000) {
    // Token has expired - remove it from localStorage
    localStorage.removeItem('token');
    return null;
  }
  return token;
}

export function getUser() {
  const token = getToken();
  // If there's a token, return the user in the payload, otherwise return null
  return token ? JSON.parse(atob(token.split('.')[1])).user : null;
}
```

With those nifty functions in place, we can use `getUser()` in `<App>` to set the `user` state.

First, import `getUser`:

```jsx
// App.jsx
import { Routes, Route } from 'react-router-dom';
// Add the following import
import { getUser } from '../../utilities/users-service';
```

Now let's put it to use with this tiny refactor:

```jsx
export default function App() {
  const [user, setUser] = useState(getUser());
```

We could use the React Developer Tools to verify it worked, but why not just add a bit of code to render the user's name in the `<NavBar>` instead?

#### 💪 Practice Exercise - Render the User's Name in `<NavBar>` (5 minutes)

1. Before `<NavBar>` can render the user's name, email, or whatever, you need to pass the `user` state as a prop (name the prop `user`).
2. Render the user's name any way you wish in `<NavBar>`.
  
> Hint:  `<NavBar>` is currently not coded to accept any props

<img src="https://i.imgur.com/vBD8dT4.png">

### Setting the `user` State When a Visitor Signs Up

Now we can finish the sign up functionality by updating the `user` state after the visitor successfully signs up.

Currently, the `signUp()` function in **users-server.js** is returning the token. However, if we take a look at the following code in **SignUpForm.jsx**...

```jsx
// The promise returned by the signUp service method 
// will resolve to the user object included in the
// payload of the JSON Web Token (JWT)
const user = await signUp(formData);
// Baby step!
console.log(user)
```

...we can see that we expect the `signUp()` function to return the user object instead.

Nothing that a quick refactor in **users-service.js** can't handle:

```js
export async function signUp(userData) {
  try {
...
    localStorage.setItem('token', token);
    // Update the following line of code
    return getUser();
...
```

Told you that would be a quick refactor 😊

We need a way to update `user` state defined in `<App>` from `<SignUpForm>`.  This requires that a function be passed from `<App>` to `<SignUpForm>` via a prop.

Ordinarily, if there's business/application logic that needs to be performed other than simply updating state, we would need to write a separate function and pass it via a prop. However, in this case, we simply need to update `user` with the `setUser()` setter function... 

#### 💪 Practice Exercise - Update `user` State From `<SignUpForm>` (5 minutes)

1. Pass `setUser` from `<App>` **down the component hierarchy** to `<SignUpForm>`.
2. In `<SignUpForm>`, replace the `console.log(user)` with a call to the `setUser` function, passing to it `user`.

> Hints:  Ordinarily we would need to destructure props passed to function components. However, class components like `<SignUpForm>` access their props as `this.props.<name of the prop>` so there's no destructuring or anything else necessary.

<hr>

Let's use DevTools to manually clear the token from Local Storage, then sign up as a new user to test out the code!

<img src="https://i.imgur.com/Qj4h58Q.png">

Nice - congrats on implementing sign up functionality!

## 3. Implement Logging Out

**AAU, I want to be able to log out of SEI CAFE just in case someone with the munchies gets a hold of my computer.**

<details><summary>❓ What did we just do to effectively "log out" the currently logged in user?</summary>
<p>

**Removed the token from local storage and set the `user` state to `null`.**

</p>
</details>

You know the flow - start with the UI that the user is going to interact with.

### Add Log Out UI

<details><summary>❓ Which component is the logical place to add a button or link used to log out?</summary>
<p>

**`<NavBar>`**

</p>
</details>

You already know how to use a `<button>` with a click handler, but we can also use React Router's `<Link>` if we prefer the "look" of a hyperlink vs. a button.

However, we don't want to use this particular `<Link>` to navigate, so we'll leave its `to` prop empty:

```jsx
// NavBar.jsx

...
<nav>
  ...
  &nbsp;&nbsp;<span>Welcome, {user.name}</span>
  &nbsp;&nbsp;<Link to="">Log Out</Link>
</nav>
```

Clicking the rendered link will not navigate.

### Add the `onClick` Event Prop & Handler

Now let's add an `onClick` prop and assign an event handler:

```jsx
<Link to="" onClick={handleLogOut}>Log Out</Link>
```

Yup, we need to code that `handleLogOut` handler:

```jsx
// NavBar.jsx

export default function NavBar({ user }) {
  // Add the following function
  function handleLogOut() {
    // Delegate to the users-service
    userService.logOut();
    // Update state will also cause a re-render
    setUser(null);
  }
  ...
```

### Finish Implementing Log Out Functionality

<details><summary>❓ We're not done yet, based upon the code in the handler, what else do we need to do?</summary>
<p>

<strong><ol>
  <li>Code and export the <code>logOut</code> function in <strong>users-service.js</strong>.</li>
  <li>Import <code>logOut</code> according to how we wrote the line of code that uses it.</li>
  <li>Pass the <code>setUser</code> setter function as a prop to <code>&LT;NavBar></code>.</li>
  <li>Destructure that prop.</li>
</ol></strong>

</p>
</details>

### Code the `logOut` Function

All the `logOut` function needs to do is remove the token:

```js
// users-service.js

export function logOut() {
  localStorage.removeItem('token');
}
```

### Import `logOut` in `<NavBar>`

We're going to import using the syntax that matches the way we invoked the function:

```jsx
// NavBar.jsx

import { Link } from 'react-router-dom';
// Using the import below, we can call any exported function using: userService.someMethod()
import * as userService from '../../utilities/users-service';
```

> Note: Using the above syntax to import provides some additional context when using the imported item.

### Pass the `setUser` Setter From `<App>` to `<NavBar>`

**💪 You got this!**

### Destructure the `setUser` Prop in `<NavBar>`

**💪 Slam dunk!**

Log out and celebrate:

<img src="https://i.imgur.com/Itiu1OE.png">

## 4. Implement Logging In

Logging in is very much like signing up!

First things first though, let's get the tedious stuff out of the way...

### Create the `<LoginForm>` Component

Productive developers always look to copy/paste work they've already written if it makes sense to do so.

<details><summary>❓ Is there a component that makes sense to copy/paste as the starting point for <code>&LT;LoginForm></code>?</summary>
<p>

**The `<SignUpForm>` is a good candidate, but we would probably want to refactor it into a function component.**

</p>
</details>

There's some good news and some bad news - which do you want first?

<details><summary>The Good News</summary>
<p>

**The `<LoginForm>` is below and ready to use!**

```jsx
// LoginForm.jsx

import { useState } from 'react';
import * as usersService from '../../utilities/users-service';

export default function LoginForm({ setUser }) {
  const [credentials, setCredentials] = useState({
    email: '',
    password: ''
  });
  const [error, setError] = useState('');

  function handleChange(evt) {
    setCredentials({ ...credentials, [evt.target.name]: evt.target.value });
    setError('');
  }

  async function handleSubmit(evt) {
    // Prevent form from being submitted to the server
    evt.preventDefault();
    try {
      // The promise returned by the signUp service method 
      // will resolve to the user object included in the
      // payload of the JSON Web Token (JWT)
      const user = await usersService.login(credentials);
      setUser(user);
    } catch {
      setError('Log In Failed - Try Again');
    }
  }

  return (
    <div>
      <div className="form-container">
        <form autoComplete="off" onSubmit={handleSubmit}>
          <label>Email</label>
          <input type="text" name="email" value={credentials.email} onChange={handleChange} required />
          <label>Password</label>
          <input type="password" name="password" value={credentials.password} onChange={handleChange} required />
          <button type="submit">LOG IN</button>
        </form>
      </div>
      <p className="error-message">&nbsp;{error}</p>
    </div>
  );
}
```

</p>
</details>

<details><summary>The Bad News</summary>
<p>

<strong>Just kidding - this is great news!

You've had considerable practice working with state, input, props, etc., so you're going to implement the rest of the login functionality as a group practice exercise!</strong>

</p>
</details>

<hr>

#### 💪 Practice Exercise - Implement Login Functionality (30 - 45 minutes)

Be sure to read all of the following before starting to code...

1. Add the `<LoginForm>` component above to the project following the naming convention for the folder and module.

2. Render the `<LoginForm>` below the `<SignUpForm>` in `<AuthPage>`. It will be an icebox item to display only one of the forms at a time.

3. Start implementing login functionality by reading the code in the `handleSubmit` function in **LoginForm.jsx** - that call to `usersService.login(credentials)` starts your journey.

    > IMPORTANT:  The existing code in **LoginForm.jsx** is complete - don't change anything.

4. Again, follow the flow from the UI to the server and back.

5. Use the code and logic we used to implement Sign Up functionality as a guide. The `login` functions that need to be added to the **users-service.js** and **users-api.js** modules are similar to the existing `signUp` functions.

6. FYI, the solution code uses the server-side route of `POST /api/users/login` mapped to a controller action named `login`.

7. The `login` controller action is the most challenging. Although in structure it's similar to `create`, it has slightly different functionality - instead of creating the user we need to query for the user based upon their `email` and then verify the password is correct using [bcrypt's `compare` method](https://www.npmjs.com/package/bcrypt#with-promises).

    > Hint 1: The `User` model's `findOne` is the appropriate query method to use to find a user based on their email.

    > Hint 2: Remember to require the bcrypt library.
    
    > Hint 3: When invoking bcrypt's `compare` method, use the syntax that returns a promise and consume it with `await`.

      <details><summary>Peek if you must...</summary>
      <p>

      ```js
      const match = await bcrypt.compare(req.body.password, user.password);
      ```

      </p>
      </details>

    > Hint 4: Be sure to structure the code so that it responds with a status code of 400 if either the user is not found in the database (bad email) or if the user is found but the password doesn't match.

    <details><summary>Feel free to use the following code if you get stuck or run out of time</summary>
    <p>

    ```js
    // controllers/api/users.js

    // Be Sure to add the following
    const bcrypt = require('bcrypt');

    module.exports = {
      create,
      login
    };

    async function login(req, res) {
      try {
        const user = await User.findOne({ email: req.body.email });
        if (!user) throw new Error();
        const match = await bcrypt.compare(req.body.password, user.password);
        if (!match) throw new Error();
        res.json( createJWT(user) );
      } catch {
        res.status(400).json('Bad Credentials');
      }
    }
    ```

    </p>
    </details>

8. See how far you can get and feel free to reach out for assistance if you get stuck - enjoy!

**Icebox**

1. Instead of showing both the `<SignUpForm>` and `<LoginForm>` simultaneously, implement showing one or the other in `<AuthPage>` - just like the [deployed SEI CAFE](https://sei-cafe.herokuapp.com/) does.

    > Hint: This is an obvious use case for a piece of ui-related state.

#### Congrats, mern-infrastructure has only one more part remaining!





<img src="https://i.imgur.com/IKHxRMa.png">

# MERN-Stack Infrastructure - Part 7

## Learning Objectives

|Students Will Be Able To:|
|---|
| Send the JWT to the Server in AJAX Requests |
| Validate the JWT and Add the Payload to `req.user` |
| Protect Server-Side Routes that Require A Logged In User |
| Save MERN-Stack Infrastructure To a New GitHub Repo |
| Create a new MERN-Stack Project from the `mern-infrastructure` Repo |

## Road Map

- The Plan - Part 7
- Infrastructure - Part 7 of 7 (Yay!)

## The Plan - Part 7

In Part 7 we will will wrap up the basic infrastructure for a MERN-Stack app.

**Part 7 - Implementing Token-Based Auth (continued):**
  1. Send the token with AJAX requests
  2. Check the token on the server and add a `user` property to `req`
  3. Implement middleware to protect server-side routes
  4. Save MERN-Stack infrastructure to a new GH repo
  5. Using `mern-infrastructure` to Create MERN-Stack Projects in the Future

## 1. Send the Token with AJAX Requests

In order to perform user-centric CRUD, the server of course, needs to know who the user is when they make a request.

During the discussion on token-based authentication, we learned that a token, or in our case more specifically a JWT, is used to identify the user.

So how do we include the JWT when sending a request that involves user-centric functionality?

The best practice is to send the token in a header of the request named `Authorization`.

### What Feature Are We Going to Implement?

We could start implementing a user-centric feature of SEI CAFE, however, that would be more work than necessary, after all, we just want to implement the infrastructure of a MERN-Stack app for now.

Instead, we'll simply mock up some functionality...

**AAU, I want to click a button to check the expiration of my log in.**

<details><summary>❓ When implementing new features, where do we start?</summary>
<p>

**With the UI.**

</p>
</details>

### Add a `<button>` to `<OrderHistoryPage>`

We'll add our feature to the `<OrderHistoryPage>`.

#### 💪 Practice Exercise - Add the `<button>` & `onClick` Handler (4 minutes)

1. Add a `<button>` with the content of "**Check When My Login Expires**" below the current `<h1>`.

    > Hint: You must return a single root component/node.

2. Add an `onClick` prop to the `<button>` and assign to it a handler named `handleCheckToken`.

3. Stub up the `handleCheckToken` function and baby step with `alert('clicked');`.

4. Ensure that clicking the button pops up the alert.

5. Make `handleCheckToken` an `async` function so that we can consume promises using `await`.

<img src="https://i.imgur.com/wXXNEgi.png">

Now, let's continue with the flow leading toward sending an AJAX request that includes the JWT...

### Add the `checkToken` Service Function

You got this...

#### 💪 Practice Exercise - Add the `checkToken` Service Function  (5 minutes)

1. Stub up and export a `checkToken` function in **users-service.js**.

2. Move the `alert('clicked');` from the `handleCheckToken` function to the `checkToken` function just stubbed up.

3. Import the `checkToken` function into **OrderHistoryPage.js** using one of the two syntaxes we've previously used.

4. Invoke the `checkToken` function from the `handleCheckToken` function. Consume the promise that `checkToken` will ultimately return using `await` assigning its resolved value to a variable named `expDate`.

5. After invoking `checkToken` add a `console.log(expDate)`.

6. Verify that clicking still pops up the alert.

### Add the `checkToken` API Function and Call It

Because we'll be making an AJAX request, we'll want to add another `checkToken` function in the **users-api.js** API module that can be called from `checkToken` in the **users-service.js** service module.

However, notice how the existing `signUp` and `login` functions in **users-api.js** aren't very DRY?

Here's a really clean refactor that will DRY things up in a jiffy...

Let's create a **utilities/send-request.js** module that will export a function that can be used in every API module in any application!

```js
// send-request.js

export default async function sendRequest(url, method = 'GET', payload = null) {
  // Fetch accepts an options object as the 2nd argument
  // used to include a data payload, set headers, etc. 
  const options = { method };
  if (payload) {
    options.headers = { 'Content-Type': 'application/json' };
    options.body = JSON.stringify(payload);
  }
  const res = await fetch(url, options);
  // res.ok will be false if the status code set to 4xx in the controller action
  if (res.ok) return res.json();
  throw new Error('Bad Request');
}
```

> Tip: Making code more DRY usually consists of recognizing repeated code, identifying what varies between the two or more functions and define those as parameters (inputs) in a new function the existing functions can invoke.

Now for the refactor of **users-api.js**:

```js
// users-api.js

// Add the following import
import sendRequest from './send-request';
const BASE_URL = '/api/users';

// Refactored code below
export function signUp(userData) {
  return sendRequest(BASE_URL, 'POST', userData);
}

export function login(credentials) {
  return sendRequest(`${BASE_URL}/login`, 'POST', credentials);
}
```

Now we're ready to code the `checkToken` function in **users-api.js** responsible for making the AJAX request to the server:

```js
export function checkToken() {
  return sendRequest(`${BASE_URL}/check-token`);
}
```

> Note: The `sendRequest` function always returns a promise and we are passing that promise to the caller of checkToken.

Now we want to call the API module's `checkToken` from within the `checkToken` function in **users-service.js** that we coded earlier.

<details><summary>❓ Looking at <strong>users-service.js</strong>, do we need import <code>checkToken</code> from <strong>users-api.js</strong>?</summary>
<p>

**No, because<br>`import * as usersAPI from './users-api';`<br>already imports all exports.**

</p>
</details>

Let's make the call, replacing the `alert('clicked')`:

```js
export function checkToken() {
  // Just so that you don't forget how to use .then
  return usersAPI.checkToken()
    // checkToken returns a string, but let's 
    // make it a Date object for more flexibility
    .then(dateStr => new Date(dateStr));
}
```

### Refactor `sendRequest` To Send the JWT

Finally, we're going to refactor **send-request.js** so that if there's a valid token in local storage, include it with the AJAX request in a header:

```js
// send-request.js

// Add the following import
import { getToken } from './users-service';

...

export default async function sendRequest(url, method = 'GET', payload = null) {
  ...
  if (payload) {
    options.headers = { 'Content-Type': 'application/json' };
    options.body = JSON.stringify(payload);
  }
  // Add the below code
  const token = getToken();
  if (token) {
    // Ensure the headers object exists
    options.headers = options.headers || {};
    // Add token to an Authorization header
    // Prefacing with 'Bearer' is recommended in the HTTP specification
    options.headers.Authorization = `Bearer ${token}`;
  }
  ...
```

Nice, we've got the JWT being sent to the server with AJAX requests!

## 2. Check the Token On the Server and Add a `user` Property To `req`

In Unit 2, we relied heavily on the fact that our OAuth/Passport code assigned the logged in user's document to `req.user`.

We want some of that goodness!

> IMPORTANT: As discussed when token-based auth was introduced, the `req.user` property will contain the user's info from the JWT's payload - it will not be a MongoDB document. If you need to modify the user's document, which should be uncommon, it will have to be retrieved from the database.

### Add the `checkToken` Middleware to **server.js**

As we learned many moons ago, middleware is used to process requests in an Express app.

Yay!  Another opportunity to write a custom middleware function that:

1. Checks if there's a token sent in an `Authorization` header of the HTTP request. For additional flexibility, we'll also check for a token being sent as a query string parameter.
2. Verifies the token is valid and hasn't expired.
3. Decodes the token to obtain the user data from its payload.
4. Then finally, adds the user payload to the Express request object.

First, create the module for the middleware function in the **config** folder:

```
touch config/checkToken.js
```

Now for some fun code:

```js
// config/checkToken.js

const jwt = require('jsonwebtoken');

module.exports = function(req, res, next) {
  // Check for the token being sent in a header or as a query parameter
  let token = req.get('Authorization') || req.query.token;
  if (token) {
    // Remove the 'Bearer ' if it was included in the token header
    token = token.replace('Bearer ', '');
    // Check if token is valid and not expired
    jwt.verify(token, process.env.SECRET, function(err, decoded) {
      // If valid token, decoded will be the token's entire payload
      // If invalid token, err will be set
      req.user = err ? null : decoded.user;  
      // If your app cares... (optional)
      req.exp = err ? null : new Date(decoded.exp * 1000);  
      return next();
    });
  } else {
    // No token was sent
    req.user = null;
    return next();
  }
};
```

Now we need to mount the above middleware function so that it processes every request:

```js
// server.js

...
app.use(express.static(path.join(__dirname, 'build')));

// Middleware to verify token and assign user object of payload to req.user.
// Be sure to mount before routes
app.use(require('./config/checkToken'));

...
```

### Add a Route to Test Out the Goodness

Add the following route to **routes/api/users.js**:

```js
// routes/api/users.js
...
const usersCtrl = require('../../controllers/api/users');

// GET /api/users/check-token
router.get('/check-token', usersCtrl.checkToken);
...
```

### Create the `checkToken` Controller Function

Keep following the flow...

```js
// controllers/api/users.js

function checkToken(req, res) {
  // req.user will always be there for you when a token is sent
  console.log('req.user', req.user);
  res.json(req.exp);
}
```

Don't forget to add `checkToken` to the exported object.

<details><summary>❓ Where did the <code>req.exp</code> property come from?</summary>
<p>

**The checkToken middleware function we just mounted in server.js**

</p>
</details>

That should do it!

<img src="https://i.imgur.com/GgRQELR.png">

Be sure to checkout the `req.user` being logged in the Express server's terminal too:

<img src="https://i.imgur.com/R0NWVoz.png">

# 😍

## 3. Implement Middleware to Protect Server-Side Routes

Any route/controller action that accesses `req.user` needs to ensure that the request is coming from a logged in user.

Yup, another opportunity for a custom middleware function:

```
touch config/ensureLoggedIn.js
```

Doesn't take much code:

```js
// config/ensureLoggedIn.js

module.exports = function(req, res, next) {
  // Status code of 401 is Unauthorized
  if (!req.user) return res.status(401).json('Unauthorized');
  // A okay
  next();
};
```

Now we can use it within any router module with routes that need to ensure that there's a logged in user.

Let's require it in **routes/api/users.js** and use it to protect the check token functionality we just coded:

```js
// routes/api/users.js

const usersCtrl = require('../../controllers/api/users');
// require the authorization middleware function
const ensureLoggedIn = require('../../config/ensureLoggedIn');

// Insert ensureLoggedIn on all routes that need protecting
router.get('/check-token', ensureLoggedIn, usersCtrl.checkToken);
```

**Congrats - that wraps up the infrastructure code for a MERN-Stack app!**

## 4. Save MERN-Stack Infrastructure To a New GitHub Repo

You'll definitely want to use the infrastructure we've coded over the last few days to launch your capstone project and likely future MERN-Stack projects as well.

First, let's update the **README.md** to something like:

```
# MERN-Stack Infrastructure

Clone this repo to provide the starter code for a comprehensive MERN-Stack project including token-based authentication.
```

### Reset the Commit History

**If you have not synced your code at any time during the 7 parts, you won't have any commits made by me and can thus skip this section.**

So that you don't have commits made by your me, let's **reset** the local repo:

```
rm -rf .git
git init
```

Next, commit your code as it stands:

```
git add -A
git commit -m "MERN-Stack Infrastructure"
```

### Create a GitHub Repo for `mern-infrastructure`

Next, go to your **personal** GitHub account and create a new repo named whatever you wish.

FYI, I'm going to name mine **mern-infrastructure**:

<img src="https://i.imgur.com/Ue3cPST.png">

Now click to copy the new repo's URL:

<img src="https://i.imgur.com/4KzM8o4.png">

Now let's add a remote that points to the new repo...

### Add the Remote:

We'll need to add a remote so that we can push to the new GH repo in the cloud.

If you **reset** the local repo, run:

```
git remote add origin <paste the copied url>
```

Otherwise, if you didn't reset the repo because you didn't sync, run the following to change where `origin` points to:

```
git remote set-url origin <paste the copied url>
```

Now you can push the code:

```
git push -u origin main
```

Congrats - refreshing the repo should confirm that the repo is ready for cloning as needed!

## 5. Using `mern-infrastructure` to Create MERN-Stack Projects in the Future

Here's the process to create a new MERN-Stack project that starts with the infrastructure code:

1. Clone the **mern-infrastructure** repo: `git clone <url of mern-infrastructure> <name-of-project>`
    > Note that the folder created will be same as `<name-of-project>` instead of mern-infrastructure

2. `cd <name-of-project>`

3. Install the Node modules:  `npm i`

4. Create a .env (`touch .env`) and add entries for `DATABASE_URL` and `SECRET`

5. Update the `"name": "mern-infrastructure"` in **package.json** to the name of your project.

6. Create a new repo on your personal GH account.

7. Copy the new GH repo's URL.

8. Update the remote's URL: `git remote set-url origin <paste the copied GH url>`

9. Make the initial commit:  `git add -A && git commit -m "Initial commit"`

10. Push for the first time:  `git push -u origin main`

11. Have fun coding your new project and don't forget to make frequent commits!

#### Congrats!

























