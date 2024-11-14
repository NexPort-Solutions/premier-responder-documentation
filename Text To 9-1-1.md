  -------------------
  **Text to 9-1-1**
  -------------------

Support for 9-1-1 text messages is included in the Premier Responder
API.  Controls used to view and send text messages are found on the
active call window.  These controls are initially disabled.  Receipt of
the Show SMS Text command from a CAD system automatically enables the
text to 9-1-1 functionality.  To manually enable, select the **911Text**
toolbar button located on the left toolbar of the active call window. 
For the **911Text** button to appear, the [Show 911Text
Button](Call Buttons Settings.md) setting must be checked on the
[Call Taker Buttons configuration
screen](Call Buttons Settings.md).

<figure><img src=".gitbook/assets/Text To 9-1-1_files/image001.png" alt=""><figcaption></figcaption></figure> 

On opening one of the emergency medical procedure windows, a texting
toolbar with a send button will appear directly below the instructions
box when the texting panel is enabled on the active call window. 
Selecting the button sends the selected content (or full content if text
has not been selected) to CAD in a Send SMS Text event.  Sent texts
appear in the dialog box of the active call window texting panel and are
truncated to 160 characters.
