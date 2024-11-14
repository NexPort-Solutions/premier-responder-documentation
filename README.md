# Expectations Getting Started

## Getting Started
---

* Startup
* Main Form
* Logging In
* Logging Out
* Database Connection

## Startup
---

To start Expectations select the shortcut on the desktop or in the Start menu.  When the main form first appears the splash screen is displayed.  Clicking on the splash screen will make it go away.

<figure><img src=".gitbook/assets/<.gitbook/assets/0 (3" alt=""><figcaption></figcaption></figure>.jpeg>)

As Expectations starts up it attempts to establish a database connection.  If successful, the Login form appears after the splash screen goes away.  If Expectations is unable to establish a database connection, use the File - Open Database menu item on the main form to manually establish a connection.  Once the connection is made to the database the Login form will appear.

## NOTE: For instructions on manually making a database connection, see the section entitled Database Connection.
---

## Main Form
---

The main form is Expectation's parent form.  All the other forms are limited to operate within the bounds of the main form.  At the top of the form are the main menus.  Within the main menus are the menu items that access the other forms.  Menu items may or may not be enabled, depending on if a user has logged in and what their security level is.  Enabled menu items are indicated by black text, disabled menu items by gray text.  User information displays on the status bar at the bottom of the form.  To exit Expectations select the control box X or the File - Exit menu item.

<figure><img src=".gitbook/assets/<.gitbook/assets/1 (3" alt=""><figcaption></figcaption></figure>.png>)

File Menu Items

* Open Database (enabled when not connected to a database)
* Close Database (enabled when connected to a database and not logged in)
* [Local Preferences](https://docs.google.com/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.2u6wntf) (enabled when logged in)
* Exit (always enabled)

Login Menu Items

* Login (enabled when not logged in and connected to a database)
* Logout (enabled when any user logs in)

Trainee/Employee Menu Items

* [View Evaluation](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.2s8eyo1) (enabled when trainee/employee logs in)

Trainer/Supervisor Menu Items

* [Write Evaluation](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.lnxbz9) (enabled when trainer/supervisor logs in)
* [Print Worksheet](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.35nkun2) (enabled when trainer/supervisor logs in)
* [Review Evaluation](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.1ksv4uv) (enabled when trainer/supervisor logs in)
* [View Evaluation](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.44sinio) (enabled when trainer/supervisor logs in)
* [Reports](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.2jxsxqh) (enabled when trainer/supervisor logs in)
* [View/Print Criteria Set](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.3rdcrjn) (enabled when trainer/supervisor logs in)

Administrator Menu Items

* [Create Trainer/Supervisor Signature Key](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.19c6y18) (enabled when logged in as level 3 trainer/supervisor on central system)
* [Create Trainee/Employee Signature Key](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.3tbugp1) (enabled when logged in as level 3 trainer/supervisor on central system)
* [Add/Modify/Delete A Trainer/Supervisor](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.19c6y18) (enabled when logged in as level 3 trainer/supervisor on central system)
* [Add/Modify/Delete A Trainee/Employee](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.3tbugp1) (enabled when logged in as level 3 trainer/supervisor on central system)
* [Add/Modify/Delete A Criteria](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.28h4qwu) (enabled when logged in as level 3 trainer/supervisor on central system)
* [Add/Modify/Delete A Criteria Set](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.nmf14n) (enabled when logged in as level 3 trainer/supervisor on central system)
* [System Properties](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.37m2jsg) (enabled when logged in as level 3 trainer/supervisor)
* [Backup/Restore](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.1mrcu09) (enabled when logged in as level 3 trainer/supervisor)
* [Global Settings](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.46r0co2) (enabled when logged in as level 3 trainer/supervisor)
* [Download](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.z337ya) (enabled when trainer/supervisor logs in)
* [Upload](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.3j2qqm3) (enabled when trainer/supervisor logs in)

Window Menu Items

* Cascade (always enabled)
* menu item for each displayed form (always enabled)

Help Menu Items

* Contents (always enabled)
* Index (always enabled)
* Deactivate Licensing (enabled when logged in as level 3 trainer/supervisor)
  * Online
  * Via Remote Internet-Enabled Computer
* About Expectations (always enabled)

## Logging In
---

In order to write, view or print evaluations a user first needs to log in.  This is accomplished from the Login form.  The Login form is accessed via the Login - Login menu item on the main form.

<figure><img src=".gitbook/assets/<.gitbook/assets/2 (3" alt=""><figcaption></figcaption></figure>.jpeg>)

