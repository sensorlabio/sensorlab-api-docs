Change password
~~~~~~~~~~~~~~~

.. http:post:: /api/v1/profile/change_password

    :synopsis: Change password for authenticated user.

    **Request**:

    .. sourcecode:: http

        GET /api/v1/profile/change_password HTTP/1.1
        Host: staging.sensorlab.io
        Content-type: application/json

        {
            "old_password": "old_password",
            "new_password": "new_password",
            "new_password_check": "new_password"
        }

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "success": true,
            "code": 100,
            "message": "New password is set for user."
        }

    **Current password is not provided**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "success": false,
            "code": 1,
            "message": "Please, provide old password. This cannot be empty."
        }

    **Old password is incorrect**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "success": false,
            "code": 2,
            "message": "Password is incorrect. Please provide you current password."
        }

    **New password or password check are not provided**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
           "success": false,
           "code": 3,
           "message": "You must provide both \"new password\" and \"new password check\"."
        }

    **New Password and password check are not equal**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
          "success": false,
          "code": 4,
          "message": "Both \"new password\" and \"new password check\" values must be equal."
        }


    **Unauthorized response**

    .. sourcecode:: http

        HTTP/1.1 401 Unauthorized

        Unauthorized

    :reqheader Authorization: "Bearer: {token}" from authentication.
    :reqheader Content-Type: application/json
    :statuscode 200: No errors.
    :statuscode 401: Wrong authorization token