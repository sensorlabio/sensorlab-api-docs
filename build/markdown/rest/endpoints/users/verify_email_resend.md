# Resend Email Verification

**NOTE**: In rare occasions email with verification link can be lost.
In this case user can request email with verification code once more.


### POST (/api/v1/users/verify_email/resend()
**Request**:

```
POST /api/v1/users/verify_email/resend HTTP/1.1
Host: staging.sensorlab.io
Content-type: application/json

{
  "email": "test@email.com"
}
```

**Success response**:

```
HTTP/1.1 200 OK
Content-type: application/json

{
  "success": true,
  "code": 100,
  "message": "Sent new verification email."
}
```

**No email provided**

```
HTTP/1.1 200 OK
Content-type: application/json

{
  "success": false,
  "code": 1,
  "message": "Please, provide email. This cannot be empty."
}
```

**Invalid email format**

```
HTTP/1.1 200 OK
Content-type: application/json

{
  "success": false,
  "code": 2,
  "message": "Please, provide correct email."
}
```

**No such user**

```
HTTP/1.1 200 OK
Content-type: application/json

{
  "success": false,
  "code": 3,
  "message": "User with this email does not exist."
}
```

**User email is verified**

```
HTTP/1.1 200 OK
Content-type: application/json

{
  "success": false,
  "code": 4,
  "message": "This email is verified already."
}
```

**Too much requests**

```
HTTP/1.1 200 OK
Content-type: application/json

{
  "success": false,
  "code": 5,
  "message": "Too much requests for this email. Please try again later."
}
```


* **Request Headers**

    
    * [Content-Type](https://tools.ietf.org/html/rfc7231#section-3.1.1.5) – application/json



* **Status Codes**

    
    * [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – No errors.
