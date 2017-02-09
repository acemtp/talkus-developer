
# External channels

Talkus has channels like live chat, email, sms, phone, twitter, facebook but you can add your own channel.

It can be useful to integrate in Talkus your own SMS provider, Snapchat or any other channel you want.

To do that, you need to implement 2 things:

- Code a webhook in your server and add the url in the [integration page ](https://app.talkus.io/admin/integrations) so we can call your server when an agent posts a message (that you need to send to the visitor using your provider).
- Call our [`sendMessage` API](?javascript#send-message) API we can create or update the visitor ticket when you receive a message from your visitor.
