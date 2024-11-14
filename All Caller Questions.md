  -------------------------
  **Universal Questions**
  -------------------------

# Universal Questions

On the **Universal Questions** tab, questions related to the default
call type appear.   The **Default Call Type** setting  is found on the
[Call-Taking Component configuration
screen](Call-Taking Component Settings.md).  Included in the
**Universal Question** are entries for emergency location, caller name,
phone number, and call type.  These can be entered remotely by CAD or
manually entered by the call-taker.  CAD is notified via change events
when these entries are updated by the call-taker.  A different call type
can be made by making a selection from the drop down list of the
designated question.  Selecting a different call type from the list
loads its associated question set.  The questions appearing on the
**Universal Questions** tab are created using the [Universal Questions
Editor](General Questions Editor.md).

<figure><img src=".gitbook/assets/All Caller Questions_files/image001.png" alt=""><figcaption></figcaption></figure> 

# Immediate Dispatch Button

The **Immediate Dispatch** button is for extremely urgent calls such as
unconscious and not breathing.  It is configurable using the settings on
[Immediate Dispatch
Button](Immediate Dispatch Button Settings.md) configuration
screen.  If enabled, it appears with the **Universal Questions** once a
location has been entered.  It can be associated with either a [Chief
Complaint](General Questions.md), a [Priority](Priorities.md) or
both.  When selected, the associated complaint and priority are
automatically set and the appropriate change events sent to CAD.  The
button is disabled once a [complaint](General Questions.md) and/or
[priority](Priorities.md) has been selected.