The Login form will automatically appear when Expectations first starts up, when a database connection is made, or when a user logs out.  Expectations installs with a single Trainer/Supervisor account, the Login Name being "Admin" and the Password "password".  To log in, enter the Login Name, Password and User Type in the appropriate boxes and select the OK button.  User information appears on the status bar at the bottom of the main form and the menus are reconfigured to accommodate the user's [security level](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.2lwamvv).  The Cancel button will close the Login form without logging in.

<figure><img src=".gitbook/assets/<.gitbook/assets/3 (3" alt=""><figcaption></figcaption></figure>.png>)

When Expectations is unable to establish a database connection at startup the login form will not appear.  In this case use the File - Open Database menu item on the main form to manually establish a connection.  Once the connection is made to the database the Login form will appear.

## NOTE: For instructions on manually making a database connection, see the section entitled Database Connection.
---

## Logging Out
---

To log out of Expectations select the Login/Logout menu item located on the main form.  User information at the bottom of the main form is cleared and the menus are reconfigured to the pre-login state.

<figure><img src=".gitbook/assets/<.gitbook/assets/4 (3" alt=""><figcaption></figcaption></figure>.jpeg>)

## Database Connection
---

After installation, Expectations is configured to establish a connection to an Access database file in the application folder by default.  Use the File - Close Database and File - Open Database menu items on the main form to locate and connect to an alternate database.

Close Database

In order to connect to an alternate database, the existing database connection must be closed.  Use the File - Close Database menu item to do this.  This menu item is enabled prior to logging in.

<figure><img src=".gitbook/assets/<.gitbook/assets/5 (2" alt=""><figcaption></figcaption></figure>.jpeg>)

Open Database

Use the File - Open Database menu item to locate and open a connection to an alternate database.  This menu item is enabled when not connected to a database.

<figure><img src=".gitbook/assets/<.gitbook/assets/6 (2" alt=""><figcaption></figcaption></figure>.jpeg>)

Select Database

Selecting the File - Open Database menu item brings up the Select Database window.  Expectations can work from either an Access or SQL Server database.  The option buttons on the Select Database window are used to select the database type.  Text boxes opposite the option buttons indicate the database to open.  Use the associated Change buttons to change the database.  A connection attempt is made when the OK button is selected.  The Select Database window closes and the Login window appears if the connection attempt is successful.

## NOTE: Expectations will remember and subsequently connect to the last database that was opened.
---

<figure><img src=".gitbook/assets/<.gitbook/assets/7 (2" alt=""><figcaption></figcaption></figure>.png>)

Selecting the Access database Change button opens a browser dialog window.  Use it to locate and select the Access database file (expectations.mdb) to connect to.  Click on the Open button to update the Access database text box on the Select Database window.  Selecting the Cancel button closes the browser without updating the database.

<figure><img src=".gitbook/assets/<.gitbook/assets/8 (3" alt=""><figcaption></figcaption></figure>.png>)

Selecting the SQL Server database Change button opens the SQL Server database window.  It is used to specify a server, connect to the server, and select a database on the server.  This process is described in the paragraphs and illustrations that follow.

<figure><img src=".gitbook/assets/<.gitbook/assets/9 (2" alt=""><figcaption></figcaption></figure>.png>)

First, use the controls located in the Select Server area of the window to specify the SQL server, either by name or IP address.  Instances of SQL servers located on the network are listed in the Server drop down selector.  If, for any reason, a server does not appear in the drop down list, the instance name or IP address can be entered into the Server box.

<figure><img src=".gitbook/assets/<.gitbook/assets/10 (3" alt=""><figcaption></figcaption></figure>.png>)

