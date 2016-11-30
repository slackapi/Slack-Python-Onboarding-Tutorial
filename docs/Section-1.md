## Section 1: ~~Steal~~ Build This Bot

The files in this project are documented with docstrings and inline comments to help you learn what's happening at each step. We'll use python classes throughout this repository to model different aspects of bots and their interactions.

Here's a quick overview of the different files in this repository and how they fit together to give you guidance if you're recreating this project or building your own bot from scratch.

### [app.py](./../app.py)
This file handles all incoming requests from Slack. In this file, we'll import the `Bot` class that we'll create in [bot.py](./../bot.py) so we can instantiate `bot` objects to react to the incoming requests we receive.

First, you'll want to create a Flask app in [`app.py`](./../app.py).
Then you'll need to add a couple routes:
- **`"/install"`** a route that renders an installation page where users can add your Slack app to their team
- **`"/thanks"`** a route that renders a thank you page to let users know your app has been sucessfully installed.
    - This route will be the endpoint of the `redirect URL` where Slack will send a temporary authorization code. We'll exchange that code for an OAuth token here, using our `bot` object's `auth` method.
- **`"/listening"`** a route that listens for all incoming requests from Slack.
    - This route will be the endpoint of the `request URL` where Slack will send all Events your app is subscribed to.
    - This route will need to handle [Slack's URL verification process](https://api.slack.com/events/url_verification).
    - We'll also want to use the __Verification Token__ from our app's **Basic Information** page to verify that the requests sent to this route are from Slack and not someone devious.
    - This route will use an `_event_handler` helper function to help our `bot` object respond properly.

Above the routes you've added, you'll need to create the **`_event_handler`** helper function that your `"/listening"` route will use. This function should match the event type of the request coming from Slack to the way you'd like your bot to respond using different methods on the `bot` object.

### [bot.py](./../bot.py)
This file contains a python class for `bot` objects. The `bot` object is used in [`app.py`](./../app.py) to respond to requests from Slack. We can store attributes like the name and emoji we'd like to use for our bot. We can save all the information we'll need for authentication on our `bot` object, like the `client_id`, `client_secret` and `verification_token` from our app's **Basic Information** page.

We'll import the `Message` class that we'll create in the [message.py](./../message.py) file so we can instantiate `message` objects to help us keep track of the current state of the messages from our bot that users will be interacting with.

First, you'll want to create a `Bot` class with an `__init__` function that will create the following attributes on each instance of a `bot` object that gets created:
- **`self.name`** the name of your bot that will be displayed to users interacting with it in Slack
- **`self.emoji`** the emoji that will be used as the profile picture for your bot
- **`self.oauth`** a python dictionary containing your app's `"client_id"`,  `"client_secret"` and the scope your app will need
    - To keep your app's information secret, after you've exported these secrets to your environment, you can access them here.
- **`self.verification`** the `verification_token` from your app's **Basic Information** page
    - Just like the secrets in `self.oauth`, after you've exported this to your environment you can access your verification token here.
- **`self.client`** a `SlackClient` object from python-slackclient which we'll use to connect to Slack's API's
    - Before the OAuth flow is completed when a user installs your app, you can connect to the `SlackClient` by passing an empty string. Once you've got the correct OAuth token, you'll need to reconnect to the client, passing the `bot_access_token` and updating this attribute.
- **`self.messages`** an empty python dictionary where we'll store `message` objects

After that you'll want to add some functionality to your bot with some `Bot` class methods. Here's a few methods you can start with:
- **`auth()`** a method that exchanges a temporary authorization code from Slack for an OAuth token
    - In this method you'll want to reconnect to the `SlackClient` and update the `self.client` attribute.
- **`open_dm()`** a method that opens up a new DM with a user

Here you can add `Bot` class methods for the different ways your bot should respond to events from Slack triggered by different ways users interact with your app. This project has a method for sending an **`onboarding_message()`** to teach users how to do different things in Slack when a user joins a team. As the user performs each of the onboarding tasks, we update the message using a `Bot` class method for each particular task.

### [message.py](./../message.py)
This file contains a python class for creating `message` objects. Creating `message` objects allows us to store information about each onboarding message our bot sends out to various new users and more easily keep track of what tasks each user has completed. This project uses a JSON file with the contents of the onboarding message we're creating with this class.

### Other Stuff

#### [Templates Folder](./../templates)
You'll need some HTML for your [installation](./../templates/install.html) and [thank you](./../templates/thanks.html) pages. Once you create this folder, we'll use Jinja templates and add the [Add to Slack](https://api.slack.com/docs/slack-button) button to allow users to install our app. The [thank you page](./../templates/thanks.html) lets users know that the app has been sucessfully installed.

#### [welcome.json](./../welcome.json)
This is a JSON file of message attachments used in the `message.py` file to create the onboarding welcome message our bot will send to new users.


---
**Next [Section 2: Create a Slack App and Bot User](./../docs/Section-2.md)**  
**Previous [README](./../README.md)**  
