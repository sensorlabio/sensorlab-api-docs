# Get list of applications


### GET (/api/v1/applications()
**Request**:

```
GET /api/v1/applications HTTP/1.1
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
            "id": "d8d7f14a-9a16-11e8-9eb6-529269fb1459",
            "name": "Sensors Application 1",
            "description": "",
            "created": "2018-05-09T10:20:01.352Z",
            "public_api_key": "sensorlab:application:62fa02f38ff6100dbbd1cdff2339ccf3",
        },
        {
            "id": "f6ca0a08-9a16-11e8-9eb6-529269fb1459",
            "name": "Sensors Application 2",
            "description": "Application description",
            "created": "2018-05-09T10:19:59.363Z",
            "public_api_key": "sensorlab:application:cc7fddc2434a1773a360c84b1be71b16"
        }
    ],
    "count": 27,
    "pages": 1
}
```


* **Query Parameters**

    
    * **page** – used for pagination. Default is 1.


    * **name** – search by name.


    * **sort** – sorting parameter.


    * **show_deleted** – if true - show deleted only applications.

    You must provide string with sorting field name and sorting type like this:

    > type,asc

    Available fields:


            * name - sort by creation date


            * created - sort by measurement type

    Available sort types:


            * asc - Ascending sort


            * desc - Descending sort




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


    * [422 Unprocessable Entity](http://tools.ietf.org/html/rfc4918#section-11.2) – Validation error.


**Possible validation errors and codes:**


* code=1 - page must be an integer

**NOTE**: Available for:


* User token
