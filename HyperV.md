
# Installation
Copy the code, select "All files" and Save as hyperv.bat. Run as admin

```batch
pushd "%~dp0"

dir /b %SystemRoot%\servicing\Packages\*Hyper-V*.mum >hyper-v.txt

for /f %%i in ('findstr /i . hyper-v.txt 2^>nul') do dism /online /norestart /add-package:"%SystemRoot%\servicing\Packages\%%i"

del hyper-v.txt

Dism /online /enable-feature /featurename:Microsoft-Hyper-V -All /LimitAccess /ALL

pause
```

---
# VMCreate.exe.config
Save the code as "VMCreate.exe.config and save it in 
>	C:\Program Files\Hyper-V

to fix an error where you can't "quick create"
```
<configuration>
  <runtime>
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
      <dependentAssembly>
        <assemblyIdentity name="Newtonsoft.Json" publicKeyToken="30ad4fe6b2a6aeed" culture="neutral" />
        <bindingRedirect oldVersion="0.0.0.0-12.0.0.0" newVersion="13.0.0.0" />
      </dependentAssembly>
    </assemblyBinding>
  </runtime>
</configuration>
```

---
# Allocate more resources 
Type these commands into cmd(Admin):

>	$ bcdedit /set hypervisorschedulertype classic

>	$ bcdedit /enum

---
# Move Virtual Disk
- Press Ctrl+x on the folder containing the virtual disk -file(s)
	- Paste it in your desired folder
	-  Right click your virtual disk -file and click "copy as path"
- Go to Hyper V -manager
	- Right click the virtual machine > click "Settings.."
	- Go to "HardDive" > paste the full, new path of the virtual disk
	- Remove the """'s" > "Apply" > "OK" 

---
# Hotkeys
## Virtual Machine Connection Key Combinations
With Hyper-V we now have the "Virtual Machine Connection" to use when interacting with a virtual machine (unlike Virtual Server which used "VMRC").  The Virtual Machine Connection window wraps the standard Remote Desktop Client and uses this to connect to the virtual machine.  As such - we are now using the Remote Desktop key combinations.  Here is a brief summary of the key combinations that can be used with the Virtual Machine Connection:

| Standard Windows Key combination | Virtual Machine Connection Key Combination | Explanation                                                                       |
| -------------------------------- | ------------------------------------------ | --------------------------------------------------------------------------------- |
| CTRL + ALT + DEL                 | CTRL + ALT + END                           | Displays the Task Manager or Windows Security dialog box on Windows (or logs in). |
| ALT + TAB                        | ALT + PAGE UP                              | Switches between programs from left to right.                                     |
| ALT + ESC                        | ALT + INSERT                               | Cycles through the programs in the order they were started.                       |
| CTRL + ESC                       | ALT + HOME                                 | Displays the Windows Start menu.                                                  |
| N/A                              | CTRL + ALT + PAUSE                         | Changes the Virtual Machine Connection window to / from full screen mode.         |
| N/A                              | CTRL + ALT + LEFT ARROW                    | Releases mouse and keyboard focus from the Virtual Machine Connection window.     |

### Some extra things to know about Virtual Machine Connection key combinations:

By default the standard Windows key combinations do not get sent to the virtual machine, unless you are in full screen mode.  You can change this so that they are always sent to the virtual machine (if the Virtual Machine Connection has focus) by going to the Hyper-V Manager and selecting Hyper-V Server Settings... and then Keyboard and selecting the Use on the virtual machine option.  I always enable this setting.

Note: CTRL + ALT + DEL will always go to the physical computer - so you need to use CTRL + ALT + END no matter what you select for a setting here.
You can change the release key combination (CTRL + ALT + LEFT ARROW) by going to the Hyper-V Manager and selecting Hyper-V Server Settings... and then Release Key and selecting one of the options from the drop down (I usually change my release key combination to be CTRL + ALT + SHIFT as I find it easier to type).

If you use the Virtual Machine Connection under an existing Remote Desktop Connection (not recommended - but I do it all the time) the Remote Desktop Connection will grab all of these key combinations before the Virtual Machine Connection gets to see them (even the release key combination).  To deal with this you will need to change the Hyper-V Server setting to allow Windows key combinations to go to the virtual machine, change the release key combination to something other than CTRL + ALT + LEFT ARROW, and use the toolbar button or Action menu of the Virtual Machine Connection to send CTRL + ALT + DEL to the virtual machine.

-------------------------------------------------------------------------