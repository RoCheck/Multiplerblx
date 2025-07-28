## [1.3.0] - 2025-07-28

### Added
- Complete GUI redesign with a modern, clean look featuring:  
  - Vertical sidebar navigation with icons and tooltips.  
  - Responsive layout with enhanced spacing and padding.  
  - Dark and light themes fully integrated with toggle support.  
- RichTextBox-based log output: color-coded, scrollable, and more readable logs.  
- Owner-drawn account ListView with alternating row colors and per-status color highlighting (Active, Banned, Error, Idle).  
- Context menu for accounts list: Copy Username, Copy Token, Copy All.  
- Double-click an account to view detailed account info popup (Username, UserID, Token, Status).  
- Editable and persistent Roblox executable path setting.  
- Basic animated tab transitions with slide effects to replace opacity glitches.  
- Improved and more robust event handling to prevent handler stacking on theme toggles.  
- Background timers for changelog fetching, instance monitoring, and server hopping with safer thread invocation.

### Changed
- Sidebar navigation now docks left instead of horizontal top; buttons redesigned for clarity and usability.  
- Status bar moved to bottom and redesigned with gradient background and improved status message coloring.  
- Logging mechanics improved with asynchronous safe UI updates and file output.  
- Server hop logic refined to kill and restart Roblox processes cleanly every 20 minutes.  
- Code restructured for better maintainability, error handling, and clarity.

### Fixed
- Resolved compilation errors related to invalid placeholder use in code (`...`).  
- Fixed missing event handler methods causing runtime errors on ListView double-click.  
- Removed illegal or missing references to `Properties.Settings` by removing or substituting setting persistence with manual editing.  
- Prevented flickering and redraw bugs during theme switching and redraws.  
- Corrected owner-draw drawing logic and ensured list row highlights and colors are consistent in both themes.

## [1.2.0] - 2025-07-27
### Added
- Slide animation for tab transitions, replacing the faulty opacity animation.
- Comprehensive error handling for file operations and HTTP requests.

### Changed
- Removed `System.Management` dependency to avoid NuGet issues; now uses RAM-only instance calculations.
- Fixed compilation errors in `Form1.cs` (syntax, event handlers, resource management).
- Updated changelog URL to reference GitHub repository.

### Fixed
- Resolved `userId` variable conflict in `GetAccountInfoAsync`.
- Corrected invalid `TabPage.Opacity` usage.
- Fixed faulty `ControlExtensions` and `this` in static context errors.

## [1.1.0] - 2025-06-15
### Added
- Ban detection for Roblox accounts via API checks.
- Server hopping feature with a 20-minute timer.
- GUI revamp with dark theme and animated buttons.
- Token export functionality to save account details.
- Account status refresh button to check for bans.

## [1.0.0] - 2025-05-01
### Added
- Initial implementation of Multiplerblx.
- Token loading from text files.
- Account fetching using Roblox API with .ROBLOSECURITY tokens.
- Basic Roblox instance launching with token authentication.
- Logging system for actions and errors.
