# Space Channel 5 Part 2 Access Mod

A screen reader accessibility mod for the Steam version of Space Channel 5 Part 2. It works with both NVDA and JAWS natively, and falls back to the Windows voice if neither is running. Download the zip from the [latest release](../../releases/latest), unzip it, and run install.bat from inside the unzipped folder. The installer also creates a desktop shortcut called 'Space Channel 5 Part 2 No Launcher' that opens the game directly, skipping Steam's launcher, which screen readers can't read.

```
Space Channel 5 Part 2 Access Mod 1.0.5
=======================================

A screen reader accessibility mod for Space Channel 5 Part 2 (Steam, PC).
It speaks the menus, captions, prompts and results the game shows, adds
audio cues for things sighted players see, and remaps Xbox controller buttons.
It changes no game files on disk; it is a winmm.dll (plus NVDA's controller
client DLL) placed next to the game.

Requirements
- Space Channel 5 Part 2, Steam version (Windows).
- Speech: JAWS and NVDA are both supported natively. If JAWS is running, the
  mod speaks through JAWS (its COM interface). Otherwise, if NVDA is running, it
  speaks through NVDA (nvdaControllerClient.dll, included). Otherwise it uses
  the Windows SAPI voice. If nvdaControllerClient.dll is missing, the mod still
  works and uses JAWS or the Windows voice.
  To force one, set speech_backend in SC5_config.ini to jaws, nvda or sapi.
- An Xbox-style controller or DualShock 4 is recommended. Keyboard works too.

Install
- Easy way: run install.bat. It finds the game in the default Steam folders.
  If it can't, drag the game folder onto install.bat, or run:
    install.bat "C:\path\to\Space Channel 5 Part 2"
  Any existing winmm.dll in the game folder is backed up as winmm.dll.bak.
- Manual way: copy winmm.dll, nvdaControllerClient.dll and SC5_config.ini into the folder that has
  "Space Channel 5 Part 2.exe".

Starting without the Steam launcher
- When you press Play in Steam, the game first opens a launcher. That launcher
  is a graphics window that screen readers can't read.
- install.bat makes a desktop shortcut called
  "Space Channel 5 Part 2 No Launcher" that opens the game directly. It also
  puts a file called steam_appid.txt (containing 71260) in the game folder,
  which stops the game from restarting itself through Steam.
- Steam must be running when you use the shortcut.
- Starting the game from the Steam library (Play) still opens the launcher.
- The launcher is skipped from then on, so if you want to change its graphics
  options, do that first (with sighted help if needed).
- To do it by hand: in the game folder, create a plain text file named
  steam_appid.txt that contains only 71260 (make sure Windows does not name it
  steam_appid.txt.txt). Then make a shortcut to "Space Channel 5 Part 2.exe"
  in the game folder, for example on your desktop, and start the game with it.
- uninstall.bat removes the shortcut, and removes steam_appid.txt if it still
  contains only 71260.

Uninstall
- Run uninstall.bat (same folder options as install). It removes winmm.dll,
  nvdaControllerClient.dll and SC5_config.ini and restores winmm.dll.bak if there was one.
- Or delete winmm.dll, nvdaControllerClient.dll and SC5_config.ini from the game folder.

Keys (only while the game window is in front)
  F1   Help: lists the mod keys and whether each one is on or off.
  F11  Status: hearts, ratings and secret notes so far (in Ulala's Dance: the round).
       Clicking the left stick (L3) does the same.
  F2   Speech on/off (everything the mod says; F1 and the toggle keys still talk).
  F3   Captions on/off (story and on-screen text).
  F4   Menu and title reading on/off.
  F5   Results and game over reading on/off.
  F6   Secret note beep on/off.
  F7   Missed secret sound on/off.
  F8   Robot pose and odd-one-out callouts on/off (Report 5).
  F9   Credits reading on/off.
  F10  Logging on/off for bug reports (says "Logging on" / "Logging off").
       Off by default. The log file is created only when logging is on.
  Each toggle says its new state and is saved to SC5_config.ini.
  F-keys are ignored while Alt, Ctrl, Shift or Windows is held. F10 is not passed
  to the game (it would otherwise open the window menu).
  Ctrl+Shift+T speech test, Ctrl+Shift+R repeat the last caption.
  Game keys: arrows move, S = Chu (choose), D = Hey (back), Enter/Start = start/pause.

Controller
- Xbox pads: A = Chu (choose), B = Hey (back). The D-pad works as the stick.
  Change or turn this off in SC5_config.ini, [controller] section.

What is announced
- Title screen ("Press Start"), title and Play menus, Help and options, Save/Load,
  play environment settings with their values.
- Credits (ending and Help and options > Credits): each line is read once, in
  scroll order, as it appears at the bottom of the screen; lines in the same
  group are read together and queued, so speech is not cut off.
- Report 6 final stage: the staff credits that scroll up during the last song
  are pictures; the mod reads each line once as it comes fully into view, queued.
  English credits only. F9 turns all credits reading on and off.
- Report select: report name, best rating, Perfect, times played and time; locked reports.
- Story captions, tutorials, name cards, Yes/No prompts with the highlighted answer.
- Story cutscenes: "Press Start to skip." when a skippable cutscene starts.
- "Checkpoint" when you reach a new area in a report (pause > restart from
  checkpoint returns there).
- Pause menu and its prompts; game over menu.
- Results: ratings, people rescued, secret notes found and missed.
- Secret notes: a beep shortly before a hidden command moment, and a low buzz
  when one is missed (both can be turned off).
- Report 5: robot poses and the "hit the one that's legit" Shadows.
- Costume room (after reports and from Play > Change costume): row, number,
  name and description of each costume and item, owned or not, "Now wearing ...".
  Names and descriptions are read from your own game's coscap_e.bin file.

Known limits
- The costume room's finish step is read as "Finish changing? S confirm, D back."
  This wording is the mod's own; the exact on-screen wording is not confirmed.
- Report 6 ratings above 100% (for example 190%) are normal: hidden secrets in
  Report 6 push the rating past 100% in the game itself.
- Some menus with no confirmed names may say "item N of M".
- Speech is English only (English captions are used).

Bug reports
- Press F10 (you hear "Logging on"), or set log=1 under [debug] in SC5_config.ini,
  play until the problem happens, press F10 again ("Logging off"), and send
  SC5_log.txt from the game folder. Turning logging on again adds to the same file. The log records only game keys
  (arrows, Enter, Space, Escape, Tab, S, D) while the game has focus.

Changes in 1.0.5
- New: install.bat creates a desktop shortcut "Space Channel 5 Part 2 No
  Launcher" and the steam_appid.txt file, so the game opens without the Steam
  launcher. uninstall.bat removes them. No changes to the mod itself.

Changes in 1.0.4
- New: native NVDA speech. When NVDA is running (and JAWS is not), speech goes
  through NVDA instead of the Windows voice. Interrupting works the same way
  as with JAWS.

Changes in 1.0.3
- Fixed: the first page of the Report 6 staff credits (the voice cast) was not read.

Changes in 1.0.2
- New: the scrolling staff credits in Report 6's final stage are read.

Changes in 1.0.1
- Fixed: the credits repeated the line on screen over and over (for example
  "Original game developed by SEGA"). Each credit line is now read once.

License: MIT (see LICENSE). Not affiliated with SEGA. Contains no game files.

Third-party notice
- nvdaControllerClient.dll (32-bit) is the NVDA Controller Client from
  NV Access Limited, included unmodified from the NVDA 2026.2 controller client
  package. It is licensed under the GNU Lesser General Public License,
  version 2.1 (see NVDA_CONTROLLER_LICENSE.txt). Its source code is available
  from NV Access at https://github.com/nvaccess/nvda (nvdaHelper folder).
  You may replace it with any compatible version of the DLL.
  NVDA is a trademark of NV Access Limited. This mod is not affiliated with
  NV Access.
```
