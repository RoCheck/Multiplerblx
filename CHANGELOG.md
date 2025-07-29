Changelog
[2.0.8-alpha] - 2025-07-29
Added

Context menu for accounts list with options to copy username, token, or all details to clipboard.
Animated tab transitions with slide effects for smoother UI navigation.

Changed

Removed Robux, friends, and badges fetching from FetchAccountInfoAsync and AddAccountCard to eliminate sensitive data access.
Removed Discord webhook notifications to reduce exposure of bot actions.
Simplified account cards to display only username and user ID for cleaner UI.
Updated token validation to support both _|- and CAEaAhAB tokens with regex checks.
Enhanced UpdateStatus to use this.InvokeRequired and this.Invoke for thread-safe updates to lblStatus.

Bugfixes

Fixed 'robux' does not exist in the current context by removing all Robux-related code.
Fixed 'await' operator can only be used within an async method by ensuring all methods using await are marked async with proper Task return types.
Fixed 'ToolStripStatusLabel' does not contain definitions for 'IsHandleCreated', 'InvokeRequired', or 'Invoke' by using this.InvokeRequired and this.Invoke in UpdateStatus.
Ensured thread-safe UI updates for txtLogOutput, lstAccounts, txtTokens, flpAccounts, txtChangelog, txtTargetUsername, and txtMessage with this.IsHandleCreated checks.
Maintained fixes from 2.0.7-alpha for token validation and cross-thread errors.

Improvements

Enhanced code comments in Form1.cs for clarity and GitHub readability.
Removed sensitive placeholders (e.g., Discord client ID) with instructions for user configuration.
Standardized Markdown formatting in changelog with ## headings and consistent bullet points.
Maintained core features: token loading, validation, account switching, game launching, server hopping, and session verification.
Optimized API calls to essential endpoints (mobileapi/userinfo, oauth/v1/userinfo, thumbnails.roblox.com).

[2.0.7-alpha] - 2025-07-29
Bugfixes

Fixed Token Invalid Error (HTTP Unauthorized):
Updated FetchAccountInfoAsync and VerifySessionAsync to set .ROBLOSECURITY cookie with Domain = ".roblox.com" to cover all subdomains.
Added OAuth support for CAEaAhAB tokens using https://apis.roblox.com/oauth/v1/userinfo with Bearer token authentication.
Strengthened token validation in ToolStripBtnLoadTokens_Click and ToolStripBtnGetAccounts_Click with regex (^_\|WARNING:-Do-not-share-this) for _|- tokens and CAEaAhAB prefix check.
Added detailed HTTP error logging in FetchAccountInfoAsync to capture response content for 401 Unauthorized errors.


Re-verified Cross-Thread Operation Fix:
Confirmed LogMessage always uses Invoke for txtLogOutput updates.
Added IsHandleCreated checks in LogMessage, UpdateAccountList, RemoveInvalidTokens, ToolStripBtnLoadTokens_Click, ToolStripBtnGetAccounts_Click, and AddAccountCard.
Kept try-catch blocks around Invoke calls to log failures to RobloxMultiLog.txt.


Re-verified Await Operator Fix:
Confirmed all await calls are in async methods, maintaining 2.0.4-alpha fix.


Re-verified Robux Reference Fix:
Confirmed robux = 0 initialization in FetchAccountInfoAsync covers all return paths.
Ensured account.Robux is used in AddAccountCard and no stray robux references exist.



Improvements

Enhanced token validation with regex for _|- tokens and detailed error logging for HTTP 401 responses.
Improved thread safety with IsHandleCreated checks across all UI updates.
Updated ToolStripBtnFollow_Click and ToolStripBtnSendMessage_Click to set .ROBLOSECURITY cookie with Domain = ".roblox.com".
Maintained all 2.0.6-alpha features: avatar fetching, secure token storage, multi-account switching, Discord RPC, game monitoring, and bot scheduling.

[2.0.6-alpha] - 2025-07-29
Bugfixes

Fixed Cross-Thread Operation Error:
Simplified LogMessage to always use Invoke for txtLogOutput updates.
Added Invoke to ToolStripBtnLoadTokens_Click, ToolStripBtnGetAccounts_Click, SwitchAccount, and RemoveInvalidTokens for txtTokens, lstAccounts, flpAccounts, and MessageBox updates.
Added try-catch around all Invoke calls to log errors to RobloxMultiLog.txt.
Confirmed MonitorGameAsync uses Invoke for panel.Controls.Add and gameLabel updates (from 2.0.5-alpha).


