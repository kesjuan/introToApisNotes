# introToApisNotes
                                          #Server & APIs
physical: the server. A server is nothing more than a big computer. physical: the server. A server is nothing more than a big computer. 
Server: A powerful computer that runs an API. 
API: The "hidden" portion of a website that is meant for computer consumption.
Client: A program that exchanges data with a server through an API.
. An API is the tool that makes a website's data digestible for a computer. Through it, a computer can view and edit data. When two systems (websites, desktops, smartphones) link up through an API, we say they are "integrated." In an integration, you have two sides, each with a special name. 
The server is the side that actually provides the API,remember that the API is simply another program running on the server,  it is sitting, waiting for others to ask it for data.
The other side is the "client." This is a separate program that knows what data is available through the API and can manipulate it typically at the request of a user. 
 When one site pulls in data from the other, the site providing the data is acting as the server, and the site fetching the data is the client.
 ```
 --------------------------------------------------------------------------------------------------------------------------
 ```
                                          #HTTP Request & Response 
On the web, the main protocol is the Hyper-Text Transfer Protocol or HTTP .When you type an address like http://example.com into a web browser, the "http" tells the browser to use the rules of HTTP when talking with the server.
Communication in HTTP centers around a concept called the Request- Response Cycle. 
The client sends the server a request to do something. The server, in turn, sends the client a response saying whether or not the server could do what the client asked.
Request - consists of a URL (http://...), a method (GET, POST, PUT, DELETE), a list of headers (User-Agent...), and a body (data).
To make a valid request, the client needs to include four things
1.URL- uniform Resource Locator. In HTTP, a URL is a unique address for a thing (a noun). Which things get addresses is entirely up to the business running the server. They can make URLs for web pages, images, or even videos of cute animals.
 URLs become an easy way for the client to tell the server which thing it wants to interact with. Of course, APIs also do not call them "things", but give them the technical name "resources."
2.Method - Most common methods seen in APIs. GET - Asks the server to retrieve a resource. POST - Asks the server to create a new resource. PUT - Asks the server to edit/update an existing resource. DELETE - Asks the server to delete a resource. 
3.List of Headers - Headers provide meta-information about a request. They are a simple list of items like the time the client sent the request and the size of the request body. an HTTP header called "User-Agent." The client uses this header to tell the server what type of device you are using, and websites smart enough to detect it can send you the best format for your device.
4.Body - The request body contains the data the client wants to send the server. A unique trait about the body is that the client has complete control over this part of the request. Unlike the method, URL, or headers, where the HTTP protocol requires a rigid structure, the body allows the client to send anything it needs.
Response - consists of a status code (200, 404...), a list of headers, and a body.
 HTTP responses includes a status code. Beyond that, the response headers and body follow the same format as requests.
Status codes are three-digit numbers that each have a unique meaning.
After a response is delivered to the client, the Request-Response Cycle is completed and that round of communication over. It is now up to the client to initiate any further interactions. The server will not send the client any more data until it receives a new request.
```
---------------------------------------------------------------------------------------------------------------------------
```
                                            #JSON & XML
Many new APIs have adopted JSON as a format because it's built on the popular Javascript programming language, which is ubiquitous on the web and usable on both the front- and back-end of a web app or service. JSON is a very simple format that has two pieces: keys and values. Keys represent an attribute about the object being described.

XML: Extensible Markup Language. XML has become a very mature and powerful data format. Like JSON, XML provides a few simple building blocks that API makers use to structure their data. The main block is called a node. 
XML always starts with a root node. The name of each node tells us the attribute of the order (like the key in JSON) and the data inside is the actual detail (like the value in JSON). ex <Node> value </Node>

If the client wants to send the server JSON data, it will set the Content-Type to "application/json." Upon receiving the request and seeing that Content-Type, the server will first check if it understands that format, and, if so, it will know how to read the data. Likewise, when the server sends the client a response, it will also set the Content-Type to tell the client how to read the body of the response.
The client can set the Accept header to tell the server what data formats it is able to accept. If the client can only speak JSON, it can set the Accept header to "application/json." The server will then send back its response in JSON. If the server doesn't support the format the client requests, it can send back an error to the client to let it know the request is not going to work.
```
---------------------------------------------------------------------------------------------------------------------------
```
                                                #Authentication
 A username and a password are two pieces of information that become your identifying marks We call these your credentials.
Logging-in with a username and password is one example of a technical process known as authentication. 
There are several techniques APIs use to authenticate a client. These are called authentication schemes.
*Basic Auth only requires a username and password. The client takes these two credentials, smooshes them together to form a single value 1, and passes that along in the request in an HTTP header called Authorization. When the server receives the request, it looks at the Authorization header and compares it to the credentials it has stored. If the username and password match one of the users in the server's list. Basic Auth: scheme that uses an encoded username and password for credentials. Authorization Header: the HTTP header used to hold credentials

* API Key authentication is a technique that overcomes the weakness of using shared credentials by requiring the API to be accessed with a unique key. In this scheme, the key is usually a long series of letters and numbers that is distinct from the account owner's login password. When the client authenticates with the API key, the server knows to allow the client access to data, but now has the option to limit administrative functions, like changing passwords or deleting accounts.
There are different ways to use API Keys, One is to have the client put the key in the Authorization header, in lieu of a username and password. Another is to add the key onto the URL (http://example.com?api_key=my_secret_key). Less common is to bury the key somewhere in the request body next to the data. Wherever the key goes, the effect is the same - it lets the server authenticate the client. There is no header for the API key. API Key Auth: scheme that uses a unique key for credentials
```
---------------------------------------------------------------------------------------------------------------------------
```
                                          #APIkeys & OAuth 
OAuth: an authentication scheme that automates the key exchange between client and server.
Access Token: a secret that the client obtains upon successfully completing the OAuth process.
Scope: permissions that determine what access the client has to user's data.
Automating the key exchange is one of the main problems OAuth solves.
There are currently two versions of OAuth, aptly named OAuth 1 and OAuth 2.
To get started, we first need to know the cast of characters involved in an OAuth exchange: 
- The User ~ A person who wants to connect two websites they use.
- The client ~The website that will be granted access to the user's data.
- The server ~ The website that has the user's data.
Steps for OAuth 2
1. User Tells Client to Connect to Server. The user kicks off the process by letting the client know they want it to connect to the server. Usually, this is by clicking a button.
2. Client Directs User to Server. The client sends the user over to the server's website, along with a URL that the server will send the user back to once the user authenticates, called the callback URL.
3. User Logs-in to Server and Grants Client Access. With their normal username and password, the user authenticates with the server. The server is now certain that one of its own users is requesting that the client be given access to the user's account and related data.
4. Server Sends User Back to Client, Along with Code. The server sends the user back to the client (to the Callback URL from Step 2). Hidden in the response is a unique authorization code for the client.
5. Client Exchanges Code + Secret Key for Access Token. The client takes the authorization code it receives and makes another request to the server. This request includes the client's secret key. When the server sees a valid authorization code and a trusted client secret key, it is certain that the client is who it claims to be and that it is acting on behalf of a real user. The server responds back with an access token.
6.  Client Fetches Data from Server. At this point, the client is free to access the server on the user's behalf. The access token from Step 6 is essentially another password into the user's account on the server. The client includes the access token with every request so it can authenticate directly with the server.

 OAuth 1 is Different 
 - Access tokens do not expire.
 - OAuth 1 includes an extra step. Between Steps 1 and 2 above, OAuth 1 requires the client to ask the server for a request token. This token acts like the authorization code in Oauth 2 and is what gets exchanged for the access token.
 - A third difference is that OAuth 1 requires requests to be digitally signed.
 
 Most API traffic happens over a channel that is already secure (HTTPS). Recognizing this, OAuth 2 eliminates signatures in an effort to make version two easier to use. The trade-off is that OAuth 2 relies on other measures to provide security to the data in transit.
 in Step 2, when the user clicks the button to allow the client access, buried in the fine print are the exact permissions the client is asking for. Those permissions, called scope, are another important feature of OAuth 2.
What makes scope powerful is that it is client-based restrictions. Unlike an API Key, where limits placed on the key affect every client equally, OAuth scope allows one client to have permission X and another permissions X and Y. That means one website might be able to view your contacts, while another site can view and edit them.
```
---------------------------------------------------------------------------------------------------------------------------
```
                                          #API Design
REST: API architecture that centers around manipulating resources.
Resource: API term for a business noun like customer or order.
Endpoint: A URL that makes up part of an API. In REST, each resource gets its own endpoints.
Query String: A portion of the URL that is used to pass data to the server.
Query Parameters: A key-value pair found in the query string (topping=cheese)
Pagination: Process of splitting up results into manageable chunks.

There are two common architectures for web-based APIs
SOAP is an XML-based design that has standardized structures for requests and responses.
REST, which stands for Representational State Transfer, is a more open approach, providing lots of conventions, but leaving many decisions to the person designing the API.
Rest Architecture 
1. Decide what resource(s) need to be available. Picking resources can be a difficult first task. One way to approach the problem is to step through what a typical interaction involves.
2. Assign URLs to those resources. In a typical REST API, a resource will have two URL patterns assigned to it. The first is the plural of the resource name, like /orders. The second is the plural of the resource name plus a unique identifier to specify a single resource, like /orders/<order_id>, where <order_id> is the unique identifier for an order. These two URL patterns make up the first endpoints that our API will support. These are called endpoints simply because they go at the end of the URL, as in http://example.com/ <endpoint_goes_here>.
3. Decide what actions the client should be allowed to perform on those resources.we say that the plural endpoint (/orders) is for listing existing orders and creating new ones. The plural with a unique identifier endpoint (/orders/<order_id>), is for retrieving, updating, or cancelling a specific order. The client tells the server which action to perform by passing the appropriate HTTP verb (GET, POST, PUT or DELETE) in the request.
4. Figure out what pieces of data are required for each action and what format they should be in. say that an order needs a crust and toppings. We also need to select a data format that the client and server can use to pass this information back and forth. XML and JSON are both good choices, but for readability sake, we'll go with JSON.

REST practitioners are split on how to solve the problem of associating resources. Some say that the hierarchy should continue to grow, giving endpoints like /customers/5/orders for all of customer #5's orders
and /customers/5/orders/3 for customer #5's third order. Others argue to keep things flat by including associated details in the data for a resource.

Query means search and string means text. The query string is a bit of text that goes onto the end of a URL to pass things along to the API. For example, everything after the question mark is the query string in http://example.com/orders?key=value. REST APIs use the query string to define details of a search. These details are called query parameters.

The API dictates what parameters it will accept, and the exact names of those parameters need to be used for them to effect the search. Our pizza parlor API could allow the client to search for orders by topping by using this URL: http://example.com/ orders?topping=pepperoni. 

The client can include multiple query parameters by listing one after another, separating them by an ampersand ("&"). For example: http://example.com/orders? topping=pepperoni&crust=thin.

Another use of the query string is to limit the amount of data returned in each request. Often, APIs will split results into sets (say of 100 or 500 records) and return one set at a time. This process of splitting up the data is known as pagination. To allow the client to page through all the data, the API will support query parameters that allow the client to specify which page of data it wants. ex. GET /orders?page=2&size=200, we know they want the second page of results, with 200 results per page, so orders 201-400.

