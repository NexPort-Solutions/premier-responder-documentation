  ----------------------
  **Software Updates**
  ----------------------

[Update Software Screen]{.underline}

Software updates in the form of a Windows Installer Package can be
installed to remote machines from the administrator Update Software
screen.  When receiving an update, first install it on the primary
workstation then launch and log into the administrator application. 
Next, within the administrator application, select the File - Update
Software menu item.

![](Installing%20Software%20Updates_files/image001.png){border="0"
width="655" height="245"}

When the Update Software screen first opens, a search is immediately
started for Premier Responder instances on the network.  The time it
takes for the search to complete varies, depending on the size of the
network.  As instances are located, entries are added to the Software
Instances list.  Each entry in the list includes the machine name,
software version, software in use (Yes or No), and update status (Not
Updated, Sending Update, Installing Update, Update Installed).

 ![](Installing%20Software%20Updates_files/image002.png){border="0"
width="655" height="504"}

Once the search completes, select the Change button to open a browser,
locate the installer, and set the path. Next check the boxes beside the
machines to be updated.  Machines showing the software in use cannot be
checked for updating.  With the installer path set and machines checked
to update, the Update button becomes enabled.

![](Installing%20Software%20Updates_files/image003.png){border="0"
width="655" height="504"}

When all is ready, select the Update button to begin. The process starts
by first sending the installer to each checked machine.  Note in the
Status column of the Software Instances list, \"Sending Update\"
followed by a percentage value that progresses to 100%.  Once the
sending phase completes, installation begins.  During this phase the
status column indicates \"Installing Update\" which is again followed by
a percentage value.

![](Installing%20Software%20Updates_files/image004.png){border="0"
width="655" height="504"}

The update process ends when the status of all checked machines
indicates \"Update Installed\".  To close the Update Software screen,
select the X (close) toolbar button.  The Refresh button clears the
Software Instances list and starts another search.

![](Installing%20Software%20Updates_files/image005.png){border="0"
width="655" height="504"}
