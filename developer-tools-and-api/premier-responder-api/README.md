# Premier Responder API

|                               |
| ----------------------------- |
| **Premier Responder API 3.0** |

**Proprietary Information**

This document is\
considered Proprietary Information by Darwin Global, LLC,\
(dba Smart Horizons), and is subject to the dictates of the Non Disclosure\
Agreement signed by the recipient.

&#x20;

**Introduction**

The\
Premier Responder Application Program Interface\
(API) is built on top of the TCP/IPnetworking protocol.  Premier\
Responder\
listens on a\
configurable port and a random port for a connection request from a computer\
aided dispatch (CAD) system.  The configurable port defaults to 2021 and is\
specified on the [CAD Interface\
configuration screen](../../Cad%20Interface%20Settings.htm).  The random port is obtainable with the Get Alternate Port\
API command.  Version 3.0 of the Premier Responder API supports 51 externally callable\
commands, an error notification for each command, and 11 event types that\
Premier Responder can generate during\
the course of a call.

&#x20;

**Message Structures**

&#x20;

API version 3.0\
includes support for both byte array and XML structured messages.  The default message structure consists of data\
values packed into a byte array with the values represented by one of seven\
possible data types.  XML structured messages include a root element with\
one or more nested\
child elements serialized to a string.  Receipt of an\
XML structured message enables XML structured events and acknowledgements from\
9-1-1 Adviser.

&#x20;

**Default Data Types**

Data values contained in\
byte array\
structured messages consists of the following\
data types: byte, boolean, integer, long, date, string and list. The data types\
described in this section are used by the API.

&#x20;

_Bytes_ are\
an integer value from 0 to 255.

&#x20;

_Booleans_ are\
single bytes that are of value zero if they are false. Any value other than\
zero represents a true.

&#x20;

_Integers_ are\
two bytes in length and are nothing more than the binary representation of\
their values. As an example, the value 3024 would be passed as the following\
byte stream:

&#x20;

|    |    |
| -- | -- |
| 0B | D0 |

&#x20;

_Longs_ are\
four bytes in length and are also binary representations of their values. As\
an example, the value 10329345 would be passed as the following byte stream:

&#x20;

|    |    |    |    |
| -- | -- | -- | -- |
| 00 | 9D | 9D | 01 |

&#x20;

_Strings_ consist\
of an integer holding the size of the string followed by single-byte ASCII\
codes for each of the characters contained in the string. As an example, the\
string Hi would be sent as the following byte stream:

&#x20;

|    |    |    |    |
| -- | -- | -- | -- |
| 00 | 02 | 48 | 69 |

&#x20;

where 00 02 is the length of the string and 48 69is\
the string itself.

&#x20;

_Dates_ are\
fourteen bytes long. They are passed in the format MMDDYYYYHHMMSS which is\
broken down into single-byte ASCII codes for each of the values in the\
formatted string. As an example, the moment January 4, 199&#x38;**@** 5:30:26 p.m. would be formatted into 01041998173026 which would\
be passed as the following byte stream:

&#x20;

|    |    |    |    |    |    |    |    |    |    |    |    |    |    |
| -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- |
| 30 | 31 | 30 | 34 | 31 | 39 | 39 | 38 | 31 | 37 | 33 | 30 | 32 | 36 |

&#x20;

_Lists_ are an\
array of associated string and integer data. They begin with a leading integer\
that indicates the number of items in the list. The list follows with each\
list item consisting of an integer followed by a string. As an example, the\
following list would be passed as the next byte stream

&#x20;

|               |            |
| ------------- | ---------- |
| **Item Data** | **String** |
| 123           | ab         |
| 456           | cd         |

&#x20;

|    |    |    |    |    |    |    |    |    |    |    |    |    |    |
| -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- |
| 00 | 02 | 00 | 7B | 00 | 02 | 61 | 62 | 01 | C8 | 00 | 02 | 63 | 64 |

&#x20;

where 00 02 signifies the length of the list, 00 7B is the item data for the first element,\
00 02 is the length of the first string element, 61 62 is the first string, 01 C8 is\
the item data for the second element, 00 02 is the length of the second string element,\
and 63 64 is the second string.

&#x20;

**Default Command Format**

Premier Responder expects\
byte array structured\
commands to follow the same format. Any commands that do not follow the proper\
format wilt result in an error response from Premier Responder. Each command consists of a\
16-bit op-code followed by any data that is associated with the command. Every\
command must have a footer consisting of two bytes of value 255.

