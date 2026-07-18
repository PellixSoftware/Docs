---
description: Allows to make network HTTP(s) requests.
icon: paper-plane
---

# http

**http\_options**

```luau
method: string -- HTTP request method (GET/POST/etc.)
headers: table<string, string> -- Request headers (key = value)
body: string -- Request body
max_redirects: number -- Maximum amount of redirects
headers_in_body: boolean -- Should headers be appended to the response body?
```



**http\_response**

```luau
status: number -- Status code 
body: string -- Response body
connect_time: number -- Time spent to connect to the host
http_version: number -- Http version number used to connect (1/2/3)
redirect_count: number -- Amount of redirects
```



{% code overflow="wrap" %}
```luau
http.request(url: string [, options: http_options, callback: (response: http_response | nil)]): http_response | nil
```
{% endcode %}

Performs an HTTP(s) request on the given url with options. If callback is specified this operation is asynchronous.

If no options are specified makes a simple GET request.

