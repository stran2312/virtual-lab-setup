# virtual-lab-setup: installing Flare VM
The installation guide and official Flare VM is here https://github.com/mandiant/flare-vm. This is just a general guide and how to solve the errors I encountered

Step 1: create an ISO image from Windows 10 Media creation tools: https://www.microsoft.com/en-us/software-download/windows10

Step 2: create a new VM on Virtual Box and select windows 10 iso with at least 80 GB.

Step 3: start the VM.

Step 4: disable windows auto update via windows setting or
Type 'regedit' in the search box then enter > find HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows > right-click new key > right-click new DWORD NoAutoUpdate enter > edit value to 1.

Step 5: disable windows tamper-protection and real-time protection in the windows security settings.

Step 6: disable windows defenter
Open powershell as administrator > type command netsh advfirewall set allprofiles state off
type 'regedit' in the search box > find HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender > new DWORD DisableAntiSpyware > edit value to 1 > reboot

Step 7: open powershell as admin > type (New-Object net.webclient).DownloadFile('https://raw.githubusercontent.com/mandiant/flare-vm/main/install.ps1',"$([Environment]::GetFolderPath("Desktop"))\install.ps1") 

Step 8: the previous script will install the file "install.ps1" to desktop so we navigate to desktop > type Unblock-File .\install.ps1 > Set-ExecutionPolicy Unrestricted >.\install.ps1

Step 9: if you encounter the sysinternals installation check sum error.
You can either download sysinternal suites from Microsoft store https://learn.microsoft.com/en-us/sysinternals/downloads/sysinternals-suite
or follow this: https://wiert.me/2021/09/28/chocolatey-force-install-sysinternals-after-hash-mismatch/

Afterwards, FlareVM will be installed successfully.

