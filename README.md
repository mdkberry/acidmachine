# acidmachine

*I love the simplicity of the original this fork was based on - https://errozero.co.uk/acid-machine/  and wanted to make a version that I could use but be able to export as midi files to Reaper, so going to see if I can do that here.*

## Installation on Windows for VSCode use

1. Clone the Repo.
Open Command Prompt.
Navigate to your projects folder: cd C:\Users\[YourUsername]\Documents\Projects (create if needed: mkdir Projects).
Clone: git clone https://github.com/mdkberry/acidmachine.git
This creates an acidmachine folder.
cd into it: `cd acidmachine`.

2. Setup in VSCode
Launch VSCode > File > Open Folder > Select the acidmachine folder.
In VSCode: Ctrl+Shift+X (Extensions view).
Search: "PHP Server" (by brapifra).
Click Install (free, no restarts needed).
Optional: Also install "PHP Intelephense" (by Ben Mewburn. alt. Intelephense) for syntax highlighting/linting if you plan heavy edits.

3. PHP setup
Download the latest stable PHP for Windows (8.3.x or 8.2.x—Thread Safe version) from the official site: php.net/downloads/windows > Click "ZIP" under "VS16 x64 Thread Safe".
Extract the ZIP to a simple folder like C:\php. This keeps it clean—no installer required.
Verify: Open Command Prompt (Win+R > cmd) > Run `C:\php\php.exe --version`. Should output something like "PHP 8.3.12". If not, redownload.
Add PHP to Your System PATH (Global Fix):
This lets VSCode (and the extension) find PHP automatically.
Right-click This PC (or My Computer) on desktop/start menu > Properties > Advanced system settings (right sidebar).
Click Environment Variables (bottom).
Under "System variables" (bottom section), find Path > Select it > Edit.
Click New > Paste C:\php (your extract path) > OK all the way out.
Restart VSCode (close fully, reopen) and Command Prompt (for good measure).
Test: In new cmd, run `php --version` should work without full path.

3. Configure VSCode Settings (Extension-Specific Fix)
Even with PATH set, tell the PHP Server where PHP lives.
In VSCode: `Ctrl+,` (comma) to open Settings.
Search: "php executable path" or "phpserver.phpPath".
Under Extensions > PHP Server, find PHP Path (or PHP Executable Path) > Click "Edit in settings.json" (top right).
Add/update these lines in the JSON (replace with your path):JSON

```json
{
  "php.validate.executablePath": "C:\\php\\php.exe",
  "phpserver.phpPath": "C:\\php\\php.exe"
}
```
Save the file (Ctrl+S). If it grays out, that's fine, it's just deprecated but still works.
Reload VSCode window: Ctrl+Shift+P > "Developer: Reload Window".

4. Open in browser
Step 4: Test the Fix

Open your acidmachine folder in VSCode.
Left-click (or right-click) index.php > PHP Server: Serve project (should now appear without error).
Status bar shows http://localhost:3000 
click it. Browser loads the rendered Acid Machine (synth controls, drum pads, etc.).
If audio/JS works: Play button loops the 303 bass + drums. Toggle pads for live grid plotting.

5. If It Still Fails

Check Output Logs: Ctrl+Shift+U (Output panel) > Dropdown > "PHP Server" or "PHP Language Server". Look for clues (e.g., "php.exe not found")—paste here if needed.

Or try CTRL+SHIFT+P > "PHP Server: Reload server" (this sorted it when I had the index.php open in VSCode at same time it loaded it into the browser automatically so check notes about that in PHP Server brapifra setup for further approaches if you use that one.)

Common Gotchas:
Wrong PHP version: Use Thread Safe (TS) for Windows servers.
Antivirus/Firewall: Allow php.exe if blocked.
Workspace Settings: If project-specific, add the JSON to .vscode/settings.json in your repo root.

Fallback Launch: Terminal (Ctrl+) > php -S localhost:8000 in project root > Browser tohttp://localhost:8000/index.php`. (Bypasses extension.)

This should zap the notification—it's usually just PATH/executable config. Once fixed, you're golden for editing that PHP-generated grid. If logs show something else (e.g., "logger.php" missing from ), we can patch that too!



