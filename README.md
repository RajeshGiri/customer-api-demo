customers-api-demo

 A test API to demonstrate the use of RAML in creating an API spec

Use cases:

1.	List existing customers in the system:
•	Calling the /customers endpoint using a get request will return a list of all customers. A consumer can poll this endpoint and keep an up-to-date copy of this API's Customers.
•	Optionally added a queryParameter as timeSinceLastUpdate to fetch from the last modified date.
•	The API could be enhanced to only return Customers updated/created within a specified date range by providing 2 input parameters.

2.	Retrieving and updating customer details via a mobile application:
•	This API enables any mobile applications to retrieve and update specific Customer details be passing the Customer id into the /Customers/{id} call using a GET or PUT.
•	The API also provides this functionality in bulk on the /customers endpoint, so updating or retrieving multiple Customers is also supported.

3.	Simple extension of the API to support future resources such as orders and products
•	With the way this RAML spec is designed using Types of objects, in this case a Customer and Address object. It would be very simple to re-use the existing call structures, rename the /customers to /orders (for example), define an order object and alter the !includes.
•	By doing this you would instantly have the capability to list all Orders, or list specific orders as you currently can with Customers.

4.	Commentary on any 'interesting' design decisions you made (and alternative options considered)
•	The ability to group similar objects using a 'collection' effectively makes the api self documenting, you can add a new type such as an order, add it to the collection resourceType and all the response and request traits are inherited and can be overrided if necessary.
•	Didn't implement authentication directly in the mule flow as the intention was that API manager would implement authentication outside as a policy on the gateway. Alternative would have been to add a spring-security element on the flow itself.
