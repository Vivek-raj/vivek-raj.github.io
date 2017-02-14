---
layout: post
title: "Designing RESTful APIs"
date: 2017-01-01
image: /imgs/REST.jpg
---
REST is an architectural model that provides for distributed interactions between various devices, servers, applications or databases.REST has become the <i>de facto</i> standard for distributed computing.
REST is a stateless architecture where state is maintained by the resources.<br/>
Here are some of the key features that will help you write better APIs.
## RESTful Urls 
The key features of REST involves separating your API into logical resources.
These resources are manipulated using HTTP requests where the methods GET, POST, PUT, DELETE have specific meaning.
These resources should be noun and not verbs. Once you have you resources defined you need to identify what actions apply to them and should they be mapped to your API. <br/>
<p style="margin-left:20px;">
<b>GET</b> - GET method is used to retrieve data from the given URI. Get only fetches the data and has no effect on the data. <br/>
<b>POST</b> - POST method is used to send data to the server using the given URI. For example, creating new user, uploading files etc.<br/>
<b>PUT</b> - PUT method is used to update the existing data on the server.<br/>
<b>DELETE</b> - DELETE method removes the data from the target server.
</p>
RESTful principles provide strategies to handle CRUD actions using HTTP methods mapped as follows:<br/>
<span class="code">GET / users</span> - Retrieves all the users.<br/>
<span class="code">GET /users/john</span> - Retrieves a specific user by his username.<br/>
<span class="code">POST /users</span> - Creates a new user.<br/>
<span class="code">PUT /users/john</span> - Updates a specific user, in this case 'john'.<br/>
<span class="code">DELETE /users/john</span> - Deletes the user with username 'john'.<br/>
The important thing to note here is that the endpoints are plural. For simplicity sake just ignore the grammar and always use plural.<br/>
##	Query Parameters - Filtering, Sorting and Searching
<p>
<b>Paging</b> - Pagination is very important because different API calls respond with different defaults. It is difficult to foresee precisely the progression of the amount of data that will be returned. <br/>Paginating your resources with default values when they are not provided by the calling client is recommended. Information about pagination is provided in the Link Header of an API.<br/>
<b>Filtering</b> - Filtering refers to using a unique query parameter for each field. For example, when requesting a list of users from the /users endpoint, you can limit the results to only active users. It can be accomplished with a request like GET /users?active=true. Here active is a query parameter that implements a filter.<br/>
<b>Sorting</b> - Sort is a generic parameter used to describe sorting rules. The sort parameter contains the names of attributes on which the sorting can be performed.<br/>
For example,<br/>
	<span class="code">GET /users?sort=first_name</span> - Fetches a list of users by sorting them from their first name
</p>
##	Documentation
Documenting the API is very important. It should be easy to find and publicly accessible. The docs must contain the complete request/response cycles. Documentation must also contains examples - either links that can be pasted into a browser or curl examples that can be pasted into the terminal.<br/>
##	snake_case vs camelCase vs spinal-case
There are 3 main types of case conventions when it comes to naming resources in APIs, camleCase, snake_case and spinal-case. These are just a way of avoiding spaces, apostrophes and other special characters while still maintaining the resemblance of natural language.<br/>
If your primary representation format is JSON then i would suggest you to follow the JavaScript naming conventions and use camelCase. It's best to use idiomatic naming conventions camelCase for C#, Java.
<p style="margin-left:20px;">
	<b>camelCase</b> - It's best to use idomatic naming conventions camelCase for C#, Java.<br/>
	<b>snake_case</b> - It is actually very easy to read (that's what i feel) when compared with JavaScript's convention of camelCase. Many popular APIs use snake_case.<br/>
	<b>spinal-case</b> - is a variant of snake_case which uses hyphen "-" to separate words. This has its own cons, because some languages do not allow hyphens in symbol names. But this is a traditional way of naming UNIX and LINUX files and folders.
</p>
##	Status Codes
HTTP defines a bunch of meaningful status codes that can be returned from APIs. The moslty used status codes are:<br/>
<p>

	<span class="code">200 OK</span> - Indicates a successful GET, POST, PUT or DELETE.<br/>
	<span class="code">201 Created</span> - New resource has been created using POST.<br/>
	<span class="code">204 No Content</span> - Response to a successful request with no body in response. For example, DELETE request.<br/>
	<span class="code">304 Not Modified</span> - Cached data is returned.<br/>
	<span class="code">400 Bad Request</span> - Malformed request or request was invalid or cannot be served.<br/>
	<span class="code">401 Unauthorized</span> - Request requires authorization or invalid user credentials.<br/>
	<span class="code">403 Forbidden</span> - User does not have access to the resource.<br/>
	<span class="code">404 Not Found</span> - Resource does not exist.<br/>
	<span class="code">500 Internal Server Error</span> - Developers should avoid this error, which occurs in the global catch block.
</p>

