  ------------------------
  **Medical Procedures**
  ------------------------

The medical procedures are viewed by selecting one of the right toolbar
buttons on the Premier Responder Calltaker window.  The buttons appear
with red cross symbols and a text label that specifies a category.  For
each button, a pop-up menu displays list of procedures within the
category.  To change the category button labels or hide the buttons use
the settings on the [Medical Procedure Buttons configuration
screen](Medical%20Procedure%20Buttons%20Settings.htm).

![](Medical%20Procedures_files/image001.png){border="0" width="697"
height="242"}

Selecting a category button and then a procedure from the subsequent
menu loads the procedure into the viewer.  CAD is notified when a
medical procedure is has started with via an API event.  The procedure
is viewed a step at a time in the text box labeled **Instructions**. 
Notes appear in the text box at the bottom of the viewer.  The same
notes appear for each step.  Buttons at the top of the viewer provide a
means of navigating through the steps.  By default, the buttons are
graphical and can be identified by a tool tip.  Text labels can be
applied to the navigation buttons using the settings on the [Medical
Procedure Buttons configuration
screen](Medical%20Procedure%20Buttons%20Settings.htm).  From left to
right, the navigation buttons function as follows:

-   **Retrace Backward** (left arrow with two lines): Display previous
    step in history (does not add to history).
-   **Go to First Step** (left arrow with single line): Display first
    step of procedure (does add to history).
-   **Go to Previous Step** (left arrow with no lines): Display previous
    step of procedure (does add to history).
-   **Go to Next Step** (right arrow with no lines): Display next step
    of procedure (does add to history).
-   **Go to Last Step** (right arrow with single line): Display last
    step of procedure (does add to history).
-   **Retrace Forward** (right arrow with two lines): Display next step
    in history (does not add to history).

![](Medical%20Procedures_files/image002.png){border="0" width="457"
height="419"}

Another means to navigate the medical procedures is by selecting a
link.  Links are typically indicated by a blue underlined font.  A link
can branch to a step in the same procedure or one in another procedure. 
Selecting a link also adds to the history of previously viewed steps.  A
maximum of 25 steps is stored in the history.

![](Medical%20Procedures_files/image003.png){border="0" width="457"
height="419"}
