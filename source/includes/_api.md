# API

## Authorization

```shell
curl -X POST \
  --user '1234562a44147d1b3b3bad556784beae:' \
  https://app.talkus.io/api/test
```

When you call Talkus endpoints, you need to add the `Authorization` header using the `Basic` authentication type. The login will be the API Key you'll find in the [integration page ](https://app.talkus.io/admin/integrations) and the password will be empty.

<aside class="notice">
Don't forget to add the semicolon (`:`) after the login in curl command.
</aside>

## Send Message

> Send a message from a new visitor (the `visitorId` will be created):

```shell
curl -X POST \
  --user '1234562a44147d1b3b3bad556784beae:' \
  -H 'Content-Type: application/json' \
  -d '{ "text": "hello there!" }' \
  https://app.talkus.io/api/visitor/message
```

> The above command returns JSON structured like this:

```json
{
  "ok": "true",
  "visitorId": "5rTdrc986vWm12"
}
```

> Send a message from an existing visitor:

```shell
curl -X POST \
  --user '1234562a44147d1b3b3bad556784beae:' \
  -H 'Content-Type: application/json' \
  -d '{ "visitorId": "5rTdrc986vWm12", "text": "I need your help!" }' \
  https://app.talkus.io/api/visitor/message
```

> The above command returns JSON structured like this:

```json
{
  "ok": "true",
  "visitorId": "5rTdrc986vWm12"
}
```

> If there's an error, it'll be like this:

```json
{
  "ok": "false",
  "error": "No text"
}
```

`POST https://app.talkus.io/api/visitor/message`

Post a new visitor message to an exiting visitor (if you set the `visitorId`) or to a new visitor (in this case, the result will contains the `visitorId`).

This entrypoint is useful if you want to add a new channel (another SMS provider for example). When your external provider sends you a message coming from a visitor's phone for example, call this entrypoint to create or update a ticket into Talkus (and so in Slack) with the visitor's message.

If it's a new visitor (you don't have visitorId), call the entrypoint without `visitorId` so we'll create a new one for you and return it. Then you store in your database the visitorId and phone number (or any other id you want) so next time this visitor sends you a message, you can provide the `visitorId` and Talkus will add the message to this existing visitor.

### Parameters

Parameter | Options | Description
--------- | ------- | -----------
text | mandatory | The visitor's message.
visitorId | optional | The id of the visitor. If not set, it'll create a new visitor and returns the new id.
type | optional | The name or emoji (using long emoji format like `:poop:`) that will be displayed on the ticket.
identity | optional | A JSON object that containing information of the visitor. [More information...](?javascript#init)

