---
title: Line Notification with IFTTT in 5 min
date: 2018-06-27 16:48:33
tags: [Line, IFTTT, Webhook, Line notify]
---

1. Go to create my applet page in [IFTTT](https://ifttt.com/create)
1. Choose `this > Webhooks > Receive a web request`
1. Set any `event name` and click `create trigger`
1. Choose `that > Line > Send message`
1. Set `Message` as `value1`
    {% asset_img "sendMessage.png" %}
1. Go to [Webhooks](https://ifttt.com/maker_webhooks)
1. Click `Documentation` on the top right corner
1. Fill up the `event name` and `value1` then try the `curl` example on the page
1. You could see a message deliver to LINE immdiately!
