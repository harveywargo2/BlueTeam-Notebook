# Overview
The Windows registry is a centralized, hierarchical database that manages resources and stores configuration settings for applications on the Windows operating system. Security account services, user interfaces, and device drivers can all use the Windows registry.

**Registry keys** containers that act like folders, with values or subkeys contained within them. 
**Registry values** are similar to files (not containers).

The main branches of the registry are called **hives**.
All the folders in the registry are called _keys_ except for these five hives.

##### Registry Structure
- Hives: contain keys (directories) and values 
- Keys: might contain subkeys and/or values 
- Subkeys: no difference between key and subkey structure 
- Values: store data

# Reference Links
## Knowledge Articles
- https://github.com/Defenders-Guide/TheDefendersGuide/tree/main/Windows/Windows%20Registry
- https://medium.com/@nikhil.aniill/windows-registry-for-cybersecurity-beginners-63eebffb4049
- https://www.avast.com/c-windows-registry

## Training Course 
- https://academy.tcm-sec.com/p/practical-windows-forensics

# Registry Run Keys (AutoRuns)
- https://www.cyborgsecurity.com/cyborg-labs/hunting-for-persistence-registry-run-keys-startup-folder/#:~:text=Persistence%2C%20especially%20amongst%20threat%20hunters%2C%20doesn%E2%80%99t%20often%20get,top%20hunts%20that%20hunt%20teams%20should%20focus%20on
- https://medium.com/@domdalcerro/run-key-persistence-threat-package-part-1-introduction-56e63140013b
- https://www.linkedin.com/pulse/windows-persistence-registry-run-keysstartup-folder-mangipudi
- https://alican-kiraz1.medium.com/threat-hunting-for-windows-registry-27778993e21b
- https://resources.infosecinstitute.com/topics/malware-analysis/common-malware-persistence-mechanisms/


The registry run keys perform the same action, but can be located in four different locations:
- HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run
- HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run
- HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunOnce
- HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\RunOnce

The difference between HKEY_LOCAL_MACHINE and HKEY_CURRENT_USER is 
- whether the referenced executable launches at startup for any user logging in
- or a specific user 
- (current_user is copied to a stored “user hive” and loaded whenever that user ID logs in)

Then there is `Run` and `RunOnce`
- the only difference is that `RunOnce` will automatically delete the entry upon successful execution.