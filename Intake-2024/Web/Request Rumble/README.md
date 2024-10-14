## Request Rumble
You can view the source code for this challenge at: https://github.com/peterw18/Intake24

### Introduction

This is a very basic Parameter Manipulation vulnerability.

According to the error messages, the JavaScript running on the client version of the website requires the password to be less than 12 characters.
However, if one enters a password less than 12 characters the PHP running server-side throws an error, requesting a password longer than 12 characters.

Therefore, the password must be changed post JS-processing, but before it reaches the backend (or we must send a request to the backend directly).

### Using Burp Suite
Burp Suite is software that, among other features, allows one to edit a HTTP request after it has been sent by the browser.

1. Ensure that the Burp Suite Proxy is correctly set up in browser, and enabled in-app.
2. Enter a password into the form that meets the JS requirements (i.e. less than 12 characters long)
3. When you click submit, the request appears in the **Proxy** window of Burp Suite, and you can view and edit it.
4. At this point, change the *password* variable to have a value longer than 12 characters (this can be found, usually, at the bottom of the request since it is POST data)
5. The PHP will return the flag since the password is longer than 12 characters

### Using Curl
Curl is a command line tool and library for transferring data with URLs. 

It is possible to directly issue a request to the *login.php* file using curl:
```
curl -X POST https://xxxxxxxx-request-rumble-web.chall.warwickcybersoc.com/login.php -d "username=admin&password=morethantwelve"
```
This directly bypasses the JS verification and so the password only needs to be longer than 12 characters to retrieve the flag.