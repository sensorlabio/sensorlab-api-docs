Email Verification
~~~~~~~~~~~~~~~~~~

.. note::
        Upon user signup email will be sent to user with link to verify email address.
        This link will have "token" parameter. You can use this endpoint to verify email.

.. http:post:: /api/v1/users/verify_email

    **Request**:

    .. sourcecode:: http

        POST /api/v1/users/verify_email HTTP/1.1
        Host: staging.sensorlab.io
        Accept: application/json

        {
          "verification_token": "944c5668682e40d8209e129480f02f5ba3cf14174ad349a82a25615cdecb23077137a581843a267fd14b3c81a1d656c68a9cc1667d3de742ce625abc1e6d920c"
        }

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: text/javascript

        {
          "success": true,
          "code": 100,
          "message": "Your email is now verified."
        }

    **No verification token provided**

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: text/javascript

        {
          "success": false,
          "code": 1,
          "message": "You must provide verification token."
        }

    **Verification token is incorrect or outdated**

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: text/javascript

        {
          "success": false,
          "code": 2,
          "message": "Email verification token is incorrect or outdated."
        }

    :reqheader Content-Type: application/json
    :statuscode 200: No errors.