&#x20;

Take for example, the command required to set the callers name. The op-code for that command\
is 7. That particular command requires the name of the caller. If the callers\
name were Bob, the command to set the callers name in Premier Responder would be passed as the\
following byte stream,

&#x20;

|    |    |    |    |    |    |    |    |    |
| -- | -- | -- | -- | -- | -- | -- | -- | -- |
| 00 | 07 | 00 | 03 | 42 | 6F | 62 | FF | FF |

&#x20;

where 00 07 is the op-code, 00 03 is the length of the string containing the callers name, 42 6F 62 is the\
callers name, and FF FF is the command footer.

&#x20;

For this particular\
command, Premier Responder will respond with a boolean true or false, depending on the success\
of the operation. If this command were successfully executed,\
the byte stream\
sent in the reply would be as follows:

&#x20;

|    |    |    |    |    |
| -- | -- | -- | -- | -- |
| 00 | 07 | 01 | FF | FF |

&#x20;

where 00 07 is the\
command that Premier Responder is responding to, 01 is a boolean true, and FF FF is the\
command footer.

&#x20;

All responses from\
Premier Responder begin with the op-code that is being responded to. This is followed by\
any data associated with the response. All responses are terminated with the previously\
mentioned footer.

&#x20;

**XML Data Types**

Text values contained in the nested message elements are\
converted to an appropriate data type for processing therefore must adhere to\
the following guidelines.

_Byte, Integer, and Long_ data types are represented by one\
or more numeric characters.

_String_ data can be any text.

_Boolean_ states are indicated as follows:

*

True = non zero numeric character

*

False = zero numeric character.

_Date_ values are represented by a 14 character\
numeric string in the format\
MMDDYYYYHHMMSS where:

*

MM (month) = 1 to 12

*

DD (day) = 1 to 31

*

YYYY (year) = 0000 to 9999

*

HH (hour) = 0 to 23

*

MM (minute) = 0 to 59

*

SS (second) = 0 to 59

_List_ data is a numbered list with list items formatted as\
follows:

> Item number + Tab + Item description + Carriage Return + Line Feed

**XML Command Format**

XML commands include a _Message_ root element, a&#x6E;_&#x4F;pCode_ child element, and additional child elements as required. \
Using the previous Set Caller command example, the XML version would be as\
follows:

> &#x20;   7
>
> &#x20;   Bob

Again, Premier Responder will respond with a boolean true or false, depending on the success\
of the operation. On successfully executing the command,\
the XML version of\
the reply would be as follows:

> &#x20;   7
>
> &#x20;   1

**Op-codes**

As seen in Table 1, version 3.0 of the Premier Responder API has three specific categories into which\
communications between Premier Responder and external applications can fall.

&#x20;

**Table 1 -** **Op-code categories**

&#x20;

|                          |                          |
| ------------------------ | ------------------------ |
| **Op-code\*\*\*\*Range** | **Category**             |
| 1-999                    | General op-code          |
| 1000-1999                | Error messages           |
| 2000-2999                | Premier Responder events |

&#x20;

All categories follow the prescribed command format. General\
op-codes are called by external programs.

Error messages are\
sent from Premier Responder whenever an error occurs. Events are sent when the user affects\
a change in Premier Responder.

&#x20;

**Error Messages**

Error messages 1001-1999 correspond to op-codes called\
by external functions. Currently all error messages are sent in response to invalid\
data passed with an op-code. For example, if a program sends a boolean with\
op-code 7 instead of an integer, Premier Responder will respond with an error message 1007. Integers\
passed with Premier Responder indicate the number of errors encountered while extracting data\
from the byte-stream. A value of 0 indicates that the number of bytes of data was\
incorrect. As most extractions are aborted upon the first error, most values\
passed with error messages will be either 0 or 1. As an example, if Premier\
Responder encounters\
a data-length error while processing a Set Caller (op-code 7) command, it would\
respond with an error message as seen in the following byte-stream:

&#x20;

|    |    |    |    |    |    |
| -- | -- | -- | -- | -- | -- |
| 03 | EF | 00 | 00 | FF | FF |

&#x20;

where 03 EF is the error code, 00 00 is the associated\
integer, here indicating a data-length error, and FF FF is the command footer.

&#x20;

