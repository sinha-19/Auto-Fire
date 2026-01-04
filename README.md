# Auto Fire - Auto Key Presser

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![GitHub issues](https://img.shields.io/github/issues/sinha-19/Auto-Fire)](https://github.com/sinha-19/Auto-Fire/issues)
[![GitHub last commit](https://img.shields.io/github/last-commit/sinha-19/Auto-Fire)](https://github.com/sinha-19/Auto-Fire/commits/main)

![autofire](https://github.com/user-attachments/assets/5130e29f-392d-4e2a-a56d-571094203bd8)

A lightweight utility for automatically pressing keys at regular intervals.

## Description

Auto Fire is a simple auto key-press utility that simulates continuous key presses after you've pressed a key once. It's useful for scenarios where repeated key presses are needed, such as in games, form filling, or text repetition.

## Features

- ⌨️ Start auto-pressing by pressing any key once
- ⏱️ Continuous pressing at 1-second intervals (configurable)
- 🛑 Stop immediately with a key combination (Ctrl+Esc+W)
- 🔄 Automatic fallback to CLI mode if keyboard listener fails
- 🪶 Lightweight with minimal dependencies
- 🐍 Works with both `keyboard` and `pynput` libraries

## Requirements

- Python 3.6 or higher
- One of the following libraries:
  - `keyboard` (preferred)
  - `pynput` (fallback)

## Installation

1. Clone the repository:
```bash
git clone https://github.com/sinha-19/Auto-Fire.git
cd Auto-Fire
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

## Usage

### Basic Usage

1. Run the script:
```bash
python rapid_fire.py
```

2. Press any key to begin auto-pressing that key every second

3. Press **Ctrl+Esc+W** to stop the auto-pressing functionality

### Fallback CLI Mode

If the keyboard listener fails to initialize (common on some Linux systems), the program automatically switches to Command-Line Interface (CLI) mode.

Available commands in CLI mode:

- `start <key>` - Start auto-pressing a key
  - Example: `start a` or `start space`
- `stop` - Stop current auto-pressing
- `interval <seconds>` - Change the press interval
  - Example: `interval 0.5`
- `exit` or `quit` - Exit the program

### Special Keys

For special keys in CLI mode, use these keywords:

| Keyword | Key |
|---------|-----|
| `space` | Space bar |
| `enter` | Enter/Return key |
| `tab` | Tab key |
| `esc` or `escape` | Escape key |
| `ctrl` | Control key |
| `alt` | Alt key |
| `shift` | Shift key |

For regular character keys, just type the character (e.g., `a`, `b`, `1`, `2`).

## Advanced Configuration

You can modify the `rapid_fire.py` script to customize:

### Change Press Interval

Modify the initialization in the main block:
```python
rapid_fire = RapidFire(interval=0.5)  # Change to desired interval in seconds
```

### Change Stop Key Combination

For the `keyboard` library, modify:
```python
self.stop_combo = "ctrl+esc+w"  # Change to your preferred combination
```

For the `pynput` library, modify:
```python
self.stop_keys = {Key.ctrl_l, Key.esc, KeyCode.from_char('w')}  # Change keys as needed
```

## Important Notes

- **Permissions**: This utility requires root/administrator privileges on most systems due to global keyboard access requirements
  - Linux: Run with `sudo python rapid_fire.py`
  - Windows: Run terminal as Administrator
  - macOS: Grant Accessibility permissions when prompted

- **Safety**: Use responsibly and ensure you know how to stop the auto-pressing (Ctrl+Esc+W or Ctrl+C in terminal)

## Troubleshooting

### Keyboard Listener Fails

If you see "Keyboard listener failed. Switching to command-line interface mode", the program will automatically switch to CLI mode. This is normal on some Linux systems and the CLI mode provides full functionality.

### Permission Errors

If you encounter permission errors:
- **Linux**: Run with `sudo`
- **Windows**: Run terminal as Administrator
- **macOS**: Grant Accessibility permissions in System Preferences

### Library Import Errors

If both `keyboard` and `pynput` fail to import, install them manually:
```bash
pip install keyboard pynput
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MPL-2.0 license - see the [LICENSE](LICENSE) file for details.

## Author

**Saket Kumar Sinha**
- GitHub: [@sinha-19](https://github.com/sinha-19)
- Repository: [Auto Fire](https://github.com/sinha-19/Auto-Fire)

## Acknowledgments

- Built with [keyboard](https://github.com/boppreh/keyboard) library (primary)
- Fallback support with [pynput](https://github.com/moses-palmer/pynput) library

---

⚠️ **Disclaimer**: Use this tool responsibly. Automated key pressing may violate terms of service for certain applications or games. Always ensure you have permission to use automation tools in your specific use case.
