  ---------------------------
  **Software Deactivation**
  ---------------------------

[Deactivate Licensing Menu]{.underline}

A **Deactivate Licensing** menu option is available from within the
**Help** menu of each application.  The menu is enabled when logged on
as an administrator and the software has been activated.  It allows for
activations to be transferred from machines that are to be
decommissioned to replacement machines.  Within the **Deactivate
Licensing** menu are submenu options for deactivating directly or
indirectly.  Use the direct method when internet access is available on
the host machine and the indirect method when not.

![](Software%20Deactivation_files/image001.png){border="0" width="216"
height="126"}

[Direct Deactivation]{.underline}

When internet access is available on the host machine the software can
be deactivated directly.  Selecting the **Deactivate Licensing -
Online** menu option opens a dialog window warning that license
credentials are required to reactivate the software on another machine. 
Clicking the **OK** button proceeds with the deactivation.  When
complete, a subsequent dialog window appears indicating deactivation
successful.  Upon closing the dialog the application terminates.

![](Software%20Deactivation_files/image002.png){border="0" width="431"
height="233"}

[Indirect Deactivation]{.underline}

When internet access is not available on the host machine, the software
must be deactivated indirectly using a machine that does have internet
access. In this case, select the **Deactivate Licensing - Via Remote
Internet-Enabled Computer** menu option.  The license credentials
required to reactivate warning dialog appears.  Click the **OK** button
to proceed with the deactivation and open the **Deactivate Manually**
dialog window. Manual deactivation is a multi-step process.  Begin by
using the **Step 1 Browse** button to locate your flash drive and set
the path of the deactivation request file. Selecting the **Save
Request** button generates the deactivation request file on the flash
drive.

![](Software%20Deactivation_files/image003.png){border="0" width="374"
height="251"}

Now take the flash drive to a computer with internet access and open
deactivation request file in web browser.  Internet Explorer is
recommended browser for doing this.  If content is blocked from loading
select option to allow blocked content.  Once loading is complete,
select File - Save As menu item and save XML deactivation installation
file to flash drive.

![](Software%20Deactivation_files/image004.png){border="0" width="735"
height="350"}

Complete the deactivation process by taking the flash drive back to the
host machine, using the **Step 2 Browse** button to locate the XML
deactivate installation file, and selecting the **Get Response**
button.  A final dialog window appears indicating deactivation
successful.  Upon closing deactivation successful dialog the application
terminates.

![](Software%20Deactivation_files/image005.png){border="0" width="374"
height="251"}
