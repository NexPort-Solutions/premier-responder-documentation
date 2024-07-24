  -----------------
  **Email Setup**
  -----------------

The **Email Setup** tab contains controls for configuring the email
server and the content of the email messages.  Within the **Email
setup** frame, the **SMTP Host** is entered which is the name of the
mail server that will receive email messages from **Email Alert**.  A
**Return address** is required by SMTP servers to be included in
outgoing messages. \*NOTE: **Email Alert** can not receive return
messages.  The **Subject** box specifies the subject line of all email
alert messages.  The **Message Header** specifies the first text that is
in all email messages. User account credentials are entered in the
**User ID** and **Password** fields for authentication purposes with the
SMTP server.

The **Email test** frame\'s controls are used to send out a test email
message using the **Email setup** settings.  Use the **Send test
message** button to send the test email message to the **Test
address**.  The test email message will contain \"Test:\" in the subject
and \"This is a test message\" in the body of the message.

**Email message settings** contains more controls for the email
messages.  Checking **Send update email for new alert event occurrence**
will send a new email message when a new occurrence happens for a
triggered alert.  **Time interval for monitoring** establishes how often
Email Alerts checks to see if a criteria for an alert has been met. The
content of all email messages can contain any of the ten items by
checking the box next to the item to include such as **Case Number** and
**Dispatcher**.

![](Email%20Setup/image001.png){border="0" width="639" height="400"}
