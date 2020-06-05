# Update sensor


### PATCH (/api/v1/sensors/(id)
**Request**:

```
PATCH /api/v1/sensors/acdfab8a-9a18-11e8-9eb6-529269fb1459 HTTP/1.1
Host: staging.sensorlab.io
Content-type: application/json

{
    "name": "Updated Sensor ID",
    "application": "b2a2fdb0-9a18-11e8-9eb6-529269fb1459"
}
```

**Success response**:

```
HTTP/1.1 200 OK
Content-type: application/json

{
    "success": true,
    "code": 100,
    "message": "Sensor updated.",
}
```


* **Request JSON Object**

    
    * **name** (*string*) – Name for your sensor.


    * **application** (*string*) – Application’s ID to connect sensor too.


    * **is_public** (*boolean*) – Set sensor public or private (true or false).



* **Request Headers**

    
    * [Authorization](https://tools.ietf.org/html/rfc7235#section-4.2) – Bearer token from authentication.


    * [Content-Type](https://tools.ietf.org/html/rfc7231#section-3.1.1.5) – application/json



* **Status Codes**

    
    * [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – No errors, will return result with applications list.


    * [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – User is not authorized - token is incorrect or outdated.


    * [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Sensor not found.


    * [422 Unprocessable Entity](http://tools.ietf.org/html/rfc4918#section-11.2) – Validation error.


**Possible validation errors and codes:**


* code=1 - field=name - Please, provide name field. This cannot be empty


* code=2 - field=application - application must be correct UUID format


* code=3 - field=is_public - is_public must be correct boolean format

**NOTE**: Available for:


* User token


* Application token

Application token will have access only to sensors assigned to this application.
