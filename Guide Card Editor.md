  -----------------------
  **Guide Card Editor**
  -----------------------

[Starting The Guide Card Editor]{.underline}

The guide card content appearing on the call-taker window during the
course of a call is entered into Premier Responder using the **Guide
Card Editor**.  To bring up the **Guide Card Editor** first [log
in](Logging%20In.htm) as an administrator and select the **Edit - Guide
Cards** menu item on the **Premier Responder** **Administrator** main
window.  When active, other Premier Responder windows are disabled.

![](Guide%20Card%20Editor_files/image006.png){border="0" width="655"
height="214"}

 

The **Guide Card Editor** consists of up to nine tabs configurable by
[call type](Available%20Call%20Types%20Editor.htm).  To change tab
labels or hide a tab use the settings on the [Guide Card Tabs
configuration screen](Guide%20Card%20Tabs%20Settings.htm).  Tabs provide
access to the [Available Guide Cards
Editor](Available%20Guide%20Cards%20Editor.htm), [Vital Points
Editor,](Vital%20Point%20Editor.htm) [Priority Categories
Editor](Priority%20Categories%20Editor.htm), General Questions Editor,
and Terms Editor.  Note that the menu item for accessing the [Priority
Categories Editor](Priority%20Categories%20Editor.htm) only appears when
the **Priority** tab is selected.  Selecting the **\'X\'** button in the
top right hand corner of the tab closes the **Guide Card Editor**.

![](Guide%20Card%20Editor_files/image001.png){border="0" width="655"
height="504"}

[Loading A Guide Card]{.underline}

To load a guide card into the editor, first indicate the **Call Type**
by making a selection from the drop down list.  This loads the
associated complaints into the **Guide Card** list and configures the
tabs in accordance with the configuration settings.  Note that the call
type must include a [Guide Card style general
question](General%20Questions%20Editor.htm) otherwise the list is
cleared.  Next select a complaint from the **Guide Card** drop down
list.  Each tab is then loaded with its own particular guide card
information that is related to the specified complaint.

![](Guide%20Card%20Editor_files/image002.png){border="0" width="655"
height="269"}

[Vital Points Tab]{.underline}

Vital point questions appear on the **Vital Points** sub tab of the
**Guide Cards** tab.  Questions are shown in question list box just
below the available editor tabs. To the right of the list box are the
tools used to format how the question will appear on **Premier Responder
Calltaker** window. To make changes to the vital point questions for the
selected **Guide Card**, first select the **Vital Points** tab to bring
it to the front.  Then, select a question from the list box to be
edited. Once a question is selected the **Vital Points** edit options
are used as follows:

-   To add a new vital point, either select the **New** button.
-   To delete the selected vital point, use the **Delete** button.
-   To move the selected vital point up in the list, use the **Up**
    button.
-   To move the selected vital point down in the list, use the **Down**
    button.
-   To change the indent level of the selected vital point, use the
    Indent level .
-   To change the answer entry type of the selected vital point, use the
    **Entry Type** drop-down list.
-   To add job text prefix or job text suffix to the selected vital
    point, fill-in the so named text box.
-   To link the selected vital point to other questions,  priorities,
    emergency, instruction, tab, or group,  select the appropriate
    button.
-   To bold, italicize, or underline the question, select the checkbox
    next to the corresponding format item.
-   To hide or display a question, select the checkbox next to the
    \"Show Question\" item.

![](Guide%20Card%20Editor_files/image003.png){border="0" width="655"
height="504"}

[Priority Tab]{.underline}

Dispatch categories for the indicated **Call Type** together with the
**Guide Card** symptoms appear on the **Priority** sub tab of the
**Guide Cards** tab.  Categories, symptoms and dispatch codes are listed
in a tree format with the symptoms shown branching off from the
categories and the codes from the symptoms.  Use the **Priority** tab
description and code text boxes to enter symptoms for the selected
**Guide Card**.  Use of the **Priority** controls is as follows:

-   To add a symptom to a category, select the category and select the
    **New** button.  A symptom is added with the title **New Symptom
    Item**.
-   To change a symptom title, select the symptom and enter the new
    symptom information in the **Description** box at the bottom of the
    tab.
-   To remove a symptom, select the symptom and select the **Delete**
    button. The symptom is removed from the list.
-   To move a symptom up in the list, select the symptom and then the
    **Up** button.  The **Up** button is disabled when the symptom
    reaches the top of the branch.
-   To move a symptom down in the list, select the symptom and then the
    **Down** button.  The **Down** button is disabled when the symptom
    reaches the bottom of the branch.
-   To change a dispatch code, select the symptom.  Enter the new code
    in the **Code** box at the bottom of the window.  The new code is
    saved automatically.

![](Guide%20Card%20Editor_files/image004.png){border="0" width="655"
height="504"}

[Call-Taker Act, Pre-Arrival, Dispatcher Act, & Background
Tabs]{.underline}

The **Call-Taker Act**, **Pre-Arrival**, **Dispatcher Act**, and
**Background** sub tabs display rich text.  To change the text on any of
these tabs, select the tab to bring it to the front and then either
enter the text directly into the rich text box or paste it from the
clipboard using the control-v key combination.  Changes are
automatically saved.

![](Guide%20Card%20Editor_files/image005.png){border="0" width="655"
height="504"}

[Short Report Tab]{.underline}

The **Short Report** sub tab is used to edit the portion of the short
report that includes the vital point entries.  Text can be pasted into
the rich text box from the clipboard using the control-v key combination
or entered directly.  Tags, representing **Report Data Items**, are
created using the buttons shown.  The tags are replaced by vital point
entries on the call-taker window [Short Report](Short%20Report.htm) tab
and in the reply to the [Get Short Report](APCO%20911Adviser%20API.htm)
API command (#39).  Use of the buttons in the **Short Report** sub tab
is as follows:

-   Select the **Insert** button and then a vital point from the pop-up
    menu to create a data item tag.
-   Select the **Remove** button to delete data items from the report.

![](Guide%20Card%20Editor_files/image007.png){border="0" width="655"
height="504"}

 
