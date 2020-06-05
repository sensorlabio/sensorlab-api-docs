# Change password


### POST (/api/v1/profile/change_password()

* **Synopsis**

    Change password for authenticated user.


**Request**:

```
GET /api/v1/profile/change_password HTTP/1.1
Host: staging.sensorlab.io
Content-type: application/json

{
    "old_password": "old_password",
    "new_password": "new_password",
    "new_password_check": "new_password"
}
```

**Success response**:

```
HTTP/1.1 200 OK
Content-type: application/json

{
    "success": true,
    "code": 100,
    "message": "New password is set for user."
}
```

**Validation error response**

```
HTTP/1.1 422 OK
Content-type: application/json

{
    "success": false,
    "code": 422,
    "message": "There are validation errors found.",
    "errors": [
        {
            "code": 1,
            "message": "Please, provide old password. This cannot be empty.",
            "param": "old_password"
        },
        {
            "code": 2,
            "message": "You must provide new password.",
            "param": "new_password"
        },
        {
            "code": 3,
            "message": "You must provide new password check.",
            "param": "new_password_check"
        }
    ]
}
```


* **Request Headers**

    
    * [Authorization](https://tools.ietf.org/html/rfc7235#section-4.2) – “Bearer: {token}” from authentication.


    * [Content-Type](https://tools.ietf.org/html/rfc7231#section-3.1.1.5) – application/json



* **Status Codes**

    
    * [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – No errors.


    * [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Wrong authorization token


    * [422 Unprocessable Entity](http://tools.ietf.org/html/rfc4918#section-11.2) – Validation error.


**Possible validation errors and codes:**


* code=1 - field=old_password - Please, provide old password. This cannot be empty


* code=2 - field=new_password - You must provide new password


* code=3 - field=new_password_check - You must provide new password check


* code=4 - field=old_password - Password is incorrect. Please provide you current password


* code=5 - field=new_password_check - Both “new password” and “new password check” values must be equal

**NOTE**: Available for:


* User token
