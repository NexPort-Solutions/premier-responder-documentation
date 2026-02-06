# Document Files Manager

***

### **Document Files Manager**

The **Document Files Manager** is used in **Premier Responder Administrator** to manage files that can be opened by hyperlink actions.

## What this feature is

This feature adds document-based hyperlink actions to guide cards by introducing the **Open_Document** action type.

It includes:

* A document catalog (files + metadata).
* A selection dialog for choosing a document when configuring hyperlink actions.
* Fallback flags for missing-file and open-error scenarios.

## Why this feature exists

This feature lets agencies attach supporting files (PDFs, reference sheets, job aids) directly to guide card hyperlinks so call-takers can open the right document during an active call.

It helps by:

* Reducing time spent searching for external files.
* Keeping document references tied to configured guide-card behavior.
* Supporting fallback behavior when a primary document is unavailable.

## Access and permissions

* **Administrator users** can open the selection workflow for **Open_Document** actions.
* **Super Admin users** can upload files, create folders, edit metadata, and remove files.
* Non-Super-Admin users can still browse and select available documents where the workflow allows selection.

## Open the manager from hyperlink actions

* Log in to **Premier Responder Administrator**.
* Open **Edit - Guide Cards**.
* Open the hyperlink actions editor for a hyperlink and choose the **Open_Document** action type.
* Select the **Select Document** button to open the document selection window.

## Step-by-step: add and link a document

Use this workflow when you are adding a new file and linking it to a hyperlink action.

1. Open the **Select Document** window from an **Open_Document** action.
2. In the tree panel, select the target folder.
3. Select **Upload** and choose a file.
4. If prompted that the file already exists, choose **Yes** to replace it or **No** to cancel.
5. Select the uploaded file in the tree.
6. Enter or update **Title** and optional **Long Description**.
7. Select **Save**.
8. Select **Select** to bind the chosen document to the action.
9. Confirm the action value now shows the document title (GUID is stored internally).

## Step-by-step: create folders

1. In the tree panel, select the parent folder.
2. Select **New Folder**.
3. Enter the folder name.
4. Select **OK**.
5. Verify the new folder appears in the tree.

## Step-by-step: configure fallback documents

Use fallback flags to control which document opens when the primary document cannot be found or opened.

1. Select a document in the tree.
2. Set **Use For Not Found** if this document should open when a linked file is missing.
3. Set **Use For Error** if this document should open when file launch fails.
4. Select **Save**.

## Selection window behavior

When opened from hyperlink actions, the selection window uses the same document manager control and adds:

* **Select** button
* **Cancel** button

If the logged-in user is a **Super Admin**, full file-management controls remain available in that same modal window.

## Metadata fields and behavior

* **Document GUID**: read-only unique identifier used internally by actions.
* **Relative Path**: read-only path under the documents root.
* **Title**: display name shown in the tree and action UI.
* **Long Description**: optional descriptive text.
* **Use For Not Found**: fallback candidate when file is missing.
* **Use For Error**: fallback candidate when open action fails.

## Tree and path behavior

* The tree displays the document **Title** when available.
* If Title is blank, the tree falls back to the file name.
* The tree uses file-type-appropriate icons.
* The **Relative Path** field is not editable in the UI.
* **Upload** and **New Folder** actions are shown beneath the tree.

## Replacing files

Upload supports in-place replacement by file name in the selected folder:

* If the target file name already exists, the user is prompted to overwrite.
* Choosing **Yes** replaces the existing file on disk.

## Remove behavior

Removing a file deletes:

* The selected file metadata entry.
* Any linked **Open_Document** actions/conditions that reference that document GUID.

## Current limitations

The following capabilities are planned but not yet available:

* Move an existing file to another folder from the UI.
* Replace a selected file through a dedicated **Replace** command.
