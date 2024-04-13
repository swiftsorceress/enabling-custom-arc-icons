# Enabling Custom Arc Icons

Ok, so after messing with Arc's files for a while, I think I've figured out how to get around the restrictions with custom icons. To do it though, you have to change some things in your computer's Library folder. The following solution worked for me and doesn't have any noticeable problems so far. Before starting, you'll need a way to edit .plist files. I used Xcode but you could use something else.



So basically, these are the steps to get custom icons working again:

1. Quit Arc before doing anything else
2. Navigate to "~/Library/Preferences" and find a folder that starts with "com.launchdarkly.client".
3. Since there may be more than one of these folders, you'll need to make sure you're in the correct one for Arc. To do this:
   1. Open the file at "~/Library/Preferences/company.thebrowser.Browser.plist"
   2. Navigate down through folders in the "com.launchdarkly.client" folder until you reach a file called "U=.plist" (the path will be something like "~/Library/Preferences/com.launchdarkly.client.rest_of_ folder_name/y/4NLB/U=.plist")
   3. Open this folder and check to see if the first 4 digits of the values matches the first 4 digits of the value for the key in the "company.thebrowser.Browser.plist" file starting with "com.launchdarkly.DiagnosticCache.diagnosticData"
4. If those match, you should have the correct file now.
5. ﻿﻿﻿In the "U= plist" file, you will need to delete the line starting with "flags-" and then save the file. This line is connected to resetting the app icon but I've not looked into how they're connected.
6. ﻿﻿﻿Now, close the file and right click on the folder titled "4NLB" and select "Get Info".
7. Check the box that says "Locked" for the "4NLB" folder. This prevents Arc from reverting the changes in the .plist file.
8. Find Arc in the applications folder
9. Right click and select "Show Package Contents"
10. Go to Contents > PlugIns, and then delete the DockTilePlugin.plugin file
11. You should now be able to replace the icon in Applications by right clicking, selecting "Get Info", and dragging the new .icns file.



This should make your custom icon persist between launches and while the application is open. BUT, if you do not feel comfortable modifying your files, do not do it. This is not at all an official solution and might cause problems or mess up files so proceed at your own risk. However I do believe that it will work fine if you end up trying it.


### Update:
Icons appear to be reset after restarting your computer.
