---
title: Talkus Developer Documentation

language_tabs:
  - shell

toc_footers:
  - <a href='https://talkus.io'>Talkus homepage</a>

includes:
  - origin
  - errors

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

Most basic form of a command, when the agent execute the command, it displays the message entered in `Value`.

Useful to create canned responses.

## Execute a Server command

## Execute a Client command

## Alias to another command

Alias a command with another one. For example by default, you have alias of `end` with `e` so instead of typing `.end` to close a discussion, you can just type `.e`.

# Webhooks

# Javascript commands

