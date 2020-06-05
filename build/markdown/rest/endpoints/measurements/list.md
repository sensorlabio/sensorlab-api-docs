# Get list of measurements


### GET (/api/v1/measurements()
**Request**:

```
GET /api/v1/measurements?sensor_id=5ab8b113fc10152c70cdeb65 HTTP/1.1
Host: staging.sensorlab.io
Content-type: application/json
```

**Success response**:

```
HTTP/1.1 200 OK
Content-type: application/json

{
    "result": [
        {
            "type": "KVF",
            "value": [
                3.896,
                4.037,
                5.42
            ],
            "timestamp": "1533627864"
        },
        {
            "type": "TTA",
            "value": [
                4.465,
                4.126,
                4.535
            ],
            "timestamp": "1533627865"
        },
    ],
    "next": "d438a4b2-9a17-11e8-9eb6-529269fb1459",
    "prev": null
}
```


* **Query Parameters**

    
    * **sensor_id** – Sensor’s ID.


    * **next** – Use next or prev fields from response to get next or previous page.


    * **type** – filter by type.



* **Response JSON Object**

    
    * **result.type** (*string*) – Measurement type.


    * **result.value** (*array*) – Array of values.


    * **result.timestamp** (*number*) – Timestamp for measurement.


    * **next** (*string*) – This param shows next measurement ID for next page. Use it with next query parameter.


    * **prev** (*string*) – This param shows prev measurement ID for prev page. Use it with next query parameter.



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


> * code=3 - field=next - This is not correct id format


> * code=4 - field=timestamp_start - timestamp_start should be correct unix timestamp format


> * code=5 - field=timestamp_stop - timestamp_stop should be correct unix timestamp format


> * code=6 - field=timestamp_stop - timestamp_stop should be more or equal timestamp_start

**NOTE**: Available for:


* User token


* Application token

Application token will have access only to measurements of sensors assigned to this application.
