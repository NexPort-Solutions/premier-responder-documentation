::::: Section1
  -------------------------------
  **Premier Responder API 3.0**
  -------------------------------

**[ ]{style="font-size:10.0pt"}**

**[Proprietary Information]{style="font-size:11.0pt"}**

**[ ]{style="font-size:10.0pt"}**

[This document is considered Proprietary Information by Darwin Global,
LLC, (dba Smart Horizons), and is subject to the dictates of the Non
Disclosure Agreement signed by the
recipient.]{style="font-size: 10.0pt; font-family: Times New Roman"}

[ ]{style="font-size:10.0pt"}

**[Introduction]{style="font-size:11.0pt"}**

**[ ]{style="font-size:10.0pt"}**

[The Premier Responder Application Program Interface (API) is built on
top of the TCP/IP networking protocol.  Premier Responder listens on a
configurable port and a random port for a connection request from a
computer aided dispatch (CAD) system.  The configurable port defaults to
2021 and is specified on the [CAD Interface configuration
screen](Cad%20Interface%20Settings.htm).  The random port is obtainable
with the Get Alternate Port API command.  Version 3.0 of the Premier
Responder API supports 51 externally callable commands, an error
notification for each command, and 11 event types that Premier Responder
can generate during the course of a
call.]{style="font-size: 10.0pt; font-family: Times New Roman"}

[ ]{style="font-size:10.0pt"}

**[Message Structures]{style="font-size:11.0pt"}**

[ ]{style="font-size: 10.0pt"}

[API version 3.0 includes support for both byte array and XML structured
messages.  The default message structure consists of data values packed
into a byte array with the values represented by one of seven possible
data types.  XML structured messages include a root element with one or
more nested child elements serialized to a string.  Receipt of an XML
structured message enables XML structured events and acknowledgements
from 9-1-1
Adviser.]{style="font-size: 10.0pt; font-family: Times New Roman"}

 

**[Default Data Types]{style="font-size:11.0pt"}**

**[ ]{style="font-size:10.0pt"}**