An error message 1000 with an associated integer of 0 indicates that an internal error\
occurred while decoding an op-code. An error message 1000 with an associated\
integer greater than 0 indicates that an op-code with that value was passed to\
Premier Responder\
and was not recognized as a valid op-code.

&#x20;

The numeric error code in XML structured error messages is\
contained in the _ErrorCode_ element.  In the event of an invalid\
command, the _ErrorCode_ value would indicate the op-code which was\
received.  A missing element in any of the  XML commands will result\
in an op-code of 1000 plus the command number and an _ErrorCode_ of 0. \
As an example, an element missing from the Set Caller\
(op-code 7) command, would result in the following response from Premier\
Responder:

> &#x20;   1007
>
> &#x20;   0

Note that\
Premier Responder\
can process multiple commands at the same time. If Premier Responder receives a byte-stream containing\
multiple messages, any of which contain an error, it will abort the processing of\
those commands that contain errors and respond with error messages for each erroneous\
command. Commands in the stream that dont contain errors will be processed.

**Premier Responder Events**

&#x20;

Version 3.0 of the Premier Responder\
API includes the events listed in Table 2.  The\
Associated Data column of the table includes the data type and XML element name\
for each data item.

&#x20;

**Table 2 - Premier**\
**Responder**\
**Events**

&#x20;

|                         |   |   |
| ----------------------- | - | - |
|                         |   |   |
| **Event Code**          |   |   |
| **Event**               |   |   |
| **Associated Data**     |   |   |
|                         |   |   |
| 2001                    |   |   |
| Caller Name has changed |   |   |
| _CaseNumber_            |   |   |
| as String               |   |   |

_CallerName_\
as String |\
|\
2002 |\
Location has changed |_CaseNumber_\
as String

_Location_\
as String |\
|\
2003 |\
Phone Number has changed |_CaseNumber_\
as String

_PhoneNumber_\
as String |\
|\
2004 |\
Emergency Type has changed |_CaseNumber_\
as String

_EmergencyType_\
as Integer |\
|\
2005 |\
Caller Complaint has changed |_CaseNumber_\
as String

_CallerComplaint_\
as Integer

_ProblemCodes_\
as List (optional) |\
|\
2006 |\
Priority Type has changed |_CaseNumber_\
as String

_PriorityType_\
as String |\
|\
2007 |\
Call State has changed |_CaseNumber_\
as String

_CallState_\
as Integer |\
|\
2010-2033 |\
Answer has changed |_CaseNumber_\
as String

_Answer_\
as String |\
|\
2100 |\
Narrative Text |_CaseNumber_\
as String

_Narrative_\
as String |\
\| 2101 | Vital Point\
Change |_CaseNumber_\
as String

_Question_\
as String

_EntryType_\
as Intege&#x72;_&#x45;ntry_\
as String |\
\| 2102 | Send SMS Text |_CaseNumber_\
as String

_SmsText_\
as String |

&#x20;

Events 2001 through 2003 are enabled by key-press\
events within the caller name, location,\
and phone number text boxes located on the general questions tab of the\
Premier Responder\
active call window. The enabled event is then generated when the text box loses focus. These events are not triggered\
when setting the caller, location, or phone number through the API.

&#x20;

Events 2004 and 2005 are generated by click-events within\
the emergency type and caller complaint\
combo-boxes located on the general questions tab of the Premier Responder\
active call window. These events\
are not triggered when setting the emergency type or caller complaint through\
the API. \
Note that event\
2005 problem codes are optional and can be enabled with a configuration setting.

&#x20;

Event 2006 is generated by a click-event within the\
data tree located on the priority tab of\
the Premier Responder active call window. This event is not triggered when setting the priority\
through the API.

&#x20;

Event 2007 is triggered\
when a calls state has changed. The associated integer is of value 1 when the\
user has initiated a new call. An associated integer of value 2 indicates that\
the user has ended the current call. This event is not triggered when a call\
is started or ended using the API.

&#x20;

Events 2010 up to 2033 are triggered when the user\
changes an answer to one of the general questions.  The general questions are\
located on the general questions tab of the Premier Responder\
active call window and do not include\
emergency location, caller name, caller phone number, or emergency type. The question\
to which an answer has been changed can be obtained simply be subtracting 2010\
from the event number. These events are not generated when a general question\
is set using the API.

&#x20;

