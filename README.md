# Auto Fire - Auto Key Presser

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![GitHub issues](https://img.shields.io/github/issues/sinha-19/Auto-Fire)](https://github.com/sinha-19/Auto-Fire/issues)
[![GitHub last commit](https://img.shields.io/github/last-commit/sinha-19/Auto-Fire)](https://github.com/sinha-19/Auto-Fire/commits/main)

![autofire](https://github.com/user-attachments/assets/5130e29f-392d-4e2a-a56d-571094203bd8)

Enable autofire for any key. Press once, then leave your computer running—Auto Fire handles the rest.

## Description

**Auto Fire** is a powerful automation tool that enables continuous key pressing without manual intervention. Simply enable the script, press your desired key once, and the tool will automatically repeat that key press at configurable intervals. Perfect for tasks requiring repetitive key presses while you're away from your computer.

Whether you're automating game mechanics, completing repetitive data entry tasks, or running extended simulations, Auto Fire provides a reliable, lightweight solution with minimal dependencies and maximum control.

## Features

- **One-Key Activation**: Press any key once to start auto-pressing
- **Configurable Intervals**: Adjust key press frequency from milliseconds to seconds
- **Instant Shutdown**: Stop with a secure key combination (Ctrl+Esc+W)
- **Robust Fallback**: Automatic CLI mode if keyboard listener fails
- **Lightweight**: Minimal resource usage with no heavy dependencies
- **Dual Library Support**: Works with both `keyboard` and `pynput` libraries
- **Cross-Platform**: Runs on Windows, Linux, and macOS

## Use Cases

- **Gaming**: Automate repetitive key presses in games (farming, mining, AFK tasks)
- **Data Entry**: Speed up repetitive form filling and data processing
- **Testing**: Automate keyboard input for testing purposes
- **Simulations**: Run long-duration simulations with constant input
- **Accessibility**: Reduce repetitive strain for users with mobility constraints
- **Automation**: Execute keyboard-dependent automation workflows

## Requirements

- Python 3.6 or higher
- One of the following libraries:
  - `keyboard` (preferred)
  - `pynput` (fallback)

## Installation

### Prerequisites
- Python 3.6 or higher installed on your system
- Administrator/root privileges (required for global keyboard access)

### Steps

1. Clone the repository:
```bash
git clone https://github.com/sinha-19/Auto-Fire.git
cd Auto-Fire
```

2. Install required dependencies:
```bash
pip install -r requirements.txt
```

3. (Optional) Create a virtual environment for isolation:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

## Usage

### Quick Start

1. Run with administrator privileges:
```bash
# Linux/macOS
sudo python rapid_fire.py

# Windows (run terminal as Administrator first)
python rapid_fire.py
```

2. **Start auto-pressing**: Press any key to begin auto-pressing that key
   - The key will repeat every 1 second by default
   - Works with any keyboard key or key combination

3. **Stop auto-pressing**: Press **Ctrl+Esc+W** simultaneously
   - Instant shutdown of auto-pressing functionality
   - Can be customized (see Advanced Configuration)

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

### Example Scenarios

**Scenario 1: Gaming - AFK Farming**
- Start the script with sudo/admin
- In your game, position character in a safe location
- Press spacebar to initiate auto-firing
- Your character will jump repeatedly at 1-second intervals
- Press Ctrl+Esc+W to stop when done

**Scenario 2: Data Entry - Repetitive Form Submission**
- Run the script
- Position cursor in the form input field
- Press Tab or Enter to auto-submit forms
- Adjust interval to 0.5 seconds for faster submission
- Stop with Ctrl+Esc+W when complete

**Scenario 3: CLI Mode Usage**
```bash
python rapid_fire.py
# If keyboard listener fails, you'll get CLI prompt
start space
# spacebar now auto-pressing
interval 0.5
# change to 0.5 second intervals
stop
# stop auto-pressing
exit
# exit program
```

## Advanced Configuration

### Customizing Press Intervals

Edit `rapid_fire.py` to modify the default press interval:

```python
# In the main block, adjust the interval parameter (in seconds)
rapid_fire = RapidFire(interval=0.5)  # Default: 1.0 second
# 0.1 = 10 times per second (gaming)
# 0.5 = 2 times per second (moderate)
# 1.0 = once per second (default, slower)
# 2.0 = once every 2 seconds (very slow)
```

### Customizing Stop Key Combination

#### For `keyboard` library:
```python
# Change the stop combination in the script
self.stop_combo = "ctrl+esc+w"  # Current setting
# Examples of alternatives:
# self.stop_combo = "ctrl+shift+x"
# self.stop_combo = "esc+esc"
# self.stop_combo = "alt+f4"
```

#### For `pynput` library:
```python
from pynput.keyboard import Key, KeyCode

# Modify the stop_keys set
self.stop_keys = {Key.ctrl_l, Key.esc, KeyCode.from_char('w')}
# Examples:
# self.stop_keys = {Key.ctrl_l, Key.shift_l, KeyCode.from_char('x')}
# self.stop_keys = {Key.esc, Key.esc}  # Double escape
```

### Performance Tuning

For optimal performance:
- **Gaming**: Use 0.1-0.2 second intervals
- **Data Entry**: Use 0.5-1.0 second intervals
- **Simulations**: Use 1.0-2.0 second intervals
- Experiment with values that work best for your use case

## Important Notes

### Permissions & Privileges

This utility requires elevated privileges due to system-level keyboard access:

- **Linux**: Run with `sudo` privilege
  ```bash
  sudo python rapid_fire.py
  ```

- **Windows**: Launch terminal as Administrator before running the script

- **macOS**: Grant Accessibility permissions in System Preferences
  ```bash
  sudo python rapid_fire.py
  ```

### Safety & Responsible Use

- **Always Know Your Exit**: Memorize your stop key combination (default: Ctrl+Esc+W)
- **Testing First**: Test in a safe environment before automation
- **Terms of Service**: Verify that automation complies with your target application's terms of service
- **Game Policy**: Some games may prohibit automation tools—use at your own risk
- **Monitoring**: Don't leave automation running unattended for extended periods
- **Emergency Stop**: You can always press Ctrl+C in the terminal to forcefully exit

## Troubleshooting

### Keyboard Listener Fails

**Problem**: "Keyboard listener failed. Switching to command-line interface mode"

**Solution**: This is normal on some systems, especially Linux. The program automatically falls back to CLI mode with full functionality.

**What to do**:
- The CLI mode works just as well as keyboard listener mode
- Use commands like `start space` and `stop` as described in Fallback CLI Mode section
- No action needed—the script handles this automatically

### Permission Denied Errors

**Problem**: Permission denied when running the script

**Solution**:
- **Linux/macOS**: Run with `sudo`
  ```bash
  sudo python rapid_fire.py
  ```
- **Windows**: Right-click terminal and select "Run as Administrator"
- **Alternative**: Grant specific permissions to your user (advanced)

### Library Import Errors

**Problem**: ImportError for `keyboard` or `pynput`

**Solution**: Install both libraries explicitly:
```bash
pip install keyboard pynput
```

**If that fails**:
```bash
pip install --upgrade keyboard pynput
# Or try with user flag
pip install --user keyboard pynput
```

### Keys Not Being Detected

**Problem**: Pressed keys aren't being registered

**Possible Causes & Solutions**:
1. Terminal doesn't have keyboard focus—click on the terminal window
2. Running without proper permissions—use `sudo` (Linux/macOS)
3. Virtual machine limitations—some VMs restrict keyboard access
4. Try switching to CLI mode if keyboard listener fails

### Script Freezes or Hangs

**Problem**: Program becomes unresponsive

**Solution**:
- Press your stop key combination (default: Ctrl+Esc+W)
- If that doesn't work, press Ctrl+C in the terminal
- Check terminal output for error messages

### Auto-Pressing Won't Stop

**Problem**: Ctrl+Esc+W doesn't stop the auto-pressing

**Solutions**:
1. Try pressing the keys separately with slight delays
2. Try Ctrl+C in the terminal window
3. Close the terminal window entirely
4. Use Task Manager (Windows) or Activity Monitor (macOS) to force-close Python

## Frequently Asked Questions

**Q: Is this tool safe to use?**
A: Yes, when used responsibly. It's a simple key press automation tool. Always be aware of your stop key combination and test in safe environments first.

**Q: Will this get me banned from games?**
A: That depends on the game's terms of service. Some games explicitly prohibit automation tools. Use at your own risk and only on games where automation is permitted.

**Q: What's the minimum interval I can use?**
A: You can go as low as 0.01 seconds (100 times per second), but keyboard hardware limitations typically cap out around 50-100 presses per second.

**Q: Does this work on Linux?**
A: Yes! Linux is fully supported. You'll need to run with `sudo` for global keyboard access.

**Q: Can I use this on macOS?**
A: Yes! macOS is supported. Grant Accessibility permissions when prompted, and run with `sudo` if needed.

**Q: Can this tool capture passwords or sensitive data?**
A: No. This tool only simulates key presses—it doesn't read or capture keyboard input from other applications.

**Q: What if I forget my stop key combination?**
A: You can always press Ctrl+C in the terminal to force exit the program.

**Q: Can I run multiple instances?**
A: Yes, but it's not recommended as they may interfere with each other. Test first.

## Technical Details

### How It Works

1. **Keyboard Listener Mode** (primary):
   - Monitors global keyboard input using the `keyboard` library
   - Listens for any key press to start auto-pressing
   - Monitors for the stop key combination to halt auto-pressing
   - Repeats the target key at specified intervals

2. **CLI Mode** (fallback):
   - Automatically activated if keyboard listener initialization fails
   - Provides command-line interface for manual control
   - Same functionality as keyboard listener mode

### System Requirements

- **OS**: Windows 10+, Linux (any distribution), macOS 10.12+
- **Python**: 3.6 or higher
- **Permissions**: Administrator/root access required
- **Dependencies**: keyboard or pynput library

### Architecture

The tool uses a simple threading model:
- Main thread listens for keyboard input
- Worker thread handles key pressing at specified intervals
- Stop signal from keyboard listener terminates the worker thread

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
