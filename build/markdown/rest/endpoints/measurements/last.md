# Get last measurement


### GET (/api/v1/measurements/last()
**Request**:

```
GET /api/v1/measurements/last?sensor_id=11e34426-9a17-11e8-9eb6-529269fb1459 HTTP/1.1
Host: staging.sensorlab.io
Content-type: application/json
```

**Success response**:

```
HTTP/1.1 200 OK
Content-type: application/json

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

    
    * **sensor_id** – Sensor’s ID.


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


    * [422 Unprocessable Entity](http://tools.ietf.org/html/rfc4918#section-11.2) – Validation error.


**Possible validation errors and codes:**

> 
> * code=1 - field=sensor_id - Please, provide sensor field. This cannot be empty


> * code=2 - field=sensor_id - This is not correct id format

**NOTE**: Available for:


* User token


* Application token

Application token will have access only to measurements of sensors assigned to this application.
