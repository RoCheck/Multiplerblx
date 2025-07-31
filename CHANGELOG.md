# Changelog

## v0.4.0 - Alpha Release (July 31, 2025)
- Fixed 401 errors during token validation with five improvements:
  - Enhanced CSRF token fetching using `https://auth.roblox.com/v1/authentication-ticket` with retries.
  - Added browser-like headers (`User-Agent`, `Origin`, `Accept`) to bypass anti-bot checks.
  - Implemented cookie format validation to reject malformed cookies.
  - Added debug log window in GUI to display detailed API errors.
  - Added fallback validation endpoint (`https://api.roblox.com/v2/user`) for robustness.
- Improved GUI layout with debug log section and wider account listbox.
- Maintained single-file structure with `requests`, `psutil` dependencies.
- Features:
  - Load up to 100 Roblox accounts from a `.txt` file.
  - Auto-fetch UserID and Username with status (Valid/Invalid/Failed).
  - Group accounts and manage via `tkinter` GUI.
  - Join games using Place IDs for selected or all accounts.
  - Leave games by closing all Roblox instances.
  - Basic `ROBLOX_singletonEvent` management via process termination.
  - Fetch and update changelog from GitHub every 2 seconds.
- Known Issues:
  - No direct `ROBLOX_singletonEvent` mutex handling; uses process termination.
  - Cookie injection for Roblox instances not implemented.
  - GUI is functional but basic (uses `tkinter`).
  - Potential delays with large account lists due to 0.5s rate limiting.
- Planned Features:
  - Proper mutex handling with `pywin32`.
  - Cookie injection for Roblox instances.
  - Enhanced GUI with `customtkinter` or themes.
  - Support for Job IDs and server-specific joining.
  - Advanced error handling for network issues.

## v0.3.0 - Alpha Release (July 31, 2025)
- Fixed token validation by adding `X-CSRF-TOKEN` header handling.
- Improved error reporting in GUI with specific status codes.
- Increased API rate limit delay to 0.5s to avoid Error 429.
- Added `Referer` header to API requests.

## v0.2.0 - Alpha Release (July 31, 2025)
- Added automatic fetching of UserID and Username.
- Updated account listbox to display “Username (UserID) - Status”.

## v0.1.0 - Alpha Release (July 31, 2025)
- Initial release with account loading, game joining/leaving, and changelog fetching.
