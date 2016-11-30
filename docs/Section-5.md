## Section 5: Make it Go

Now we're ready to start our project locally! :raised_hands:

With your virtual environment turned on and your secrets exported to the environment, go ahead and start your app:

```bash
python app.py
```

![start_appy](https://cloud.githubusercontent.com/assets/4828352/20549064/cad48f8c-b0dd-11e6-8a85-25bff2815d2e.png)

Since Slack will need to talk to your app through teh interwebs, let's expose our app to the world wide web through an [Ngrok](https://ngrok.com/) tunnel. In a terminal window, open up an ngrok tunnel for the port your Flask app will be served on locally. (The default port for Flask is 5000)

```bash
ngrok http 5000
```

![start_ngrok_https](https://cloud.githubusercontent.com/assets/4828352/20549065/ceb8f7b4-b0dd-11e6-8946-119e50518781.png)

Your terminal output should show both an http and https url ending in `ngrok.io`. Copy the **https** url and navigate in your browser to the **Events Subscriptions** tab in your app's settings page. In the **Request URL** form, paste the ngrok url and add `/listening` to the end.

![request_url](https://cloud.githubusercontent.com/assets/4828352/20549180/e7d1f808-b0de-11e6-9aba-d05c34c3c4b7.png)

Flip the **Enable Events** switch to on and you should receive an alert letting you know Slack is about to turn on the Events tap.

![enable_events_alert](https://cloud.githubusercontent.com/assets/4828352/20549185/f2e5f596-b0de-11e6-8d90-ce869b20ef8c.png)

After you've enabled events, you'll need to add a **redirect URL** in your app's **OAuth & Permissions** settings page. This is where the `/thanks` endpoint we've set up earlier in our Flask app comes in. Just append `/thanks` to the end of the ngrok https url and paste it into the **Redirect URL(s)** form on the OAuth Settings section and hit save.

![redirect_url_thanks](https://cloud.githubusercontent.com/assets/4828352/20549300/d5aa215e-b0df-11e6-9796-3cb6fb1da7b4.png)

Now your app is ready to be installed on a Slack team! :tada:

---
**Next [More Info: README](./../README.md)**  
**Previous [Section 4: App Credentials](./../docs/Section-4.md)**  
