# Javascript functions

```javascript
talkus('commandName');
```

On the client side of the live chat plugin, you can add more javascript code after the Talkus snippet to interact with the plugin.

## Init

> Anonymous initialization:

```javascript
talkus('init', 'yourappid');
```

This function must be the first one to call to initialize Talkus.

You can call it multiple times if you want to update the identity of the visitor. Useful for Single Page Application (SPA).

> Initialization with identification of the visitor:

```javascript
talkus('init', 'yourappid', {
  id: '1234'
  name: 'John Doe',
  email: 'john@doe.com',
  ...
});
```

If your visitor is logged, you often want to provide extra info to Talkus so your agents will be able to know who the visitor is.

To do that, you have to add a *third parameter* to the `talkus('init')` function that contains a javascript object.

This object can contains any keys/values you want but the following keys are used by Talkus to enhance the visitor:

Key | Value | Description
--- | --------- | -----------
id | optional, must be unique | An **unique** string that is linked to this visitor. We'll use it to identify the visitor in our database. So even if the visitor is on another computer or in incognito mode, you'll have all the information about him. **The id must be uniq per visitor**.
name | optional, String | Name of the visitor. We'll use it to name the visitor Slack channel.
email | optional, 'john@doe.com' | Email address of the visitor. If you provide the email, Talkus will not ask the visitor for his email. If Talkus has the email but not the name, it'll use the email to name the Slack channel. An email will be sent if the visitor leave a live chat.
phone | optional, '+33123456789' | Phone number of the visitor. Talkus will use it to send SMS.
picture | optional, 'http://a.co/i.png' | The url to the picture of the visitor avatar. It'll be displayed in your Slack channel.
tag | optional, 'pro' | You can programmatically tag ticket in the html code. Tagging is useful to separate different type of visitors or subdomains. For example, you can create a `pro` tag for pro visitors that needs instant support. All tickets will go to `#zz-pro` Slack channel instead of the default `#talkus-support` where you can set Slack notification to a higher level to never miss them.

You can **add any other fields you want**, they'll be displayed in Slack visitor information. It can be useful for example to display if the visitor uses a free or paying plan, display a link to your backoffice for this visitor, ...

<aside class="notice">
All values must be strings. No numbers nor objects.
</aside>

## Show

```javascript
talkus('show');
```

Display Talkus button. By default, the button is displayed so you don't need to call it.

## Hide

```javascript
talkus('hide');
```

Hide Talkus button.

## Open

```javascript
talkus('open');
```

Open Talkus plugin.

## Close

```javascript
talkus('close');
```

Close Talkus plugin.

## News

```javascript
talkus('news');
```

Open Talkus plugin on the news tab.

## Faq

```javascript
talkus('faq', 'query');
```

Open Talkus plugin on the faq tab and search for `query`.

## FaqId

```javascript
talkus('faqId', '1234567');
```

Open Talkus plugin on a specific faq entry using the `Id` of the faq.

## Reset

```javascript
talkus('reset');
```

Remove all cookies/localstorage information on the browser.


## NoTalkusOnMobile

```javascript
talkus('noTalkusOnMobile');
```

Disable completely Talkus on mobile. This function must be called *before* the talkus('init') call.

## Callback

```javascript
talkus('callback', function(name) {
  console.log('callback', name);
});
```

Receive event from Talkus. Add a callack Talkus will call when events occur.

Name | Parameters | Description
---- | ---------- | -----------
`notification` | nbNotification (Number) | Called when the visitor received a new notification (message from agents). `nbNotification` contains the number of notification (by default, it's the number displayed in the red bubble on the top right of the Talkus button).
`open` | | Called when the visitor opened the plugin.
`messageSend` | [texts] | Called when a message from the visitor is sent to the agent. `texts` is an array of string.

```javascript
talkus('close');
```

> will call your callback function with `close` as first parameter.

For each `talkus(commandName)` call, it'll call your callback, `Name` will be commandName.

## SendMessage

```javascript
talkus('sendMessage', 'Hello');
```

Send to Talkus a message like if the visitor typed it.
