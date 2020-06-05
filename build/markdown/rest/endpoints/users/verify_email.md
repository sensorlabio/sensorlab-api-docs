# Email Verification

**NOTE**: Upon user signup email will be sent to user with link to verify email address.
This link will have “token” parameter. You can use this endpoint to verify email.


### POST (/api/v1/users/verify_email()
**Request**:

```
POST /api/v1/users/verify_email HTTP/1.1
Host: staging.sensorlab.io
Content-type: application/json

{
  "verification_token": "944c5668682e40d8209e129480f02f5ba3cf14174ad349a82a25615cdecb23077137a581843a267fd14b3c81a1d656c68a9cc1667d3de742ce625abc1e6d920c"
}
```

**Success response**:

```
HTTP/1.1 200 OK
Content-type: application/json

{
  "success": true,
  "code": 100,
  "message": "Your email is now verified."
}
```

**No verification token provided**

```
HTTP/1.1 200 OK
Content-type: application/json

{
  "success": false,
  "code": 1,
  "message": "You must provide verification token."
}
```

**Verification token is incorrect or outdated**

```
HTTP/1.1 200 OK
Content-type: application/json

{
  "success": false,
  "code": 2,
  "message": "Email verification token is incorrect or outdated."
}
```


* **Request Headers**

    
    * [Content-Type](https://tools.ietf.org/html/rfc7231#section-3.1.1.5) – application/json



* **Status Codes**

    
    * [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – No errors.