Once a SQL server has been specified, use the controls in the Server Log In area to establish a connection.  In order to connect to the specified server, it must be configured to use SQL authentication and allow network connections.  Additionally, a login and password for the server must be obtained.  To make the connection to the server, enter the login name and password into the appropriate boxes and then select the Login button.

<figure><img src=".gitbook/assets/<.gitbook/assets/11 (2" alt=""><figcaption></figcaption></figure>.png>)

Once the SQL server connection has been established, Expectations related databases are listed in the Select Database area of the window.  Making a database selection from the list enables the OK button at the bottom of the window.

<figure><img src=".gitbook/assets/<.gitbook/assets/12 (3" alt=""><figcaption></figcaption></figure>.png>)

To create a new database, enter a name into the text box located to the left of the Create Database button.  The button is enabled as long as the entered name is valid.  After entering the database name select the Create Database button.

<figure><img src=".gitbook/assets/<.gitbook/assets/13 (2" alt=""><figcaption></figcaption></figure>.png>)

If successful, the Database Created window appears with information on how to connect to the newly-created SQL Server database.  Click OK to see the new database in the Select Database list.

<figure><img src=".gitbook/assets/<.gitbook/assets/14 (3" alt=""><figcaption></figcaption></figure>.png>)

Finally, select the desired database from the list and then click on the OK button.  The SQL Server database window now closes and the selected database appears in the SQL Server database text box on the Select Database window.  Selecting the Cancel button closes the window without updating the database.

<figure><img src=".gitbook/assets/<.gitbook/assets/15 (2" alt=""><figcaption></figcaption></figure>.png>)

Migration to SQL Server

At launch or when switching the choice in the Select Database dialog, you can choose to automatically migrate older MS Access databases and update them using the [Conversion Options](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.111kx3o) dialog. If your database is already of the current version, or if you wish to manually perform the switch over to using a SQL Server database, please use the following procedure:

1. A server must be available on the network.  If not, download and install either [SQL Server 2005 Express](http://www.microsoft.com/sqlserver/2005/en/us/express.aspx) or [SQL Server 2008 Express](http://www.microsoft.com/sqlserver/2008/en/us/express.aspx).  These are limited versions of SQL Server.  Installation and configuration instructions are available on the download site.
2. Connect to the [central](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.37m2jsg) Access database file as described above.
3. [Download](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.z337ya) the [departments, shifts, and phases](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.3l18frh) that are to be relocated to the new database.
4. [Download](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.z337ya) the [trainers/supervisors](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.206ipza), [trainees/employees](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.4k668n3), [criteria sets](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.2zbgiuw), and [evaluations](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.1egqt2p) that are to be relocated to the new database.
5. Create and connect to the SQL Server database as described above.
6. With Expectations connected to the SQL Server database, login by entering Admin and password respectively for Login Name and Password.
7. [Upload](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.3j2qqm3) the previously downloaded departments, shifts, and phases.
8. Assign a department to the Admin user in the [Modify Trainer/Supervisor](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.3ygebqi) window.
9. [Upload](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.3j2qqm3) the previously downloaded trainers/supervisors, trainees/employees, criteria sets, and evaluations.

> Note: Relocating evaluations to a SQL Server database is optional.  While they are not required for authoring new evaluations, they may be wanted for historical reference.

> NOTE: At this time during the update process, Training & Development application records may only be migrated automatically (rather than manually) from an MS Access database to SQL Server.  For those older MS Access databases which do not meet the criteria specified in the [Conversion Options](/document/d/10fcvgcmvNWnKnY9D04qr5zSIS2eHLsIQNc2Yaq5GgV8/edit#bookmark=id.111kx3o) help topic for updating 'in-place', please consider converting your database to SQL Server automatically.  If migrating your older MS Access database to SQL Server is not feasible at this time and the "Keep MS Access" button is not enabled, please contact Smart Horizons for assistance in separating out the database into multiple MS Access databases (each of which may be updated separately by the software, as normal).
---
