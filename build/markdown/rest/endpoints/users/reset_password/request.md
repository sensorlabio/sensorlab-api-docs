# Request password reset


### POST (/api/v1/users/reset_password/request()
**Request**:

```
POST /api/v1/users/reset_password/request HTTP/1.1
Host: staging.sensorlab.io
Content-type: application/json

{
  "email": "test@test.com"
}
```

**Success response**:

```
HTTP/1.1 200 OK
Content-type: application/json

{
  "success": true,
  "code": 100,
  "message": "Password reset link has been sent to your email"
}
```

**Email is not provided**

```
HTTP/1.1 200 OK
Content-type: application/json

{
    "success": false,
    "code": 1,
    "message": "Please, provide an email to reset password"
}
```

**User not found**

```
HTTP/1.1 200 OK
Content-type: application/json

{
    "success": false,
    "code": 2,
    "message": "There's no such user in the database"
}
```

**Too much password request. Right now it’s possible to request password reset 3 time an hour.**

```
HTTP/1.1 200 OK
Content-type: application/json

{
    "success": false,
    "code": 3,
    "message": "Too much password reset requests"
}
```


* **Request Headers**

    
    * [Content-Type](https://tools.ietf.org/html/rfc7231#section-3.1.1.5) – application/json



* **Status Codes**

    
    * [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – No errors.
