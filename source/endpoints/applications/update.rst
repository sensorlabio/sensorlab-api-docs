Update application
~~~~~~~~~~~~~~~~~~

.. http:patch:: /api/v1/applications/(id)

    **Request**:

    .. sourcecode:: http

        PATCH /api/v1/applications/f6ca0a08-9a16-11e8-9eb6-529269fb1459 HTTP/1.1
        Host: staging.sensorlab.io
        Content-type: application/json

        {
            "name": "Updated Application Name",
            "description": "Updated Application Description"
        }

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "success": true,
            "code": 100,
            "message": "Application updated.",
        }

    **Unauthorized response**

    .. sourcecode:: http

        HTTP/1.1 401 Unauthorized

        Unauthorized

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
                    "message": "Please, provide name field. This cannot be empty.",
                    "param": "name"
                }
            ]
        }

    :<json string name: Name for your application
    :<json string description: Description for your application

    :reqheader Authorization: Bearer token from authentication.
    :reqheader Content-Type: application/json
    :statuscode 200: No errors, will return result with applications list.
    :statuscode 401: User is not authorized - token is incorrect or outdated.
    :statuscode 404: Application not found.
    :statuscode 422: Validation error.

    **Possible validation errors and codes:**

    - `code=1` - `Please, provide name field. This cannot be empty`.

.. note::
    Available for:

    - User token