# Get last measurement for sensor


### GET (/api/v1/sensors/(id/measurements/last()
**Request**:

```
GET /api/v1/sensors/0028fcf0-9c90-11e8-8ee7-d12e1783ec90/measurements/last HTTP/1.1
Host: staging.sensorlab.io
Accept: application/json
```

**Success response**:

```
HTTP/1.1 200 OK
Content-Type: text/javascript

{
    "type": "UDX",
    "value": [
        6.625,
        8.893,
        9.414
    ],
    "timestamp": 1533627864
}
```


* **Query Parameters**

    
    * **type** – filter by type.



* **Response JSON Object**

    
    * **type** (*string*) – Measurement type.


    * **value** (*string*) – Array of values.


    * **timestamp** (*string*) – Timestamp for measurement.



* **Request Headers**

    
    * [Authorization](https://tools.ietf.org/html/rfc7235#section-4.2) – Bearer token from authentication.


    * [Content-Type](https://tools.ietf.org/html/rfc7231#section-3.1.1.5) – application/json



* **Status Codes**

    
    * [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – No errors, will return result with sensors list.


    * [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – User is not authorized - token is incorrect or outdated.


**NOTE**: Available for:


* User token


* Application token

Application token will have access only to measurements of sensors assigned to this application.
