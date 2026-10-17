---
description: Allows to access WebView.
icon: globe-pointer
---

# webview

{% code overflow="wrap" %}
```luau
 webview.create([title: string]): webview_instance | nil
```
{% endcode %}

Create a new webview instance. Returns `nil` if webview runtime wasn't found.

If `title` wasn't specified, uses web page title.

User data directory used by the webview is `SOFTWARE_ROOT_DIR\Cache\WebView`.

Can only be called from `draw` callback.

