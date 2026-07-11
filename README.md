# usb-printer-shair-win11-to-win10-or-win10-to-win11
Fix 1: Registry (Point and Print)

On Windows 10:

Open CMD as Administrator:

regedit

Go:

HKEY_LOCAL_MACHINE
\Software
\Policies
\Microsoft
\Windows NT
\Printers

Create:

DWORD (32-bit)

Name:

RestrictDriverInstallationToAdministrators

Value:

0

Restart PC.

Fix 2: Add printer manually

Windows 10:

Control Panel
→ Devices and Printers
→ Add printer

Click:

The printer that I want isn't listed

Choose:

Select a shared printer by name

Type:

\\Windows11-PC\HP1020
Fix 4: Driver problem

On Windows 10 install same driver.

Example:

HP:

install HP LaserJet driver

Canon:

install Canon driver

Then add shared printer.

Fix 3: Windows 11 recent security issue

On Windows 11:

Open CMD administrate:

reg add "HKLM\System\CurrentControlSet\Control\Print" /v RpcAuthnLevelPrivacyEnabled /t REG_DWORD /d 0 /f

Restart:

net stop spooler
net start spooler

* Fix 4: Clear stuck printer

in Both PCs:
run CMD admin:

net stop spooler
del %systemroot%\System32\spool\printers\* /q
net start spooler
* Fix 5: Firewall

Windows 11:

Allow:

Control Panel
→ Windows Defender Firewall
→ Allow app

Enable:

✅ File and Printer Sharing

Fix 8: Add user permission

Printer Properties:

Sharing → Permissions

Add:

Everyone

Give:

✅ Print

Most common working combination (Windows 11 host + Windows 10 client)
Enable sharing
Install printer driver on Win10
Registry:
RestrictDriverInstallationToAdministrators = 0
Restart spooler
Add printer using:
\\PCNAME\PrinterShareName

server pc
* Computer\HKEY_CURRENT_USER\Software\Microsoft\Windows NT\CurrentVersion\Windows (right click permission) everyone
* Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows NT\Printers
new key RPC , new RpcOverTcp 0
new: 
* RpcOverNamedPipes 1

* HKEY-LOCAL-MACHINE\SYSTEM\CURRENTCONTROLSET\CONTROL\PRINT
RpcAuthnLevelPrivacyEnabled   0

* edit group policy
administrative Templetes
printers
configure rpcconnection settings
enable
RPC over named pipes

* configure RPC listener setting 
enabled
RPC over named pipes and TCP

* CONFIGURE OVER TCP PORT
ENABLED
 0


* Press the Windows key + R then enter services.msc
  Double-click on Printer Spooler then click Stop
  Now go to 
  Go to Printer Spooler once again and click StartDelete the printer driver

* printer uninstall
Press Win + R.
Type:
printui /s /t2

  


