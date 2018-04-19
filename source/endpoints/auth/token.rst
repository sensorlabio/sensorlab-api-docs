Get authentication token
~~~~~~~~~~~~~~~~~~~~~~~~

.. http:post:: /api/v1/auth/token

    **Request**:

    .. sourcecode:: http

        POST /api/v1/auth/token HTTP/1.1
        Host: staging.sensorlab.io
        Accept: application/json

        {
          "email": "test@email.com"
          "password": "password",
        }

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: text/javascript

        {
            "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI1YWJhMTY1ZTQ4MmJlYzJkZjg4N2M2YTMiLCJpYXQiOjE1MjIxNDY0MTYsImV4cCI6MTUyMjIzMjgxNn0.-6kJm1Rbd_SPbuwc6kg6FHuJnUii8FtKI9DXR0J5-Ig"
        }

    **Unauthorized response**

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: text/plain

        Unauthorized

    :reqheader Content-Type: application/json
    :statuscode 200: No errors.
    :statuscode 401: Wrong authorization credentials