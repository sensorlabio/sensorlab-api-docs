User Signup
~~~~~~~~~~~

.. http:post:: /api/v1/users/signup

    **Request**:

    .. sourcecode:: http

        POST /api/v1/users/signup HTTP/1.1
        Host: staging.sensorlab.io
        Content-type: application/json

        {
          "email": "test@email.com",
          "password": "password",
          "password_check": "password"
        }

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "success": true,
            "code": 100,
            "message": "User has been successfully signed up."
        }

    **Email is not provided error response**

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "success": false,
            "code": 1,
            "message": "Please, provide email. This cannot be empty"
        }

    **Incorrect email format response**

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "success": false,
            "code": 2,
            "message": "Please, provide correct email."
        }

    **Email is not unique and exists in the database**

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "success": false,
            "code": 3,
            "message": "Someone already registered this email."
        }

    **One or both password fields are empty**

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "success": false,
            "code": 4,
            "message": "Please provide both \"password\" and \"password_check\" fields. They cannot be empty."
        }

    **Passwords are not equal**

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "success": false,
            "code": 5,
            "message": "Both \"password\" and \"password_check\" fields must be equal."
        }

    :reqheader Content-Type: application/json
    :statuscode 200: No errors.