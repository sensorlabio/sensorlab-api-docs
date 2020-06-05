Basic information
=================

REST API provides number of endpoints to work with sensorlab.io

You work with your sensors, applications, measurements, etc via REST API using your own user credentials or your can work
with sensors and measurements using application credentials.

REST API exchange information with JSON objects. Result depends on endpoint type and HTTP status.

Here are the main HTTP statuses you should handle:

- `200` - Normal response. Result depends on endpoint type.

- `400` - This status will appear if your JSON object in request is malformed.

Example:

    .. sourcecode:: http

        HTTP/1.1 400 Bad Request
        Content-Type: applications/json

        {
            "success": false,
            "code": 400,
            "message": "Please, check data you send and try again"
        }

- `401` - REST API returns this status if there's problem with authentication with token or authentication credentials are wrong.

Example:

    .. sourcecode:: http

        HTTP/1.1 401 Unauthorized
        Content-Type: applications/json

        {
            "success": false,
            "code": 401,
            "message": "Unauthorized"
        }

- `403` - REST API returns this status if there's no access to the requested object (for example, sensor is not public and you are trying to access it using only public api key)

Example:

    .. sourcecode:: http

        HTTP/1.1 403 Forbidden
        Content-Type: text/javascript

        {
            "success": false,
            "code": 403,
            "message": "Sensor measurements are not public"
        }

- `404` - REST API will return this error if there's no requested endpoint or object for this endpoint doesn't exist.

You can identify is it missing endpoint or object by parameter `type`.
In case of `object` value for `type` there will be `object_type` field that will help to detect what type of object is missing.

Missing endpoint example:

    .. sourcecode:: http

        HTTP/1.1 404 Not Found
        Content-Type: applications/json

        {
            "success": false,
            "code": 404,
            "type": "endpoint",
            "message": "Endpoint doesn't exist"
        }

Missing object example:

    .. sourcecode:: http

        HTTP/1.1 404 Not Found
        Content-Type: applications/json

        {
            "success": false,
            "code": 404,
            "type": "object",
            "object_type": "sensor",
            "message": "Sensor not found"
        }

Object types available:

        - user
        - sensor
        - application
        - measurement
        - sensor_alert

- `422` - validation error. Some endpoints require correct request params or correct fields in JSON object.

Some fields can be required or require special format. All those errors will be available in the `errors` field.

Example:

    .. sourcecode:: http

        HTTP/1.1 422 Unprocessable Entity
        Content-Type: applications/json

        {
            "success": false,
            "code": 422,
            "message": "There are validation errors found.",
            "errors": [
                {
                    "code": 3,
                    "message": "`threshold_type` is required",
                    "param": "threshold_type"
                }
            ]
        }

- `500` - If there are any problems with API you will get response with this status.

Example:

    .. sourcecode:: http

        HTTP/1.1 500 Internal Server Error
        Content-Type: applications/json

        {
            "error": true,
            "status": 500,
            "message": "Internal error, please, try again"
        }