Event 2100 is triggered when a comment is entered\
using the narrative dialog window or when a vital point entry is made and the\
vital point narrative is configured to send the entry, question + entry, or job\
text.  This event is also triggered when a medical procedure loads in the\
viewer via the active call window toolbar buttons, a general question or vital\
point entry, or a Med Set Procedure (op code 28) API command from CAD. \
Optionally, the 2100 op code can be configured to trigger on an SOP completed or\
skipped action or an ERG selected material, guide or placard.

&#x20;

Event 2101 is triggered when a vital point entry\
is made and the vital point narrative is configured to send the question + entry\
type + entry.  The entry type is indicated by an integer value where: 1 = yes/no\
check box selection, 2 = text box entry, 3 = drop down list selection.

&#x20;

Event 2102 occurs when one of the send buttons adjoining the\
questions on the All Caller's Interrogation and Vital Points tabs is selected or\
the Send button on the texting panel of the active call window is selected.

&#x20;

All events follow the\
prescribed command format. As an example, if the user changes the name of the\
caller to John for case number one, Premier Responder would generate an event and send the\
following byte-stream:

&#x20;

|    |    |    |    |    |    |    |    |    |    |    |    |    |
| -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- |
| 07 | D1 | 00 | 01 | 31 | 00 | 04 | 4A | 6F | 68 | 6E | FF | FF |

&#x20;

where 07 D1 is the\
event number, 00 01 is the length of the case number string, 31 is the case\
number, 00 04 is the length of the caller name string, 4A 6F 68 6E is the callers\
name, and FF FF is the command footer.

&#x20;

The XML equivalent of the previous Caller Name changed event\
example would look as follows:

> &#x20;   2001
>
> &#x20;   1
>
> &#x20;   John

**General Op-codes**

&#x20;

Version 3.0 of the Premier Responder API supports 51 different op-codes\
which are defined in this section. Each definition contains the following:

&#x20;

* op-code value
* command name
* input\
  parameters and return values, including
  * XML element name
  * data type
* command description

&#x20;

The commands that compose version 3.0 of the Premier\
Responder API\
are as follows:

&#x20;

**1** **Login**

&#x20;

Parameters:

_AccessLevel_\
as integer

_UserName_ as string

Return:

Success\
as boolean

&#x20;

Note: This\
command logs a user in. Premier Responder currently supports two access levels: 0 being a user\
and 1 being an administrator. Administrators have access to the SOP and User\
editing programs.

&#x20;

**2** **Logout**

&#x20;

Parameters:

None

Return:

Success\
as boolean

&#x20;

Note: This\
function logs the current user out.

&#x20;

**3** **Get**\
**User**

&#x20;

Parameters:

None

Return:

UserName\
as string

AccessLevel\
as integer

&#x20;

Note: This command retrieves the identity of the current Premier Responder user.

&#x20;

**4** **Begin**\
**Call**

&#x20;

Parameters:

_CaseNumber_\
as string

_StartDate_\
as date

Return:

Success\
as boolean

&#x20;

Note: This\
command initiates a new case. Sending an\
empty string for Case Number indicates that\
Premier Responder\
is to generate it internally. The command must specify the Start Date. Premier\
Responder\
will return a failure indication if it is already processing a case.

&#x20;

**5** **End**\
**Call**

&#x20;

Parameters:

_EndDate_\
as date

Return:

Success\
as boolean

&#x20;

Note: This command terminates processing\
of the current case and saves the call information to the cases.mdb database\
file. The calling program must specify the End Date.

&#x20;

**6** **Get**\
**Report**

&#x20;

Parameters:

None

Return:

ReportContents\
as string

&#x20;

Note: This command returns a string\
containing all of the information contained in the report. Use this command to\
retrieve responses to questions and SOP actions, etc.

&#x20;

**7** **Set**\
**Caller**

&#x20;

Parameters:

_CallerName_ as string

Return:

_Success_ as boolean

&#x20;

Note: This\
command sets the current callers name.

&#x20;

**8** **Get**\
**Caller**

&#x20;

Parameters:

None

Return:

_CallerName_ as string

&#x20;

Note: This command retrieves the current\
callers name.

**9** **Set Location**

&#x20;

Parameters:

_Location_ as string

Return:

_Success_ as boolean

&#x20;

Note: This command set the current\
location.

&#x20;

**10** **Get**\
**Location**

&#x20;

Parameters:

None

Return:

_Location_ as string

&#x20;

Note: This command retrieves the current\
location.

**11** **Set Phone Number**

&#x20;

Parameters:

_PhoneNumber_ as string

Return:

_Success_ as boolean

&#x20;

Note: This command sets the current phone\
number.

**12** **Get Phone Number**

&#x20;

Parameters:

None

Return:

_PhoneNumber_ as string

&#x20;

Note: This command retrieves the current phone number.

&#x20;

**13** **Get**\
**Category List**

&#x20;

Parameters:

None

Return:

_Categories_ as list

Note: This command returns a list of emergency categories for which guide\
cards are present. The list consists of paired integer and string values which\
indicate the category ID and name.  The default emergency categories are: 0 LE,\
1 Med,\
and 2 Fire.

&#x20;

**14** **Set**\
**Category**

&#x20;

Parameters:

_CategoryId_ as integer

Return:

_Success_ as boolean

&#x20;

Note: This\
command sets the emergency category of the currently active call.  If a\
call is not currently active,\
then the default emergency category is set.  Possible values for Category\
ID can be obtained using the Get Category List command.

&#x20;

**15** **Get**\
**Category**

&#x20;

Parameters:

None

Return:

_CategoryId_ as integer

&#x20;

Note: This\
command returns the emergency category of the call appearing on the call-taker\
window.  If a call does not appear on the call taker window, then the\
default emergency category is returned.

**16** **Get Complaint List**

&#x20;

Parameters:

_CategoryId_ as integer

Return:

_Complaints_ as list

&#x20;

Note: This command returns all complaints that are available for the\
specified category. Each list item includes the complaint identification number\
together with a text description.

&#x20;

**17** **Set**\
**Complaint**

&#x20;

Parameters:

_ComplaintId_ as integer

Return:

_Success_ as boolean

&#x20;

Note: This command sets the complaint for\
the currently active call. If a call is not active then the command will fail. \
Possible values for Complaint ID can be obtained using the Get Complaint List\
command.

&#x20;

**18** **Get**\
**Complaint**

&#x20;

Parameters:

None

Return:

_ComplaintId_ as integer

&#x20;

Note: This command returns the Complaint ID\
of the call appearing on the call-taker window.  If a call does not appear\
on the call-taker window or a complaint has not been selected then 9999 is\
returned.

**19** **Get Priority List**

&#x20;

Parameters:

_ComplaintId_ as integer

Return:

_Priorities_ as list

_Symptoms_ as list

&#x20;

Note: This command returns two lists. \
The first list contains the priorities for the emergency category of the\
currently active call.  If a call is not active then the default emergency\
category is used.  The second list contains the symptoms\
associated with the specified Complaint ID\
and previously determined emergency category. Each\
priority list item includes the priority level\
and optional priority code, if entered, otherwise the priority name. The\
symptom list items include priority level that the symptom is\
associated with and the symptom name.

&#x20;

**20** **Set**\
**Priority**

&#x20;

Parameters:

_Symptom_ as string

Return:

_Success_ as boolean

&#x20;

Note: This\
command is used to set the priority of the currently active call.  The\
Symptom parameter can either be a symptom name, a priority name, or optional\
priority code.  If a call is not active or the specified Symptom parameter\
is invalid then the command will fail.

&#x20;

**21** **Get**\
**Priority**

&#x20;

Parameters:

None

Return:

_Symptom_ as string

&#x20;

Note: Use this command to retrieve the\
optional priority code for the node selected on the priority tab of the Premier\
Responder active call window.  If the priority code was not entered then the node text is\
returned instead.  The node text may indicate either a priority or symptom\
name.  If a call is not active or a node has not been selected then an\
empty string is returned.

&#x20;

**22** **View**\
**Tab**

&#x20;

Parameters:

_TabIndex_ as integer

Return:

_Success_ as boolean

&#x20;

Note: The\
active call window currently includes 9 tabs which are numbered from 0 to\
8\.  Each tab is configurable by call type with a custom label.  All\
but the All Caller's Interrogation tab can be hidden.\
&#x20;Tabs 0 to 2 are specialized and contain the all caller's interrogation\
questions, vital point questions and priorities.  Tabs 3 to 6 are for\
viewing any rich text content such as pre-arrival instructions, call-taker\
actions, dispatcher actions or background information.  Tabs 7 and 8 are\
also specialized and are for viewing the short report and standard operating\
procedures.  The return value will indicate\
success if the specified tab is valid and is not hidden.

&#x20;

**23** **Get**\
**Tab**

&#x20;

