  ---------------------------------------------
  **Selecting a SQL Server Archive Database**
  ---------------------------------------------

# SQL Server Archive Window

The **SQL Server Setup** configuration screen is used to select a SQL
Server database for the purpose of archiving calls.  In the **SQL
Server** section are controls used to open a server connection.  Below,
the **Cases Archive** section includes functionality for creating and
selecting a database.  On the **Archive** tab toolbar, the **SQL Connect
Timeout** selector appears conditionally with the **SQL Server Setup**
configuration screen.  To close the tab without making an archive
selection, click one of the other tabs or the \'X\' toolbar button.

<figure><img src=".gitbook/assets/Case Archive SQL_files/image001.png" alt=""><figcaption></figcaption></figure>{border="0" width="655"
height="504"}

# Connect To Server

The controls in the **SQL Server** section are used to specify a server
and to enter the login information.  In the **Instance** drop down are
the names of servers found on the network.  When initially loaded, the
results of a best-effort network search for a SQL server are displayed.
To change the server, simply make a selection from the list.  If the
desired server does not show in the list, the name or the IP address and
port number can be manually entered as follows:

1.  To connect to a default instance of SQL Server, enter either:

    -   the server host name

    -   the server IP address

2.  To connect to a named instance of SQL Server, enter either:

    -   the server host name\\instance name

    -   the server IP address, port number

After specifying the server, enter the **Login Name** and **Password**
for an account having sufficient permissions to create a database, then
select the **Connect** button.  The **Cases Archive** area of the window
is initially disabled and becomes enabled upon successfully opening a
connection.  If any of the connection information is changed, the
**Cases Archive** controls are again disabled.  Use the **SQL Connect
Timeout** selector to specify how long to wait for the connection to be
made before an error is indicated.

# Create Archive

The controls in the **Cases Archive** section are used to create a new
database and select an archive.  Once a valid database name has been
entered in the **Name** text box, the **Create** button is enabled. 
Select the **Create** button to create the database.  If successful, the
database is added to the **Select** list.  The archive is then selected
from the databases that appear in the list.
