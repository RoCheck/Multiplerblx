# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [2.0.8-alpha] - 2025-07-29

### ✨ Added
- **Context Menu Enhancement**: Added right-click context menu for accounts list with options to copy username, token, or all details to clipboard
- **UI Animations**: Implemented animated tab transitions with smooth slide effects for enhanced navigation experience

### 🔄 Changed
- **Security Improvements**: Removed Robux, friends, and badges fetching from `FetchAccountInfoAsync` and `AddAccountCard` to eliminate sensitive data access
- **Notification System**: Removed Discord webhook notifications to reduce exposure of bot actions
- **UI Simplification**: Simplified account cards to display only username and user ID for cleaner interface
- **Token Support**: Updated token validation to support both `_|-` and `CAEaAhAB` tokens with regex pattern matching
- **Thread Safety**: Enhanced `UpdateStatus` to use `this.InvokeRequired` and `this.Invoke` for proper thread-safe UI updates

### 🐛 Fixed
- Resolved `'robux' does not exist in the current context` compilation error by removing all Robux-related code
- Fixed `'await' operator can only be used within an async method` by ensuring proper async method signatures with Task return types
- Corrected `'ToolStripStatusLabel' does not contain definitions` error by implementing proper thread-safe UI updates
- Ensured thread-safe operations for all UI controls: `txtLogOutput`, `lstAccounts`, `txtTokens`, `flpAccounts`, `txtChangelog`, `txtTargetUsername`, and `txtMessage`
- Maintained all fixes from v2.0.7-alpha for token validation and cross-thread errors

### 🚀 Improvements
- **Code Quality**: Enhanced code comments in `Form1.cs` for better clarity and GitHub readability
- **Security**: Removed sensitive placeholders (Discord client ID) with clear user configuration instructions
- **Documentation**: Standardized Markdown formatting throughout changelog with consistent headings and bullet points
- **Core Features**: Maintained essential functionality including token loading, validation, account switching, game launching, server hopping, and session verification
- **API Optimization**: Streamlined API calls to essential endpoints only (`mobileapi/userinfo`, `oauth/v1/userinfo`, `thumbnails.roblox.com`)

---

## [2.0.7-alpha] - 2025-07-29

### 🐛 Critical Fixes

#### Token Authentication Issues
- **Fixed HTTP 401 Unauthorized Errors**: Updated `FetchAccountInfoAsync` and `VerifySessionAsync` to properly set `.ROBLOSECURITY` cookie with `Domain = ".roblox.com"` for full subdomain coverage
- **OAuth Support**: Added support for `CAEaAhAB` tokens using `https://apis.roblox.com/oauth/v1/userinfo` with Bearer token authentication
- **Enhanced Validation**: Strengthened token validation with regex pattern `^_\|WARNING:-Do-not-share-this` for `_|-` tokens and `CAEaAhAB` prefix verification
- **Error Logging**: Implemented detailed HTTP error logging to capture response content for 401 Unauthorized errors

#### Thread Safety Improvements
- **Cross-Thread Operations**: Re-verified and enhanced thread-safe UI updates across all components
- **Handle Validation**: Added `IsHandleCreated` checks in critical methods: `LogMessage`, `UpdateAccountList`, `RemoveInvalidTokens`, `ToolStripBtnLoadTokens_Click`, `ToolStripBtnGetAccounts_Click`, and `AddAccountCard`
- **Error Handling**: Implemented comprehensive try-catch blocks around all `Invoke` calls with logging to `RobloxMultiLog.txt`

#### Code Quality Assurance
- **Async Operations**: Re-verified all `await` calls are properly contained within async methods
- **Reference Fixes**: Confirmed `robux = 0` initialization covers all return paths in `FetchAccountInfoAsync`

### 🚀 Improvements
- **Authentication Flow**: Enhanced token validation with regex patterns and detailed HTTP 401 error logging
- **Thread Safety**: Improved thread safety with comprehensive `IsHandleCreated` checks across all UI updates
- **Cookie Management**: Updated `ToolStripBtnFollow_Click` and `ToolStripBtnSendMessage_Click` to use proper domain-wide cookie settings
- **Feature Retention**: Maintained all v2.0.6-alpha features including avatar fetching, secure token storage, multi-account switching, Discord RPC, game monitoring, and bot scheduling

