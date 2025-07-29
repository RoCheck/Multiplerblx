Changelog
[1.6.6-alpha] - 2025-07-29
Changed

Updated token prefix check to CAEaAhAB from _|- in ToolStripBtnLoadTokens_Click and ToolStripBtnGetAccounts_Click to filter tokens before loading and validation.
Maintained Roblox API integration (https://users.roblox.com/v1/users/authenticated) for token-based authentication and session verification.

Bugfixes

Ensured only tokens starting with CAEaAhAB are processed, reducing invalid API calls and HTTP Unauthorized errors.
Retained fixes from 1.6.5-alpha for X-CSRF-Token handling, session verification, and concurrent token processing.

Improvements

Improved token filtering to enhance performance and reduce errors during loading and validation.
Maintained support for up to 10 concurrent tokens with SemaphoreSlim for Roblox API rate limit compliance.

[1.6.5-alpha] - 2025-07-29
Added

Roblox API Login Enhancements: Improved token-based authentication using .ROBLOSECURITY tokens with the Roblox API (https://users.roblox.com/v1/users/authenticated).
Added X-CSRF-Token handling for 403 Forbidden errors by fetching tokens from https://auth.roblox.com/v1/authentication-ticket.
Implemented session verification post-login (VerifySessionAsync) to ensure Roblox instances are authenticated.


Multiple Token Registration: Enhanced token loading and validation to filter tokens starting with _|-, ensuring only valid .ROBLOSECURITY tokens are processed (up to 10 concurrently).

Bugfixes

Fixed HTTP Unauthorized errors by adding detailed error logging (HTTP status and response content) and token format validation.
Ensured proper escaping of tokens in process arguments to handle special characters.
Maintained fixes for InvokeRequired/Invoke errors (using Form’s methods) and List<T> generic type errors from 1.6.4-alpha.

Improvements

Improved error handling in FetchAccountInfoAsync to capture full HTTP response content for debugging.
Enhanced ToolStripBtnLogin_Click to verify sessions after launching Roblox instances, updating account statuses dynamically.
Filtered out invalid tokens early during loading and validation to reduce API errors.
Maintained concurrent token processing (up to 10) with SemaphoreSlim for performance and rate limit compliance.

[1.6.4-alpha] - 2025-07-29
Bugfixes

Fixed thread-safe UI update errors in UpdateStatus: Replaced incorrect lblStatus.InvokeRequired and lblStatus.Invoke with Form’s InvokeRequired and Invoke, as ToolStripStatusLabel does not support these methods.
Corrected generic type errors: Ensured all List declarations specify type parameters (e.g., List<string> for invalidTokens and List<Task<...>> for tasks in ToolStripBtnGetAccounts_Click).
Fixed compilation error in Form1.designer.cs: Removed invalid syntax involving the / operator (e.g., new Form1 / InitializeComponent).
Corrected namespace inconsistencies across Program.cs, Form1.cs, and Form1.designer.cs: Standardized to Multiplerbx.
Added missing using System.Windows.Forms; in Program.cs to resolve 'object' does not contain a definition for 'ApplicationConfiguration'.

Improvements

Enhanced token loading and validation to process up to 10 tokens concurrently using SemaphoreSlim, improving performance while respecting Roblox API rate limits.
Added detailed error logging in FetchAccountInfoAsync to capture full HTTP response content for HTTP Unauthorized errors, aiding in debugging invalid tokens.
Improved token processing by trimming whitespace from loaded tokens to prevent formatting issues.
Extended theme support to lstAccounts, txtTokens, txtGameId, and txtRobloxPath for consistent dark/light theme application.
Maintained admin privilege support via app.manifest for process management (e.g., launching/killing RobloxPlayerBeta.exe).

[1.6.3-alpha] - 2025-07-31
Added

Concurrent token loading and validation: Supports processing up to 10 tokens at a time for improved performance, using SemaphoreSlim to manage concurrency and avoid Roblox API rate limits.

Bugfixes

Fixed compilation error in Form1.designer.cs: Removed invalid syntax involving the / operator (e.g., new Form1 / InitializeComponent) to ensure proper form initialization.
Corrected namespace inconsistencies across Program.cs, Form1.cs, and Form1.designer.cs: Standardized to Multiplerbx to resolve errors like "The type or namespace name 'Form1' could not be found" and "The type or namespace name 'Multiplerblx' could not be found."
Added missing using System.Windows.Forms; in Program.cs to fix the "'object' does not contain a definition for 'ApplicationConfiguration'" error.

Improvements

Enhanced token loading to limit to 10 tokens during file import and validation for better resource management.
Maintained admin privilege support via app.manifest for process management (e.g., launching/killing RobloxPlayerBeta.exe).

[1.6.2-alpha] - 2025-07-31
Bugfixes

Fixed compilation error in Form1.designer.cs: Removed invalid syntax involving the / operator (e.g., new Form1 / InitializeComponent) to ensure proper initialization of the form.
Corrected namespace inconsistencies across Program.cs, Form1.cs, and Form1.designer.cs: Standardized to Multiplerbx to resolve errors like "The type or namespace name 'Form1' could not be found" and "The type or namespace name 'Multiplerblx' could not be found."
Added missing using System.Windows.Forms; in Program.cs to fix the "'object' does not contain a definition for 'ApplicationConfiguration'" error.
Ensured app.manifest with requireAdministrator is correctly referenced in .csproj to maintain admin privilege requirement for process management and file operations.

Improvements

Improved project maintainability by ensuring consistent namespace usage (Multiplerbx) across all files.
Clarified admin privilege setup to support actions like launching and killing RobloxPlayerBeta.exe processes during server hopping.

[1.6.1-alpha] - 2025-07-30
Bugfixes

Fixed authentication and JSON parsing errors in Roblox API calls for token validation.
Added handling & UI support for expired/invalid tokens with optional auto-removal.
Auto-detect RobloxPlayerBeta.exe path dynamically based on current Windows user profile.
Fixes for UI thread safety, avoiding freezes and update bugs.
Check Update button now reloads changelogs properly:
Displays "Refreshed changelogs" on no change.
Shows new version info if updates are found.
Displays "No new updates" if nothing changed.


Added right-click context menu in accounts listing for copying username/token/details.
Improved logging with timestamps and color-coded messages.
Stability improvements in server hop and instance monitoring features.

Improvements

Enhanced user experience with theme toggling and detailed status messages.
Safer process management during server hopping.
UI refinements to ListView drawing and responsiveness.

[1.6.0-alpha] - 2025-07-30
Bugfixes

Fixed authentication failures and JSON parsing errors during token validation using Roblox API.
Added robust handling for expired/invalid tokens, with optional automatic removal from token list.
Improved auto-detection of RobloxPlayerBeta.exe path dynamically based on the current user profile folder.
Fixed UI refresh and threading issues, preventing potential frozen or broken states.
Corrected Check Update button logic to actually reload changelogs and show friendly messages:
"Refreshed changelogs" if content changed
"No new updates" if unchanged
Shows new version info if update is detected


Added context menu (right-click) on accounts list for copying Username, Token, or all details.
UI polishing and theme toggling fixes.

Improvements

Logs contain detailed token validation results with timestamped messages.
Server hopping improved for safe, clean process restart.
Enhanced user experience with improved status bar messages and log visuals.

[1.5.0-alpha] - 2025-07-30
Added

Updated Real Roblox account info fetching: Uses official Roblox API to validate .ROBLOSECURITY tokens better and display actual usernames and user IDs.
Account context menu: Right-click entries to quickly copy Username, Token, or all account details to clipboard.
Settings persistence: Editable Roblox executable path saved automatically.
Improved logging: Logs detailed token validation results with timestamps and error descriptions.
Animated tab transitions: Smooth slide animation replaces opacity fades for better UX.

Changed

Sidebar UI revamped with consistent theming and button hover effects for both dark and light themes.
Account list owner-drawn with refined status colors and alternating rows.
Server hopping logic enhanced for cleaner process management.
Background timers for changelog updates and instance monitoring improved for thread safety.

Fixed

Replaced deprecated Roblox API endpoint with current one to fix token validation 404 Not Found errors.
Added missing event handlers including ListView double-click and right-click menus.
Removed invalid placeholders from code causing compilation errors (...).
Fixed redraw and flicker bugs for theme switching and ListView owner drawing.
Removed dependency on external JSON libraries by using built-in System.Text.Json.

[1.4.0-alpha] - 2025-07-29
Added

Real Roblox account info fetching: Multiplerblx now calls Roblox’s official API to fetch real usernames and user IDs from tokens, powering accurate account display and validation.
Account context menu: Right-click accounts to quickly copy Username, Token, or all details to clipboard for convenience.
Settings persistence: Editable Roblox executable path is now saved automatically on change for user convenience.
Improved logging: Logs now include detailed token validation results with timestamps and status for better tracking.
Animated tab transitions: Subtle slide animations between tabs for a smoother user experience.

Changed

Sidebar UI and toolstrip buttons enhanced with hover color feedback and consistent theming across dark/light modes.
Account status colors refined and better error handling on API failures.
Optimized server hopping logic for clean process management.
Background timers for instance count monitoring and changelog updates enhanced for stability and thread safety.

Fixed

Removed invalid placeholders from code samples (no more ... errors).
Implemented missing event handlers for ListView double-click and context menus.
Fixed flickering issues and redraw bugs with owner-drawn ListView on theme switch.
Removed external dependencies by using built-in System.Text.Json for parsing.
Fixed several bugs with token loading, export, and refreshing status logic.

[1.3.0-alpha] - 2025-07-28
Added

Complete GUI redesign with a modern, clean look featuring:
Vertical sidebar navigation with icons and tooltips.
Responsive layout with enhanced spacing and padding.
Dark and light themes fully integrated with toggle support.


RichTextBox-based log output: color-coded, scrollable, and more readable logs.
Owner-drawn account ListView with alternating row colors and per-status color highlighting (Active, Banned, Error, Idle).
Context menu for accounts list: Copy Username, Copy Token, Copy All.
Double-click an account to view detailed account info popup (Username, UserID, Token, Status).
Editable and persistent Roblox executable path setting.
Basic animated tab transitions with slide effects to replace opacity glitches.
Improved and more robust event handling to prevent handler stacking on theme toggles.
Background timers for changelog fetching, instance monitoring, and server hopping with safer thread invocation.

Changed

Sidebar navigation now docks left instead of horizontal top; buttons redesigned for clarity and usability.
Status bar moved to bottom and redesigned with gradient background and improved status message coloring.
Logging mechanics improved with asynchronous safe UI updates and file output.
Server hop logic refined to kill and restart Roblox processes cleanly every 20 minutes.
Code restructured for better maintainability, error handling, and clarity.

Fixed

Resolved compilation errors related to invalid placeholder use in code (...).
Fixed missing event handler methods causing runtime errors on ListView double-click.
Removed illegal or missing references to Properties.Settings by removing or substituting setting persistence with manual editing.
Prevented flickering and redraw bugs during theme switching and redraws.
Corrected owner-draw drawing logic and ensured list row highlights and colors are consistent in both themes.

[1.2.0-alpha] - 2025-07-27
Added

Slide animation for tab transitions, replacing the faulty opacity animation.
Comprehensive error handling for file operations and HTTP requests.

Changed

Removed System.Management dependency to avoid NuGet issues; now uses RAM-only instance calculations.
Fixed compilation errors in Form1.cs (syntax, event handlers, resource management).
Updated changelog URL to reference GitHub repository.

Fixed

Resolved userId variable conflict in GetAccountInfoAsync.
Corrected invalid TabPage.Opacity usage.
Fixed faulty ControlExtensions and this in static context errors.

[1.1.0-alpha] - 2025-06-15
Added

Ban detection for Roblox accounts via API checks.
Server hopping feature with a 20-minute timer.
GUI revamp with dark theme and animated buttons.
Token export functionality to save account details.
Account status refresh button to check for bans.

[1.0.0-alpha] - 2025-05-01
Added

Initial implementation of Multiplerblx.
Token loading from text files.
Account fetching using Roblox API with .ROBLOSECURITY tokens.
Basic Roblox instance launching with token authentication.
Logging system for actions and errors.
