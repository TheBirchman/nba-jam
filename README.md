# nba-jam
This repository contains the required resource files for running (and modifying) NBA JAM v4.00.14 on mobile devices. Below is a brief explanation of the files contained within and the successes and challenges with each.

## SD Card Android Filepath for Resource Files
Internal Storage/Android/Data/com.eamobile.nbajam_na_wf/res/

## The Viewable & Editable Archive Files
All of these files can be opened and viewed using 7zip or WinRAR. In my experience, re-insertion is much easier with WinRAR, though either works with the g archive file.

- g: all player texture files in .pvr format. 
Download PVRTexTool (free) to view the .pvr file and save as .png. Edit in your favorite photo editing client and save. Re-open the edited png in PVRTexTool, Edit > Encode > RGBA 4 4 4 4 > Check 'Vertical Flip' > Encode. Then File > 'Save As Legacy...' as a .pvr file with the same name as the original file you edited. Add the new texture back to the archive and return it to the res folder on your android device. The edited player will now show up with the updated textures.

- i: most other image assets used by the application, like team logos, menu screens and player portraits. Editable files are in .png format (no additional extraction or re-encoding necessary).

- ga: player animation files in .anim format (very little work has been done on these files)

- a: all audio files stored in a .caf (Core Audio File) format. The core audio chunks are encoded in a proprietary .ea_cdata format. Use the ffmpeg command line tool (or the Audacity plugin) to decode and convert this audio to .wav or 16bit linear PCM (however, once this is done, it's currently not possible to re-encode the audio as .ea_cdata wrapped by .caf for insertion into the game).
    *NB: the above applies to only ORIGINAL audio files. Audio for players added in updates can be imported as raw audio into Audacity,          but it's unclear as to what format the core audio chunks are in (Andrew Wiggins and Jamal Crawford are reproducible examples)*
    
## The CONSOLE Files
These files are saved as .csv and can be opened with any text editor or Microsoft Excel. *Note: Between application update 2.00.14 and current version, it appears only SOME edits within these files have a noticeable in-game impact. Still testing...

- NBAJAM_Players_CONSOLE.csv : Player names, unique ID, biographical information, in-game scaled height, player ratings, team assignment, assigned animations and tendencies. *Recently discovered: changing player's first/last name causes game crash. This was not the case in 2.00.14.*

- NBAJAM_Teams_CONSOLE.csv : Team name, city, abbreviation, overall (rating?? -- unclear where this is used), x and y coordinates for in-game map, color scheme, division and stadium

## Other important files

- NBAJAM_iPhone_ENG_US.btp : in 2.00.14, opening this file in a hex-editor and searching for a player's last name (Rubio, for instance) and replace it with a last name of the exact same length (ie Birch) and saving changed the in-game display name for that player (character select and display name during gameplay). However, in the current version, changes in this file don't seem to have any in-game impact.

- The .vars Files : these files, 8 in total (plus localization files), were added in the 4.0 update and probably explain why normal hex and CONSOLE-file editing no longer work in the same way. All can be opened in your favorite text editor and seem to be reference files with a variety of purposes. They're listed below 
  - NBAJAM_AudioManager.vars
  - NBAJAM_ChallengeDefinition.vars
  - NBAJAM_ClassicCampaign_CampaignCentralState.vars
  - NBAJAM_ClassicCampaign_UnlockPlayerState.vars
  - NBAJAM_ClassicCampaignData.vars
  - NBAJAM_kazaamplayerdatabase.vars
  - NBAJAM_kazaamteamdatabase.vars
  - NBAJAM_Loader.vars
  - NBAJAM_Localization_ENG_US.vars
