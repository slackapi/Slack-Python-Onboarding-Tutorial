## Section 4: App Credentials

Let's revisit that tempting **Basic Information** page. Here you'll find your app's **Client ID**, **Client Secret** and **Verification Token** under the _App Credentials_ section.

![app_credentials](https://cloud.githubusercontent.com/assets/4828352/20548888/198e2270-b0dc-11e6-9a92-5fe3842be4ba.png)

The Client ID is used to identify your app when requests are sent to Slack's API's. The Client Secret is used to validate your app's authenticity during the OAuth negotiation process. The Verification Token is used to verify requests sent by Slack and received by your server.

Just like you wouldn't graffiti your email username and password at the bus stop, it's important to prevent your _App Credentials_ from becoming part of a public repository. To protect your app's secrets, this project exports these secrets to your local environment.

If you're using Bash or Zsh and your virtual environment is activated, you can export your app's secrets like this:

```bash
export CLIENT_ID='XXXXXXXXXXX.xxxxxxxxxx'
export CLIENT_SECRET='xxXXxxXXXXXxxxxXXX'
export VERIFICATION_TOKEN='xxxXXXxxXXxxX'
```

Our app will grab these secrets from our environment.

---
**Next [Section 5: Make it Go](./../docs/Section-5.md)**  
**Previous [Section 3: Subscribe to Events](./../docs/Section-3.md)**  
