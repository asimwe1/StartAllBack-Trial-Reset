# Note
I do not condone piracy, if you find StartAllBack to be truly useful and have some money to spare, consider buying a license key: https://www.startisback.com/#buy-tab

---

# Reset Trial
To reset the 100 day trial of StartAllBack, open Command Prompt as an administrator and paste the command below (make sure to double check to avoid destroying your system)

**3.6.11**
```
reg delete "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\CLSID\{36b74d56-9dfb-6ba1-cee4-0a97d8f99e0}" /f
```

---

**3.6.8**
```
reg delete "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\CLSID\{yyyy yyyy}" /f
```

---

**3.6.6**
```
reg delete "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\CLSID\{dfb8a420-11e2-7851-274d-9b9002af292}" /f
```

If it returns `The operation completed successfully.` that means you successfully reset the trial.
