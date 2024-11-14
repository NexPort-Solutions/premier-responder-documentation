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
Button](Call%20Buttons%20Settings.htm) setting must be checked on the
[Call Taker Buttons configuration
screen](Call%20Buttons%20Settings.htm).

<figure><img src=".gitbook/assets/Text To 9-1-1_files/image001.png" alt=""><figcaption></figcaption></figure>{border="0" width="697"
height="405"}

With text to 9-1-1 functionality enabled, a texting panel appears at the
bottom of the active call window.  On the right side of the texting
panel is a free text field with an associated **Send** button. 
Selecting the button sends the entered text to CAD in a Send SMS Text
event.  Sent texts are truncated to 160 characters.  Both sent and
received texts are seen in the dialog box on the left side of the
panel.  Sent texts appear in blue and received texts in red.  Note that
the size of the texting panel can be changed by dragging the top of the
panel up or down.  To hide text to 9-1-1 related controls, select the
**911Text** toolbar button or the **X** (Close) button found at the top
right of the texting panel.

<figure><img src=".gitbook/assets/Text To 9-1-1_files/image002.png" alt=""><figcaption></figcaption></figure>{border="0" width="697"
height="501"}

When enabling text to 9-1-1 functionality, send buttons or hyperlinks
can be made to appear on selected tabs by checking the related [911Text
check box](Guide%20Card%20Tabs%20Settings.htm) on the [Guide Cards Tab
Settings configuration screen](Guide%20Card%20Tabs%20Settings.htm). The
tab send buttons and hyperlinks, when selected, result in a Send SMS
Text event with the adjoining question or instruction being sent to
CAD.  Sent texts appear in the dialog box of the active call window
texting panel and are truncated to 160 characters.

<figure><img src=".gitbook/assets/Text To 9-1-1_files/image003.png" alt=""><figcaption></figcaption></figure>{border="0" width="697"
height="501"}

On opening one of the emergency medical procedure windows, a texting
toolbar with a send button will appear directly below the instructions
box when the texting panel is enabled on the active call window. 
Selecting the button sends the selected content (or full content if text
has not been selected) to CAD in a Send SMS Text event.  Sent texts
appear in the dialog box of the active call window texting panel and are
truncated to 160 characters.