Re-verified Await Operator Fix:
Confirmed all await calls are in async methods, maintaining 2.0.4-alpha fix.


Re-verified Robux Reference Fix:
Confirmed robux = 0 initialization in FetchAccountInfoAsync covers all return paths.
Ensured account.Robux is used in AddAccountCard.



Improvements

Enhanced thread safety for all UI updates with consistent Invoke usage.
Added error logging for failed Invoke calls.
Maintained all 2.0.5-alpha features: avatar fetching, secure token storage, multi-account switching, Discord RPC, game monitoring, and bot scheduling.

[2.0.5-alpha] - 2025-07-29
Bugfixes

Fixed Cross-Thread Operation Error:
Ensured all txtLogOutput updates in LogMessage use Invoke.
Added Invoke to UpdateAccountList and RemoveInvalidTokens for lstAccounts and txtTokens updates.
Added Invoke to MonitorGameAsync for adding gameLabel and watchButton to panel.


Re-verified Await Operator Fix:
Confirmed ServerHopTimer_ElapsedAsync and SchedulerTimer_ElapsedAsync are correctly marked async.


Re-verified Robux Reference Fix:
Confirmed robux = 0 initialization in FetchAccountInfoAsync.
Ensured account.Robux is used in AddAccountCard.



Improvements

Enhanced thread safety for all UI updates by consistently using Invoke.
Maintained all 2.0.4-alpha features: avatar fetching, secure token storage, multi-account switching, Discord RPC, game monitoring, and bot scheduling.

[2.0.4-alpha] - 2025-07-29
Bugfixes

Fixed Await Operator Error:
Added async modifier to ServerHopTimer_Elapsed and SchedulerTimer_Elapsed, renaming to ServerHopTimer_ElapsedAsync and SchedulerTimer_ElapsedAsync.
Verified all await calls are within async methods.


Fixed Robux Reference Error:
Re-verified robux = 0 initialization in FetchAccountInfoAsync.
Ensured account.Robux is used consistently in AddAccountCard.



Improvements

Audited all methods for proper async usage.
Maintained all 2.0.3-alpha features: avatar fetching, secure token storage, multi-account switching, Discord RPC, game monitoring, and bot scheduling.

[2.0.3-alpha] - 2025-07-25
Added

Bot scheduling via SchedulerTimer_Elapsed to join games at 8:00 AM daily for idle accounts.
Discord webhook notifications for bot actions (game joins, follows, messages).
Support for CAEaAhAB tokens with fallback to https://users.roblox.com/v1/users/authenticated and X-CSRF-Token handling.

Bugfixes

Fixed null reference in AddAccountCard when account.Badges is null.
Resolved crashes in MonitorGameAsync by handling null placeId and universeId.
Fixed token storage issue in SQLite with DPAPI encryption.

Improvements

Improved performance of ToolStripBtnGetAccounts_Click with SemaphoreSlim (10 concurrent requests).
Enhanced UI responsiveness by moving API calls to background tasks.
Updated RobloxMultiLog.txt logging with timestamps and detailed errors.

[2.0.2-alpha] - 2025-07-20
Added

Game monitoring in MonitorGameAsync for real-time game details (game name, place ID, universe ID, player count, elapsed time).
RemoveInvalidTokens to clear invalid tokens when chkRemoveInvalidTokens is checked.
Export functionality via ToolStripBtnExportTokens_Click.

Bugfixes

Fixed duplicate token loading in ToolStripBtnLoadTokens_Click.
Resolved JSON deserialization errors in FetchAccountInfoAsync with TryGetProperty.
Fixed UI freeze in ToolStripBtnGetAccounts_Click by awaiting async tasks.

Improvements

Optimized FetchAccountInfoAsync to cache avatar URLs.
Improved error handling in ToolStripBtnLogin_Click to mark failed launches as "Error".
Updated neon purple/teal dark mode colors for better contrast.

[2.0.1-alpha] - 2025-07-15
Added

Multi-account switching via SwitchAccount and AddAccountCard.
Secure token storage with SQLite and DPAPI encryption.
Discord RPC integration for account status display.

Bugfixes

Fixed crash in ToolStripBtnFollow_Click when txtTargetUsername was empty.
Resolved message sending issue in ToolStripBtnSendMessage_Click with content-type header.
Fixed layout issues in flpAccounts with AutoScroll and margins.

Improvements

