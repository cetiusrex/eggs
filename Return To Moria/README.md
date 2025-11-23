Prerequists:
- Must have a working pterodactyle instalation, setting that up is beyond the scope of this document
- Must have outbound internet working to connect to the Epic services. The game will not function without that.

How to install the moria egg:
1: Enter the admin area and click on the "Nests" tab on the left side:
  https://i.nva.wtf/qqr4ks.png

2: Select "Import Egg" on the right side:
  https://i.nva.wtf/33qoaw.png

3: Select the file and the Nest to associate the egg with and then click "Import"
  https://i.nva.wtf/a06i9n.png

4: You shouldn't need to edit anything, but feel free to make changes.

5: Click "save" at the bottom of the egg window. This might be unnecessary, but I do it just to make sure:
  https://i.nva.wtf/737xmn.png


How to setup a Return to Moria server in pterodactyle:
1: Enter the admin area and click the "Servers" tab on the left side:
  https://i.nva.wtf/cr3bxb.png

2: Click the "Create new" button in the right side:
  https://i.nva.wtf/g2b09x.png

3: Under "Core Details" enter the name of the server (NOTE: This only applies to the name of the pterodactyle instance, not the name of the RtM server itself), enter in the owner. Optionally you can set it to not start the server once it's installed, but that's not really necessary:
  https://i.nva.wtf/8ae0ez.png

4: Under "Allocation Management" enter the server you want to install this, then select the port. Return to Moria only needs one port:
  https://i.nva.wtf/er1h35.png

5: You can generally leave "Application Feature Limits" alone, unless you want to configure backups or a database, but databases aren't necessary. A backup though, is always a good idea.

6: In the "Resource Management" section, you can configure the "Memory" and "Disk Space". Return to Moria runs fine with 4gb of RAM and about 16gb of space:
  https://i.nva.wtf/hekv5v.png

7: For "Nest Configuration", select the appropriate Nest and Egg:
  https://i.nva.wtf/iu4fyr.png

8: The "Docker Configuration" and "Startup Configuration" sections don't really need to be edited unless you know what you are doing with them, that's a bit beyone the scope of this document.

9: The "Service Variables" section is the meat of the configuration.
  9a: World Name: Set this to what you want the server to be called inside the game. This variable gets hard coded into the save game, you can not change this without starting a new game.

  9b: Server PAssword: If you want to set a password for other players to have to use to log into your server.

  9c: Steam App ID: DON'T CHANGE THIS!

  9d: Windows Install: DON'T CHANGE THIS!

  9e: Winetricks: DON'T CHANGE THIS! (Caveate: If you need to add another driver like DX, you may need to edit this, testing on over 10 servers has shown vcrun2022 works fine alone)

  9f: Wine Debug: DON'T CHANGE THIS!

  9g: Difficult, setting this changes the default difficulty levels (NOTE: In order for any of the Custom dfifficult variables to work, you MUST set this to custom):
    Options:
      - story
      - solo
      - normal
      - hard
      - custom

  9h: Default DLC's: This is the DLC's used to build a new map, ommitting this should make it so the free update should work. Setting this requires that all players connecting to the server must have the DLC's listed. (NOTE: currently only "DurinsFold" can be listed)

  9i: DLC Upgrade: THIS ONLY APPLIES IF YOU ARE UPGRADING A SAVED WORLD TO THE LISTED DLCS (NOTE: currently only "DurinsFold" can be listed). Otherwise you can leave this blank

  9j: Seed: if you have a seed integer you prefer, otherwise just leave it random for a procedurally generated map.

  9k: World Type: This defines whether your server will be campaign or sandbox. (NOTE: This ONLY applies to new servers, if you import an existing save that is hard coded in the save)

  9l: Comabat Difficulty: The base enemy damage and hit points.
    Options:
      - verlow
      - low
      - default
      - high
      - veryhigh

  9m: Enemy Agression: How often enemies attack and how many will attack at once.
    Options:
      - low
      - default
      - high

  9n: Survival Difficulty: The strength of various buffs, speed a dwarf succumbs to despair and the decay rates of stamina, energy and hunger.
    Options:
      - verlow
      - low
      - default
      - high
      - veryhigh

  9o: Mining Drops: Volume of ore that drops from each vein.
    Options:
      - low
      - default
      - high

  9p: World Drops: The drop rates of rewards for defeating orcs and enemies.
    Options:
      - low
      - default
      - high
    
  9q: Horde Frequency: How often noisy actions will trigger a horde of orcs.
    Options:
      - verlow
      - low
      - default
      - high
      - veryhigh

  9r: Siege Frequency: How often orcs will target and attack a dwarf base.
    Options:
      - verlow
      - low
      - default
      - high
      - veryhigh
  9s: Patrol Frequency: How often orc and enemy groups spawn.
    Options:
      - verlow
      - low
      - default
      - high
      - veryhigh

10: Once you have the server tuned how you enjoy, click "Create Server"

11: Optiona: You can watch the server install progression for issues or errors.

12: If you have set the "Start server after install", it will start up the server automatically, otherwise press the "Start" button.

13: IMPORTANT NOTE: YOU MUST START THE SERVER ONCE FOR ALL THE FILES TO POPULATE CORRECTLY!!!

14: If you are starting a brand new server and don't hve any save files to import, you can copy down the IP and Port and start playing!

How to import an existing save into Pterodacyl:
1: First, you need to stop the server if it is running.

2: Click on the "Files" tab:
  https://i.nva.wtf/ci5pp6.png

3: Fine the "Moria" directory and click onthat, then find the "Saved" directory, then the "SaveGamesDedicated" directory, this will be where your saved world is:
  https://i.nva.wtf/r5j27s.png

4: Select all of the files and click "Delete" (NOTE: IF THESE ARE FROM A WORLD YOU WANT TO SAVE, DOWNLOAD THEM FIRST!!):
  https://i.nva.wtf/gni8h6.png

5: Find the save you want to upload (Not going to detail how to do that, other guides have that information), then either click the "Upload" button and search for your file, or drag the file right onto the Pterodacyl screen:
  https://i.nva.wtf/atzkrm.png

6: Go to the base container directory and select the "MoriaServerConfig.ini" file and open it up:
  https://i.nva.wtf/t1oboj.png

7: Edit the line "OptionalWorldFilename" under "[World]" and put in the name of your sav file, WITHOUT The .sav extension:
  https://i.nva.wtf/wubvh5.png

8: DO NOT EDIT THE DIFFICULTY SETTINGS FROM HERE!!

9: Click "Save Content"

10: Start your server, you should now have your saved file booting up.

11: NOTE: Setting "UpgradeOptionalDLC.Array" to a DLC will REQUIRE all players to have that DLC to join your server.