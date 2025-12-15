# Google Drive ACL Sync Tool

A Python automation tool to enforce folder permissions based on a "single source of truth" (a Master Users Sheet).

This tool is useful for **Access Control Enforcement** in corporate environments, ensuring that only authorized employees have access to specific sets of documents.

## ⚙️ How It Works

1.  **Reads Config:** Fetches a list of allowed email addresses from a specified Google Sheet.
2.  **Scans Folder:** Iterates through all Google Sheets within a target Drive folder.
3.  **Audits Permissions:** Compares actual file permissions against the allowed list.
4.  **Auto-Remediation:**
    *   ❌ **Revokes** access for users found on files but *not* in the master list.
    *   ✅ **Grants** Editor (`writer`) access to users in the master list who are missing access.
5.  **Reporting:** Generates a new Spreadsheet with a full log of all actions taken.

## 🚀 Setup & Usage

1.  Open the notebook in **Google Colab**.
2.  Update the configuration variables in the second cell:
    ```
    FOLDER_ID = 'YOUR_TARGET_FOLDER_ID'      # ID of the folder to manage
    EMAIL_SHEET_ID = 'YOUR_MASTER_SHEET_ID'  # ID of the sheet with allowed emails
    ```
3.  Run all cells.
4.  Authenticate via the Google OAuth prompt.
5.  Review the output log for removed/added permissions.

## ⚠️ Warning

**This script performs destructive actions.** 
It will actively remove permissions for any user not present in your Master Sheet. Run a test on a non-critical folder first.

## Requirements
*   `google-api-python-client`
*   `pandas`

## License
MIT
