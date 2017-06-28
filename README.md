# Multi-channel bot

This document describes how to set up a sample Express app which talks to Facebook bots.

## Install all dependencies:

    ```
    npm install
    ```

## Getting credentials

### Watson Conversation
Follow the steps outlined in [this document](https://github.com/watson-developer-cloud/conversation-simple/blob/master/README.md#configuring-the-application-environmnet) and paste your Conversation bot's credentials in the sample `.env` file in the project directory.

If you don't have a Conversation service instance,  follow [these steps](https://github.com/watson-developer-cloud/conversation-simple/blob/master/README.md#before-you-begin) to get started.

### Facebook Messenger
Follow the Getting Started section of this [document](https://github.com/howdyai/botkit/blob/master/readme-facebook.md) from Botkit.

*Some helpful hints for Facebook Messenger:*
 * Log into the Facebook App settings page. You need to add two Products- Messenger and Webhooks.
 * When setting up Messenger, make sure you have subscribed your page with your app, otherwise your app won't send back responses to your page. This step is also important cause Facebook will provide you with the _FB_ACCESS_TOKEN_ your bot will need to communicate via Messenger.
 * When setting up the webhook,
    * You'll have to first set up [localtunnel](https://localtunnel.github.io/www/) locally and start it on the same port where you plan to run your Express app. Let's say you run your app on port 5000, then in one terminal window run the following command:
    ```lt --port 5000```
  lt will provide you with a url, part of which will be the webhook url.
    * Add (`https://<your localtunnel url>/facebook/receive`) as Facebook Messenger's webhook. The webhook url must contain _https://_.
    eg:  If your localtunnel url is `http://litjqjglwn.localtunnel.me` your webhook url will be `https://litjqjglwn.localtunnel.me/facebook/receive`, otherwise Facebook will show an error.
    * You need to only subscribe to _Messages_ event under Webhooks.

Once you obtain the access token (provided by Facebook), the verify token (created by you) and the app secret key for your Facebook app (provided by Facebook), paste them in the .env file of your project.
```
FB_ACCESS_TOKEN=<your access token>
FB_VERIFY_TOKEN=<your verify token>
FB_APP_SECRET=<your apps secret key>
```

When you're ready to test your bot, go to your Facebook homepage and find the page you created. Click on _Message_ to start chatting with your Watson Conversation bot!

## Starting the server


Once you have added your credentials in the `.env` file, start the example express app by running this command:
```
node server.js
```

Voila! You're all set! Start chatting on your social channel to test your bot.
