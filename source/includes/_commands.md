# Commands

On [Command page](https://app.talkus.io/admin/commands), you can create dot commands. A dot command always starts with a dot (.) and are executed only when typed inside a visitor channel (where you answer to your visitor). When you type a dot command, the visitor doesn't see it but he'll see the result of the command, except if the result starts with a double dot (..), in this case, the result will be only be visible to the agent.

## Post a message

Most basic form of a dot command, when the agent execute the command, it displays the message entered in `Value`.

Useful to create canned responses.

## Execute a Server command

Call a webhook on your server when the dot command is executed by the agent. It's a `POST` requests on your server containing a JSON with all the information you need, agent who executed the command, on which visitor, the discussion.

You can reply to this `POST` either with:

```json
"I am a test message"
```

- a string, in this case, the string will be pushed in the discussion and so it'll be displayed to the visitor. If you don't want the visitor sees it, start the string with a double dot (..).

```json
{
    "text": "I am a test message",
    "attachments": "[{ \"text\": \"And here's an attachment!\" }]"
}
```

- a JSON object in the [Slack format](https://api.slack.com/docs/messages/builder). So you can craft advanced messages with attachement and all other Slack formatting features.

For example, you can create a command `.ban` that will call your server and your server will ban the visitor on your product.

Another example, for an e-commerce website, can be `.status` that will find the status of the latest visitor order and returns it to the agent and / or visitor.

## Execute a Client command

Execute the javascript code you entered in `Value` input in the browser of the visitor.

```javascript
window.location.href = 'http://google.com';
```

If you use this code in a command called `.google`, when executed, it'll redirect the visitor to google homepage.

## Alias to another command

Alias a command with another one. For example by default, you have alias of `end` with `e` so instead of typing `.end` to close a discussion, you can just type `.e`.
