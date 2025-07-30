## Recovered ChangeLogs

## [1.6.3-alpha] - 2025-05-15

### ✨ Added
- **Token Export**: Added functionality to export valid tokens to a text file via a SaveFileDialog.
- **Basic Theme Support**: Introduced initial dark theme with neon purple accents for better visual appeal.
- **Account Status**: Added status tracking for accounts ("Idle", "Active", "Invalid Token") in the ListView.

### 🔄 Changed
- **Token Loading**: Improved token loading to support up to 10 tokens with basic validation for `.ROBLOSECURITY` format.
- **UI Layout**: Adjusted ListView columns to display username, user ID, token preview, and status.
- **Error Logging**: Enhanced logging to include more detailed error messages for failed operations.

### 🐛 Fixed
- **File Reading Errors**: Fixed crashes when reading invalid or empty token files.
- **UI Freezing**: Added basic thread safety for UI updates during token loading.
- **Token Parsing**: Corrected issues with token parsing to handle whitespace and invalid characters.

## [1.6.2-alpha] - 2025-04-30

### ✨ Added
- **Follow User Functionality**: Implemented ability to follow a target username using the Roblox API.
- **Message Sending**: Added basic message sending functionality for accounts via the Roblox chat API.
- **Changelog Tab**: Introduced a tab to display changelog fetched from a GitHub URL.

### 🔄 Changed
- **HTTP Client Setup**: Configured `HttpClient` with a custom `User-Agent` to mimic Roblox client requests.
- **Token Input**: Improved token input handling to strip whitespace and validate token format.
- **UI Feedback**: Added status label updates for user actions like loading tokens and launching games.

### 🐛 Fixed
- **API Authentication**: Fixed issues with `.ROBLOSECURITY` cookie handling for API requests.
- **Null Reference Errors**: Resolved null reference exceptions in account fetching when API responses were empty.
- **Log File Writing**: Fixed file access conflicts when writing to `RobloxMultiLog.txt`.

## [1.6.1-alpha] - 2025-04-15

### ✨ Added
- **Multi-Account Support**: Added ability to manage multiple Roblox accounts using `.ROBLOSECURITY` tokens.
- **Account Fetching**: Implemented fetching of account details (username, user ID) using the Roblox API.
- **Game Launching**: Added functionality to launch Roblox instances with specified game IDs and tokens.

### 🔄 Changed
- **UI Structure**: Introduced a tabbed interface with Accounts, Changelog, and Settings tabs.
- **Token Storage**: Stored tokens in memory within a `List<Account>` for easier management.
- **Logging**: Added basic logging to a file (`RobloxMultiLog.txt`) for debugging.

### 🐛 Fixed
- **Crash on Invalid Tokens**: Added validation to prevent crashes when invalid tokens are provided.
- **UI Initialization**: Fixed issues with control initialization in the Windows Forms designer.
- **API Response Handling**: Improved handling of unexpected API response formats.

## [1.6.0-alpha] - 2025-03-31

### ✨ Added
- **Initial UI**: Created a basic Windows Forms UI with a ListView for account display and TextBox for token input.
- **Token Loading**: Added functionality to load `.ROBLOSECURITY` tokens from a text file via OpenFileDialog.
- **Basic Account Management**: Implemented basic account switching by updating the active token.

### 🔄 Changed
- **Project Setup**: Initialized the project with C# and Windows Forms, targeting .NET Framework.
- **API Integration**: Added initial Roblox API integration for user info retrieval using `.ROBLOSECURITY` cookies.

### 🐛 Fixed
- **File Dialog Errors**: Fixed crashes when no file was selected in the OpenFileDialog.
- **Initial Build Issues**: Resolved compilation errors related to missing references and namespaces.

## [1.5.0-alpha] - 2025-03-15

### ✨ Added
- **Project Initialization**: Created the initial project structure for Multiplerbx, a Roblox multi-account management tool.
- **Basic HTTP Requests**: Implemented basic HTTP requests to the Roblox API for testing authentication.
- **Core Dependencies**: Added dependencies for `System.Net.Http` and `System.Text.Json` for API communication.

### 🔄 Changed
- **Development Environment**: Set up the development environment with Visual Studio and .NET Framework 4.8.
- **Initial Configuration**: Configured basic project settings and file structure.

### 🐛 Fixed
- **Initial Setup Bugs**: Fixed issues with project configuration and missing NuGet packages.
