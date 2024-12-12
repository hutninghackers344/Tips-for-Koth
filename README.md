# Tips-for-Koth
Here i will taught you some basics techniques used in Koth for defending :)


![wall](https://github.com/user-attachments/assets/53c4dde6-8bf3-4327-b081-50de8851a3f6)


#Using chattr to block write access to king.txt
--> echo your_username > /root/king.txt
--> chattr +aie /root/king.txt

Bypass of this simple chattr:

----> lsattr /root/king.txt (used for checking how much attributes are used using chattr)
----> chattr -aie /root/king.txt

Using loop to defend:
----> while true; do echo "USERNAME" > /root/king.txt && cat /root/king.txt; sleep 1; done &

Mounting file :

----> mount  --bind -o ro /root/king.txt /root/king.txt

Unmount it :

----> umount -f /root/king.txt


Many users are using user land rootkit which propaly not that hard to detect or remove:

----> mv /etc/ld.so.preload /dev/null
(or) ----> echo '' > /tmp/.t && mount --bind -o ro /tmp/.t /etc/ld.so.preload



Hide your process pid from ps auxf by mounting it :

--> mount  --bind -o ro /tmp /proc/your_process_pid

Killing shells :
----> pkill -9 -t pts/your_oponent-pts-id


Also many many players in koth are now days using their lkms or kernel based rootkits they are hard to detect as well as but if ur fast enough to stop them form loading just use this commands :

----> sysctl -w kernel.modules_disabled=1
---->  sysctl -p (apply changes)

For finding SUID binary :
---> find / -perm /4000 2>/dev/null


Or i f u want to remove SUID binary you can do so by which also stop users who using pwnkit:
----> chmod -s $(which find)


chattr loop:

----> while [ 1 ]; do chattr -ia /root/king.txt 2>/dev/null; echo -n "YourUsername" >| /root/king.txt 2>/dev/null; chattr +ia /root/king.txt 2>/dev/null; done &



FOr windows defending can do by :

attrib blocking or using ur own loop:


attrib:
attrib +A +S +R +H C:\king.txt



refrences: https://github.com/fasc8/Chattr-for-KOTH
https://hackmag.com/security/persistence-cheatsheet/

