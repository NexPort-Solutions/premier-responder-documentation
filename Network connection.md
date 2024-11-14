  ------------------------
  **Network Connection**
  ------------------------

The Premier Responder application can communicate with a Computer Aided
Dispatch system via a TCP connection that listens for a connection
request on port 2021.  The sets of messages by which the Premier
Responder communicates are documented in the Premier Responder
Application Program Interface (API) and include:

-   Commands to Premier Responder (example: Login, Begin Call, Get
    Caller, etc.)
-   Normal responses for the regular commands
-   Error responses for the regular commands (for messages that are too
    short, too long etc.)
-   Premier Responder events to CAD (example: caller name has changed,
    general answer has changed, etc.)

(Network connection)

<figure><img src=".gitbook/assets/Network connection_files/image001.png" alt=""><figcaption></figcaption></figure>{border="0" width="603"
height="231"}

A normal or error response will be sent back to the CAD for each
incoming command.  Also, premier responder events are sent to the CAD in
response to call taker entries.  Further details of this communication
are specified in the [Premier Responder
API](APCO%20911Adviser%20API.htm) document.
