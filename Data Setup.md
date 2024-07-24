  ----------------
  **Data Setup**
  ----------------

[Locating Premier Responder Data]{.underline}

Since Email Alert is monitoring Premier Responder calls, it must
establish a connection to the database where calls are being saved
before it can operate.  The controls on the **Data Setup** tab are used
to specify the database to monitor.  When incorrectly configured, the
status panel indicates **Data Setup Error**.

![](Data%20Setup/image001.png){border="0" width="639" height="400"}

[Premier Responder Folder]{.underline}

The **Premier Responder Folder** text box at the top of the **Data
Setup** tab displays the path to the folder containing the Premier
Responder data files.  A red background means the Premier Responder data
files are not in the specified folder.  Use the **Browse** button
opposite the text box to change the path.  This opens a **Browse For
Folder** dialog window.

![](Data%20Setup/image002.png){border="0" width="320" height="373"}

Use the **Browse For Folder** dialog to find an installation of Premier
Responder, either on the local machine or on the network, then select
the **OK** button.  The change is saved to the **Premier Responder
Folder** text box.  Once the necessary data files are located, the text
box background color changes to white.

![](Data%20Setup/image003.png){border="0" width="627" height="60"}

[Select Database To Monitor]{.underline}

**Email Alerts** can monitor either the cases database in the Premier
Responder folder or an Access, SQL Server, or Oracle archive.  Use the
radio buttons on the left side in the **Select database to monitor** box
to specify the type of database to monitor.  Opposite each radio button
is a text box that indicates the current database for the designated
type.  The database for the selected type is displayed in the lower text
box.  A red background in any of the text boxes indicates an invalid
database.

![](Data%20Setup/image004.png){border="0" width="618" height="194"}

[Access Archive]{.underline}

To change the current **Archive Access database**, use the **Browse**
button opposite the radio button.  This opens the **Access Setup** tab. 
At the top of the tab, the **Email Alerts folder** text box displays the
path where the database resides.  The **Browse** button is used to
locate and select another folder.  Below the **Email Alerts folder**
text box are option buttons for specifying a file.  When the **Auto
Select** option is enabled, the adjoining radio buttons indicate the
time span of the archive file.

![](Data%20Setup/image005.png){border="0" width="639" height="400"}

To manually specify an archive, click on the **Manual Select** option
button and select the desired file in the list box to the right.  The
full path of the archive file is displayed in the lower text box. 
Selecting the **OK** button closes the tab and saves the changes to the
**Archive Access database** text box on the main form.

![](Data%20Setup/image006.png){border="0" width="602" height="51"}

[SQL Server Archive]{.underline}

The **Browse** button opposite the **Archive SQL Server database** radio
button and text box is used to change the SQL Server archive.  It brings
up the **SQL Setup** tab.  At the top of the tab, the database server
can either be selected from the **Server** drop down list or typed in. 
After entering the server, log in to the server by entering the **Log In
ID** and **Password** then selecting the **Connect** button.  Use the
**SQL Connect Timeout** selector to specify how long to wait for the
connection to be made before an error is indicated.

![](Data%20Setup/image008.png){border="0" width="639" height="400"}

Upon successfully logging in, available databases are displayed in the
**Select Database** list.  Select the desired database from the list
then click on the **OK** button.  The **SQL Setup** tab closes and
changes are saved to the **Archive SQL Server database** text box on the
main form.

![](Data%20Setup/image009.png){border="0" width="598" height="32"}

[Oracle Archive]{.underline}

The **Browse** button opposite the **Archive Oracle database** radio
button and text box is used to change the Oracle archive.  It brings up
the **Oracle Setup** tab.  At the top of the tab, the database is
specified by making the appropriate entries in the **Host**, **Port**,
and **Instance** text boxes.  Next log in to the server by entering the
**User** and **Password** then selecting the **Connect** button.

![](Data%20Setup/image010.png){border="0" width="639" height="400"}

Upon successfully logging in, available databases are displayed in the
**Select Database** list.  Select the desired database from the list
then click on the **OK** button.  The **Oracle Setup** tab closes and
changes are saved to the **Archive Oracle database** text box on the
main form.

![](Data%20Setup/image011.png){border="0" width="598" height="36"}

[Data Setup Completed]{.underline}

Once the data setup is correctly completed, all text box backgrounds
will be white.
