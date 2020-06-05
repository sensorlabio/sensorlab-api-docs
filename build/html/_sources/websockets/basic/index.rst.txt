Basic Information
=================

You can receive measurements and alerts in real-time using websockets.

Sensorlab.io websockets is based on `Socket.IO <https://socket.io/>`_.

Socket.IO is mainly used with Javascript, but you can find different implementation for other languages.

Here some links on libraries:

- `Javascript <https://github.com/socketio/socket.io-client>`_
- `Java <https://github.com/socketio/socket.io-client-java>`_
- `C++ <https://github.com/socketio/socket.io-client-cpp>`_

There are 3 main namespaces:

- /measurements - namespace to receive measurements
- /alerts - namespace to receive alerts
- /public - namespace to receiver measurements from public sensors

/measurements and /alerts requires JWT for authentication, /public requires public api key from application.