Parameters:

None

Return:

_TabId_ as byte where:

* 0 = General Questions
* 1 = Vital Points
* 2 = Priority
* 3 = Call-Taker Actions
* 4 = Pre-Arrival
* 5 = Dispatcher Actions
* 6 = Background
* 7 = Short Report
* 8 = SOP
* 255 = Call Not Active

&#x20;

Note: Use this command to retrieve the currently viewed tab.

**24** **SOP Get Procedure List**

&#x20;

Parameters:

None

Return:

_ProcedureList_ as list

&#x20;

Note: This\
command returns a list of all available SOPs. SOPs are referred to by their\
associated data in the returned list.

&#x20;

**25** **SOP**\
**Set Procedure**

&#x20;

Parameters:

_ProcedureId_ as integer

Return:

_Success_ as Boolean

&#x20;

Note: Use this command to set the current SOP.

&#x20;

**26** **SOP**\
**Get Procedure**

&#x20;

Parameters:

None

Return:

_ProcedureId_ as integer

&#x20;

Note: Use this command to retrieve the current SOP procedure that is being viewed.

&#x20;

**27Med**\
**Get Procedure List**

&#x20;

Parameters:

None

Return:

_CategoryName1_ as string

_CategoryList1_ as list

_CategoryName2_ as string

_CategoryList2_ as list

_CategoryName3_ as string

_CategoryList3_ as list

_CategoryName4_ as string

_CategoryList4_ as list

_CategoryName5_ as string

_CategoryList5_ as list

_CategoryName6_ as string

_CategoryList6_ as list

&#x20;

Note: This command returns a name and list\
for each category of the medical instructions, these being: CPR, Childbirth, Obstructed Airway, and Airway Control.\
The list data items include a procedure id and a procedure name.

&#x20;

**28Med**\
**Set Procedure**

&#x20;

Parameters:

_ProcedureId_ as integer

Return:

_Success_ as boolean

&#x20;

Note: This\
command works only after the window has been displayed, otherwise a boolean false\
is returned. Use this function to set the current medical procedure.

&#x20;

**29Med**\
**Get Procedure**

&#x20;

Parameters:

None

Return:

_ProcedureId_ as integer

&#x20;

Note: Use this command to retrieve the currently viewed medical procedure.\
A return value of zero indicates that no procedure is currently being viewed.

&#x20;

**30Med Set Window**

&#x20;

Parameters:

_Visible_ as boolean

_Top_ as integer

_Left_ as integer

Return:

_Success_ as boolean

&#x20;

Note: The Top and Left units are given in\
twips.  Passing 0 for either indicates to keep the current value for that\
parameter. Use this command to show, hide,\
or position the\
medical Instructions\
window.  A call must be active in\
order to obtain a successful result.

&#x20;

**31ERG**\
**Set Window**

&#x20;

Parameters:

_Visible_ as boolean

_Top_ as integer

_Left_ as integer

Return:

_Success_ as boolean

&#x20;

Note:\
The Top and Left units are given in twips.  Passing 0 for either\
indicates to keep the current value\
for that parameter. Use this command to show,\
hide, or\
position the ERG window.  A call must\
be active in order to obtain a successful result.

&#x20;

**32** **Set**\
**Main Window**

&#x20;

Parameters

_Wrapped_ as boolean

_Top_ as integer

_Left_ as integer

Return:

_Success_ as boolean

&#x20;

Note:\
The Top and Left units are given in twips.  Passing 0 for either\
indicates to\
keep the current value for that parameter otherwise they are used to reposition the\
Premier Responder main window.  The Wrapped flag has\
no effect and serves only as a place holder for backward compatibility with\
existing interfaces.

&#x20;

**33** **Lock**\
**Interface**

&#x20;

Parameters:

_Lock_ as boolean

Return:

_Success_ as boolean

&#x20;

Note: This command disables the\
Login/Logout and Begin/End Call features of the Premier Responder user interface.

&#x20;

**34** **Shutdown**

&#x20;

Parameters:

None

Return:

_Success_ as boolean

&#x20;

Note: This command is used to terminate\
Premier Responder. It is not guaranteed to return a value.

&#x20;

**35** **Get**\
**Case Number**

&#x20;

Parameters:

None

Return:

_CaseNumber_ as string

&#x20;

Note: This command retrieves the current\
Case Number.

&#x20;

&#x20;**36** **Get**\
**Complaint Name**

