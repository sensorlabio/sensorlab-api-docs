# Get application


### GET (/api/v1/applications/(id)
**Request**:

```
GET /api/v1/applications/d8d7f14a-9a16-11e8-9eb6-529269fb1459 HTTP/1.1
Host: staging.sensorlab.io
Content-type: application/json
```

**Success response**:

```
HTTP/1.1 200 OK
Content-type: application/json

{
    "id": "d8d7f14a-9a16-11e8-9eb6-529269fb1459",
    "name": "Sensors Application",
    "description": "Sensor Description",
    "created": "2018-05-09T10:20:01.352Z",
    "public_api_key": "sensorlab:application:62fa02f38ff6100dbbd1cdff2339ccf3"
 }
```


* **Request Headers**

    
    * [Authorization](https://tools.ietf.org/html/rfc7235#section-4.2) – Bearer token from authentication.


    * [Content-Type](https://tools.ietf.org/html/rfc7231#section-3.1.1.5) – application/json



* **Response JSON Object**

    
    * **id** (*string*) – Application ID.


    * **name** (*string*) – Application name.


    * **description** (*string*) – Application description.


    * **public_api_key** (*string*) – Public API key.



* **Status Codes**

    
    * [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – No errors, will return result with applications list.


    * [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – User is not authorized - token is incorrect or outdated.


    * [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Application not found


**NOTE**: Available for:


* User token
