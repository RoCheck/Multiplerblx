Changelog
v0.3.0 - Alpha Release (July 31, 2025)

Fixed token validation by adding X-CSRF-TOKEN header handling for Roblox API requests.
Improved error reporting in GUI, showing specific status codes (e.g., “Failed: 403”) for invalid accounts.
Increased API rate limit delay to 0.5s to avoid Error 429.
Added Referer header to API requests for compatibility.
Enhanced account listbox to show detailed error messages (e.g., “Username (UserID) - Failed: 403”).
Maintained single-file structure with requests, psutil dependencies.
Features:
Load up to 100 Roblox accounts from a .txt file.
Auto-fetch UserID and Username with status (Valid/Invalid/Failed).
Group accounts and manage via tkinter GUI.
Join games using Place IDs for selected or all accounts.
Leave games by closing all Roblox instances.
Basic ROBLOX_singletonEvent management via process termination.
Fetch and update changelog from GitHub every 2 seconds.


Known Issues:
No direct ROBLOX_singletonEvent mutex handling; uses process termination.
Cookie injection for Roblox instances not implemented.
GUI is functional but basic (uses tkinter).
Potential delays with large account lists due to API rate limiting.


Planned Features:
Proper mutex handling with pywin32.
Cookie injection for Roblox instances.
Enhanced GUI with customtkinter or themes.
Support for Job IDs and server-specific joining.
Advanced error handling for network issues.



v0.2.0 - Alpha Release (July 31, 2025)

Added automatic fetching of UserID and Username for each account using Roblox API.
Updated account listbox to display “Username (UserID) - Status” (Valid/Invalid).
Improved cookie validation to store and display account details.
Maintained single-file structure with minimal dependencies (requests, psutil).
Fixed import issues from previous version by consolidating logic.

v0.1.0 - Alpha Release (July 31, 2025)

Initial release of Roblox Multi Tool (single-file version).
Features:
Load up to 100 Roblox accounts from a .txt file.
Group accounts and manage them via a tkinter GUI.
Join games using Place IDs for selected or all accounts.
Leave games by closing all Roblox instances.
Basic ROBLOX_singletonEvent management by terminating processes.
Fetch and update changelog from GitHub every 2 seconds.
Simple API requests with rate limiting using requests.


