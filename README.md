Clear Logs

1 Save the .bat file to your desktop.

2 Unblock the .bat file.

3 Right click or press and hold on the .bat file, and click/tap on Run as administrator.

4 If prompted by UAC, click/tap on Yes.

5 A command prompt will now open to clear the event logs. The command prompt will automatically close when finished.

---

**OPTION TWO**

#### **To Clear All Event Viewer Logs in PowerShell**

1 Open an **elevated Windows PowerShell**.  
  
2 Copy and paste the command below you want to use into the elevated PowerShell, and press **Enter.**

```plaintext
Get-WinEvent -ListLog * | where {$_.RecordCount} | ForEach-Object -Process { [System.Diagnostics.Eventing.Reader.EventLogSession]::GlobalSession.ClearLog($_.LogName) }
```

**OR**

```plaintext
Get-EventLog -LogName * | ForEach { Clear-EventLog $_.Log } 
```

**OR**

```plaintext
wevtutil el | Foreach-Object {wevtutil cl "$_"}
```

** The event logs will now be cleared. You can close PowerShell when it's finished.**