[Data values contained in ]{style="font-size:10.0pt"} [byte array
structured
messages]{style="font-size: 10.0pt; font-family: Times New Roman"}[
consists of the following data types: byte, boolean, integer, long,
date, string and list.  The data types described in this section are
used by the API.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

*[Bytes ]{style="font-size:10.0pt"}*[are an integer value from 0 to
255.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

*[Booleans ]{style="font-size:10.0pt"}*[are single bytes that are of
value zero if they are false.  Any value other than zero represents a
true.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

*[Integers ]{style="font-size:10.0pt"}*[are two bytes in length and are
nothing more than the binary representation of their values.  As an
example, the value 3024 would be passed as the following byte
stream:]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

  -------------------------------- --------------------------------
  [0B]{style="font-size:10.0pt"}   [D0]{style="font-size:10.0pt"}
  -------------------------------- --------------------------------

[ ]{style="font-size:10.0pt"}

*[Longs ]{style="font-size:10.0pt"}*[are four bytes in length and are
also binary representations of their values.  As an example, the value
10329345 would be passed as the following byte
stream:]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

  -------------------------------- -------------------------------- -------------------------------- --------------------------------
  [00]{style="font-size:10.0pt"}   [9D]{style="font-size:10.0pt"}   [9D]{style="font-size:10.0pt"}   [01]{style="font-size:10.0pt"}
  -------------------------------- -------------------------------- -------------------------------- --------------------------------

[ ]{style="font-size:10.0pt"}

*[Strings ]{style="font-size:10.0pt"}*[consist of an integer holding the
size of the string followed by single-byte ASCII codes for each of the
characters contained in the string.  As an example, the string "Hi"
would be sent as the following byte stream:]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

  -------------------------------- -------------------------------- -------------------------------- --------------------------------
  [00]{style="font-size:10.0pt"}   [02]{style="font-size:10.0pt"}   [48]{style="font-size:10.0pt"}   [69]{style="font-size:10.0pt"}
  -------------------------------- -------------------------------- -------------------------------- --------------------------------

[ ]{style="font-size:10.0pt"}

[where 00 02 is the length of the string and 48 69 is the string
itself.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

*[Dates ]{style="font-size:10.0pt"}*[are fourteen bytes long.  They are
passed in the format "MMDDYYYYHHMMSS" which is broken down into
single-byte ASCII codes for each of the values in the formatted string.
 As an example, the moment ]{style="font-size:10.0pt"}[January 4,
1998]{style="font-size:10.0pt"}[ **@**
]{style="font-size:10.0pt"}[5:30:26 p.m.]{style="font-size:10.0pt"}[
would be formatted into "01041998173026" which would be passed as the
following byte stream:]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

  -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- --------------------------------
  [30]{style="font-size:10.0pt"}   [31]{style="font-size:10.0pt"}   [30]{style="font-size:10.0pt"}   [34]{style="font-size:10.0pt"}   [31]{style="font-size:10.0pt"}   [39]{style="font-size:10.0pt"}   [39]{style="font-size:10.0pt"}   [38]{style="font-size:10.0pt"}   [31]{style="font-size:10.0pt"}   [37]{style="font-size:10.0pt"}   [33]{style="font-size:10.0pt"}   [30]{style="font-size:10.0pt"}   [32]{style="font-size:10.0pt"}   [36]{style="font-size:10.0pt"}
  -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- --------------------------------

[ ]{style="font-size:10.0pt"}

*[Lists ]{style="font-size:10.0pt"}*[are an array of associated string
and integer data.  They begin with a leading integer that indicates the
number of items in the list.  The list follows with each list item
consisting of an integer followed by a string.  As an example, the
following list would be passed as the next byte
stream]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

  ------------------------------------------- ----------------------------------------
  **[Item Data]{style="font-size:10.0pt"}**   **[String]{style="font-size:10.0pt"}**
  [123]{style="font-size:10.0pt"}             [ab]{style="font-size:10.0pt"}
  [456]{style="font-size:10.0pt"}             [cd]{style="font-size:10.0pt"}
  ------------------------------------------- ----------------------------------------

[ ]{style="font-size:10.0pt"}

  -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- --------------------------------
  [00]{style="font-size:10.0pt"}   [02]{style="font-size:10.0pt"}   [00]{style="font-size:10.0pt"}   [7B]{style="font-size:10.0pt"}   [00]{style="font-size:10.0pt"}   [02]{style="font-size:10.0pt"}   [61]{style="font-size:10.0pt"}   [62]{style="font-size:10.0pt"}   [01]{style="font-size:10.0pt"}   [C8]{style="font-size:10.0pt"}   [00]{style="font-size:10.0pt"}   [02]{style="font-size:10.0pt"}   [63]{style="font-size:10.0pt"}   [64]{style="font-size:10.0pt"}
  -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- --------------------------------

[ ]{style="font-size:10.0pt"}

[where 00 02 signifies the length of ]{style="font-size:10.0pt"}[the
list, 00 7B is the item data for the first element, 00 02 is the length
of the first string element, 61 62 is the first string, 01 C8 is the
item data for the second element, 00 02 is the length of the second
string element, and 63 64 is the second
string.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[Default Command Format]{style="font-size:11.0pt"}**

**[ ]{style="font-size:10.0pt"}**

[Premier Responder]{style="font-size:10.0pt"}[ expects byte array
structured commands to follow the same format.  Any commands that do not
follow the proper format wilt result in an error response from Premier
Responder.  Each command consists of a 16-bit op-code followed by any
data that is associated with the command.  Every command must have a
footer consisting of two bytes of value 255.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Take for example, the ]{style="font-size:10.0pt"}[command required to
set the caller's name.  The op-code for that command is 7.  That
particular command requires the name of the caller.  If the caller's
name were Bob, the command to set the caller's name in Premier Responder
would be passed as the following byte stream,]{style="font-size:
10.0pt"}

[ ]{style="font-size:10.0pt"}

  -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- --------------------------------
  [00]{style="font-size:10.0pt"}   [07]{style="font-size:10.0pt"}   [00]{style="font-size:10.0pt"}   [03]{style="font-size:10.0pt"}   [42]{style="font-size:10.0pt"}   [6F]{style="font-size:10.0pt"}   [62]{style="font-size:10.0pt"}   [FF]{style="font-size:10.0pt"}   [FF]{style="font-size:10.0pt"}
  -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- --------------------------------

[ ]{style="font-size:10.0pt"}

[where 00 07 is the op-code, 00 03 is the length of
]{style="font-size:10.0pt"}[the string containing the caller's name, 42
6F 62 is the caller's name, and FF FF is the command
footer.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[For this ]{style="font-size:10.0pt"}[particular command, Premier
Responder will respond with a boolean true or false, depending on the
success of the operation.  If this command were successfully executed,
]{style="font-size:10.0pt"} [the byte stream sent in the reply would be
as
follows]{style="font-size: 10.0pt; font-family: Times New Roman"}[:]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

  -------------------------------- -------------------------------- -------------------------------- -------------------------------- --------------------------------
  [00]{style="font-size:10.0pt"}   [07]{style="font-size:10.0pt"}   [01]{style="font-size:10.0pt"}   [FF]{style="font-size:10.0pt"}   [FF]{style="font-size:10.0pt"}
  -------------------------------- -------------------------------- -------------------------------- -------------------------------- --------------------------------

[ ]{style="font-size:10.0pt"}

[where ]{style="font-size:10.0pt"}[00 07 is the command that Premier
Responder is responding to, 01 is a boolean true, and FF FF is the
command footer.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[All responses ]{style="font-size:10.0pt"}[from Premier Responder begin
with the op-code that is being responded to.  This is followed by any
data associated with the response.  All responses are terminated with
the previously mentioned footer.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[**XML Data Types**]{style="font-size: 11pt"}

**[ ]{style="font-size:10.0pt"}**

Text values contained in the nested message elements are converted to an
appropriate data type for processing therefore must adhere to the
following guidelines.

**[ ]{style="font-size:10.0pt"}**

*Byte, Integer, and Long* data types are represented by one or more
numeric characters.

**[ ]{style="font-size:10.0pt"}**

*String* data can be any text.

**[ ]{style="font-size:10.0pt"}**

[*Boolean* states are indicated as follows:]{style="font-size:10.0pt"}

-   [True = non zero numeric character]{style="font-size:10.0pt"}

-   [False = zero numeric character.]{style="font-size:10.0pt"}

**[ ]{style="font-size:10.0pt"}**

[*Date* values are represented by a 14 character numeric
string]{style="font-size:10.0pt"}[ in the format MMDDYYYYHHMMSS
where:]{style="font-size:10.0pt"}

-   MM (month) = 1 to 12

-   DD (day) = 1 to 31

-   YYYY (year) = 0000 to 9999

-   [HH (hour) = 0 to 23]{style="font-size:10.0pt"}

-   MM (minute) = 0 to 59

-   SS (second) = 0 to 59

**[ ]{style="font-size:10.0pt"}**

*List* data is a numbered list with list items formatted as follows:

> Item number + Tab + Item description + Carriage Return + Line Feed

[**XML Command Format**]{style="font-size: 11pt"}

**[ ]{style="font-size:10.0pt"}**

[XML commands include a *Message* root element, an *OpCode* child
element, and additional child elements as required.  Using the previous
Set Caller command example, the XML version would be as
follows:]{style="font-size:10.0pt"}

> \<Message\>\
>     \<OpCode\>7\</OpCode\>\
>     \<CallerName\>Bob\</CallerName\>\
> \</Message\>

[Again, Premier Responder will respond with a boolean true or false,
depending on the success of the operation.  On successfully
executing]{style="font-size:10.0pt"}[ the
command]{style="font-size:10.0pt"}[, ]{style="font-size:10.0pt"} [the
XML version of the reply would be as
follows]{style="font-size: 10.0pt; font-family: Times New Roman"}[:]{style="font-size:10.0pt"}

> \<Message\>\
>     \<OpCode\>7\</OpCode\>\
>     \<Success\>1\</Success\>\
> \</Message\>

**[Op-codes]{style="font-size:11.0pt"}**

**[ ]{style="font-size:10.0pt"}**

[As seen in Table 1, version 3.0 of ]{style="font-size:10.0pt"}[the
Premier Responder API has three specific categories into which
communications between Premier Responder and external applications can
fall.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[Table 1 - ]{style="font-size:10.0pt"}[Op-code
categories]{style="font-size:10.0pt"}**

[ ]{style="font-size:10.0pt"}

::: {align="center"}
  ------------------------------------------------------------------------------------------------------- ------------------------------------------------------
  **[Op-code]{style="font-size:10.0pt"}[ ]{style="font-size:10.0pt"}[Range]{style="font-size:10.0pt"}**   **[Category]{style="font-size:10.0pt"}**
  [1-999]{style="font-size:10.0pt"}                                                                       [General op-code]{style="font-size:10.0pt"}
  [1000-1999]{style="font-size:10.0pt"}                                                                   [Error messages]{style="font-size:10.0pt"}
  [2000-2999]{style="font-size:10.0pt"}                                                                   [Premier Responder events]{style="font-size:10.0pt"}
  ------------------------------------------------------------------------------------------------------- ------------------------------------------------------
:::

[ ]{style="font-size:10.0pt"}

[All categories follow the prescribed command format.  General
]{style="font-size:10.0pt"}[op-codes are called by external
programs.]{style="font-size:10.0pt"}

[Error messages ]{style="font-size:10.0pt"}[are sent from Premier
Responder whenever an error occurs.  Events are sent when the user
affects a change in Premier Responder.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[Error Messages]{style="font-size:11.0pt"}**

**[ ]{style="font-size:10.0pt"}**

[Error messages 1001-1999 correspond to op-codes called by external
functions.  Currently all error messages are sent in response to invalid
data passed with an op-code.  For example, if a program sends a boolean
with op-code 7 instead of an integer, Premier Responder will respond
with an error message 1007.  Integers passed with Premier Responder
indicate the number of errors encountered while extracting data from the
byte-stream.  A value of 0 indicates that the number of bytes of data
was incorrect.  As most extractions are aborted upon the first error,
most values passed with error messages will be either 0 or 1.  As an
example, if Premier Responder encounters a data-length error while
processing a Set Caller (op-code 7) command, it would respond with an
error message as seen in the following
byte-stream:]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

  -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- --------------------------------
  [03]{style="font-size:10.0pt"}   [EF]{style="font-size:10.0pt"}   [00]{style="font-size:10.0pt"}   [00]{style="font-size:10.0pt"}   [FF]{style="font-size:10.0pt"}   [FF]{style="font-size:10.0pt"}
  -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- --------------------------------

[ ]{style="font-size:10.0pt"}

[where 03 EF is the error code, 00 00 is the associated integer, here
indicating a data-length error, and FF FF is the command
footer.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[An error message 1000 with an ]{style="font-size:10.0pt"}[associated
integer of 0 indicates that an internal error occurred while decoding an
op-code.  An error message 1000 with an associated integer greater than
0 indicates that an op-code with that value was passed to Premier
Responder and was not recognized as a valid
op-code.]{style="font-size:10.0pt"}

 

The numeric error code in XML structured error messages is contained in
the *ErrorCode* element.  In the event of an invalid command, the
*ErrorCode* value would indicate the op-code which was received.  A
missing element in any of the  XML commands will result in an op-code of
1000 plus the command number and an *ErrorCode* of 0.  [As an example,
an element missing from the Set Caller (op-code 7) command, would result
in the following response from Premier
Responder:]{style="font-size:10.0pt"}

> \<Message\>\
>     \<OpCode\>1007\</OpCode\>\
>     \<ErrorCode\>0\</ErrorCode\>\
> \</Message\>

[Note ]{style="font-size:10.0pt"}[that Premier Responder can process
multiple commands at the same time. If Premier Responder receives a
byte-stream containing multiple messages, any of which contain an error,
it will abort the processing of those commands that contain errors and
respond with error messages for each erroneous command.  Commands in the
stream that don't contain errors will be
processed.]{style="font-size:10.0pt"}

**[ ]{style="font-size:10.0pt"}**

**[Premier Responder Events]{style="font-size:11.0pt"}**

[ ]{style="font-size: 10.0pt"}

[Version 3.0 of the Premier Responder ]{style="font-size: 10.0pt"} [API
includes the events listed in Table 2.  The Associated Data column of
the table includes the data type and XML element name for each data
item.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[Table 2 - Premier Responder Events]{style="font-size:10.0pt"}**

[ ]{style="font-size:10.0pt"}

::: {align="center"}
+-----------------------+-----------------------+-----------------------+
| **[Event              | **[Event]{style=      | **[Associated         |
| Code]{style=          | "font-size:10.0pt"}** | Data]{style=          |
| "font-size:10.0pt"}** |                       | "font-size:10.0pt"}** |
+-----------------------+-----------------------+-----------------------+
| [2001]{styl           | [Caller Name has      | *[CaseNumber]{style=  |
| e="font-size:10.0pt"} | changed]{styl         | "font-size:10.0pt"}*[ |
|                       | e="font-size:10.0pt"} | as                    |
|                       |                       | String]{styl          |
|                       |                       | e="font-size:10.0pt"} |
|                       |                       |                       |
|                       |                       | *[CallerName]{style=  |
|                       |                       | "font-size:10.0pt"}*[ |
|                       |                       | as                    |
|                       |                       | String]{styl          |
|                       |                       | e="font-size:10.0pt"} |
+-----------------------+-----------------------+-----------------------+
| [2002]{styl           | [Location has         | *[CaseNumber]{style=  |
| e="font-size:10.0pt"} | changed]{styl         | "font-size:10.0pt"}*[ |
|                       | e="font-size:10.0pt"} | as                    |
|                       |                       | String]{styl          |
|                       |                       | e="font-size:10.0pt"} |
|                       |                       |                       |
|                       |                       | *[Location]{style=    |
|                       |                       | "font-size:10.0pt"}*[ |
|                       |                       | as                    |
|                       |                       | String]{styl          |
|                       |                       | e="font-size:10.0pt"} |
+-----------------------+-----------------------+-----------------------+
| [2003]{styl           | [Phone Number has     | *[CaseNumber]{style=  |
| e="font-size:10.0pt"} | changed]{styl         | "font-size:10.0pt"}*[ |
|                       | e="font-size:10.0pt"} | as                    |
|                       |                       | String]{styl          |
|                       |                       | e="font-size:10.0pt"} |
|                       |                       |                       |
|                       |                       | *[PhoneNumber]{style= |
|                       |                       | "font-size:10.0pt"}*[ |
|                       |                       | as                    |
|                       |                       | String]{styl          |
|                       |                       | e="font-size:10.0pt"} |
+-----------------------+-----------------------+-----------------------+
| [2004]{styl           | [Emergency Type has   | *[CaseNumber]{style=  |
| e="font-size:10.0pt"} | changed]{styl         | "font-size:10.0pt"}*[ |
|                       | e="font-size:10.0pt"} | as                    |
|                       |                       | String]{styl          |
|                       |                       | e="font-size:10.0pt"} |
|                       |                       |                       |
|                       |                       | *[                    |
|                       |                       | EmergencyType]{style= |
|                       |                       | "font-size:10.0pt"}*[ |
|                       |                       | as                    |
|                       |                       | Integer]{styl         |
|                       |                       | e="font-size:10.0pt"} |
+-----------------------+-----------------------+-----------------------+
| [2005]{styl           | [Caller Complaint has | *[CaseNumber]{style=  |
| e="font-size:10.0pt"} | changed]{styl         | "font-size:10.0pt"}*[ |
|                       | e="font-size:10.0pt"} | as                    |
|                       |                       | String]{styl          |
|                       |                       | e="font-size:10.0pt"} |
|                       |                       |                       |
|                       |                       | *[Ca                  |
|                       |                       | llerComplaint]{style= |
|                       |                       | "font-size:10.0pt"}*[ |
|                       |                       | as                    |
|                       |                       | Integer]{styl         |
|                       |                       | e="font-size:10.0pt"} |
|                       |                       |                       |
|                       |                       | *                     |
|                       |                       | [ProblemCodes]{style= |
|                       |                       | "font-size:10.0pt"}*[ |
|                       |                       | as List               |
|                       |                       | (optional)]{styl      |
|                       |                       | e="font-size:10.0pt"} |
+-----------------------+-----------------------+-----------------------+
| [2006]{styl           | [Priority Type has    | *[CaseNumber]{style=  |
| e="font-size:10.0pt"} | changed]{styl         | "font-size:10.0pt"}*[ |
|                       | e="font-size:10.0pt"} | as                    |
|                       |                       | String]{styl          |
|                       |                       | e="font-size:10.0pt"} |
|                       |                       |                       |
|                       |                       | *                     |
|                       |                       | [PriorityType]{style= |
|                       |                       | "font-size:10.0pt"}*[ |
|                       |                       | as                    |
|                       |                       | String]{styl          |
|                       |                       | e="font-size:10.0pt"} |
+-----------------------+-----------------------+-----------------------+
| [2007]{styl           | [Call State has       | *[CaseNumber]{style=  |
| e="font-size:10.0pt"} | changed]{styl         | "font-size:10.0pt"}*[ |
|                       | e="font-size:10.0pt"} | as                    |
|                       |                       | String]{styl          |
|                       |                       | e="font-size:10.0pt"} |
|                       |                       |                       |
|                       |                       | *[CallState]{style=   |
|                       |                       | "font-size:10.0pt"}*[ |
|                       |                       | as                    |
|                       |                       | Integer]{styl         |
|                       |                       | e="font-size:10.0pt"} |
+-----------------------+-----------------------+-----------------------+
| [2010-2033]{styl      | [Answer has           | *[CaseNumber]{style=  |
| e="font-size:10.0pt"} | changed]{styl         | "font-size:10.0pt"}*[ |
|                       | e="font-size:10.0pt"} | as                    |
|                       |                       | String]{styl          |
|                       |                       | e="font-size:10.0pt"} |
|                       |                       |                       |
|                       |                       | *[Answer]{style=      |
|                       |                       | "font-size:10.0pt"}*[ |
|                       |                       | as                    |
|                       |                       | String]{styl          |
|                       |                       | e="font-size:10.0pt"} |
+-----------------------+-----------------------+-----------------------+
| [2100]{styl           | [Narrative            | *[CaseNumber]{style=  |
| e="font-size:10.0pt"} | Text]{styl            | "font-size:10.0pt"}*[ |
|                       | e="font-size:10.0pt"} | as                    |
|                       |                       | String]{styl          |
|                       |                       | e="font-size:10.0pt"} |
|                       |                       |                       |
|                       |                       | *[Narrative]{style=   |
|                       |                       | "font-size:10.0pt"}*[ |
|                       |                       | as                    |
|                       |                       | String]{styl          |
|                       |                       | e="font-size:10.0pt"} |
+-----------------------+-----------------------+-----------------------+
| [2101]{styl           | [Vital Point          | *[CaseNumber]{style=  |
| e="font-size:10.0pt"} | Change]{styl          | "font-size:10.0pt"}*[ |
|                       | e="font-size:10.0pt"} | as                    |
|                       |                       | String]{styl          |
|                       |                       | e="font-size:10.0pt"} |
|                       |                       |                       |
|                       |                       | *[Question]{style=    |
|                       |                       | "font-size:10.0pt"}*[ |
|                       |                       | as                    |
|                       |                       | String]{styl          |
|                       |                       | e="font-size:10.0pt"} |
|                       |                       |                       |
|                       |                       | *[EntryType]{style=   |
|                       |                       | "font-size:10.0pt"}*[ |
|                       |                       | as                    |
|                       |                       | Integer]{styl         |
|                       |                       | e="font-size:10.0pt"} |
|                       |                       |                       |
|                       |                       | *[Entry]{style=       |
|                       |                       | "font-size:10.0pt"}*[ |
|                       |                       | as                    |
|                       |                       | String]{styl          |
|                       |                       | e="font-size:10.0pt"} |
+-----------------------+-----------------------+-----------------------+
| [2102]{styl           | Send SMS Text         | *[CaseNumber]{style=  |
| e="font-size:10.0pt"} |                       | "font-size:10.0pt"}*[ |
|                       |                       | as                    |
|                       |                       | String]{styl          |
|                       |                       | e="font-size:10.0pt"} |
|                       |                       |                       |
|                       |                       | [ *SmsText* as        |
|                       |                       | String]{styl          |
|                       |                       | e="font-size:10.0pt"} |
+-----------------------+-----------------------+-----------------------+
:::

[ ]{style="font-size:10.0pt"}

[Events 2001 through 2003 are enabled by key-press
events]{style="font-size:10.0pt"}[ within the caller name, location, and
phone number text boxes located on the general questions tab of the
]{style="font-size:10.0pt"}[ Premier
Responder]{style="font-size:10.0pt"}[ active call window.  The enabled
event is then generated when the ]{style="font-size:10.0pt"}[text box
loses focus.  These events are not triggered when setting the caller,
location, or phone number through the API.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Events 2004 and 2005 are generated by click-events within
]{style="font-size:10.0pt"}[the emergency type and caller complaint
combo-boxes located on the general questions tab of the Premier
Responder ]{style="font-size:10.0pt"} [ active call
window]{style="font-size:10.0pt"}[.  These events are not triggered when
setting the emergency type or caller complaint through the API. 
]{style="font-size:10.0pt"} [Note that event 2005 problem codes are
optional and can be enabled with a configuration
setting.]{style="font-size: 10.0pt; font-family: Times New Roman"}

[ ]{style="font-size:10.0pt"}

[Event 2006 is generated by a click-event within the data
]{style="font-size:10.0pt"}[tree located on the priority tab of the
Premier Responder ]{style="font-size:10.0pt"}[ active call
window]{style="font-size:10.0pt"}[.  This event is not triggered when
setting the priority through the API.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Event 2007 is ]{style="font-size:10.0pt"}[triggered when a call's state
has changed.  The associated integer is of value 1 when the user has
initiated a new call.  An associated integer of value 2 indicates that
the user has ended the current call.  This event is not triggered when a
call is started or ended using the API.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Events 2010 up to 2033 are triggered when the user changes an answer to
one of the general questions.  The general questions are located on the
general questions tab of the Premier Responder
]{style="font-size:10.0pt"} [ active call
window]{style="font-size:10.0pt"}[ and do not include emergency
location, caller name, caller phone number, or emergency type.  The
question to which an answer has been changed can be obtained simply be
subtracting 2010 from the event number.  These events are not generated
when a general question is set using the API.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Event 2100 is triggered when a comment is entered using the narrative
dialog window or when a vital point entry is made and the vital point
narrative is configured to send the entry, question + entry, or job
text.  This event is also triggered when a medical procedure loads in
the viewer via the active call window toolbar buttons, a general
question or vital point entry, or a Med Set Procedure (op code 28) API
command from CAD.  Optionally, the 2100 op code can be configured to
trigger on an SOP completed or skipped action or an ERG selected
material, guide or placard.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Event 2101 is triggered when a vital point entry is made and the vital
point narrative is configured to send the question + entry type +
entry.  The entry type is indicated by an integer value where: 1 =
yes/no check box selection, 2 = text box entry, 3 = drop down list
selection.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

Event 2102 occurs when one of the send buttons adjoining the questions
on the All Caller\'s Interrogation and Vital Points tabs is selected or
the Send button on the texting panel of the active call window is
selected.

[ ]{style="font-size:10.0pt"}

[All events follow ]{style="font-size:10.0pt"}[the prescribed command
format. As an example, if the user changes the name of the caller to
"John" for case number one, Premier Responder would generate an event
and send the following byte-stream:]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

  -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- --------------------------------
  [07]{style="font-size:10.0pt"}   [D1]{style="font-size:10.0pt"}   [00]{style="font-size:10.0pt"}   [01]{style="font-size:10.0pt"}   [31]{style="font-size:10.0pt"}   [00]{style="font-size:10.0pt"}   [04]{style="font-size:10.0pt"}   [4A]{style="font-size:10.0pt"}   [6F]{style="font-size:10.0pt"}   [68]{style="font-size:10.0pt"}   [6E]{style="font-size:10.0pt"}   [FF]{style="font-size:10.0pt"}   [FF]{style="font-size:10.0pt"}
  -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- -------------------------------- --------------------------------

[ ]{style="font-size:10.0pt"}

[where 07 D1 is ]{style="font-size:10.0pt"}[the event number, 00 01 is
the length of the case number string, 31 is the case number, 00 04 is
the length of the caller name string, 4A 6F 68 6E is the caller's name,
and FF FF is the command footer.]{style="font-size:10.0pt"}

 

The XML equivalent of the previous Caller Name changed event example
would look as follows:

> \<Message\>\
>     \<OpCode\>2001\</OpCode\>\
>     \<CaseNumber\>1\</CaseNumber\>\
>     \<CallerName\>John\</CallerName\>\
> \</Message\>

**[General Op-codes]{style="font-size:11.0pt"}**

[ ]{style="font-size:10.0pt"}

[Version 3.0 of the Premier Responder API supports 51 different op-codes
which are defined in this section.  Each definition contains the
following:]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

-   [op-code value]{style="font-size: 10.0pt"}
-   [command name]{style="font-size: 10.0pt"}
-   [input parameters and return values, including
    ...]{style="font-size: 10.0pt; font-family: Times New Roman"}
    -   [XML element name]{style="font-size:10.0pt"}
    -   [data type]{style="font-size:10.0pt"}
-   [command description]{style="font-size: 10.0pt"}

 

[The commands that compose version 3.0 of the Premier Responder API are
as follows:]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[1]{style="font-size:10.0pt"}**[             
**Login**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[ *AccessLevel* ]{style="font-size:10.0pt"} [as
integer]{style="font-size:10.0pt"}

[*UserName* as
]{style="font-size:10.0pt"}[string]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[Success]{style="font-size:10.0pt; font-style:italic"}[
]{style="font-size:10.0pt"}[as boolean]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: ]{style="font-size:10.0pt"}[This command logs a user in.  Premier
Responder currently supports two access levels: 0 being a user and 1
being an administrator.  Administrators have access to the SOP and User
editing programs.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[2]{style="font-size:10.0pt"}**[             
**Logout**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[None]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[Success]{style="font-size:10.0pt; font-style:italic"}[
]{style="font-size:10.0pt"}[as boolean]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: ]{style="font-size:10.0pt"}[This function logs the current user
out.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[3]{style="font-size:10.0pt"}**[              **Get
User**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[None]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[UserName]{style="font-size:10.0pt; font-style:italic"}[
]{style="font-size:10.0pt"}[as string]{style="font-size:10.0pt"}

[AccessLevel]{style="font-size:10.0pt; font-style:italic"}[
]{style="font-size:10.0pt"}[as integer]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: This ]{style="font-size:10.0pt"}[command retrieves the identity
of the current Premier Responder user.]{style="font-size:
10.0pt"}

[ ]{style="font-size:10.0pt"}

**[4]{style="font-size:10.0pt"}**[              **Begin
Call**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[ *CaseNumber* ]{style="font-size:10.0pt"} [as
string]{style="font-size:10.0pt"}

[ *StartDate* ]{style="font-size:10.0pt"} [as
date]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[Success]{style="font-size:10.0pt; font-style:italic"}[
]{style="font-size:10.0pt"}[as boolean]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: ]{style="font-size:10.0pt"}[This command initiates a new case.
 ]{style="font-size:10.0pt"}[Sending an empty string for Case Number
]{style="font-size:10.0pt"}[indicates that Premier Responder is to
generate it internally.  The command must specify the Start Date.
 Premier Responder will return a failure indication if it is already
processing a case.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[5]{style="font-size:10.0pt"}**[              **End
Call**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[ *EndDate* ]{style="font-size:10.0pt"} [as
date]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[Success]{style="font-size:10.0pt; font-style:italic"}[
]{style="font-size:10.0pt"}[as boolean]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: This command terminates processing of the current case and saves
the call information to the cases.mdb database file.  The calling
program must specify the End Date.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[6]{style="font-size:10.0pt"}**[              **Get
Report**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[None]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[ReportContents]{style="font-size:10.0pt; font-style:italic"}[
]{style="font-size:10.0pt"}[as string]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: This command returns a string containing all of the information
contained in the report.  Use this command to retrieve responses to
questions and SOP actions, etc.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[7]{style="font-size:10.0pt"}**[              **Set
Caller**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[*CallerName* as string]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*Success* as boolean]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: ]{style="font-size:10.0pt"}[This command sets the current
caller's name.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[8]{style="font-size:10.0pt"}**[              **Get
Caller**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[None]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*CallerName* as string]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: This command retrieves the current caller's
name.]{style="font-size:10.0pt"}

[\
**9**              **Set Location**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[*Location* as string]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*Success* as boolean]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: This command set the current location.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[10]{style="font-size:10.0pt"}**[           **Get
Location**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[None]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*Location* as ]{style="font-size:10.0pt"}[string]{style="font-size:
10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: This command retrieves the current
location.]{style="font-size:10.0pt"}

[\
**11**           **Set Phone Number**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

*PhoneNumber*[ as
]{style="font-size:10.0pt"}[string]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*Success* as boolean]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: This command sets the current phone
number.]{style="font-size:10.0pt"}

[\
**12**           **Get Phone Number**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[None]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*PhoneNumber* as
]{style="font-size:10.0pt"}[string]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: This command retrieves ]{style="font-size:10.0pt"}[the current
phone number.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[13]{style="font-size:10.0pt"}**[           **Get Category
List**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[None]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*Categories* as list]{style="font-size:10.0pt"}

**[ ]{style="font-size:10.0pt"}**

[Note: This command ]{style="font-size:10.0pt"}[returns a list of
emergency categories for which guide cards are present.  The list
consists of paired integer and string values which indicate the category
ID and name.  The default emergency categories are: 0 LE, 1 Med, and 2
Fire.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[14]{style="font-size:10.0pt"}**[           **Set
Category**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

*CategoryId*[ as integer]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*Success* as boolean]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: This command sets the emergency category of the currently active
call.  If a call is not ]{style="font-size:10.0pt"}[currently
active]{style="font-size:10.0pt"}[, then the default emergency category
is set.  Possible values for Category ID can be obtained using the Get
Category List command.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[15]{style="font-size:10.0pt"}**[           **Get
Category**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[None]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*CategoryId* as integer]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: ]{style="font-size:10.0pt"}[This command returns the emergency
category of the call appearing on the call-taker window.  If a call does
not appear on the call taker window, then the default emergency category
is returned.]{style="font-size:10.0pt"}

[\
**16**           **Get Complaint List**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

*CategoryId*[ as integer]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*Complaints* as list]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: This command ]{style="font-size:10.0pt"}[returns all complaints
that are available for the specified category.  Each list item includes
the complaint identification number together with a text
description.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[ 17]{style="font-size:10.0pt"}**[          **Set
Complaint**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

*ComplaintId*[ as integer]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*Success* as boolean]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: This command sets the complaint for the currently active call. 
If a call is not active then the command will fail.  Possible values for
Complaint ID can be obtained using the Get Complaint List
command.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[18]{style="font-size:10.0pt"}**[           **Get
Complaint**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[None]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*ComplaintId* as integer]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: This command returns the Complaint ID of the call appearing on
the call-taker window.  If a call does not appear on the call-taker
window or a complaint has not been selected then 9999 is
returned.]{style="font-size:10.0pt"}

[\
**19**           **Get Priority List**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

*ComplaintId*[ as integer]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*Priorities* as list]{style="font-size:10.0pt"}

[*Symptoms* as list]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: This command returns two lists.  The first list contains the
priorities for the emergency category of the currently active call.  If
a call is not active then the default emergency category is used.  The
second list contains the symptoms associated with the specified
Complaint ID]{style="font-size:10.0pt"}[ and previously determined
emergency category]{style="font-size:10.0pt"}[.  Each priority list item
includes the priority level and optional priority code, if entered,
otherwise the priority name.  The symptom list items include priority
level that the symptom is associated with and the symptom
name.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[20]{style="font-size:10.0pt"}**[           **Set
Priority**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[*Symptom* as string]{style="font-size:
10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*Success* as boolean]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: ]{style="font-size:10.0pt"}[This command is used to set the
priority of the currently active call.  The Symptom parameter can either
be a symptom name, a priority name, or optional priority code.  If a
call is not active or the specified Symptom parameter is invalid then
the command will fail.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[21]{style="font-size:10.0pt"}**[           **Get
Priority**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[None]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*Symptom* as string]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: Use this command to retrieve the optional priority code for the
node selected on the priority tab of the Premier Responder
]{style="font-size:10.0pt"}[ active call
window]{style="font-size:10.0pt"}[.  If the priority code was not
entered then the node text is returned instead.  The node text may
indicate either a priority or symptom name.  If a call is not active or
a node has not been selected then an empty string is
returned.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[22]{style="font-size:10.0pt"}**[           **View
Tab**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

*TabIndex*[ as integer]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*Success* as ]{style="font-size:10.0pt"}[boolean]{style="font-size:
10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: The active call window currently includes 9 tabs which are
numbered from 0 to 8.  Each tab is configurable by call type with a
custom label.  All but the All Caller\'s Interrogation tab can be
hidden.  Tabs 0 to 2 are specialized and contain the all caller\'s
interrogation questions, vital point questions and priorities.  Tabs 3
to 6 are for viewing any rich text content such as pre-arrival
instructions, call-taker actions, dispatcher actions or background
information.  Tabs 7 and 8 are also specialized and are for viewing the
short report and standard operating procedures.  The return value will
indicate success if the specified tab is valid and is not
hidden.]{style="font-size: 10.0pt; font-family: Times New Roman"}

[ ]{style="font-size:10.0pt"}

**[23]{style="font-size:10.0pt"}**[           **Get
Tab**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[None]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*TabId* as byte where:]{style="font-size:10.0pt"}

-   0 = General Questions

-   1 = Vital Points

-   2 = Priority

-   3 = Call-Taker Actions

-   4 = Pre-Arrival

-   5 = Dispatcher Actions

-   6 = Background

-   7 = Short Report

-   8 = SOP

-   255 = Call Not Active

[ ]{style="font-size:10.0pt"}

[Note: Use ]{style="font-size:10.0pt"}[this command to retrieve the
currently viewed tab.]{style="font-size:
10.0pt"}

[\
**24**           **SOP Get Procedure List**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[None]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*ProcedureList* as list]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: ]{style="font-size:10.0pt"}[This command returns a list of all
available SOPs.  SOPs are referred to by their associated data in the
returned list.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[25]{style="font-size:10.0pt"}**[           **SOP Set
Procedure**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

*ProcedureId*[ as
]{style="font-size:10.0pt"}[integer]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*Success* as Boolean]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: Use ]{style="font-size:10.0pt"}[this command to set the current
SOP.]{style="font-size:
10.0pt"}

[ ]{style="font-size:10.0pt"}

**[26]{style="font-size:10.0pt"}**[           **SOP Get
Procedure**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[None]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*ProcedureId* as integer]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: Use this command to retrieve ]{style="font-size:10.0pt"}[the
current SOP procedure that is being viewed.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[27]{style="font-size:10.0pt"}**[           **Med Get Procedure
List**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[None]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[ *CategoryName1* as string]{style="font-size:10.0pt"}

[*CategoryList1* as list]{style="font-size:10.0pt"}

[ *CategoryName2* as string]{style="font-size:10.0pt"}

[*CategoryList2* as list]{style="font-size:10.0pt"}

[ *CategoryName3* as string]{style="font-size:10.0pt"}

[*CategoryList3* as list]{style="font-size:10.0pt"}

[ *CategoryName4* as string]{style="font-size:10.0pt"}

[*CategoryList4* as list]{style="font-size:10.0pt"}

[ *CategoryName5* as string]{style="font-size:10.0pt"}

[*CategoryList5* as list]{style="font-size:10.0pt"}

[ *CategoryName6* as string]{style="font-size:10.0pt"}

[*CategoryList6* as list]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: This command returns a name and list for each category of the
]{style="font-size:10.0pt"}[med]{style="FONT-SIZE: 10pt"}[ical
instructions, these being: ]{style="font-size:10.0pt"}[CPR, Childbirth,
Obstructed Airway, and Airway Control.  The list data items include a
procedure id and a procedure name.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[28]{style="font-size:10.0pt"}**[           **Med Set
Procedure**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

*ProcedureId*[ as integer]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*Success* as boolean]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: ]{style="font-size:10.0pt"}[This command works only after the
window has been displayed, otherwise a boolean false is returned. Use
this function to set the current medical
procedure.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[29]{style="font-size:10.0pt"}**[           **Med Get
Procedure**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[None]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*ProcedureId* as integer]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: Use this ]{style="font-size:10.0pt"}[command to retrieve the
currently viewed medical procedure. A return value of zero indicates
that no procedure is currently being viewed.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[30]{style="font-size:10.0pt"}**[          
]{style="font-size:10.0pt"} **[Med Set
Window]{style="font-size:10.0pt"}**

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

*Visible*[ as boolean]{style="font-size:10.0pt"}

[*Top* as integer]{style="font-size:10.0pt"}

[*Left* as integer]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*Success* as ]{style="font-size:10.0pt"}[boolean]{style="font-size:
10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: The Top and Left units are given in twips.  Passing 0 for either
indicates to keep the current value for that parameter.  Use this
command to show,
]{style="font-size:10.0pt"}[hide]{style="font-size:10.0pt"}[, or
]{style="font-size:10.0pt"}[position]{style="font-size:10.0pt"}[ the
medical Instructions window.]{style="font-size:10.0pt"}[  A call must be
active in order to obtain a successful
result.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[31]{style="font-size:10.0pt"}**[           **ERG Set
Window**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[*Visible* as ]{style="font-size:10.0pt"}[boolean]{style="font-size:
10.0pt"}

[*Top* as integer]{style="font-size:10.0pt"}

[*Left* as ]{style="font-size:10.0pt"}[integer]{style="font-size:
10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*Success* as boolean]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: ]{style="font-size:10.0pt"}[ The Top and Left units are given in
twips.  Passing 0 for either ]{style="font-size:10.0pt"} [indicates to
keep the current value for that parameter.  Use this command to show,
]{style="font-size:10.0pt"}[ hide]{style="font-size:10.0pt"}[, or
]{style="font-size:10.0pt"}[ position]{style="font-size:10.0pt"}[ the
ERG window.  A call must be active in order to obtain a successful
result.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[32]{style="font-size:10.0pt"}**[           **Set Main
Window**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters]{style="font-size:10.0pt"}

[*Wrapped* as boolean]{style="font-size:10.0pt"}

[*Top* as integer]{style="font-size:10.0pt"}

[*Left* as integer]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*Success* as boolean]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: ]{style="font-size:10.0pt"}[ The Top and Left units are given in
twips.  Passing 0 for either ]{style="font-size:10.0pt"} [indicates to
keep the current value for that parameter otherwise they are
used]{style="font-size:10.0pt"}[ to reposition the
]{style="font-size:10.0pt"} [Premier Responder main window.  The Wrapped
flag has no effect and serves only as a place holder for backward
compatibility with existing interfaces.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[33]{style="font-size:10.0pt"}**[           **Lock
Interface**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[*Lock* as boolean]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*Success* as boolean]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: This command disables the Login/Logout and Begin/End Call
features of the Premier Responder user
interface.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[34]{style="font-size:10.0pt"}**[          
**Shutdown**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[None]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*Success* as boolean]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note:      This command is used to terminate Premier Responder.  It is
not guaranteed to return a value.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[35]{style="font-size:10.0pt"}**[           **Get Case
Number**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[None]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*CaseNumber* as string]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: This command retrieves the current Case
Number.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}**[36]{style="font-size:10.0pt"}**[          
**Get Complaint Name**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[None]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*ComplaintName* as string]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: This command retrieves the current
Complaint.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[ 37]{style="font-size:10.0pt"}**[           **Get Priority
Symptom**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[None]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*Symptom* as string]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Note: This command returns the selected symptom for the call in
progress or, if waiting, for the previously completed
call.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}**[38]{style="font-size:10.0pt"}**[          
**Get Actual Priority**]{style="font-size:10.0pt"}

[  ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[None]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*Priority* as string]{style="font-size:10.0pt"}

[  ]{style="font-size:10.0pt"}

[Note: This command ]{style="font-size:10.0pt"}[ returns
]{style="font-size:10.0pt"}[the selected priority category for the call
in progress or, if waiting, for the previously completed
call.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}**[39]{style="font-size:10.0pt"}**[          
**Get Short Report**]{style="font-size:10.0pt"}

[  ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[None]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[ReportContents]{style="font-size:10.0pt; font-style:italic"}[ as
string]{style="font-size:10.0pt"}
:::::

[ ]{style="font-size:10.0pt"}

[Note: This command ]{style="font-size:10.0pt"}[ returns
]{style="font-size:10.0pt"}[the short report for the call in progress
or, if waiting, for the previously completed
call.]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

**[40]{style="font-size:10.0pt"}**[           **Set Complaint
Code**]{style="font-size: 10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:
10.0pt"}

[*ProblemCode* Text as string]{style="font-size: 10.0pt"}

[Return:]{style="font-size:
10.0pt"}

[*Success* as boolean]{style="font-size:
10.0pt"}

**[ ]{style="font-size:10.0pt"}**

[Note: This command sets the complaint using a code that has been
associated with one of the complaints.]{style="font-size:
10.0pt"}

 

**[41]{style="font-size:10.0pt"}**[           **Get Complaint
Codes**]{style="font-size: 10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:
10.0pt"}

[None]{style="font-size: 10.0pt"}

[Return:]{style="font-size:
10.0pt"}

[Problem Codes as list]{style="font-size: 10.0pt"}

**[ ]{style="font-size:10.0pt"}**

[Note: This command retrieves the problem codes associated with the
current Complaint.  Note that a complaint can have more than one
associated code.  Each list item includes the complaint ID number
together with the problem code.]{style="font-size:
10.0pt"}

 

**[42]{style="font-size:10.0pt"}**[           **Get Complaint Code
List**]{style="font-size: 10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:
10.0pt"}

[*CategoryId* as integer]{style="font-size:
10.0pt"}

[Return:]{style="font-size:
10.0pt"}

[*ProblemCodes* as list]{style="font-size: 10.0pt"}

**[ ]{style="font-size:10.0pt"}**

[Note: This command ]{style="font-size: 10.0pt"} [returns all complaints
and associated problem codes that are available under the specified
category.  Note that a complaint can have more than one associated
code.  Each list item includes the complaint ID number together with the
problem code.]{style="font-size:10.0pt"}

 

**[4]{style="font-size:10.0pt"}3**[          
]{style="font-size: 10.0pt"}**[Get Alternate
Port]{style="font-size: 10.0pt; font-family: Times New Roman"}**

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:
10.0pt"}

[None]{style="font-size: 10.0pt"}

[Return:]{style="font-size:
10.0pt"}

[*PortNumber* as
long]{style="font-size: 10.0pt; font-family: Times New Roman"}

**[ ]{style="font-size:10.0pt"}**

[Note: ]{style="font-size: 10.0pt"} [In addition to port 2021, Premier
Responder also monitors a random port that is determined by the system
when the software loads.  This command returns the alternate port
Premier Responder listens on for connection requests.  The purpose of
the alternate port is to provide each instance of Premier Responder a
unique port number to monitor, when there are multiple instances of the
software
running]{style="font-size: 10.0pt; font-family: Times New Roman"}[.]{style="font-size:10.0pt"}

 

**[44]{style="font-size:10.0pt"}**[          
]{style="font-size: 10.0pt"}**[Set Window
State]{style="font-size: 10.0pt; font-family: Times New Roman"}**

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:
10.0pt"}

*WindowState* as integer

[Return:]{style="font-size:
10.0pt"}

*Success* as boolean

**[ ]{style="font-size:10.0pt"}**

[Note: This command sets the state of all open Premier Responder
windows]{style="font-size: 10.0pt"}[.  The possible values for Window
State are: 0 = Normal, 1 = Minimized.]{style="font-size:10.0pt"}

 

**[45]{style="font-size:10.0pt"}**[           **Get Settings
List**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[None]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*SettingsList* as list]{style="font-size:10.0pt"}

**[ ]{style="font-size:10.0pt"}**

[Note: Returns a list of the settings contained in the configuration
database.]{style="font-size:10.0pt"}

 

**[46]{style="font-size:10.0pt"}**[           **Read
Setting**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[*SettingName* as string]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*SettingName* as string]{style="font-size:10.0pt"}

[*SettingValue* as string]{style="font-size:10.0pt"}

**[ ]{style="font-size:10.0pt"}**

[Note: Returns the name and value of the specified
setting.]{style="font-size:10.0pt"}

 

**[47]{style="font-size:10.0pt"}**[           **Write
Setting**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[*SettingName* as string]{style="font-size:10.0pt"}

[*SettingValue* as string]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*Success* as boolean]{style="font-size:10.0pt"}

**[ ]{style="font-size:10.0pt"}**

[Note: ]{style="font-size:10.0pt"}[ Updates specified setting value in
the configuration database.  Changes are not applied until software is
restarted or Apply Setting Changes API command is sent. 
]{style="font-size:10.0pt"}Be aware the [Premier Responder software does
not currently perform any validation of the setting value, therefore
this responsibility must be assumed by CAD.]{style="font-size:10.0pt"}

 

**[48]{style="font-size:10.0pt"}**[           **Apply Setting
Changes**]{style="font-size:10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[None]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*Success* as boolean]{style="font-size:10.0pt"}

**[ ]{style="font-size:10.0pt"}**

[Note: All settings contained in the configuration database are
reapplied.]{style="font-size:10.0pt"}

 

**[49]{style="font-size:10.0pt"}**[           **Set Case
Number**]{style="font-size: 10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[*CaseNumber* as string]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*Success* as boolean]{style="font-size:10.0pt"}

**[ ]{style="font-size:10.0pt"}**

[Note: Sets the case number to the specified value if a call is in
progress.  The command fails if a call is not in
progress.]{style="font-size:10.0pt"}

 

**[50]{style="font-size:10.0pt"}**[           **Get Version
Number**]{style="font-size: 10.0pt"}

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

[None]{style="font-size:10.0pt"}

[Return:]{style="font-size:10.0pt"}

[*VersionNumber* as string]{style="font-size:10.0pt"}

**[ ]{style="font-size:10.0pt"}**

[Note: Returns the Premier Responder software four part version number
in the format **MAJ.MIN.REV.BLD** where **MAJ** is the major number,
**MIN** is the minor number, **REV** is the revision number and **BLD**
is the build number.]{style="font-size:10.0pt"}

 

**[51]{style="font-size:10.0pt"}**[          
]{style="font-size: 10.0pt"}**Show SMS Text**

[ ]{style="font-size:10.0pt"}

[Parameters:]{style="font-size:10.0pt"}

*SmsText* as string

[Return:]{style="font-size:10.0pt"}

[Success as boolean]{style="font-size:10.0pt"}

**[ ]{style="font-size:10.0pt"}**

[Note: Text to 9-1-1 functionality is enabled then text is displayed in
dialog box of active call window texting
panel.]{style="font-size:10.0pt"}
