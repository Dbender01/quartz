tags: #programming 

## API
A.P.I is actually an acronym that stands for **Application Programming Interface**. At the most basic level this means a few things. 
- The word **Application** refers to any piece of software that serves a distinct function.
- The word **Interface** means that it can interact with other applications. An API ^[ Application Programming Interface ] creates a contract of sorts. One application sends a **request** to another and expects a **response**.
- Most of the things we will be talking about an extent are API's because they are applications that interface with one another in this request and response format 




## RESTful
R.E.S.T ^[Representational State Transfer] is another acronym standing for **Representational State Transfer**. This is an architectural style, meaning that it is a method in which an API can be created and organized.

There are several different request types for a REST api. Here are the four most common.
- POST - in the simplest terms this typically means something is created behind the scenes. It also can technically also include a piece of data being deleted.
- PUT - similar to POST, objects can be created or deleted. The main difference is that If the exact same POST request is given multiple times, multiple things will happen. If the exact same PUT request is sent multiple times, only 1 thing will happen. 
- DELETE - Exactly what it sounds like. Its worth stating that 1 DELETE request should only ever delete one thing.
- GET - Will retrieve data from a system and make no changes.  

>[!info]  Some Advanced Terminology 
>Idempotence can describe what will happen when multiple requests are sent. A request is __idempotent__ if repeats of the same request will cause only one process to happen, like a PUT or DELETE. A request is __non-idempotent__ if multiple identical requests will cause a process to run multiple times like a POST request. A request like GET is actually considered __nullipotent__ because it has no effect on the data.


Here are a few steps that show how a message is transferred in a rest api. 
1. A request is send via HTTP ^[HTTP is a system of rules for for fetching resources such as HTML documents] using a route. This initially process is how pretty much any webpage on the internet is sent to your browser. When I go to https://www.kroger.com/ I am making an http request to see the html page at `www.kroger.com` 
2. Next the data is packaged. This is sort of like the envelope the data is mailed in. The most common for a REST API is JSON ^[JavaScript Object Notation] Here is an example of a json response from the [Kroger API]() from a GET request using the endpoint `locations/{locationId}`
	```json
	"data": {

		"address": {},
    
		"chain": "KROGER",
    
		"phone": "5551234567",
    
		"departments": [],
    
		"geolocation": {},
    
		"hours": {},
    
		"locationId": "01400376",
    
		"storeNumber": "00376",
    
		"divisionNumber": "014",
    
		"name": "Kroger Landen"   

	},
	```

3.  Once the request is sent, the API will run its internal functions based on the request, once it is finished it will format a response, likely in JSON and return it to the requester. JSON is good because its somewhat universal, easy to be read by computer and people, and its fairly easy for most programming languages to interpret. In general REST is the more modern Architecture for an API


## SOAP 
SOAP ^[Simple Object Access Protocol] is an older architecture style for API's that came before REST. SOAP is less flexible than REST, but also more secure because of its more rigid rules. Here are two key ways SOAP differs from REST.
1. Every type of request is a POST request, there is no GET, DELETE, or PUT.
2. SOAP uses XML ^[Extensible Markup Language] rather than JSON. Here is an example of what the xml of a soap request might look like 

```xml
<?xml version="1.0"?>  
  
<soap:Envelope  
xmlns:soap="http://www.w3.org/2003/05/soap-envelope/"  
soap:encodingStyle="http://www.w3.org/2003/05/soap-encoding">  
  
<soap:Body xmlns:m="http://www.example.org/stock">  
  <m:GetStockPriceResponse>  
    <m:Price>34.5</m:Price>  
  </m:GetStockPriceResponse>  
</soap:Body>  
  
</soap:Envelope>
```


## Message Queues
Message queue is a pretty broad term and could mean a few things depending on the implementation. The basic idea is that a queue is just data waiting in a line to be processes, and in this context its done with messages. A message queue should enable communications between services, programs, and dissimilar components to happen all at once. Here is a visualization to get the idea

![[MessageQueue.png]]

The green circles are different apps that need something from the blue circles. If every green circle sent a message at the same time the blue system would get overwhelmed. The job of the message queue is to take in all of the green requests and hand them off at a pace the blue circles can handle. This usually happens very quickly, and from the perspective of the green circles, it allows a message to be transferred  at anytime without having a threat of overwhelming the blue system.   



Some sources 
[What is an API? Amazon](https://aws.amazon.com/what-is/api/#:~:text=API%20stands%20for%20Application%20Programming,other%20using%20requests%20and%20responses.)
[What is REST API? Redhat](https://www.redhat.com/en/topics/api/what-is-a-rest-api)
[Understanding REST Request Methods](https://www.soapui.org/learn/api/rest-request-method-verbs/#:~:text=The%20most%20common%20are%3A%20GET,specified%20without%20breaking%20existing%20infrastructure)
