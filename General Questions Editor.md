  -----------------------------------------
  **Universal Questions Editor Controls**
  -----------------------------------------

# Editing Universal Questions

The **Universal Questions** editing functionality of the **Call Types**
tab is used to author the question sets associated with each of the call
types.  To open the **Universal Questions** editing controls, first
select a **Call Type** on the Call Types sub tab, then select the
adjacent **Universal Questions** sub tab within **Premier Responder
Administrator**.

<figure><img src=".gitbook/assets/General Questions Editor_files/image001.png" alt=""><figcaption></figcaption></figure>{border="0"
width="655" height="504"}

# Universal Questions Editor Description

The **Call Types** tab can be used to expose the **Universal Questions**
editing controls in the following manner:

-   The **Call Types** sub tab **Select** list box is used to select the
    question set to edit.
-   The **Universal Questions** sub tab **Select** list box displays the
    available questions from which a selection is made.
-   The **Question** edit screen exposes question-related controls and
    fills them with the details of the selected question.
-   The **List Items** edit screen exposes list item-related controls
    and, for those universal questions that have them, fills them with
    the list item details.

# Selecting A Question Set

To edit the universal questions for one of the call types, make a
selection from the **Call Types** sub tab **Select** list box.  The
associated question set loads into the **Question** edit screen of the
**Universal Questions** editor.  Note that, for liability reasons, only
limited editing of the medical questions is allowed.

<figure><img src=".gitbook/assets/General Questions Editor_files/image003.png" alt=""><figcaption></figcaption></figure>{border="0"
width="297" height="171"}

# Changing the Universal Questions

The **Universal Questions** manipulation buttons are used to add,
delete, order, and save modifications made to the Universal Questions. 
A question must be selected before using the **New**, **Delete**,
**Save**, **Up**, or **Down** buttons.  Click on the text of a question
to select it.  The selected question appears highlighted in the list. 
The universal question manipulation buttons are used as follows:

-   The **New** button appends a generic question to the bottom of the
    list.  There is a limit of 24 questions.  Upon reaching the maximum
    number of question allowed, the button is disabled.
-   The **Delete** button immediately deletes a selected question upon
    clicking.
-   The **Save** button saves edits made to the selected question. Note
    that if any deletions, edits, or additions are not saved prior to
    closing the \"Call Types\" tab, an \"Exit without saving?\" dialog
    appears to provide a last chance to save changes.
-   The **Up** button is used to move the selected question up the
    list.  When the question reaches the top of the list the button is
    disabled.
-   The **Down** button moves the question down the list.  When the
    question reaches the bottom of the list the button is disabled.

# Editing A Question

The **Question** edit screen of the **Universal Questions** editor
contains question related edit fields.  On the **List Items** edit
screen are edit fields used to enter information for list box style
questions.

<figure><img src=".gitbook/assets/General Questions Editor_files/image004.png" alt=""><figcaption></figcaption></figure>{border="0"
width="441" height="338"}

The **Question** editing controls consist of the following:

-   The tool bar and text box at the top of the **Question** edit screen
    are used to edit the question text.  The **Font** and **Color** drop
    down lists are used to change the font and color of the selected
    block of text.  To set or clear bold, italic, or underline font
    style for the selected block of text, use the **B**, *I*, and
    # U buttons.
-   The **Align** selection indicates if the question text is to be
    centered,  left or right justified.
-   The **Type** selection determines the style of the answer box and
    special functionality associated with the question.
-   The **Width** numeric control is used to set the width of the answer
    box.
-   The **Value** numeric control is used to assign a point value to the
    question for call scoring purposes.
-   The **Show** check box indicates the initial state, whether active
    or inactive. Inactive questions only appear when activated by an
    action, question link, or group link.
-   The **Mandatory** check box, when checked, indicates the question
    must be answered before an active call can be ended.
-   The **Job Text - Prefix** text box is used to enter text that will
    prepend a text entry in the narrative sent to CAD when the [job text
    narrative option](General%20Questions%20Narrative%20Settings.htm) is
    enabled.
-   The **Links** buttons are used to attach links to respectively-named
    Premier Responder Calltaker text and control items that initiate an
    action when an entry is made.

# Links Attached to Questions

Links attached to questions affect the behavior of Premier Responder
when an entry is made during a call.[  An action is initiated when any
entry is made for a question with an attached
link. ]{style="mso-spacerun: yes"} When the **Links -\> \"Question\"**
button is clicked, a pop-up menu appears listing the available links. 
Click on a link to attach it to the question.  An attached link is
indicated by a check mark next to it.

<figure><img src=".gitbook/assets/General Questions Editor_files/image005.png" alt=""><figcaption></figcaption></figure>{border="0"
width="386" height="209"}

The resulting actions initiated by the different link types are as
follows:

-   A **Question** link activates another question.
-   An **Emergency** link loads the indicated guide card.
-   A **Priority** link automatically sets the [dispatch
    priority](Priorities.htm).
-   An **Instruction** link displays the specified [medical
    instruction](Medical%20Procedures.htm).
-   A **Tab** link changes the selected tab on the call taker window.
-   A **Group** link makes an association with another question so that
    when a question is activated/deactivated, all associated questions
    are also activated/deactivated.

