---
description: WebView instance type.
icon: globe-www
---

# webview\_instance

#### Almost every single function here works only in the [draw](../callbacks/draw.md) callback.



{% code overflow="wrap" %}
```luau
webview_instance:navigate(url: string)
```
{% endcode %}

Navigate to the specified url.



{% code overflow="wrap" %}
```luau
webview_instance:set_html(content: string)
```
{% endcode %}

Set a html page content.



{% code overflow="wrap" %}
```luau
webview_instance:set_window_bounds(x: number, y: number, w: number: h: number)
```
{% endcode %}

Change bounds of the window containing a webview.



{% code overflow="wrap" %}
```luau
webview_instance:set_visible(visible: false)
```
{% endcode %}

Change instance visibility state.



{% code overflow="wrap" %}
```luau
webview_instance:set_input(input: boolean)
```
{% endcode %}

Change whether webview accepts inputs or not.



{% code overflow="wrap" %}
```luau
webview_instance:set_closeable(closeable: boolean)
```
{% endcode %}

Make it possible for a user to close a webview with mouse (changes it's visibility).



{% code overflow="wrap" %}
```luau
webview_instance:set_topmost(topmost: boolean)
```
{% endcode %}

Make webview instance render even when menu is not opened.



{% code overflow="wrap" %}
```luau
webview_instance:get_bounds(): left, right, top, bottom
```
{% endcode %}

Get webview bounds inside a window (absolute coordinates).



{% code overflow="wrap" %}
```luau
webview_instance:get_window_bounds(): left, right, top, bottom
```
{% endcode %}

Get window bounds which contains a webview.



{% code overflow="wrap" %}
```luau
webview_instance:eval_js(content: string [, callback: function(err: string | nil, res: string | nil) ]): boolean
```
{% endcode %}

Evaluate a javascript code in the webview.

Returns `true` when was submitted successfully.

`err` is non-nil only on internal error.

Works only when executed on `ready` state.



{% code overflow="wrap" %}
```luau
webview_instance:add_oncreate_js(content: string)
```
{% endcode %}

Add a script to be executed on document creation. Works only when executed on `ready` state.





#### Properties:

{% code overflow="wrap" %}
```luau
view.core_address: uintptr_t
```
{% endcode %}

Address of the core `ICoreWebView2` interface.



{% code overflow="wrap" %}
```luau
view.controller_address: uintptr_t
```
{% endcode %}

Address of the controller `ICoreWebView2Controller2` interface.



{% code overflow="wrap" %}
```luau
view.state: 'creating'|'ready'|'failed'|'?'
```
{% endcode %}

State of the the webview.



{% code overflow="wrap" %}
```luau
visible: boolean
```
{% endcode %}

If webview is currently visible.



{% code overflow="wrap" %}
```luau
hovered: boolean
```
{% endcode %}

If webview is currently hovered.



{% code overflow="wrap" %}
```luau
window_hovered: boolean
```
{% endcode %}

If webview container window is currently hovered.



{% code overflow="wrap" %}
```luau
title: string
```
{% endcode %}

Current webview `document.title` value.
