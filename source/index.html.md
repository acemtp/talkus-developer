---
title: Talkus Developer Documentation

toc_footers:
  - <a href='https://talkus.io'>Talkus Homepage</a>
  - <a href='http://faq.talkus.io'>Talkus Faq</a>
  - <a href='https://github.com/acemtp/talkus-developer/blob/master/source/index.html.md'>Report an issue in this doc</a>

includes:
  - api
  - commands
  - webhooks
  - javascript-functions
  - external-channel

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
