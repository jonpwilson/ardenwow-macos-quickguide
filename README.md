# ardenwow-macos-quickguide

A quick guide on running ArdenWoW on MacOS. Huge thanks to B1G for his Linux guide which was helpful in pointing out which folders needed unzipping: https://github.com/Besevse/ardenwow-linux-quickguide

This guide is assuming you have WoWSilicon (https://wowsilicon.github.io/) installed (currently version 3.2.2) and have 7zip installed through your package manager of choice.

---

# Step 1: Getting the launcher working

Download the launcher from:
`https://downloads.ardenwow.com/launcher-download/ArdenWoW-Launcher-Setup.exe`

Running the installer directly through WoWSilicon gets stuck on a Powershell running stub, so we'll extract it manually instead.

1. Move `ArdenWoW-Launcher-Setup.exe` into its own directory, then extract it:

   ```
   7z x ArdenWoW-Launcher-Setup.exe
   ```

   You should see output similar to this:

   <img width="476" height="359" alt="Screenshot_20260928_194611" src="https://github.com/user-attachments/assets/eed302ae-45d9-467b-905a-45f3d53eb660" />

2. Extraction leaves you with two folders: `$R0` and `$PLUGINSDIR`. You can ignore `$R0`, since it only contains the uninstaller. `$PLUGINSDIR` is the one we need.

3. Bash tends to have trouble with directory names that start with `$`, so rename it and move into it:

   ```
   mv \$PLUGINSDIR PLUGINSDIR
   cd PLUGINSDIR
   ```

4. Inside `PLUGINSDIR` there's another archive, `app-64.7z`. Extract it too:

   ```
   7z x app-64.7z
   ```

Everything is now extracted and ready to launch.

---

# Step 2: Getting it to launch

In WoWSilicon, add a new Profile, select WrathSilicon (3.3.5a) and tick the 'Use third-party launcher' tick box

Click on the Set/Change button next to Launcher Path and select the ArdenWoW Launcher.exe which is based in the `PLUGINSDIR` extracted before. The 'Install Launcher' button should change to 'Open Launcher' instead.

Click on 'Open Launcher' and install as normal but don't press play when it has finished, instead exit the installer and press 'Set/Change' button next to Game Path. Here you need to point to the installation directory 

I'm using Steam's "Add a Non-Steam Game" feature, but the same approach should work in any Wine prefix.

1. First, run `PLUGINSDIR/resources/elevate.exe` inside your Wine prefix. In Steam, add it as a non-steam game and select that exe as the target:

   <img width="1469" height="717" alt="Screenshot_20260928_200050-1" src="https://github.com/user-attachments/assets/7df41c0e-5dc5-464f-aa27-16f27d6eed47" />

2. After a few seconds, `elevate.exe` will run and close on its own. Now we can start the launcher. **Don't add the launcher as a new shortcut.** Instead, change the target of the `elevate.exe` shortcut you already added. You can also rename the shortcut if you like:

   <img width="1469" height="717" alt="Screenshot_20260928_200401" src="https://github.com/user-attachments/assets/56dd18d5-d419-428a-a04a-e3baebb7d4c4" />

3. ArdenWoW should now launch and install correctly, but you can't play just yet. To get into the game, add the following under the shortcut's launch options in Steam:

   ```
   WINEDLLOVERRIDES="divxtac=d" %command%
   ```

   <img width="634" height="93" alt="Screenshot_20260928_200958" src="https://github.com/user-attachments/assets/53ad9d47-49e6-474e-9f82-f34a6d0ea8a2" />

Everything should work now. Enjoy the game!!

<img width="829" height="571" alt="Screenshot_20260928_201526" src="https://github.com/user-attachments/assets/8b5af6ef-65ca-45a8-b7ff-c99d1428bc45" />
