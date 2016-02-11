# Flask Session Cookies

Flask is a (micro?)framework for writing web servers in Python. It
provides a construct called sessions, which allow you to send
cryptographically signed and serialized cookies between the client
and server. Session cookies are signed using a configuration specified
global variable called SECRET_KEY.

Flask versions 0.9 and lower used the Python pickle library for
serialization. This leaves the server vulnerable to arbitrary code
execution, in the case that the SECRET_KEY is leaked.

### References
 - http://flask.pocoo.org/
 - http://flask.pocoo.org/docs/0.10/quickstart/#sessions
 - http://flask.pocoo.org/docs/0.10/upgrading/#version-0-10
