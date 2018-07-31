Update sensor
~~~~~~~~~~~~~

.. http:patch:: /api/v1/sensors/(id)

    **Request**:

    .. sourcecode:: http

        PATCH /api/v1/sensors/5ab8b113fc10152c70cdeb65 HTTP/1.1
        Host: staging.sensorlab.io
        Content-type: application/json

        {
            "name": "Updated Sensor ID",
            "application": "5b4f3e3d8ef5ae0a1473e1da"
        }

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "success": true,
            "code": 100,
            "message": "Sensor updated.",
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

    :<json string name: Name for your sensor.
    :<json string application: Application's ID to connect sensor too.

    :reqheader Authorization: Bearer token from authentication.
    :reqheader Content-Type: application/json
    :statuscode 200: No errors, will return result with applications list.
    :statuscode 401: User is not authorized - token is incorrect or outdated.
    :statuscode 404: Sensor not found.
    :statuscode 422: Validation error.

    **Possible validation errors and codes:**

    - `code=1` - `Please, provide name field. This cannot be empty`.

.. note::
    Available for:

    - User token
    - Application token

    Application token will have access only to sensors assigned to this application.