# Troubleshooting Database Connectivity Issues in Premier Responder and Expectations

This guide helps troubleshoot database connectivity problems in Premier Responder, considering its requirement for both x86 and x64 OLEDB drivers. These products depend on the MSOLEDBSQL provider for connectivity.

### Prerequisite <a href="#id-1-install-oledb-drivers" id="id-1-install-oledb-drivers"></a>

Installation of the [Microsoft Visual C++ Redistributable](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist) is a prerequisite, and while the x64 installer for Microsoft OLE DB Driver installs both the 64-bit and 32-bit driver, the x64 installer for the Microsoft Visual C++ Redistributable doesn't install 32-bit binaries. You must install both the x86 and x64 versions of the C++ redistributable package to install the x64 OLE DB driver package. You may be asked to restart the computer.

### Install OLEDB Drivers <a href="#id-1-install-oledb-drivers" id="id-1-install-oledb-drivers"></a>

Expectations and Premier Responder require version 18.7.4 version of the Microsoft OLE DB Driver for SQL Server (MSOLEDBSQL). Some Windows systems do not come with this driver already installed. Follow the directions below to install them.

* Visit the official Microsoft download page: \
  [https://learn.microsoft.com/en-us/sql/connect/oledb/release-notes-for-oledb-driver-for-sql-server?view=sql-server-ver16#1874](https://learn.microsoft.com/en-us/sql/connect/oledb/release-notes-for-oledb-driver-for-sql-server?view=sql-server-ver16#1874)&#x20;
* Download x64 version of the 18.7.4 MSOLEDBSQL  driver&#x20;
* Run both installers, following the on-screen prompts.

### Install .NET Framework <a href="#id-2-install-net-framework" id="id-2-install-net-framework"></a>

* Premier Responder may require specific .NET Framework versions.
* Check your software documentation or system requirements for details.
* Download and install the necessary x86 and/or x64 .NET Framework versions from the official Microsoft website.

### Restart Your System <a href="#id-3-restart-your-system" id="id-3-restart-your-system"></a>

* Restart your computer after driver installations to apply changes.

### 4. Verify Installation <a href="#id-4-verify-installation" id="id-4-verify-installation"></a>

* Confirm both OLEDB drivers are listed in "Programs and Features" or "Apps & features."

### 5. Test Premier Responder <a href="#id-5-test-premier-responder" id="id-5-test-premier-responder"></a>

* Launch Premier Responder and test its database connection.

### Advanced Troubleshooting <a href="#advanced-troubleshooting" id="advanced-troubleshooting"></a>

* **Install SQL Server Management Studio (SSMS):** This may install missing dependencies or help diagnose connection problems.
* **Contact Nexport Solutions Support:** For persistent issues, contact support for expert assistance.

**Note:** Always refer to official Microsoft documentation and Premier Responder documentation for the most accurate information.

### Verify the versions of MSOLEDBSQL provider installed

**Open up the 32 bit (x86) version of Powershell**\
<figure><img src=".gitbook/assets/../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

**Paste in the following script:**

{% code lineNumbers="true" fullWidth="true" %}
```powershell
foreach ($provider in [System.Data.OleDb.OleDbEnumerator]::GetRootEnumerator()) {
    $properties = @{}
    for ($i = 0; $i -lt $provider.FieldCount; $i++) {
        $properties[$provider.GetName($i)] = $provider.GetValue($i)
    }
    [PSCustomObject]$properties
}
```
{% endcode %}

**When you run the script a list of 32bit providers will be displayed. In that list look for a provider with:**

```powershell
SOURCES_NAME           :  MSOLEDBSQL
```

**If the Provider does not show up then the 32bit (x86) version of the driver is not properly installed.** [**See the instructions for installing the MSOLEDBSQL provider**](troubleshooting-database-connectivity-issues-in-premier-responder-and-expectations.md#id-1-install-oledb-drivers-1)

