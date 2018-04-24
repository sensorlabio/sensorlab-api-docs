Resend Email Verification
~~~~~~~~~~~~~~~~~~~~~~~~~

.. note::
        In rare occasions email with verification link can be lost.
        In this case user can request email with verification code once more.

.. http:post:: /api/v1/users/verify_email/resend

    **Request**:

    .. sourcecode:: http

        POST /api/v1/users/verify_email/resend HTTP/1.1
        Host: staging.sensorlab.io
        Accept: application/json

        {
          "email": "test@email.com"
        }

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: text/javascript

        {
          "success": true,
          "code": 100,
          "message": "Sent new verification email."
        }

    **No email provided**

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: text/javascript

        {
          "success": false,
          "code": 1,
          "message": "Please, provide email. This cannot be empty."
        }

    **Invalid email format**

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: text/javascript

        {
          "success": false,
          "code": 2,
          "message": "Please, provide correct email."
        }

    **No such user**

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: text/javascript

        {
          "success": false,
          "code": 3,
          "message": "User with this email does not exist."
        }

    **User email is verified**

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: text/javascript

        {
          "success": false,
          "code": 4,
          "message": "This email is verified already."
        }

    **Too much requests**

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: text/javascript

        {
          "success": false,
          "code": 5,
          "message": "Too much requests for this email. Please try again later."
        }

    :reqheader Content-Type: application/json
    :statuscode 200: No errors.