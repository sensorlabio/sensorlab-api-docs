Get user authentication token
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. http:post:: /api/v1/auth/user/token

    **Request**:

    .. sourcecode:: http

        POST /api/v1/auth/user/token HTTP/1.1
        Host: staging.sensorlab.io
        Content-type: application/json

        {
          "email": "test@email.com",
          "password": "password"
        }

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI1YWJhMTY1ZTQ4MmJlYzJkZjg4N2M2YTMiLCJpYXQiOjE1MjIxNDY0MTYsImV4cCI6MTUyMjIzMjgxNn0.-6kJm1Rbd_SPbuwc6kg6FHuJnUii8FtKI9DXR0J5-Ig"
        }

    :reqheader Content-Type: application/json
    :statuscode 200: No errors.
    :statuscode 401: Wrong authorization credentials
    :statuscode 422: Validation error.

    **Possible validation errors and codes:**

    - code=1 - field=email - Please, provide email. This cannot be empty
    - code=2 - field=password - Please, provide password to get token
    - code=3 - field=email - Email is invalid
    - code=4 - field=email - User does not exist
    - code=5 - field=email - Email is not verified
    - code=6 - field=password - Password is incorrect

.. note:: Not every endpoint is available for application token. You will find more information in the endpoint description itself.