# Question Types

The **Type** property determines the style of the answer box and special
functionality of associated with the question.  The styles and
functionality assigned to the different question types are as follows:

-   **List Box** sets the answer box style to a drop down list.

-   **Text Box** sets the answer box style to a plain text box.

-   **Guide Card** sets the answer box style to a drop down list which
    is populated with the complaint selections for the call type. 
    Additionally CAD can remotely set the complaint as well as receive a
    complaint entry made by the call taker.  Note that only a single
    **Guide Card** style question is allowed.  Also know that, without a
    **Guide Card** style question, [guide card
    editing](Guide%20Card%20Editor.htm) is disabled.

-   **Location** sets the answer box style to a text box.  Additionally
    CAD can remotely set the location and receive any entered changes
    made by the call taker.  Note that only a single **Location** style
    question is allowed.

-   **Phone Num** sets the answer box style to a text box.  Additionally
    CAD can remotely set the phone number as well as receive any entered
    changes made by the call taker.  Note that only a single **Phone
    Num** style question is allowed.

-   **Caller Name** sets the answer box style to a text box. 
    Additionally CAD can remotely set the location as well as receive
    any entered changes made by the call taker.  Note that only a single
    **Caller Name** style question is allowed.

-   **Call Type** sets the answer box style to a drop down list that is
    automatically populated with all of the call types.  Additionally
    CAD can remotely set the call type as well as receive a change to
    the call type entry made by the call taker.  Note that only a single
    **Call Type** style question is allowed.

-   **Text & List** sets the answer box style text box with an
    associated list box to the right of it.  Additionally, when the
    question is activated, the list box is defaulted to the first item
    in the list.

-   **None** hides the answer box so that only the question text
    appears.

# List Items

The **List Items** section of the **Universal Questions sub tab** is
enabled only for **List Box**, **Guide Card**, and **Text & List** style
questions.

<figure><img src=".gitbook/assets/General Questions Editor_files/image007.png" alt=""><figcaption></figcaption></figure>{border="0"
width="627" height="367"}

Located within the **List Items** section are the following controls:

-   The **Select** list box displays the selections that will appear in
    the answer boxes.

-   The four graphical buttons are used to add, order and delete the
    list items.

-   The **Links** buttons are used to associated a selection with an
    action.

-   The **Job Text & Report Text** text boxes are used for entering
    substitution text for the CAD narrative and [Short
    Report](Short%20Report.htm) (respectively).

# Managing List Items

There are four graphical buttons located within the **List Items**
section of the **Universal Questions sub tab**.  These are used to add,
order, and delete the selections.  A tool tip that indicates the
function appears when hovering the mouse cursor over the button.  To add
a new item to the list, select the **New** graphical button.  This adds
a new generic list item.  Next, enter the item text in the
**Description** text box.  The new item\'s text should update and be
present in the **Select** listbox.

<figure><img src=".gitbook/assets/General Questions Editor_files/image008.png" alt=""><figcaption></figcaption></figure>{border="0"
width="436" height="121"}

An existing list item can be edited by first selecting it in the list
and then supplying alternate text in the **Description** text box. 
Modifications to the list item text should be immediately visible in the
**Select** listbox.

<figure><img src=".gitbook/assets/General Questions Editor_files/image009.png" alt=""><figcaption></figcaption></figure>{border="0"
width="441" height="119"}

To delete a list item, first select it and then click the **Delete**
button.  The selection is removed from the list.  List items can be
arranged in the list using the arrow buttons.  Use the **Up** button to
move the selected item up one position in the list.  The **Down** button
moves the selected item down one position in the list.

# Links Attached to List Items

Item links differ from question links in that they are attached to a
selection so that the action is initiated when a selection is made with
an attached link.  Note that, to prevent conflicting actions, an item
link overrides a question link (if present).  To attach a link to a list
item, first **Select** a list item from the listbox.  Next click on one
of the **Links** buttons and select a link in the corresponding drop
down list.  An attached link is indicated by a check mark next to it.

<figure><img src=".gitbook/assets/General Questions Editor_files/image011.png" alt=""><figcaption></figcaption></figure>{border="0"
width="453" height="433"}

# Entering CAD Narrative

When Premier Responder is interfaced to a CAD system, Universal Question
narratives are sent to CAD as entries are made.  The narrative is
configurable using the settings on the [Universal Question Narrative
configuration screen](General%20Questions%20Narrative%20Settings.htm). 
It can include text for both the question plus the entry, the entry
only, or an abbreviated job text.  The **Job Text** text box is used to
enter an abbreviated narrative for a selection type entry. 

<figure><img src=".gitbook/assets/General Questions Editor_files/image012.png" alt=""><figcaption></figcaption></figure>{border="0"
width="430" height="144"}

# Entering Report Text

The **Report Text** text box is used to enter text that replaces the
tags in the [Short Report](Short%20Report.htm).  If **Report Text** is
not entered for an item, then the item\'s text is used as-is in the
tags.

# Saving Changes

After completing changes to a question, click the **Save** button at the
top of the **Call Types** main tab.  Afterwards, you can either continue
editing questions or click the **X** button at the top right of the tab
to exit.
