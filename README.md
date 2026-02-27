# WSL Manager for VS Code

Manage your Windows Subsystem for Linux distributions directly from the VS Code sidebar.

## Features

### Sidebar View

Click the WSL icon in the Activity Bar to see all installed distributions with their name (★ for default), state (Running / Stopped), and WSL version (1 / 2).

### Lifecycle

| Action | Description |
|--------|-------------|
| **Start** | Start a distribution |
| **Stop** | Stop a distribution |
| **Shutdown All** | Stop all running WSL instances |

### Distribution Management

| Action | Description |
|--------|-------------|
| **Install** | Install a new distribution from the online catalog with a custom instance name |
| **Remove** | Unregister a distribution (with double confirmation) |
| **Set as Default** | Change the default distribution |
| **Convert WSL Version** | Switch between WSL 1 and WSL 2 |

### Backup & Restore

| Action | Description |
|--------|-------------|
| **Export** | Export to tar or VHD format |
| **Import** | Import from a tar or VHD file |

### Development

| Action | Description |
|--------|-------------|
| **Open Terminal** | Launch the distribution in the VS Code integrated terminal |
| **Open in VS Code (WSL)** | Connect via WSL remote |
| **Edit .wslconfig** | Edit global WSL settings |
| **Edit wsl.conf** | Edit per-distribution settings |

## Usage

### From the Sidebar

1. Click the WSL icon in the Activity Bar
2. Right-click a distribution to open the context menu

### From the Command Palette

`Ctrl+Shift+P` → type `WSL Manager:` and select an action.

### Inline Actions

Hover over a distribution to reveal quick-action buttons for terminal and start/stop.

## License

MIT
