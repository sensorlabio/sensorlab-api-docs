Get application authentication token
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. http:post:: /api/v1/auth/application/token

    **Request**:

    .. sourcecode:: http

        POST /api/v1/auth/application/token HTTP/1.1
        Host: staging.sensorlab.io
        Content-type: application/json

        {
          "public_api_key": "sensorlab:application:62fa02f38ff6100dbbd1cdff2339ccf3",
          "private_api_key": "9a57d7e74ead4ec610539dcf5124db0d"
        }

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI1YWJhMTY1ZTQ4MmJlYzJkZjg4N2M2YTMiLCJpYXQiOjE1MjIxNDY0MTYsImV4cCI6MTUyMjIzMjgxNn0.-6kJm1Rbd_SPbuwc6kg6FHuJnUii8FtKI9DXR0J5-Ig"
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

    **Validation error response**

    .. sourcecode:: http

        HTTP/1.1 422 OK
        Content-type: application/json

        {
            "success": false,
            "code": 422,
            "message": "There are validation errors found.",
            "errors": [
                {
                    "code": 1,
                    "message": "Please, provide public api key. This cannot be empty.",
                    "param": "public_api_key"
                }
            ]
        }

    :reqheader Content-Type: application/json
    :statuscode 200: No errors.
    :statuscode 401: Wrong authorization credentials
    :statuscode 422: Validation error.

    **Possible validation errors and codes:**

    - code=1 - field=public_api_key - Please, provide public api key. This cannot be empty
    - code=2 - field=private_api_key - Please, provide private api key. This cannot be empty

.. note:: Not every endpoint is available for application token. You will find more information in the endpoint description itself.