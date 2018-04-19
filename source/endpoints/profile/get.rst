Get profile
~~~~~~~~~~~

.. http:post:: /api/v1/profile

    :synopsis: Get user profile. This can also be used to check authorization token.

    **Request**:

    .. sourcecode:: http

        GET /api/v1/profile HTTP/1.1
        Host: staging.sensorlab.io
        Accept: application/json

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: text/javascript

        {
            "email": "test@test.com"
        }

    **Unauthorized response**

    .. sourcecode:: http

        HTTP/1.1 401 Unauthorized
        Content-Type: text/plain

        Unauthorized

    :reqheader Authorization: "Bearer: {token}" from authentication.
    :reqheader Content-Type: application/json
    :statuscode 200: No errors.
    :statuscode 401: Wrong authorization token