&#x20;

Parameters:

None

Return:

_ComplaintName_ as string

&#x20;

Note: This command retrieves the current\
Complaint.

&#x20;

**37** **Get**\
**Priority Symptom**

&#x20;

Parameters:

None

Return:

_Symptom_ as string

&#x20;

Note: This command returns the selected\
symptom for the call in progress or, if waiting, for the previously completed\
call.

&#x20;

&#x20;**38** **Get**\
**Actual Priority**

&#x20;&#x20;

Parameters:

None

Return:

_Priority_ as string

&#x20;&#x20;

Note: This command\
returns the selected priority category for\
the call in progress or, if waiting, for the previously completed call.

&#x20;

&#x20;**39Get**\
**Short Report**

&#x20;&#x20;

Parameters:

None

Return:

ReportContents as string

&#x20;

Note: This command\
returns the short report for the call in\
progress or, if waiting, for the previously completed call.

&#x20;

**40**          **Set Complaint Code**

&#x20;

Parameters:

_ProblemCode_ Text as string

Return:

_Success_ as boolean

Note: This command sets the complaint using a code that has been\
associated with one of the complaints.

&#x20;

**41**          **Get Complaint Codes**

&#x20;

Parameters:

None

Return:

Problem Codes as list

Note: This command retrieves the problem codes associated with the\
current Complaint.  Note that a complaint can have more than one associated\
code.  Each list item includes the complaint ID number together with the problem\
code.

&#x20;

**42**          **Get Complaint Code List**

&#x20;

Parameters:

_CategoryId_ as integer

Return:

_ProblemCodes_ as list

Note: This command\
returns all complaints and associated problem\
codes that are available under the specified category.  Note that a complaint\
can have more than one associated code.  Each list item includes the complaint\
ID number together with the problem code.

&#x20;

**4\*\*\*\*3**          **Get**\
**Alternate Port**

&#x20;

Parameters:

None

Return:

_PortNumber_ as\
long

Note:\
In addition to\
port 2021, Premier Responder also monitors a random port that is determined by the system\
when the software loads.  This command returns the alternate port\
Premier Responder listens\
on for connection requests.  The purpose of the alternate port is to provide\
each instance of Premier Responder a unique port number to monitor, when there are multiple\
instances of the software running.

&#x20;

**44**          **Set**\
**Window State**

&#x20;

Parameters:

_WindowState_ as integer

Return:

_Success_ as boolean

Note: This command sets the state of all open\
Premier Responder windows.  The possible values\
for Window State are: 0 = Normal, 1 = Minimized.

&#x20;

**45**          **Get Settings List**

&#x20;

Parameters:

None

Return:

_SettingsList_ as list

Note: Returns a list of the settings\
contained in the configuration database.

&#x20;

**46**          **Read Setting**

&#x20;

Parameters:

_SettingName_ as string

Return:

_SettingName_ as string

_SettingValue_ as string

Note: Returns the name and value of the\
specified setting.

&#x20;

**47**          **Write Setting**

&#x20;

Parameters:

_SettingName_ as string

_SettingValue_ as string

Return:

_Success_ as boolean

Note:\
Updates specified setting value in the configuration database.  Changes are\
not applied until software is restarted or Apply Setting Changes API command is\
sent.  Be aware the\
Premier Responder software does not currently perform any\
validation of the setting value, therefore this responsibility must be assumed\
by CAD.

&#x20;

**48**          **Apply Setting Changes**

&#x20;

Parameters:

None

Return:

_Success_ as boolean

Note: All settings contained in the\
configuration database are reapplied.

&#x20;

**49**          **Set Case Number**

&#x20;

Parameters:

_CaseNumber_ as string

Return:

_Success_ as boolean

Note: Sets the case number to the specified\
value if a call is in progress.  The command fails if a call is not in progress.

&#x20;

**50**          **Get Version Number**

&#x20;

Parameters:

None

Return:

_VersionNumber_ as string

Note: Returns the Premier Responder software four\
part version number in the format **MAJ.MIN.REV.BLD** where **MAJ** is the\
major number, **MIN** is the minor number, **REV** is the revision number\
and **BLD** is the build number.

&#x20;

**51**          **Show SMS Text**

&#x20;

Parameters:

_SmsText_ as string

Return:

Success as boolean

Note: Text to 9-1-1 functionality is\
enabled then text is displayed in dialog box of active call window texting\
panel.
