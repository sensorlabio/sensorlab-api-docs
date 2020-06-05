# Authentication endpoints


* Get user authentication token


* Get application authentication token


There are two main authentication endpoints - one for user (you) and one for applications.

You will retrieve a JSON Web Token (JWT) which you will pass later on to other endpoints.

With user auth you can work with most endpoints - your profile, application, sensors, measurements. For example, you
can create you own custom dashboard with any programming language you prefer and use you email and password to access that dashboard.

Application authentication has access to sensors, connected to application and measurements of those sensors.

You can create as many different applications you want and use only Public and Private API keys to authenticate applications -
absolutely no need to pass email or password from your account.
