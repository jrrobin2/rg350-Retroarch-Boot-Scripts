# rg350-Retroarch-Boot-Scripts
Scripts to make it easier to switch back and forth from the default gmenu2X and retroarch as a launcher for rg350/rg280v and like devices

The idea came from Sichroteph's thread on Reddit https://v.redd.it/pgj0t0ftve971 to enable "deep sleep" for Retroarch on rg350 and 280 devices.  Sichroteph's scripts worked great but the problem for me was that I needed to drop out of Retroarch from time to time to access other utilities on the gmenu2X menus.  To do this manually meant you had to ssh in to the device and rename or remove the frontend_start script

I modified Sichroteph's script to present the user with a choice on boot for either gmenu2X or retroarch using dialog.  The menu would timeout after a few seconds and just load retroarch instead.

What I found was that the fronted is constantly spawned after it ends in order to keep the program launch/return to menu loop going.  If I did nothing else then exiting retroarch would result in the frontend_start script being launched again and prompting again after every program execution in gmenu2X.  To defeat this I added a flag file that would be checked each time to determine if retroarch should be loaded automatically or not.

 I also wrote another script that needs to be added as a new link in gmenu2X to remove the flag file and revert back to the normal behaviour.
 
 I happy side effect I discovered is that the Dialog UI would not be displayed on screen during boot.  I presume this is because we are in a framebuffer graphics mode instead of text mode but didn't care why.  I like this better anyway.  The net effect is that you need only hold down the start button during boot (after the boot logo apears) to revert to gmenu2X.  To go back to boot directly to retroarch run the RenableRetroArchBoot script from gmenu2X.
 
 Script locations:
 /media/data/local/sbin/ for frontend_start
 /media/data/local/home/ for RenableRetroarchBoot
