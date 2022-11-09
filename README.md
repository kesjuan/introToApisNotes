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

XML has become a very mature and powerful data format. Like JSON, XML provides a few simple building blocks that API makers use to structure their data. The main block is called a node. 
XML always starts with a root node. The name of each node tells us the attribute of the order (like the key in JSON) and the data inside is the actual detail (like the value in JSON). ex <Node> value </Node>