---

## [2.0.6-alpha] - 2025-07-29

### 🐛 Major Fixes

#### Cross-Thread Operation Errors
- **UI Thread Safety**: Simplified `LogMessage` to consistently use `Invoke` for all `txtLogOutput` updates
- **Method Updates**: Added proper `Invoke` calls to `ToolStripBtnLoadTokens_Click`, `ToolStripBtnGetAccounts_Click`, `SwitchAccount`, and `RemoveInvalidTokens`
- **Error Handling**: Implemented try-catch blocks around all `Invoke` calls with error logging to `RobloxMultiLog.txt`
- **Game Monitoring**: Confirmed `MonitorGameAsync` uses proper `Invoke` for `panel.Controls.Add` and `gameLabel` updates

#### Code Verification
- **Async Compliance**: Re-verified all `await` calls are within async methods (maintained from v2.0.4-alpha)
- **Reference Integrity**: Confirmed `robux = 0` initialization and consistent `account.Robux` usage

### 🚀 Improvements
- **Thread Safety**: Enhanced thread safety for all UI updates with consistent `Invoke` usage patterns
- **Error Logging**: Added comprehensive error logging for failed `Invoke` operations
- **Feature Maintenance**: Preserved all v2.0.5-alpha features including avatar fetching, secure token storage, multi-account switching, Discord RPC, game monitoring, and bot scheduling

---

## [2.0.5-alpha] - 2025-07-29

### 🐛 Fixes
- **Thread Safety**: Ensured all `txtLogOutput` updates in `LogMessage` use proper `Invoke` calls
- **UI Updates**: Added `Invoke` to `UpdateAccountList` and `RemoveInvalidTokens` for safe `lstAccounts` and `txtTokens` updates
- **Game Monitoring**: Added `Invoke` to `MonitorGameAsync` for thread-safe addition of `gameLabel` and `watchButton` to panels
- **Async Verification**: Re-verified `ServerHopTimer_ElapsedAsync` and `SchedulerTimer_ElapsedAsync` async compliance
- **Reference Consistency**: Confirmed `robux = 0` initialization and `account.Robux` usage in `AddAccountCard`

### 🚀 Improvements
- **Thread Safety**: Enhanced thread safety across all UI updates with consistent `Invoke` implementation
- **Feature Retention**: Maintained all v2.0.4-alpha capabilities including avatar fetching, secure token storage, multi-account switching, Discord RPC, game monitoring, and bot scheduling

---

## [2.0.4-alpha] - 2025-07-29

### 🐛 Critical Fixes
- **Async Operations**: Fixed await operator errors by adding `async` modifier to `ServerHopTimer_Elapsed` and `SchedulerTimer_Elapsed` (renamed to `*Async` variants)
- **Method Compliance**: Verified all `await` calls are properly contained within async methods
- **Reference Errors**: Re-verified `robux = 0` initialization in `FetchAccountInfoAsync` and consistent `account.Robux` usage in `AddAccountCard`

### 🚀 Improvements
- **Code Audit**: Comprehensive audit of all methods for proper async/await usage patterns
- **Feature Stability**: Maintained all v2.0.3-alpha features including avatar fetching, secure token storage, multi-account switching, Discord RPC, game monitoring, and bot scheduling

---

## [2.0.3-alpha] - 2025-07-25

### ✨ Added
- **Bot Scheduling**: Implemented automated bot scheduling via `SchedulerTimer_Elapsed` to join games at 8:00 AM daily for idle accounts
- **Discord Integration**: Added Discord webhook notifications for comprehensive bot action tracking (game joins, follows, messages)
- **Token Support**: Enhanced support for `CAEaAhAB` tokens with fallback to `https://users.roblox.com/v1/users/authenticated` and proper X-CSRF-Token handling

