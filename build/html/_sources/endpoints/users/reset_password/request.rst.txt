Request password reset
~~~~~~~~~~~~~~~~~~~~~~

.. http:post:: /api/v1/users/reset_password/request

    **Request**:

    .. sourcecode:: http

        POST /api/v1/users/reset_password/request HTTP/1.1
        Host: staging.sensorlab.io
        Content-type: application/json

        {
          "email": "test@test.com"
        }

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
          "success": true,
          "code": 100,
          "message": "Password reset link has been sent to your email"
        }

    **Email is not provided**

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "success": false,
            "code": 1,
            "message": "Please, provide an email to reset password"
        }

    **User not found**

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "success": false,
            "code": 2,
            "message": "There's no such user in the database"
        }

    **Too much password request. Right now it's possible to request password reset 3 time an hour.**

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "success": false,
            "code": 3,
            "message": "Too much password reset requests"
        }

    :reqheader Content-Type: application/json
    :statuscode 200: No errors.