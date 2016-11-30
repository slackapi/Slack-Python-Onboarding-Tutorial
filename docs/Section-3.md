## Section 3: Subscribe to Events

Once you've got your fancy new automaton, let's have it subscribe to some events in Slack!

On your app's settings page you'll find **Event Subscriptions** on the left navigation bar.

Near the bottom of the page under the **Bot Events** section you'll be able to subscribe your bot to the events.

![add_bot_events](https://cloud.githubusercontent.com/assets/4828352/20548810/8ea539b4-b0db-11e6-859d-e75f98a29ddc.png)

This project uses the following events:

- [message.channels](https://api.slack.com/events/message.channels)
- [message.im](https://api.slack.com/events/message.im)
- [pin_added](https://api.slack.com/events/pin_added)
- [reaction_added](https://api.slack.com/events/reaction_added)
- [team_join](https://api.slack.com/events/team_join)

After you've subscribed to all the events your app will need, make sure to **Save Changes**.

![save_changes](https://cloud.githubusercontent.com/assets/4828352/20575405/fca754dc-b16d-11e6-880d-5eb8dd5d5196.png)

---
**Next [Section 4:  App Credentials](./../docs/Section-4.md)**  
**Previous [Section 2: Create a Slack App and Bot User](./../docs/Section-2.md)**  
