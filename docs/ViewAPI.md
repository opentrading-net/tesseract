# View Application Programming Interface
The View API is a dynamically generated interface that allows client systems to access and operate on data exposed by a [view](View.md).

The View API is a REST JSON based API in the [OpenApi](https://swagger.io/specification/) format. For a given view ({view} placeholder below) the REST interface will be:

* ```http://{tesseract host}/api/{view}/swagger-ui?session={session name}``` 
    * HTTP GET 
    * Renders Swagger UI view of the API
* ```http://{tesseract host}/api/{view}/openapi.json?session=<session name>``` 
    * HTTP GET 
    * Returns the [OAS3](https://swagger.io/specification/) JSON specification for the API
* ```http://{tesseract host}/api/{view}?session={session name}&criteria={escaped JSON}``` 
    * HTTP GET returns JSON data items for the supplied criteria
* ```http://{tesseract host}/api/{view}/{action}?session={session name}```
    * HTTP POST 
    * Executes view action with the supplied criteria, row data and action data and returns data items
    * Request payload is the view criteria, updated, created, deleted items and action data (if applicable)

The session URL parameter is common to all of the REST operations and is optional. If it is not specified then the default session will be used.

