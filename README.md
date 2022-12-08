# Exam_2420 README

## 1: to update most of the software in your ubuntu OS, you can use the commands:
```
sudo apt-get update
```
then you can run the command:
```
sudo apt-get upgrade
```

## 2:
![image](https://user-images.githubusercontent.com/100608327/206564019-1394ced4-ed17-47b1-a01b-5bb5cf90178c.png)
this is the editted code, the commands I used were,
r to replace the singular letters with the correct letter.
for the bottom, where the echo and the :digit:, i used ciw, which replaces the entire word and allows you to type the new word in.

## 3:
some of the options I have found in the man page in order to create this journalctl command:
![image](https://user-images.githubusercontent.com/100608327/206564888-80d59d31-6f37-4340-bf46-887815ad20f6.png)
![image](https://user-images.githubusercontent.com/100608327/206565142-6de0233a-b2f2-4453-b3db-644559a9da4b.png)
![image](https://user-images.githubusercontent.com/100608327/206565276-28956428-6dfb-4b6d-8a22-235f99f24403.png)
![image](https://user-images.githubusercontent.com/100608327/206565429-5bc68446-695c-48b2-a975-6f3a95d08a35.png)
I found these commands/options for the command by typing the "/" in the man page and procceeded to search for the properties listed in the question from the notion. For example, because you would like for it to output a pretty json file, I searched up "/--pretty or, /pretty" it would narrow down my options. I did it like that for each component of the command.
### THE COMMAND:
```
journalctl --boot --priority=warning --output=json --pretty
```

## 4:
multiple home directories:
![image](https://user-images.githubusercontent.com/100608327/206566331-afe90c24-8ab7-4496-8bcc-ac7b4819ed53.png)
![image](https://user-images.githubusercontent.com/100608327/206567866-01a38d86-943e-467d-9e92-080a52e28e7e.png)

This is my script for this question, the output of the script is below:
![image](https://user-images.githubusercontent.com/100608327/206567948-28d4609d-d9d2-492c-ad0e-39df6587c7fa.png)

MY ACTUAL UPDATED SCRIPT IN A CODE BLOCK:
```
#!/bin/bash

# Find all of the regular users with a UID from 1000 to 5000
# by using awk to search the /etc/passwd file
# and save the output to the /etc/motd file
awk -F: '$3 >= 1000 && $3 <= 5000 {print $1 " " $3 " " $7}' /etc/passwd > /etc/motd

# Find all of the currently logged in users by using the who or w command
# and print only the username to the /etc/motd file
who | awk '{print $1}' >> /etc/motd
```
## 5:
service file code:
```
[Unit]
Description=Updates the /etc/motd file with information about regular users and currently logged in users

[Service]
Type=oneshot
ExecStart=/bin/bash -c '/bin/find_users'

[Install]
WantedBy=multi-user.target
```
output of service file:
![image](https://user-images.githubusercontent.com/100608327/206571479-77469712-e9ce-4858-afc2-17854595f475.png)

## 6:
timer file:
```
[Unit]
Description=Runs the motd-updater service 1 minute after booting and every day

[Timer]
OnBootSec=1min
OnUnitActiveSec=1d

[Install]
WantedBy=timers.target
```





