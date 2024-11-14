  ----------------------------
  **CAD Interface Settings**
  ----------------------------

Selecting **CAD Interface** from the **Configuration Settings** list on
the **Settings** window displays the following settings:

-   **Reset PC time**: When checked, sets the local PC time to the call
    start time supplied by CAD when off by more than the indicated
    number of minutes.
-   **Vital Point Summary**: When checked, appends the job text for
    entered vital points to the short report.
-   **Include Problem Codes**: When checked, appends a list of
    associated problem codes to the Complaint Change event that is sent
    in response to call-taker complaint entry.
-   **Force End Call**: When checked, End Call API command will end call
    in progress regardless of unanswered mandatory questions.
-   **Include Call Score**: When checked, the call score is included in
    case report returned by Get Report API command.
-   **Include Time To Dispatch**: When checked, the time to dispatch is
    included in case report returned by Get Report API command.
-   **Send Short Report On Entry**: When checked, the short report is
    automatically sent when call type entered.
-   **Send Short Report On End**: When checked, the short report is
    automatically sent when call is ended.
-   **Clear On Wrap**: When checked, previous call information is
    cleared on receipt of Set Main Window command with Wrapped field
    set.
-   **Get Report:** Indicates type and text format of report sent to CAD
    in response to Get Report command.  Possible values are:  Case
    Report Rich Text, Case Report Plain Text, Short Report Rich Text,
    and Short Report Plain Text.
-   **Default TCP Port**: Specifies the default port Premier Responder
    listens on for connection requests from CAD.
-   **Send Delay Critical**: Specifies a time period (in milliseconds)
    that Premier Responder waits after sending op-codes 2001 to 2007
    before sending another message.
-   **Send Delay Non-Critical**: Specifies a time period (in
    milliseconds) that Premier Responder waits after sending op-codes
    other than 2001 to 2007 events before sending another message.
-   **Connected**: Text to display on the Premier Responder Calltaker
    main window title bar when CAD is connected.
-   **Disconnected**: Text to display on the Premier Responder Calltaker
    main window title bar when CAD is not connected.
-   **CAD Commands**: Comma separated list of command numbers indicating
    CAD commands to record in the application event log. To log all
    commands set to -1.
-   **Responder Events**: Comma separated list of message numbers
    indicating Premier Responder messages to record in the application
    event log. To log all messages set to -1.
-   **Narrative Preface**: Text used to preface the comment that is sent
    to CAD from the narrative dialog window.
-   **Narrative Length**: Specifies the maximum length of the comment
    that can be entered into the narrative dialog window. A value of 0
    indicates no limit.
-   **Priority Length**: Specifies the maximum length of the Priority
    Type text field in Priority Change Event. A value of 0 indicates no
    limit.

<figure><img src=".gitbook/assets/CAD Interface Settings_files/Image001.png" alt=""><figcaption></figcaption></figure>{border="0"
width="655" height="504"}
