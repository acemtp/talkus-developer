---
title: Talkus Developer Documentation

language_tabs:
  - shell

toc_footers:
  - <a href='https://talkus.io'>Talkus Homepage</a>
  - <a href='http://faq.talkus.io'>Talkus Faq</a>
  - <a href='https://github.com/acemtp/talkus-developer/blob/master/source/index.html.md'>Report an issue in this doc</a>

includes:

search: true
---

# Introduction

Welcome to the Talkus Developer Documentation.

Talkus is very customizable and open. You'll find on this page all the API and integration you can do with Talkus.

# Definitions

## Agent

An agent is an user of your company that is inside your Slack team and handle support requests.

## Visitor

A visitor is one of your users that is not in Slack and contact you by a Talkus channel (email, live chat, sms, twitter...).

## Visitor Channel

A Visitor Channel is a Slack channel where you interact with a specific visitor. It's *not* the `#talkus-support`. Visitor Channel names always start with `#z-`.

# Commands

On [Command page](https://app.talkus.io/admin/commands), you can create dot commands. A dot command always starts with a dot (.) and are executed only when typed inside a visitor channel (where you answer to your visitor). When you type a dot command, the visitor doesn't see it but he'll see the result of the command, except if the result starts with a double dot (..), in this case, the result will be only be visible to the agent.

## Post a message

Most basic form of a dot command, when the agent execute the command, it displays the message entered in `Value`.

Useful to create canned responses.

## Execute a Server command

Call a webhook on your server when the dot command is executed by the agent. It's a `POST` requests on your server containing a JSON with all the information you need, agent who executed the command, on which visitor, the discussion.

You can reply to this `POST` either with:

- a string, in this case, the string will be pushed in the discussion and so it'll be displayed to the visitor. If you don't want the visitor sees it, start the string with a double dot (..).

```json
{
    "text": "I am a test message http://slack.com",
    "attachments": [
        {
            "text": "And here's an attachment!"
        }
    ]
}
```

- a JSON object in the [Slack format](https://api.slack.com/docs/messages/builder). So you can craft advanced messages with attachement and all other Slack formatting features.

For example, you can create a command `.ban` that will call your server and your server will ban the visitor on your product.

Another example, for an e-commerce website, can be `.status` that will find the status of the latest visitor order and returns it to the agent and / or visitor.

## Execute a Client command

Execute the javascript code you entered in `Value` input in the browser of the visitor.

```javscript
  window.url.location = 'http://google.com';
```

If you use this code in a command called `.google`, when executed, it'll redirect the visitor to google homepage.

## Alias to another command

Alias a command with another one. For example by default, you have alias of `end` with `e` so instead of typing `.end` to close a discussion, you can just type `.e`.

# Webhooks

# Javascript functions

With the live chat plugin, you have access to a set of Talkus functions to control the plugin.

```javscript
  talkus('commandName');
```

## talkus('init')


