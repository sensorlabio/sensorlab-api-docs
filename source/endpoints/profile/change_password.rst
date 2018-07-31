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

    **Validation error response**

    .. sourcecode:: http

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


    **Unauthorized response**

    .. sourcecode:: http

        HTTP/1.1 401 Unauthorized

        Unauthorized

    :reqheader Authorization: "Bearer: {token}" from authentication.
    :reqheader Content-Type: application/json
    :statuscode 200: No errors.
    :statuscode 401: Wrong authorization token
    :statuscode 422: Validation error.

    **Possible validation errors and codes:**

    - `code=1` - `Please, provide name field. This cannot be empty`.
    - `code=2` - `You must provide new password.`
    - `code=3` - `You must provide new password check.`
    - `code=4` - `Password is incorrect. Please provide you current password.`
    - `code=5` - `Both "new password" and "new password check" values must be equal.`

.. note::
    Available for:

    - User token