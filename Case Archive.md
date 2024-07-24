  ------------------
  **Case Archive**
  ------------------

The **Case Archive** tab is used to configure Premier Responder to
archive cases.  To open the \"Case Archive\" tab, first log into the
**Premier Responder Administrator**.  Then select the **Configure -\>
Archive** menu item from the main window.

![](Case%20Archive_files/image001.png){border="0" width="655"
height="144"}

When a call is ended, the call information is saved to the working cases
database on the computer running Premier Responder.  Archiving the case
moves the case to an archive database which can be on the same computer
or another computer.  Typically, several Premier Responder workstations
will archive cases to a common database.  The Case Archive tab controls
the archive features.

![](Case%20Archive_files/image002.png){border="0" width="655"
height="504"}

When the **Enable Auto Archive** checkbox is checked, cases are
automatically sent to the archive database.  The archive database can be
selected as either an Access, SQL Server, or Oracle database using the
**Archive Cases to Access database**, **Archive cases to SQL Server
database**, or **Archive cases to Oracle database** radio buttons. The
**Archive Path** text box shows the path of the selected database.

When **Enable Auto Archive** is unchecked,  or when the connection to
the archive fails (such as when the network is offline), the cases will
be stored on the local machine.  These cases can later be sent to the
archive database by enabling auto archive or automatically sent when the
network comes back online.

As more positions conduct transactions on the cases archive the
possibility for contention increases.  To lessen the effects of multiple
processes vying for exclusive access to the archive, the **Archive Query
Timeout** setting is provided for limiting the time of database queries
and the **Archive Max Retries** setting for specifying the number
attempts that can be made to complete a transaction.  Both settings have
a range of 1 to 10 with **Archive Query Timeout** defaulting to 3 and a
default of 5 for **Archive Max Retries**.
