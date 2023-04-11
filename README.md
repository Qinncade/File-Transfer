# File-Transfer
## Collection of File Transfer possibilities

Sometimes it is useful to have a Plan B if you need to transfer a file from or to a remote machine.

## Base64
If all else fails, there is always plan y.
Convert a File or Program to a Base64 string Copy & Paste it to the Target and deconvert it.
Nix to Nix
```bash
base64 file.ext > fileb64.txt
cat fileb64.txt
```
Copy the Base64 string.
```bash
vim string.b64
```
Paste the string to any Text-Editor.
```bash
base64 -d string.b64 > file.ext
```
