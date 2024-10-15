# GTNH-offline-mode-bypass
GTNH server is made to be played in online mode (setting online-mode=true in server.properties) because in offline mode UUID generation breaks some mods and is also against the projects' policy (So people with cracked minecraft don't play it I think).
Some of these mods are:
 - Amun-Ra (Galacticraft extesion)
 - Better Questing (GTNH main questing mod)

When you switch the server into offline mode (setting online-mode=false in server.properties) and try to connect with an offline client that didn't join while the server was in online mode, it will display an error message and kick you off the server. This is generally fine and works for it's intended purpose of not allowing users with cracked minecraft to play.

One issue I ran into and why I am trying to find a fix for this is that when you own a legal copy of minecraft but want to have multiple accounts play at the same time. For example, to be on different farms/places, it becomes impossible. In Prism Launcher this is called offline accounts and allow you to launch multiple minecraft sessions with offline accounts alongside your main one (with Microsoft account logged in).

# Temporary solution how to play Gregtech: New Horizons in offline mode
This method is only usable in private servers, as you need to manually create multiple files for each user (Or small friend servers). You could automate it using some scripts, but it would be too fragile and unreliable.

For this you will need:
1. Basic understanding of directory structure and operating of minecraft server
2. Knowing how to work with JSON files
3. Having a tool to edit minecraft .dat files (For example this one: https://github.com/jaquadro/NBTExplorer)

## Step 1
1. Download the newest java 21 GT:NH server from the official website: https://downloads.gtnewhorizons.com/ServerPacks/
2. Extract it into the folder you want and run the server for the first time using the start .sh or .bat file.
3. Accept Eula and run it again until you see 'Unloading dimension 1'

## Step 2
1. Launch your minecraft client with GT:NH where you are logged in using Microsoft account.
2. Connect to the server, wait a few second until everything renders and then leave.

## Step 3
1. Go back to the server, write 'stop' and hit Enter to save everything and stop the server.
2. You can also close your minecraft client if you plan on running the offline one instead

## Step 4
1. Prepare a username for the account you will be logging in with
2. Prepare a random UUID for the account. (For example from here: https://www.uuidtools.com/minecraft)
3. Locate the folder to which you extracted the server, there you should see two files 'usercache.json' and 'usernamecache.json'
4. Open the first file with any text editor, copy the only record there is (It should be the account you connected to the server earlier) and modify the username and UUID to the ones you prepared earlier. Do the same with the second file.

## Step 5
1. Go to the 'World' folder and there into 'playerdata'. There should be multiple files.
2. Copy all of them into some temporary directory, the one with the random letters and numbers in its name, rename to the UUID you prepared. All the other rename to the username you prepared. (You can see how they are named, it is kinda logical)
3. Now take all the renamed files from the temp directory and copy them back into the main one. (So now there are all the files twice but with different names)

## Step 6
1. The last thing you need to do is go back into the 'World' dir and open serverutilities/players. There, copy the file and rename it to the username you prepared
2. Open that file with the .dat editor you should have prepared and modify the Name and UUID entries to the ones you prepared (UUID is without the dashes)

## Step 7
1. Now you just change online-mode=true in server.properties to false, start the server back up
2. Start minecraft client with GT:NH where you have the username you prepared and had set up in previous steps and connect to the server. It should let you in just fine.

Repeat Steps 4 to 6 for as many users as you need.
