Create application
~~~~~~~~~~~~~~~~~~

.. http:post:: /api/v1/applications

    **Request**:

    .. sourcecode:: http

        POST /api/v1/applications HTTP/1.1
        Host: staging.sensorlab.io
        Content-type: application/json

        {
            "name": "Application Name",
            "description": "Application Description"
        }

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "success": true,
            "code": 100,
            "message": "Application created.",
            "application": {
                "id": "7e970572-9a16-11e8-9eb6-529269fb1459",
                "name": "Application Name",
                "description": "Application Description",
                "public_api_key": "sensorlab:application:62fa02f38ff6100dbbd1cdff2339ccf3",
                "private_api_key": "146d3ac9d9900c8151a73ca09b39ca7f"
            }
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
                    "message": "Please, provide name field. This cannot be empty.",
                    "param": "name"
                }
            ]
        }

    :<json string name: Name for your application
    :<json string description: Description for your application

    :>json object application: Application data.
    :>json string application.id: Application ID.
    :>json string application.name: Application name.
    :>json string application.description: Application description.
    :>json string application.public_api_key: Public API key.
    :>json string application.private_api_key: Generated private API key.
        Please note, that Private API Key will appear only once after app creation.
        You will be able to generate new one though.

    :reqheader Authorization: Bearer token from authentication.
    :reqheader Content-Type: application/json
    :statuscode 200: No errors, will return result with applications list.
    :statuscode 401: User is not authorized - token is incorrect or outdated.
    :statuscode 422: Validation error.


    **Possible validation errors and codes:**

    - `code=1` - `Please, provide name field. This cannot be empty`.

.. note::
    Available for:

    - User token