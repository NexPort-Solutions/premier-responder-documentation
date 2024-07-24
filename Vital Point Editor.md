  --------------------------
  **Key Questions Editor**
  --------------------------

[The Key Questions Editor]{.underline}

The Key Questions Editor is found on the **Key Questions** sub tab of
the [Available Guide Cards
Editor](Available%20Guide%20Cards%20Editor.htm).  Seen on the left panel
of the status bar, at the bottom of the **Premier Responder
Administrator** window, is the call type/guide card selection that was
made on the **Available Guide Cards** sub tab.  Related key questions
appear in the **Select** list on the left side of the Key Questions
Editor.  Use the **New** button on the main toolbar to add a question to
the list.  Click on a question in the **Select** list to select it for
editing.  The selected key question can be removed from the list with
the **Delete** button or the order changed with  the **Up** and **Down**
buttons.  Changes are made on the **Question** and **List Items** edit
screens.  Select the **Close** (X) button to close the **Guide Cards**
tab.

![](Vital%20Point%20Editor_files/image001.png){border="0" width="655"
height="504"}

[Question Edit Screen]{.underline}

The edit fields seen on the **Question** screen define the key
question.  They determine its appearance, the type of entry, and how the
software reacts to call-taker input.  The **Question** edit screen is
used as follows:

-   The tool bar at the top of the **Question** edit screen includes the
    following rich text editing functionality:

> 1.  **Font** combo - use to change font of selected block of text.
> 2.  **Color** combo - use to change color of selected block of text.
> 3.  **B** button - use to set or clear bold font style of selected
>     block of text.
> 4.  ***I*** button - use to set or clear italicfont style of selected
>     block of text.
> 5.  **[U]{.underline}** button - use to set or clear underline font
>     style of selected block of text.

-   The question text is entered into the edit field below the tool bar
    and appears on the left side of the [Key
    Questions](Vital%20Points.htm) tab of the active call window.
-   The **Type** specifies the style of the answer box.  These are seen
    on the right side of the [Key Questions](Vital%20Points.htm) tab. 
    Possible entry types are:

> 1.  **None** - no data entry
> 2.  **Yes/No** - make yes or no check box selection
> 3.  **Free Text** - text entry
> 4.  **Y/N & Text** - make yes or no check box selection and/or a text
>     entry
> 5.  **Item List** - make selection from a drop down list
> 6.  **RuleOfNines** - text entry with hyperlink to [Rule of Nines
>     dialog window](Vital%20Points.htm) for determining extent of burns

-   **Indent:** a value from 0 to 3 that indicates how much the question
    text is to be indented.
-   **Value:** assign a point value from 0 to 100 for call scoring
    purposes.
-   **Show:** unchecked to hide the question.  The question remains
    hidden until activated by a [Show_Vital_Point
    action](Actions%20Editor.htm), a question link, or a group link from
    another key question.
-   **Mandatory:** when checked, indicates the question must be answered
    before an active call can be ended.
-   **Job Text - Prefix:** descriptive prefix for a **Free Text** type
    question.  Appears in front of the text entry in [Narrative
    Text](APCO%20911Adviser%20API.htm) event that is sent to
    [CAD](911Adviser%20Acronyms.htm).
-   **Job Text - Suffix:** descriptive suffix for a **Free Text** type
    question.  Appears after the text entry in [Narrative
    Text](APCO%20911Adviser%20API.htm) event that is sent to
    [CAD](911Adviser%20Acronyms.htm).
-   **Links:** indicate actions to take when an entry is made.  The type
    of link each button creates is indicated by the label.  The buttons
    are:

> 1.  **Question:** activates another question.
> 2.  **Priority:** sets the [dispatch priority](Priorities.htm).
> 3.  **Tab:** selects a call-taker window tab.
> 4.  **Emergency:** loads a guide card.
> 5.  **Instruction:** displays a [medical
>     procedure](Medical%20Procedures.htm).
> 6.  **Group:** activates the question being edited from the activation
>     of another question.

![](Vital%20Point%20Editor_files/image002.png){border="0" width="655"
height="504"}

[List Items Edit **Screen**]{.underline}

Shown on the **List Items** edit screen are the key question
selections.  The screen is disabled when the **Entry Type** indicates
[None]{.underline} or [Free Text]{.underline}.  For **Yes/No** and **Y/N
& Text** question styles the selections are fixed (**YES** and **NO**
only) and editing restricted to entering links and narratives.  **Item
List** style questions can have an indefinite number of selections.  The
**List Items** edit screen is used as follows:

-   The **Select** list shows the current list items and is used to
    select one for editing.
-   The toolbar buttons above the **Select** list are used to manage the
    items in the list.  They are used as follows:

> 1.  The **New** button adds an item to the list.
> 2.  The **Delete** button removes the selected list item from the
>     list.
> 3.  The **Up** button moves the selected item up in the list.
> 4.  The **Down** button moves the selected item down in the list.

-   The item description that appears in the drop down list is entered
    in the **Description** field.
-   The narrative that is sent to [CAD](911Adviser%20Acronyms.htm) in
    the [Narrative Text](APCO%20911Adviser%20API.htm) event is entered
    in the **Job Text** field.
-   The substitution text that replaces data item tags in the [Short
    Report](Short%20Report.htm) is entered in **Report Text** field.
-   The **Links** buttons are used to create link actions that execute
    when a selection is made.  The type of link each button creates is
    indicated by its label.  The buttons are:

> 1.  **Question:** activates another question.
> 2.  **Priority:** sets the [dispatch priority](Priorities.htm).
> 3.  **Tab:** selects a call-taker window tab.
> 4.  **Emergency:** loads a guide card.
> 5.  **Instruction:** displays a [medical
>     procedure](Medical%20Procedures.htm).

[Creating Default Links & Item Links]{.underline}

The **Links** buttons on the **Question** and **List Items** edit
screens open pop-up menus with the possible link actions.  To create a
link, select a link action other than **None**.  The active link action
appears checked.  Selecting **None** in the menu clears the link
action.  Note that list item link actions override question link
actions.

![](Vital%20Point%20Editor_files/image003.png){border="0" width="474"
height="444"}
