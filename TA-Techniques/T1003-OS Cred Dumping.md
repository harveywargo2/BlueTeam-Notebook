 - https://book.hacktricks.xyz/windows-hardening/stealing-credentials
 - https://attack.mitre.org/techniques/T1003/

# LSASS (T1003.001)
LSASS stores credentials in memory on behalf of users with active Windows sessions. The purpose of storing these credentials is so that users can access network resources, file shares, mail, and more without having to re-authenticate to each individual service.

LSASS stores credential material in various forms, including:
-   Reversibly encrypted plaintext
-   Kerberos Tickets
-   NT hashes
-   LM hashes

Credentials are cached to LSASS whenever a user authenticated in an interactive manner. The following types of activity will put the user’s credential material into memory:
-   Starting a local session
-   Starting an RDP session
-   Running a task via RunAs
-   Running an active Windows Service
-   Running a scheduled task
-   Running a batch job
-   Running a task by utilizing a remote administration tool

#### Attack References 
- https://redcanary.com/threat-detection-report/techniques/lsass-memory/
- https://pentestlab.blog/2021/05/24/dumping-rdp-credentials/
- https://www.slideshare.net/heirhabarov/hunting-for-credentials-dumping-in-windows-environment
- https://threathunterplaybook.com/hunts/windows/170105-LSASSMemoryReadAccess/notebook.html

- https://clymb3r.wordpress.com/2013/04/09/modifying-mimikatz-to-be-loaded-using-invoke-reflectivedllinjection-ps1/

#### TaskManager, ProcDump & Comsvc.dll
- https://lolbas-project.github.io/lolbas/Libraries/comsvcs/
- https://modexp.wordpress.com/2019/08/30/minidumpwritedump-via-com-services-dll/
- https://www.ired.team/offensive-security/credential-access-and-credential-dumping/dump-credentials-from-lsass-process-without-mimikatz

Typical Paths of DLL & Binaries
~~~
c:\windows\system32\comsvcs.dll

c:\windows\system32\lsass.exe
~~~
#### Using ADPlus
- https://lolbas-project.github.io/lolbas/OtherMSBinaries/Adplus
- https://mrd0x.com/adplus-debugging-tool-lsass-dump/
~~~
C:\Program Files (x86)\Windows Kits\10\Debuggers\x64\adplus.exe

C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\adplus.exe
~~~

#### Silent Process Exit
- https://github.com/deepinstinct/LsassSilentProcessExit
- https://www.deepinstinct.com/blog/lsass-memory-dumps-are-stealthier-than-ever-before-part-2

#### WerFault/Shtinkering
- https://media.defcon.org/DEF%20CON%2030/DEF%20CON%2030%20presentations/Asaf%20Gilboa%20-%20LSASS%20Shtinkering%20Abusing%20Windows%20Error%20Reporting%20to%20Dump%20LSASS.pdf

#### Nanodump
- https://github.com/helpsystems/nanodump

#### Dumpert
- https://github.com/outflanknl/Dumpert
- https://outflank.nl/blog/2019/06/19/red-team-tactics-combining-direct-system-calls-and-srdi-to-bypass-av-edr/

#### Pypykatz
- https://andreafortuna.org/2020/03/20/pypykatz-a-mimikatz-python-implementation/
- https://github.com/skelsec/pypykatz


#### Mimikatz
