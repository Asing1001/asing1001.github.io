---
title: '[GTM] Get the item order in a list'
date: 2019-02-21 11:55:02
tags: [GTM, variables, custom javascript]
---

Google Tag Manager(GTM) is a back office for quickly managing HTML on webpages, basically, it enables the maintainer to do **Everything** on their website without changing the code base. There are three major elements in GTM which are Tag, Variable, and Trigger.

## Tag

A Tag will be triggered by the **Trigger** you set and passing both the system defined variables and the user-defined variables to your Tag, then you could take the action such as sending it to GA or manipulate DOM on your pages.

{% asset_img "tag.png" %}

## Variable

{% asset_img "customjs.png" %}

Other than System defined variables, you could create your own by Javascript:
Select `User-Defined Variables`, then select the type `Custom Javascript`

```js
function() {
  try {
    var element = {{Click Element}}
    var elementClass = {{Element class}}
    if (!element || !elementClass) return
    var selector = '.' + elementClass.split(' ').join('.')
    var list = document.querySelectorAll(selector)
    var order = [].indexOf.call(list, element) + 1
    return order
  } catch (e) {
    if (window.dataLayer.filter(function (obj) {
      return obj.errorMsg === e.message;
    }).length == 0) {
      window.dataLayer.push({
        'event': 'variable error',
        'errorMsg': e.message
      });
    }
  }
}
```

## Trigger

{% asset_img "trigger.png" %}
