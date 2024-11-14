  -----------------
  **Case Review**
  -----------------

The **Case Review** tab is used construct queries against the cases
archive database for the purpose of reviewing and grading calls. 
Database queries are made to retrieve specific cases by selecting data
columns and entering criteria to search for.  To open **Case Review**
tab, log into Premier Responder Supervisor and select the **Tools** -
**Case Review** menu item.

<figure><img src=".gitbook/assets/Case Review_files/image001.png" alt=""><figcaption></figcaption></figure>{border="0" width="639"
height="400"}

The working database appears on the center status bar panel at the
bottom of the Premier Responder Supervisor window.  To use a different
database, select the **Archive - Open** menu item on the **Case Review**
tab toolbar.  This opens the **Select Database** tab and hides **Case
Review**.  On the **Select Database** tab, the **Use Access file
database**, **Use SQL Server database**, and **Use Oracle database**
options are for selecting the currently configured Access, SQL Server,
or Oracle archives.  Use the related **Change** button to configure a
different archive.  See the **Access Archive**, **SQL Server Archive**,
or **Oracle Archive** paragraphs in the [Email Alert - Data
Setup](Data%20Setup.htm) help topic.  Selecting the **Use cases
database** button configures the software to use the local cases data
file.  The **OK** button saves changes made on the **Select Database**
tab and returns to **Case Review**.  To exit without saving changes,
select the **X** or close button at the top right of the screen.  Upon
connecting to a new database, the bottom right status bar panel displays
the number of cases.

<figure><img src=".gitbook/assets/Case Review_files/image006.png" alt=""><figcaption></figcaption></figure>{border="0" width="639"
height="400"}

A query is constructed by indicating the data columns to include in the
query output.  This is done using the check boxes within the **Data
Columns** list.  Checked columns are included in the query output.  The
**Edit** button can be used to change the **Column Name**.  [A search
criterion]{style="font-size: 12.0pt; "}[ is
]{style="font-size: 12.0pt; font-family: Times New Roman"}entered at the
right of the form after first selecting an associated data column. 
Selecting the **Clear** button clears all search criteria and reloads
the default data columns.  Use the **Sample** drop down list to select a
random percentage of the query results for QA purposes.  The **Sample**
button defaults to 100 percent.

<figure><img src=".gitbook/assets/Case Review_files/image002.png" alt=""><figcaption></figcaption></figure>{border="0" width="639"
height="400"}

The **IS**, **FROM**, and **LIKE** option buttons are used to indicate
whether to find data values that match the [criterion
]{style="font-size: 12.0pt; font-family: Times New Roman"} exactly, fall
within a specified range, or match a pattern.  Selecting the **LIKE**
option button enables pattern matching.  The table below lists the
wildcard characters that can be used when pattern matching is enabled. 
If any of the wildcard characters are detected in a [criterion it is
left as it is, otherwise the default is to encase it between two %
wildcard characters so that any occurrence of the entered criterion in
the data column will result in a
match.]{style="font-size: 12.0pt; font-family: Times New Roman"}

   Wildcard character                                        Description                                                                                                                   Example
  -------------------- ---------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------
           \%                                   Any string of zero or more characters.                           \'%bleeding%\' finds records where  \'bleeding\' occurs anywhere in the text of the data column while  \'%bleeding\' finds those that end with \'bleeding\'.
    \_ (underscore)                                     Any single character.                                                                               \'\_xyz\' finds all four-character text entries that end with \'xyz\'.
         \[ \]              Any single character within the specified range (\[a-f\]) or set (\[abcdef\]).                          \'\[a-z\]ear\' finds text entries ending with \'ear\' and beginning with any single character between \'a\' and \'z\'.
         \[\^\]         Any single character not within the specified range (\[\^a-f\]) or set (\[\^abcdef\]).                          \'432\[\^l\]%\' finds all text entries beginning with \'432\' and where the following character is not \'l\'.

After the search criteria has been entered, selecting the **QA** button
or **Case-QA** menu item opens the **QA Cases** tab and loads the
resulting case records.  When Microsoft Excel is installed then case
records may also be exported to Excel using the **Export** button.  As
the query is executing, a message is displayed on the middle panel of
the status bar.  Once the query completes a progress bar appears over
the status bar while the query results are being processed.  While the
progress bar is visible, the operation can be aborted with the toolbar
**Cancel** toolbar button.  All other controls are disabled while the
query is running.

<figure><img src=".gitbook/assets/Case Review_files/image003.png" alt=""><figcaption></figcaption></figure>{border="0" width="639"
height="400"}

The **QA Cases** tab opens with case records resulting from the **QA**
button or **Case - QA** menu item selection.  Case records can be sorted
on any data column in either ascending or descending order.  [Clicking a
column header one time sorts case records on the column in ascending
order.  To sort on a column in descending order, click the column header
twice]{style="font-size: 12.0pt; font-family: Times New Roman"}.  Selecting
the **X** button at the far right of the toolbar closes the **QA Cases**
tab.

<figure><img src=".gitbook/assets/Case Review_files/image004.png" alt=""><figcaption></figcaption></figure>{border="0" width="639"
height="400"}

Selecting a case record on the **QA Cases** tab and then the **Open**
button or double clicking on a case record loads it into the [**Case
Report** tab](Case%20Reports.htm).  The [**Case Report**
tab](Case%20Reports.htm) appears with the selected case, hiding the **QA
Cases** tab.  To return to the **QA Cases** tab, select the **X**
toolbar button at the top right of the [**Case Report**
tab](Case%20Reports.htm).

<figure><img src=".gitbook/assets/Case Review_files/image005.png" alt=""><figcaption></figcaption></figure>{border="0" width="639"
height="400"}
