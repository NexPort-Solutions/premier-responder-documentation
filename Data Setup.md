  ----------------
  **Data Setup**
  ----------------

# Locating Premier Responder Data

Since Email Alert is monitoring Premier Responder calls, it must
establish a connection to the database where calls are being saved
before it can operate.  The controls on the **Data Setup** tab are used
to specify the database to monitor.  When incorrectly configured, the
status panel indicates **Data Setup Error**.

<figure><img src=".gitbook/assets/Data Setup/image001.png" alt=""><figcaption></figcaption></figure>

# Premier Responder Folder

The **Premier Responder Folder** text box at the top of the **Data
Setup** tab displays the path to the folder containing the Premier
Responder data files.  A red background means the Premier Responder data
files are not in the specified folder.  Use the **Browse** button
opposite the text box to change the path.  This opens a **Browse For
Folder** dialog window.

<figure><img src=".gitbook/assets/Data Setup/image002.png" alt=""><figcaption></figcaption></figure>

Use the **Browse For Folder** dialog to find an installation of Premier
Responder, either on the local machine or on the network, then select
the **OK** button.  The change is saved to the **Premier Responder
Folder** text box.  Once the necessary data files are located, the text
box background color changes to white.

<figure><img src=".gitbook/assets/Data Setup/image003.png" alt=""><figcaption></figcaption></figure>

# Select Database To Monitor

**Email Alerts** can monitor either the cases database in the Premier
Responder folder or an Access, SQL Server, or Oracle archive.  Use the
radio buttons on the left side in the **Select database to monitor** box
to specify the type of database to monitor.  Opposite each radio button
is a text box that indicates the current database for the designated
type.  The database for the selected type is displayed in the lower text
box.  A red background in any of the text boxes indicates an invalid
database.

<figure><img src=".gitbook/assets/Data Setup/image004.png" alt=""><figcaption></figcaption></figure>

# Access Archive

To change the current **Archive Access database**, use the **Browse**
button opposite the radio button.  This opens the **Access Setup** tab. 
At the top of the tab, the **Email Alerts folder** text box displays the
path where the database resides.  The **Browse** button is used to
locate and select another folder.  Below the **Email Alerts folder**
text box are option buttons for specifying a file.  When the **Auto
Select** option is enabled, the adjoining radio buttons indicate the
time span of the archive file.

<figure><img src=".gitbook/assets/Data Setup/image005.png" alt=""><figcaption></figcaption></figure>

To manually specify an archive, click on the **Manual Select** option
button and select the desired file in the list box to the right.  The
full path of the archive file is displayed in the lower text box. 
Selecting the **OK** button closes the tab and saves the changes to the
**Archive Access database** text box on the main form.

<figure><img src=".gitbook/assets/Data Setup/image006.png" alt=""><figcaption></figcaption></figure>

# SQL Server Archive

The **Browse** button opposite the **Archive SQL Server database** radio
button and text box is used to change the SQL Server archive.  It brings
up the **SQL Setup** tab.  At the top of the tab, the database server
can either be selected from the **Server** drop down list or typed in. 
After entering the server, log in to the server by entering the **Log In
ID** and **Password** then selecting the **Connect** button.  Use the
**SQL Connect Timeout** selector to specify how long to wait for the
connection to be made before an error is indicated.

<figure><img src=".gitbook/assets/Data Setup/image008.png" alt=""><figcaption></figcaption></figure>

Upon successfully logging in, available databases are displayed in the
**Select Database** list.  Select the desired database from the list
then click on the **OK** button.  The **SQL Setup** tab closes and
changes are saved to the **Archive SQL Server database** text box on the
main form.

<figure><img src=".gitbook/assets/Data Setup/image009.png" alt=""><figcaption></figcaption></figure>

# Oracle Archive

The **Browse** button opposite the **Archive Oracle database** radio
button and text box is used to change the Oracle archive.  It brings up
the **Oracle Setup** tab.  At the top of the tab, the database is
specified by making the appropriate entries in the **Host**, **Port**,
and **Instance** text boxes.  Next log in to the server by entering the
**User** and **Password** then selecting the **Connect** button.

<figure><img src=".gitbook/assets/Data Setup/image010.png" alt=""><figcaption></figcaption></figure>

Upon successfully logging in, available databases are displayed in the
**Select Database** list.  Select the desired database from the list
then click on the **OK** button.  The **Oracle Setup** tab closes and
changes are saved to the **Archive Oracle database** text box on the
main form.

<figure><img src=".gitbook/assets/Data Setup/image011.png" alt=""><figcaption></figcaption></figure>

# Data Setup Completed

Once the data setup is correctly completed, all text box backgrounds
will be white.
