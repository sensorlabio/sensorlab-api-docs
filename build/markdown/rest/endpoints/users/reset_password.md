# Reset password


### POST (/api/v1/users/reset_password()
**Request**:

```
POST /api/v1/users/reset_password HTTP/1.1
Host: staging.sensorlab.io
Content-type: application/json

{
  "token": "a19a7dbc5504d95775cf5caf17c71032fba7329facfb5a455cbf1326a57806f61569eb8b3912b1429387b04b5252f4a045839ac80319ef732c37f1f78870784b"
  "password": "new_password",
  "password_check": "new_password"
}
```

**Success response**:

```
HTTP/1.1 200 OK
Content-type: application/json

{
  "success": true,
  "code": 100,
  "message": "Password updated."
}
```

**Token is not provided**

```
HTTP/1.1 200 OK
Content-type: application/json

{
    "success": false,
    "code": 1,
    "message": "You must provide token."
}
```

**Token is incorrect or outdated**

```
HTTP/1.1 200 OK
Content-type: application/json

{
    "success": false,
    "code": 2,
    "message": "Token is incorrect or already has been used."
}
```

**Provided passwords are not equal**

```
HTTP/1.1 200 OK
Content-type: application/json

{
    "success": false,
    "code": 3,
    "message": "Both \"password\" and \"password_check\" fields must be equal."
}
```


* **Request Headers**

    
    * [Content-Type](https://tools.ietf.org/html/rfc7231#section-3.1.1.5) – application/json



* **Status Codes**

    
    * [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – No errors.
