Update sensor
~~~~~~~~~~~~~

.. http:patch:: /api/v1/sensors/(id)

    **Request**:

    .. sourcecode:: http

        PATCH /api/v1/sensors/acdfab8a-9a18-11e8-9eb6-529269fb1459 HTTP/1.1
        Host: staging.sensorlab.io
        Content-type: application/json

        {
            "name": "Updated Sensor ID",
            "application": "b2a2fdb0-9a18-11e8-9eb6-529269fb1459"
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

    :<json string name: Name for your sensor.
    :<json string application: Application's ID to connect sensor too.
    :<json boolean is_public: Set sensor public or private (true or false).

    :reqheader Authorization: Bearer token from authentication.
    :reqheader Content-Type: application/json
    :statuscode 200: No errors, will return result with applications list.
    :statuscode 401: User is not authorized - token is incorrect or outdated.
    :statuscode 404: Sensor not found.
    :statuscode 422: Validation error.

    **Possible validation errors and codes:**

    - code=1 - field=name - Please, provide name field. This cannot be empty
    - code=2 - field=application - `application` must be correct UUID format
    - code=3 - field=is_public - `is_public` must be correct boolean format

.. note::
    Available for:

    - User token
    - Application token

    Application token will have access only to sensors assigned to this application.