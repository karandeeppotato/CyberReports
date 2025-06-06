# IP Address
192.168.56.103

# NMAP SCAN RESULTS

## OPEN PORTS

http 80 Apache httpd 2.4.51
netbios-ssn 139
netbios-ssn 445
http 10000 MiniServ 1.981 (Webmin httpd)
http 20000 MiniServ 1.830 (Webmin httpd)

# Timeline

1) Viewing the source code of the apache webpage hosted on port 80, found an encrypted message at the very bottom.
2) ++++++++++[>+>+++>+++++++>++++++++++<<<<-]>>++++++++++++++++.++++.>>+++++++++++++++++.----.<++++++++++.-----------.>-----------.++++.<<+.>-.--------.++++++++++++++++++++.<------------.>>---------.<<++++++.++++++. 
3) Decoded String: .2uqPEfj3D<P'a-3
4) I noticed 2 SMB ports open so I decided to check for anonymous login but it was blocked
5) Used enum4linux to scan for shares, found a user "cyber".
6) Using the decoded string as password and username cyber, I can log into the usermin page hosted on port 20000
7) Found an online Email Client, on checking the webApp, I found a CLI tab that opens a command prompt.
8) With a simple ls command, I found a user.txt which is likely the user flag
9) The privilege is pretty open and I can see a lot of vectors which I can exploit my way to escalate the privilege
10) Found a file upload section, uploaded my linpeas file to try an privEsc. Cannot run an executable at the current privilege level
11) Found a backups directory in var directory which includes an old password.
12) Since our current user has the privilege to execute tar, I saved the old pass file in a tarball at /home/cyber directory
13) The old pass: Ts&4&YurgtRX(=~h, I can use it to gain root access.
14) Found the root flag in /root directory 
 
# Flags

User Flag: 3mp!r3{You_Manage_To_Break_To_My_Secure_Access} 
Root Flag: 3mp!r3{You_Manage_To_BreakOut_From_My_System_Congratulation}

Author: Icex64 & Empire Cybersecurity