### 🐛 Fixed
- **Null Reference**: Resolved null reference exception in `AddAccountCard` when `account.Badges` is null
- **Game Monitoring**: Fixed crashes in `MonitorGameAsync` by implementing proper null handling for `placeId` and `universeId`
- **Data Storage**: Resolved token storage issues in SQLite with proper DPAPI encryption implementation

### 🚀 Improvements
- **Performance**: Enhanced `ToolStripBtnGetAccounts_Click` performance using `SemaphoreSlim` with 10 concurrent request limit
- **UI Responsiveness**: Improved UI responsiveness by migrating API calls to background tasks
- **Logging**: Updated `RobloxMultiLog.txt` logging system with timestamps and detailed error reporting

---

## [2.0.2-alpha] - 2025-07-20

### ✨ Added
- **Game Monitoring**: Implemented real-time game monitoring in `MonitorGameAsync` displaying game name, place ID, universe ID, player count, and elapsed time
- **Token Management**: Added `RemoveInvalidTokens` functionality with user-controlled invalid token removal via `chkRemoveInvalidTokens`
- **Export Features**: Implemented token export functionality through `ToolStripBtnExportTokens_Click`

### 🐛 Fixed
- **Token Loading**: Resolved duplicate token loading issues in `ToolStripBtnLoadTokens_Click`
- **JSON Parsing**: Fixed JSON deserialization errors in `FetchAccountInfoAsync` using `TryGetProperty` for safer parsing
- **UI Performance**: Eliminated UI freezing in `ToolStripBtnGetAccounts_Click` by properly awaiting async tasks

### 🚀 Improvements
- **Caching**: Optimized `FetchAccountInfoAsync` with avatar URL caching for improved performance
- **Error Handling**: Enhanced error handling in `ToolStripBtnLogin_Click` with proper "Error" status marking for failed launches
- **Theme**: Updated neon purple/teal dark mode color scheme for improved contrast and visual appeal

---

## [2.0.1-alpha] - 2025-07-15

### ✨ Added
- **Multi-Account System**: Implemented comprehensive multi-account switching via `SwitchAccount` and `AddAccountCard`
- **Secure Storage**: Added secure token storage using SQLite database with DPAPI encryption
- **Discord RPC**: Integrated Discord Rich Presence for real-time account status display

### 🐛 Fixed
- **Input Validation**: Fixed application crash in `ToolStripBtnFollow_Click` when `txtTargetUsername` field was empty
- **Message System**: Resolved message sending failures in `ToolStripBtnSendMessage_Click` by adding proper content-type headers
- **Layout Issues**: Fixed layout problems in `flpAccounts` with proper `AutoScroll` and margin configurations

### 🚀 Improvements
- **Token Filtering**: Enhanced `ToolStripBtnLoadTokens_Click` to filter `_|-` or `CAEaAhAB` tokens with 10-token limit
- **Status Display**: Improved `UpdateStatus` with color-coded feedback (success: MediumSeaGreen, error: IndianRed)
- **User Experience**: Added hover effects to account card buttons for better interactivity

---

## [2.0.0-alpha] - 2025-07-10

### ✨ Major Release - Complete UI Overhaul
- **Modern UI**: Introduced completely redesigned interface with neon purple/teal dark mode theme (purple: 128, 0, 128, teal: 0, 128, 128)
- **Dynamic Accounts**: Implemented `flpAccounts` for dynamic account card display showing avatar, username, Robux, friends, and badges
- **Automation Features**: Added automated following and messaging through `ToolStripBtnFollow_Click` and `ToolStripBtnSendMessage_Click`
- **Server Hopping**: Implemented automatic server hopping with 20-minute timer intervals

### 🐛 Fixed
- **Initialization**: Resolved application crash during `Form1` initialization by correcting `InitializeComponent` calls
- **HTTP Management**: Fixed HTTP client disposal issues by implementing single `HttpClient` instance pattern
- **Changelog Display**: Corrected changelog rendering in `txtChangelog` using WebView2 integration

### 🚀 Improvements
- **Account Display**: Replaced basic ListBox with enhanced ListView for `lstAccounts` showing username, user ID, token, and status
- **Logging System**: Added comprehensive logging to `RobloxMultiLog.txt` for all actions and errors
- **Token Processing**: Enhanced token loading to automatically skip blank lines and filter invalid tokens

