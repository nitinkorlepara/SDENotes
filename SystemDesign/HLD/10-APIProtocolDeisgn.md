# API Communication Protocol

- A web service is a standardized method for propagating messages between client and server applications. A web service is a software module that is intended to carry out a specific set of functions.
- Request, Response,
- Types
  - SOAP( Simple Object Access Protocol)
    - WSDL ( Web Service Description Language)
    - UDDI- Universal Description , Discovery Language
    - Follows XML format ( message is encoded as XML document)

  - REST( Representational State Transfer )
    - Resource ( entity)
    - URI( address of the resource)
    - HTTP Method ( GET, POST, PUT, DELETE)
    - Stateless ( client request to the server contains all the information necessary for the server to understand and fulfill the request)
    - Cacheable
    - Layered System
    - Response can be XML,HTML,JSON,CSV....

## Restful Web Services

Restful web services are a way of providing interoperability between computer systems on the internet. They use HTTP requests to perform CRUD (Create, Read, Update, Delete) operations.

- Principles of REST
  1. **Stateless**: Each request from a client contains all the information needed to process the request.
  2. **Client-Server Architecture**: The client and server are separate entities that communicate over a network.
  3. **Cacheable**: Responses must define themselves as cacheable or non-cacheable.
  4. **Uniform Interface**: A consistent way of interacting with resources, typically using standard HTTP methods.

- HTTP Methods
  - **GET**: Retrieve data from the server.
  - **POST**: Send data to the server to create a new resource.
  - **PUT**: Update an existing resource.
  - **DELETE**: Remove a resource.
  - **HEAD**: Used to retrieve the headers of a resource without fetching the body. It is useful for checking if a resource has been modified.
  - **OPTIONS**: Used to describe the communication options for the target resource. It can be used to check the allowed HTTP methods on a resource.
  - **PATCH**: Used to apply partial modifications to a resource. It is useful for updating specific fields without sending the entire resource.

- Status Codes
  - **200 OK**: The request was successful.
  - **201 Created**: A new resource was created successfully.
  - **204 No Content**: The request was successful but there is no content to return.
  - **400 Bad Request**: The request could not be understood by the server.
  - **404 Not Found**: The requested resource could not be found.
  - **500 Internal Server Error**: An error occurred on the server.

- Conclusion
  - Restful web services are widely used for building APIs due to their simplicity and scalability.
