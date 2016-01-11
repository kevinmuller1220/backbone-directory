## Employee Directory ##

### Sample Application built with Backbone.js and Twitter Bootstrap ###

"Backbone Directory" is a simple Employee Directory application built with [Backbone.js](http://backbonejs.org) and [Twitter Bootstrap] (http://twitter.github.io/bootstrap/).

Employee Directory, a sample application that demonstrates how to build modern web apps with Backbone.js and Twitter Bootstrap.
Because of the continued interest in the application as a starting point and a reference for Backbone.js and Twitter Bootstrap, I decided to give it a well deserved update.

New in this version:

Latest version of Backbone.js (1.0)
Latest version of Twitter Bootstrap (2.3.1)
Layout is now responsive
Data persistence layer is now abstracted (see below)
Additional data persistence options: In-memory datastore, Node.js/MongoDB, Parse.com (In addition to PHP and Java)
New GitHub repository organization (see below)
Bug fixes and cleaner code
Running the Application

You can test the hosted version of the application here, or you can download the code (see GitHub repository information below) and test the application locally.

Data Persistence Abstraction

Among the great feedback I received, a number of you mentioned you wanted a self-contained version of the app with no dependency on a specific back end to be able to “download and run” without having to set up a server and a database. So I rearchitected the persistence layer with simple and pluggable data adapters. By default the application now uses an in-memory data store, but other adapters are available. To change the data persistence strategy, just comment out model-in-memory.js in index.html and uncomment one of the other data adapters using the table below as a reference.

I initially published the application with two implementations of a RESTful back end: A Java version using Jersey, and a PHP version using Slim. A year later, I’m adding the long overdue Node.js/MongoDB back end.

<table>
	<tr style="font-weight:bold;">
		<td width="200">Adapter</td>
		<td>Description</td>
		<td width="200">Back end Repo</td>
	</tr>
	<tr>
		<td style="width:140px">model-in-memory.js</td>
		<td>In-memory data store</td>
		<td style="width:170px">No server required</td>
	</tr>
	<tr>
		<td>model-rest-json.js</td>
		<td>Backbone.js default behavior. The application gets data through RESTFul services.</td>
		<td><a href="https://github.com/kevinmuller1220/directory-rest-nodejs">directory-server-nodejs</a><br><br>
		<a href="https://github.com/kevinmuller1220/directory-rest-php">directory-server-php</a><br><br>
		directory-server-java
		</td>
	</tr>
	<tr>
		<td>model-rest-jsonp.js</td>
		<td>If the server serving your pages and the server serving your data are on different domains, use this adapter instead to avoid the same origin policy error.</td>
		<td><a href="https://github.com/kevinmuller1220/directory-rest-nodejs">directory-server-nodejs</a><br><br>
		<a href="https://github.com/kevinmuller1220/directory-rest-php">directory-server-php</a><br><br>
		directory-server-java
		</td>
	</tr>
	<tr>
		<td>model-websql.js</td>
		<td>Uses local database using the WebSQL api.</td>
		<td>No server required</td>
	</tr>
	<tr>
		<td>model-parse-dot-com.js</td>
		<td>Don’t want to host your own data infrastructure? Parse.com is a cloud service that will host your data for you. Use this adapter to test your app with  sample data I deployed on Parse.com.</td>
		<td>No server required</td>
	</tr>
</table>

The Node.js, Java, and PHP RESTful back ends work with both JSON and JSONP. If the request includes a query parameter named “callback”, a JSONP response is returned, otherwise, a regular JSON response is returned.

The application runs out-of-the-box with an in-memory data store.

If you want to experiment the application with other persistence layers, download the REST services in the following repositories:

- [directory-rest-nodejs](https://github.com/kevinmuller1220/directory-rest-nodejs) (Node.js/MongoDB implementation)
- [directory-rest-php](https://github.com/kevinmuller1220/directory-rest-php) (PHP implementation)

