# Create application


### POST (/api/v1/applications()
**Request**:

```
POST /api/v1/applications HTTP/1.1
Host: staging.sensorlab.io
Content-type: application/json

{
    "name": "Application Name",
    "description": "Application Description"
}
```

**Success response**:

```
HTTP/1.1 200 OK
Content-type: application/json

{
    "success": true,
    "code": 100,
    "message": "Application created.",
    "application": {
        "id": "7e970572-9a16-11e8-9eb6-529269fb1459",
        "name": "Application Name",
        "description": "Application Description",
        "public_api_key": "sensorlab:application:62fa02f38ff6100dbbd1cdff2339ccf3",
        "private_api_key": "146d3ac9d9900c8151a73ca09b39ca7f"
    }
}
```


* **Request JSON Object**

    
    * **name** (*string*) – Name for your application


    * **description** (*string*) – Description for your application



* **Response JSON Object**

    
    * **application** (*object*) – Application data.


    * **application.id** (*string*) – Application ID.


    * **application.name** (*string*) – Application name.


    * **application.description** (*string*) – Application description.


    * **application.public_api_key** (*string*) – Public API key.


    * **application.private_api_key** (*string*) – Generated private API key.
    Please note, that Private API Key will appear only once after app creation.
    You will be able to generate new one though.



* **Request Headers**

    
    * [Authorization](https://tools.ietf.org/html/rfc7235#section-4.2) – Bearer token from authentication.


    * [Content-Type](https://tools.ietf.org/html/rfc7231#section-3.1.1.5) – application/json



* **Status Codes**

    
    * [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – No errors, will return result with applications list.


    * [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – User is not authorized - token is incorrect or outdated.


    * [422 Unprocessable Entity](http://tools.ietf.org/html/rfc4918#section-11.2) – Validation error.


**Possible validation errors and codes:**


* code=1 - Please, provide name field. This cannot be empty

**NOTE**: Available for:


* User token
