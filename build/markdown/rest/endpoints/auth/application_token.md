# Get application authentication token


### POST (/api/v1/auth/application/token()
**Request**:

```
POST /api/v1/auth/application/token HTTP/1.1
Host: staging.sensorlab.io
Content-type: application/json

{
  "public_api_key": "sensorlab:application:62fa02f38ff6100dbbd1cdff2339ccf3",
  "private_api_key": "9a57d7e74ead4ec610539dcf5124db0d"
}
```

**Success response**:

```
HTTP/1.1 200 OK
Content-type: application/json

{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI1YWJhMTY1ZTQ4MmJlYzJkZjg4N2M2YTMiLCJpYXQiOjE1MjIxNDY0MTYsImV4cCI6MTUyMjIzMjgxNn0.-6kJm1Rbd_SPbuwc6kg6FHuJnUii8FtKI9DXR0J5-Ig"
}
```


* **Request Headers**

    
    * [Content-Type](https://tools.ietf.org/html/rfc7231#section-3.1.1.5) – application/json



* **Status Codes**

    
    * [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – No errors.


    * [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Wrong authorization credentials


    * [422 Unprocessable Entity](http://tools.ietf.org/html/rfc4918#section-11.2) – Validation error.


**Possible validation errors and codes:**


* code=1 - field=public_api_key - Please, provide public api key. This cannot be empty


* code=2 - field=private_api_key - Please, provide private api key. This cannot be empty

**NOTE**: Not every endpoint is available for application token. You will find more information in the endpoint description itself.
