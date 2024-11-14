# Troubleshooting Database Connectivity Issues in Premier Responder and Expectations

This guide helps troubleshoot database connectivity problems in Premier Responder, considering its requirement for both x86 and x64 OLEDB drivers. These products depend on the MSOLEDBSQL provider for connectivity.

### Prerequisite <a href="#id-1-install-oledb-drivers" id="id-1-install-oledb-drivers"></a>

Installation of the [Microsoft Visual C++ Redistributable](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist) is a prerequisite, and while the x64 installer for Microsoft OLE DB Driver installs both the 64-bit and 32-bit driver, the x64 installer for the Microsoft Visual C++ Redistributable doesn't install 32-bit binaries. You must install both the x86 and x64 versions of the C++ redistributable package to install the x64 OLE DB driver package.

### 1. Install OLEDB Drivers <a href="#id-1-install-oledb-drivers" id="id-1-install-oledb-drivers"></a>

* Visit the official Microsoft download page: \
  **Full List of Versions:** [https://learn.microsoft.com/en-us/sql/connect/oledb/release-notes-for-oledb-driver-for-sql-server?view=sql-server-ver16](https://learn.microsoft.com/en-us/sql/connect/oledb/release-notes-for-oledb-driver-for-sql-server?view=sql-server-ver16)\
  **Latest Version Only:** [https://learn.microsoft.com/en-us/sql/connect/oledb/download-oledb-driver-for-sql-server?view=sql-server-ver16](https://learn.microsoft.com/en-us/sql/connect/oledb/download-oledb-driver-for-sql-server?view=sql-server-ver16)
* Download **both** the x86 and x64 versions of the appropriate OLEDB driver (e.g., MSOLEDBSQL v19).
* Run both installers, following the on-screen prompts.

### 2. Install .NET Framework <a href="#id-2-install-net-framework" id="id-2-install-net-framework"></a>

* Premier Responder may require specific .NET Framework versions.
* Check your software documentation or system requirements for details.
* Download and install the necessary x86 and/or x64 .NET Framework versions from the official Microsoft website.

### 3. Restart Your System <a href="#id-3-restart-your-system" id="id-3-restart-your-system"></a>

* Restart your computer after driver installations to apply changes.

### 4. Verify Installation <a href="#id-4-verify-installation" id="id-4-verify-installation"></a>

* Confirm both OLEDB drivers are listed in "Programs and Features" or "Apps & features."

### 5. Test Premier Responder <a href="#id-5-test-premier-responder" id="id-5-test-premier-responder"></a>

* Launch Premier Responder and test its database connection.

### Advanced Troubleshooting <a href="#advanced-troubleshooting" id="advanced-troubleshooting"></a>

* **Install SQL Server Management Studio (SSMS):** This may install missing dependencies or help diagnose connection problems.
* **Contact Nexport Solutions Support:** For persistent issues, contact support for expert assistance.

**Note:** Always refer to official Microsoft documentation and Premier Responder documentation for the most accurate information.
