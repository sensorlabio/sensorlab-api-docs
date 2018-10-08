Check reset password token
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. note::
    Use this endpoint to pre-check that token is correct before trying to reset password

.. http:post:: /api/v1/users/reset_password/check

    **Request**:

    .. sourcecode:: http

        POST /api/v1/users/reset_password/check HTTP/1.1
        Host: staging.sensorlab.io
        Content-type: application/json

        {
          "token": "a19a7dbc5504d95775cf5caf17c71032fba7329facfb5a455cbf1326a57806f61569eb8b3912b1429387b04b5252f4a045839ac80319ef732c37f1f78870784b"
        }

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
          "success": true,
          "code": 100,
          "message": "Token is correct."
        }

    **Token is not provided**

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "success": false,
            "code": 1,
            "message": "You must provide token."
        }

    **Token is incorrect or outdated**

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "success": false,
            "code": 2,
            "message": "Token is incorrect or already has been used."
        }

    :reqheader Content-Type: application/json
    :statuscode 200: No errors.