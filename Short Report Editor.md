  -------------------------
  **Short Report Editor**
  -------------------------

The **Short Report Editor** is used to construct a dynamically generated
report.   Included in the report are pre-determined entries from the
[General Questions](General%20Questions.htm).  These are inserted into
the static content of the report when it is generated.  The short report
appears on the [Short Report tab](Short%20Report.htm) of the active call
window and is also sent to [CAD](911Adviser%20Acronyms.htm) upon receipt
of the [Get Short Report API command (op code
39)](APCO%20911Adviser%20API.htm).

To access the Short Report Editor:

-   Log into [Premier Responder
    Administrator](911Adviser%20Administrator.htm) as Administrator
-   From the **Premier Responder Administrator** window select
    **Edit-Call Type** menu item.
-   The **Short Report Editor** lies within the bordered area labeled
    **Short Report** on the **Call Types** sub tab of the [Call Type
    Editor](Available%20Call%20Types%20Editor.htm).

![](Short%20Report%20Editor_files/image001.png){border="0" width="655"
height="504"}

The **Short Report** **Editor** is initially disabled.  Once a call type
selection is made, the related report content is loaded into the edit
box.  Static text can be entered with the keyboard or pasted in from a
word processor.  Data item tags are indicated by a blue underlined
font.  These are write protected and cannot be edited.

![](Short%20Report%20Editor_files/image002.png){border="0" width="419"
height="237"}

Data item tags are placed in the report with the **Insert** button. 
Click the location in the report where the tag is to be inserted.  The
**Insert** button is enabled as long as the cursor is not on a tag.  A
popup menu showing the General Questions for the selected call type
appears when it is selected.  A tag representing the selected item in
the popup is inserted at the location of the cursor.  The tag ID is the
question number from the menu.  A data item from the menu may be
inserted into the report multiple times.

![](Short%20Report%20Editor_files/image003.png){border="0" width="281"
height="246"}

When the report is generated, tags are replaced by answers to the
general questions.  For text box entries, the answer replaces the tag
directly.  Optional replacement text can be specified for list item
selections.  The replacement text is entered on the **List Items** sub
tab of the **General Questions** **Editor**.  In the **Select** list,
click on one of the items in the list then enter the text that will
replace the tag in the **Report Text** edit box.

![](Short%20Report%20Editor_files/image004.png){border="0" width="655"
height="504"}

Use the **Remove** button to delete a data item tag.  It is enabled
after clicking on a tag in the report edit box.  With the cursor on the
unwanted tag, select the **Remove** button.  The tag is immediately
deleted from the report.

![](Short%20Report%20Editor_files/image005.png){border="0" width="419"
height="238"}

Any changes made to the short report or replacement text enables the
**Save** button on the main toolbar.  Select the **Save** button to save
changes.  To exit the **Short Report Editor** click on the **Close
Editor** button.
