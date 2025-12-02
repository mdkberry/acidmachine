# Acid Machine

A fork of the original web-based music sequencer that became [Acid Machine](https://errozero.co.uk/acid-machine/). This fork aims to add MIDI export functionality for use with DAWs like Reaper.

![Acid Machine - Original First Run Screenshot](dev/screenshots/original-first-run-1.png)

## Features

- Web-based music sequencer
- 303 bass and drum patterns
- Interactive grid interface
- Planned MIDI export functionality

## Installation on Windows for VSCode

### Prerequisites

- [Git](https://git-scm.com/)
- [Visual Studio Code](https://code.visualstudio.com/)
- [PHP](https://www.php.net/downloads.php) (Thread Safe version, 8.2.x or 8.3.x recommended)

### Step 1: Clone the Repository

```bash
# Open Command Prompt
cd C:\Users\[YourUsername]\Documents\Projects

# Create projects folder if needed
mkdir Projects

# Clone the repository
git clone https://github.com/mdkberry/acidmachine.git

# Navigate to the project
cd acidmachine
```

### Step 2: Setup in VSCode

1. Launch VSCode
2. File → Open Folder → Select the `acidmachine` folder
3. Install required extensions:
   - **PHP Server** (by brapifra) - for running the local server
   - **PHP Intelephense** (by Ben Mewburn) - for syntax highlighting and linting (optional)

### Step 3: PHP Configuration

1. **Download PHP**:
   - Visit [php.net/downloads/windows](https://www.php.net/downloads.php)
   - Download the "VS16 x64 Thread Safe" ZIP version

2. **Extract PHP**:
   ```bash
   # Extract to a simple location
   C:\php\
   ```

3. **Verify Installation**:
   ```bash
   C:\php\php.exe --version
   # Should output something like "PHP 8.3.12"
   ```

4. **Add PHP to System PATH**:
   - Right-click "This PC" → Properties → Advanced system settings
   - Click "Environment Variables"
   - Under "System variables", find "Path" → Edit
   - Click "New" → Add `C:\php`
   - Click "OK" to save all changes
   - Restart VSCode and Command Prompt

5. **Test PATH**:
   ```bash
   php --version
   # Should work without specifying full path
   ```

### Step 4: Configure VSCode Settings

1. Open VSCode Settings: `Ctrl+,`
2. Search for "php executable path" or "phpserver.phpPath"
3. Edit `settings.json` and add:

```json
{
  "php.validate.executablePath": "C:\\php\\php.exe",
  "phpserver.phpPath": "C:\\php\\php.exe"
}
```

4. Save the file (`Ctrl+S`)
5. Reload VSCode window: `Ctrl+Shift+P` → "Developer: Reload Window"

### Step 5: Run the Application

1. In VSCode, right-click `index.php` → "PHP Server: Serve project"
2. Status bar should show: `http://localhost:3000`
3. Click the link to open in your browser
4. The Acid Machine interface should load with synth controls and drum pads
5. Test functionality:
   - Click "Play" to loop 303 bass + drums
   - Toggle pads for live grid plotting

### Troubleshooting

#### Check Output Logs
- Open Output panel: `Ctrl+Shift+U`
- Select "PHP Server" or "PHP Language Server" from dropdown
- Look for error messages

#### Reload Server
If issues persist:
- `Ctrl+Shift+P` → "PHP Server: Reload server"

#### Common Issues

- **Wrong PHP version**: Ensure you're using Thread Safe (TS) version for Windows
- **Antivirus/Firewall**: Allow `php.exe` if blocked
- **Project-specific settings**: Add the JSON configuration to `.vscode/settings.json` in your project root

#### Fallback Method
If the extension fails, use the terminal method:
```bash
# In VSCode terminal
php -S localhost:8000

# Open browser to:
# http://localhost:8000/index.php
```

## Contributing

This project is in active development with plans to add MIDI export functionality.

## License

This project is a fork of the original [Acid Machine](https://errozero.co.uk/acid-machine/) and inherits its MIT License terms.

The MIT License allows free use, modification, and distribution of the software. For the full license text, see the [LICENSE](LICENSE) file.

**Original Author**: errozero (2015)


