# Change Log

## [0.17.1] - 2025-02-28

### Fixed
- README: corrected Edit wsl.conf description to reflect UNC path usage

## [0.17.0] - 2025-02-28

### Added
- Remove Multiple Distributions: bulk-remove with multi-select checkbox
- Available from the view title menu (...) and Command Palette
- Double confirmation: first modal warning with list, then type the count to confirm
- Progress notification showing removal of each distribution
- Partial failure handling: reports which removals succeeded and which failed

## [0.16.6] - 2025-02-28

### Fixed
- Edit wsl.conf: auto-add `wsl.localhost` to VS Code `security.allowedUNCHosts` setting before opening

## [0.16.5] - 2025-02-28

### Fixed
- Edit wsl.conf: switched from vscode-remote:// to UNC path (\\wsl.localhost\\) for reliable file opening without WSL extension dependency
- Auto-starts the distribution if stopped before opening wsl.conf
- Keeps warning + confirmation when creating a new wsl.conf

## [0.16.4] - 2025-02-28

### Fixed
- wsl.conf creation: warn user then create only on confirmation
- Fixed Windows cmd.exe quoting issues in all WSL shell commands
  - hasWslConf: use `test -f` (no quoting needed)
  - ensureWslConf: use `touch` directly
  - setDefaultUser: use `bash -c` with single quotes
  - setupUser/createUser: use `bash -c` with single quotes to avoid pipe interpretation by cmd.exe
  - Password single quotes properly escaped

## [0.16.3] - 2025-02-28

### Changed
- Edit wsl.conf now warns and asks for confirmation before creating the file when it does not exist

## [0.16.2] - 2025-02-28

### Fixed
- Edit wsl.conf now creates the file if it does not exist, fixing "Unable to resolve resource" error on distros without a pre-existing wsl.conf

## [0.16.1] - 2025-02-27

### Changed
- Clone wizard now includes user configuration step with three options:
  - Create new user: username + password, set as default login user
  - Set existing user as default: change the default login user to an existing account
  - Keep as-is: clone without modifying users
- Added setDefaultUser method that preserves existing wsl.conf content
- Added createUser method (user creation without overwriting wsl.conf)

## [0.16.0] - 2025-02-27

### Added
- Clone Distribution command: duplicate an existing distro under a new name
- Available from context menu (right-click) and Command Palette
- Clone preserves WSL version of the source distribution
- 2-step wizard: enter clone name → select install location

## [0.15.1] - 2025-02-27

### Changed
- Comprehensive README rewrite covering all features: install wizard, cache, cloud-init, cgroup management, settings

## [0.15.0] - 2025-02-27

### Added
- cloud-init support for compatible distributions during install
- Optional step to select a cloud-init user-data YAML file
- Simple validation (checks for #cloud-config header)
- Supported distros: AlmaLinux, Fedora, Ubuntu, Oracle Linux, openSUSE, SUSE, eLxr
- When cloud-init is used, user/password setup is delegated to cloud-init (no manual setupUser)
- user-data placed at %USERPROFILE%\.cloud-init\<instanceName>.user-data before first boot

## [0.14.0] - 2025-02-27

### Changed
- Distro selection now shows cached images at the top with a "Cached" separator
- Selecting a cached distro skips the cache/fresh choice (with stale warning if expired)
- Cache clear now uses multi-select for individual distro deletion

## [0.13.0] - 2025-02-27

### Added
- Distribution image cache system for faster repeated installs
- Cache enabled by default (`wslManager.cache.enabled`)
- Configurable cache expiry warning (`wslManager.cache.expiryDays`, default 30)
- Clear Distribution Cache command (clear all or per-distro)
- Cache indicator in distro selection list
- Stale cache warning when image exceeds expiry threshold

### Changed
- --name install path now exports to cache after install for future reuse
- Legacy install path saves exported tar to cache
- Cache-based install uses import + setupUser flow

## [0.11.0] - 2025-02-27

### Added
- Demo GIF in README for intuitive overview
- Toggle cgroup v1 entry in README features table

## [0.10.0] - 2025-02-27

### Fixed
- WSL version detection now normalizes non-ASCII characters before parsing
- Added --help fallback when version string parsing fails (encoding issues)

## [0.9.0] - 2025-02-27

### Changed
- WSL --name support detection now checks version >= 2.4.4 instead of parsing --help

## [0.8.0] - 2025-02-27

### Changed
- Native --name install now uses OOBE for user setup (2 steps + terminal)
- OOBE provides proper distro-specific initialization (sudo NOPASSWD, UID 1000, etc.)
- Legacy export/import path retains manual user creation (5 steps)

## [0.7.0] - 2025-02-27

### Added
- Auto-add `kernelCommandLine = cgroup_no_v1=all` to .wslconfig on install
- Toggle command to enable/disable cgroup_no_v1 setting (with optional WSL restart)
- Updated .wslconfig template to include cgroup_no_v1=all by default

## [0.6.0] - 2025-02-27

### Added
- Auto-detect WSL --name flag support and use native install when available
- Legacy export/import fallback for older WSL versions

### Changed
- Install wizard shows 4 steps (with --name) or 5 steps (legacy) depending on WSL version
- Install directory selection only shown in legacy mode
- Temporary distro hiding only applied in legacy mode

## [0.5.0] - 2025-02-27

### Fixed
- Edit wsl.conf now uses vscode-remote URI instead of UNC path to avoid security errors

## [0.4.0] - 2025-02-27

### Fixed
- Detail items (State, WSL Version) now show correct tooltip instead of "Unknown"

## [0.3.0] - 2025-02-27

### Changed
- Set Default no longer shows a notification popup
- Removed "Default Distribution" detail item from the tree view

## [0.2.0] - 2025-02-27

### Added
- Custom instance naming for installations (always required, online distro names are reserved)
- User creation wizard during install (username, password, sudo group)
- Hidden temporary distributions from sidebar during install

### Changed
- Terminal now opens in the user's home directory instead of the Windows mount path
- Terminals are automatically closed when stopping or removing a distribution
- Simplified install flow by removing complex backup/restore logic

## [0.1.0] - 2025-02-27

### Added
- Activity Bar view with WSL Manager sidebar
- Distribution list showing name, state, WSL version, and default indicator
- Start, stop, and shutdown all distributions
- Install new distributions from online catalog with custom instance names
- Remove distributions with double confirmation
- Set default distribution
- Convert between WSL 1 and WSL 2
- Export and import in tar / VHD format
- Open distribution in VS Code integrated terminal
- Open distribution via WSL remote connection
- Edit `.wslconfig` and `wsl.conf`
- State-aware context menus and inline actions
- Auto-refresh every 30 seconds
- Full Command Palette support
- Configurable settings (refresh interval, export format, confirmation dialogs)
