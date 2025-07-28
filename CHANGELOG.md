All notable changes to the Multiplerblx project will be documented in this file.

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