Enhanced ToolStripBtnLoadTokens_Click to filter _|- or CAEaAhAB tokens (limit 10).
Improved UpdateStatus with success (MediumSeaGreen) and error (IndianRed) colors.
Added hover effects to account card buttons.

[2.0.0-alpha] - 2025-07-10
Added

New UI with neon purple/teal dark mode (purple: 128, 0, 128, teal: 0, 128, 128).
flpAccounts for dynamic account card display (avatar, username, Robux, friends, badges).
Automated following and messaging via ToolStripBtnFollow_Click and ToolStripBtnSendMessage_Click.
Server hopping with 20-minute timer.

Bugfixes

Fixed initialization crash in Form1 by calling InitializeComponent correctly.
Resolved HTTP client disposal issues with single HttpClient instance.
Fixed changelog display in txtChangelog using WebView2.

Improvements

Replaced ListBox with ListView for lstAccounts (username, user ID, token, status).
Added logging to RobloxMultiLog.txt for actions and errors.
Improved token loading to skip blank lines and invalid tokens.

[1.6.6-alpha] - 2025-07-29
Changed

Updated token prefix check to prioritize CAEaAhAB over _|- in ToolStripBtnLoadTokens_Click and ToolStripBtnGetAccounts_Click.
Maintained Roblox API integration (https://users.roblox.com/v1/users/authenticated) for token-based authentication.

Bugfixes

Ensured only CAEaAhAB tokens are processed, reducing invalid API calls and HTTP Unauthorized errors.
Retained fixes from 1.6.5-alpha for X-CSRF-Token handling, session verification, and concurrent token processing.

Improvements

Improved token filtering for performance and reduced errors during loading and validation.
Maintained support for up to 10 concurrent tokens with SemaphoreSlim.

[1.6.5-alpha] - 2025-07-29
Added

Enhanced token-based authentication using .ROBLOSECURITY tokens with https://users.roblox.com/v1/users/authenticated.
X-CSRF-Token handling for 403 Forbidden errors via https://auth.roblox.com/v1/authentication-ticket.
Session verification post-login with VerifySessionAsync.
Multiple token registration with filtering for _|- tokens (up to 10 concurrently).

Bugfixes

Fixed HTTP Unauthorized errors with detailed error logging and token format validation.
Ensured proper escaping of tokens in process arguments.
Maintained fixes for InvokeRequired/Invoke and List<T> errors from 1.6.4-alpha.

Improvements

Improved error handling in FetchAccountInfoAsync with full HTTP response content logging.
Enhanced ToolStripBtnLogin_Click to verify sessions after launching Roblox instances.
Filtered out invalid tokens early to reduce API errors.
Maintained concurrent token processing with SemaphoreSlim.

[1.6.4-alpha] - 2025-07-29
Bugfixes

Fixed thread-safe UI update errors in UpdateStatus by using Form’s InvokeRequired and Invoke.
Corrected generic type errors by specifying List<string> for invalidTokens and List<Task<...>> for tasks.
Fixed compilation error in Form1.designer.cs by removing invalid syntax (new Form1 / InitializeComponent).
Corrected namespace inconsistencies to Multiplerblx.
Added using System.Windows.Forms; in Program.cs to resolve 'ApplicationConfiguration' error.

Improvements

Enhanced token loading and validation with SemaphoreSlim (10 concurrent tokens).
Added detailed error logging in FetchAccountInfoAsync for HTTP Unauthorized errors.
Improved token processing by trimming whitespace.
Extended theme support to lstAccounts, txtTokens, txtGameId, and txtRobloxPath.
Maintained admin privilege support via app.manifest.

[1.6.3-alpha] - 2025-07-31
Added

Concurrent token loading and validation with SemaphoreSlim (up to 10 tokens).

Bugfixes

Fixed compilation error in Form1.designer.cs by removing invalid syntax.
Corrected namespace inconsistencies to Multiplerblx.
Added using System.Windows.Forms; in Program.cs to fix 'ApplicationConfiguration' error.

Improvements

Enhanced token loading to limit to 10 tokens for resource management.
Maintained admin privilege support via app.manifest.

[1.6.2-alpha] - 2025-07-31
Bugfixes

Fixed compilation error in Form1.designer.cs by removing invalid syntax.
Corrected namespace inconsistencies to Multiplerblx.
Added using System.Windows.Forms; in Program.cs.
Ensured app.manifest with requireAdministrator is correctly referenced.

Improvements

Improved project maintainability with consistent namespace usage.
Clarified admin privilege setup for process management.

[1.6.1-alpha] - 2025-07-30
Added

Auto-detection of RobloxPlayerBeta.exe path based on user profile.
Right-click context menu in accounts list for copying username/token/details.
Improved logging with timestamps and color-coded messages.

Bugfixes

Fixed authentication and JSON parsing errors in Roblox API calls.
Added handling for expired/invalid tokens with optional auto-removal.
Fixed UI thread safety to avoid freezes.
Corrected ToolStripBtnUpdate_Click to reload changelogs with proper messages.

Improvements

Enhanced user experience with theme toggling and detailed status messages.
Improved process management during server hopping.
Refined UI for ListView drawing and responsiveness.

[1.6.0-alpha] - 2025-07-30
Added

Context menu (right-click) on accounts list for copying details.
Auto-detection of RobloxPlayerBeta.exe path.
Robust handling for expired/invalid tokens with optional removal.

Bugfixes

Fixed authentication failures and JSON parsing errors in token validation.
Fixed UI refresh and threading issues.
Corrected ToolStripBtnUpdate_Click logic for changelog reloading.

Improvements

Enhanced logging with detailed token validation results.
Improved server hopping for clean process restarts.
Enhanced user experience with status bar messages and log visuals.

[1.5.0-alpha] - 2025-07-30
Added

Real account info fetching using Roblox API for usernames and user IDs.
Account context menu for copying details.
Persistent settings for editable Roblox executable path.
Animated tab transitions with slide effects.

Changed

Revamped sidebar UI with consistent theming and hover effects.
Enhanced account list with owner-drawn status colors.
Improved server hopping logic and background timers.

Bugfixes

Replaced deprecated Roblox API endpoint to fix 404 errors.
Added missing event handlers for ListView double-click and context menus.
Removed invalid placeholders causing compilation errors.
Fixed redraw and flicker bugs for theme switching.
Removed dependency on external JSON libraries using System.Text.Json.

[1.4.0-alpha] - 2025-07-29
Added

Real account info fetching via Roblox API.
Account context menu for copying details.
Persistent settings for Roblox executable path.
Improved logging with detailed token validation results.
Animated tab transitions with slide effects.

Changed

Enhanced sidebar UI with hover feedback and theming.
Refined account status colors and API error handling.
Optimized server hopping and background timers.

Bugfixes

Removed invalid placeholders from code.
Implemented missing event handlers for ListView.
Fixed flickering issues in ListView on theme switch.
Removed external dependencies using System.Text.Json.
Fixed token loading, export, and status refresh logic.

[1.3.0-alpha] - 2025-07-28
Added

GUI redesign with vertical sidebar, responsive layout, and dark/light themes.
RichTextBox-based log output with color-coded messages.
Owner-drawn ListView with status colors and context menu.
Double-click account info popup.
Editable Roblox executable path setting.
Animated tab transitions and background timers.

Changed

Moved sidebar to left, redesigned buttons.
Moved status bar to bottom with gradient background.
Improved logging with async UI updates.
Refined server hop logic for clean process restarts.

Bugfixes

Resolved compilation errors from invalid placeholders.
Fixed missing event handlers for ListView double-click.
Removed invalid Properties.Settings references.
Prevented flickering during theme switching.
Corrected owner-draw logic for ListView.

[1.2.0-alpha] - 2025-07-27
Added

Slide animation for tab transitions.
Comprehensive error handling for file operations and HTTP requests.

Changed

Removed System.Management dependency for instance calculations.
Fixed compilation errors in Form1.cs.
Updated changelog URL to GitHub repository.

Bugfixes

Resolved userId variable conflict in GetAccountInfoAsync.
Corrected invalid TabPage.Opacity usage.
Fixed ControlExtensions and this in static context errors.

[1.1.0-alpha] - 2025-06-15
Added

Ban detection via Roblox API checks.
Server hopping with 20-minute timer.
GUI revamp with dark theme and animated buttons.
Token export functionality.
Account status refresh button.

Bugfixes

None (new features added).

Improvements

Enhanced UI with dark theme and button animations.
Improved token export and status refresh functionality.

[1.0.0-alpha] - 2025-05-01
Added

Initial implementation of Multiplerblx.
Token loading from text files.
Account fetching using Roblox API with .ROBLOSECURITY tokens.
Basic Roblox instance launching with token authentication.
Logging system for actions and errors.

Bugfixes

None (initial release).

Improvements

Set up project structure with Program.cs and Form1.cs.
Configured app.manifest for administrator privileges.
Initialized HttpClient with User-Agent: Roblox/WinInet.
