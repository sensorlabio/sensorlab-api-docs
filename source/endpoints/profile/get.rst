Get profile
~~~~~~~~~~~

.. http:post:: /api/v1/profile

    :synopsis: Get user profile. This can also be used to check authorization token.

    **Request**:

    .. sourcecode:: http

        GET /api/v1/profile HTTP/1.1
        Host: staging.sensorlab.io
        Content-type: application/json

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "email": "test@test.com"
        }

    **Unauthorized response**

    .. sourcecode:: http

        HTTP/1.1 401 Unauthorized
        Content-Type: applications/json

        {
            "success": false,
            "code": 401,
            "message": "Unauthorized"
        }

    :reqheader Authorization: "Bearer: {token}" from authentication.
    :reqheader Content-Type: application/json
    :statuscode 200: No errors.
    :statuscode 401: Wrong authorization token

.. note::
    Available for:

    - User token