---

## [1.6.6-alpha] - 2025-07-29

### 🔄 Changed
- **Token Priority**: Updated token prefix validation to prioritize `CAEaAhAB` over `_|-` tokens in `ToolStripBtnLoadTokens_Click` and `ToolStripBtnGetAccounts_Click`
- **API Integration**: Maintained robust Roblox API integration using `https://users.roblox.com/v1/users/authenticated` for token-based authentication

### 🐛 Fixed
- **Token Processing**: Ensured exclusive `CAEaAhAB` token processing, significantly reducing invalid API calls and HTTP Unauthorized errors
- **Error Reduction**: Retained all fixes from v1.6.5-alpha for X-CSRF-Token handling, session verification, and concurrent token processing

### 🚀 Improvements
- **Performance**: Enhanced token filtering for improved performance and reduced error rates during loading and validation
- **Concurrency**: Maintained support for up to 10 concurrent token operations with `SemaphoreSlim`

---

## [1.6.5-alpha] - 2025-07-29

### ✨ Added
- **Enhanced Authentication**: Implemented robust token-based authentication using `.ROBLOSECURITY` tokens with `https://users.roblox.com/v1/users/authenticated`
- **CSRF Handling**: Added comprehensive X-CSRF-Token handling for 403 Forbidden errors via `https://auth.roblox.com/v1/authentication-ticket`
- **Session Verification**: Implemented post-login session verification through `VerifySessionAsync`
- **Concurrent Processing**: Added support for multiple token registration with `_|-` token filtering (up to 10 concurrent operations)

### 🐛 Fixed
- **Authentication Errors**: Resolved HTTP Unauthorized errors with detailed error logging and comprehensive token format validation
- **Process Security**: Ensured proper token escaping in process arguments for security
- **Thread Safety**: Maintained fixes for `InvokeRequired`/`Invoke` operations and `List<T>` errors from v1.6.4-alpha

### 🚀 Improvements
- **Error Handling**: Enhanced error handling in `FetchAccountInfoAsync` with complete HTTP response content logging
- **Session Management**: Improved `ToolStripBtnLogin_Click` to verify sessions after launching Roblox instances
- **Token Validation**: Implemented early invalid token filtering to reduce API errors
- **Performance**: Maintained efficient concurrent token processing with `SemaphoreSlim`

---

## [1.6.4-alpha] - 2025-07-29

### 🐛 Critical Fixes
- **Thread Safety**: Resolved thread-safe UI update errors in `UpdateStatus` by implementing proper `Form.InvokeRequired` and `Invoke` patterns
- **Type Safety**: Corrected generic type errors by explicitly specifying `List<string>` for `invalidTokens` and `List<Task<...>>` for task collections
- **Compilation**: Fixed compilation error in `Form1.designer.cs` by removing invalid syntax (`new Form1` / `InitializeComponent`)
- **Namespace**: Corrected namespace inconsistencies to `Multiplerblx` throughout the project
- **Dependencies**: Added `using System.Windows.Forms;` in `Program.cs` to resolve `ApplicationConfiguration` errors

### 🚀 Improvements
- **Concurrency**: Enhanced token loading and validation with `SemaphoreSlim` supporting 10 concurrent token operations
- **Error Logging**: Added detailed error logging in `FetchAccountInfoAsync` for HTTP Unauthorized error diagnosis
- **Token Processing**: Improved token processing with automatic whitespace trimming
- **Theme Support**: Extended theme support to `lstAccounts`, `txtTokens`, `txtGameId`, and `txtRobloxPath` controls
- **Security**: Maintained administrator privilege support via `app.manifest` configuration

---

*For versions 1.6.3-alpha and earlier, see [Legacy Changelog](CHANGELOG_LEGACY.md)*

---

## Version Information

- **Alpha releases** are development versions with potential breaking changes
- **Beta releases** are feature-complete versions undergoing testing  
- **Stable releases** are production-ready versions
