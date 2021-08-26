# cron:
The **cron** service allows us to schedule commands to run at regular intervals like:
- Every 30 minutes
- Every day at midnight
- Every 1st of the month
- Every December 15th

## Editing the contab:
The crontab file is located /var/spool/cron/crontabs. To set up a cron job, we need to edit the crontab configuration file. Rather than edit the fiels directly, it's best to use the below command

```bash
crontab -e
```

## Cronjob Syntax:
![Crontab Syntax](https://miro.medium.com/max/1288/1*SspOSwP0HKaQCnhO1oe-rg.png)

```bash
a b c d e command
# a - Minute 0-59
# b - Hour 0-23
# c - Day 1 - 31
# d - Month 1-12
# e - Day(of week) 0-6
```

## Cron Characters:
- * - any value
- 5, 6 - List of values (5 and 6)
- 1-4 - Range of values (1 to 4)
- */5 - Step values (every 5)

```bash
0 4 8-14 * *
# 0 - Minute 0-59
# 4 - Hour 0-23
# 8-14 Day 1-31
# * - Month 1-12
# * - Day (of week) 0-6
```

**Run a job at minute 30, every hour (every time the clock shows x:30)**
```bash
30 * * * * command
```

**Run a job every day at 6:30am (when hour is 6 and minute is 30)**
```bash
30 6 * * * command
```

**Run a job every monday at 6:30am**
```bash
30 6 * * 1 command
```

**Run a job every monday in April at 6:30am**
```bash
30 6 * 4 1 command
```

**Run a job at midnight on the first of every month**
```bash
0 0 1 * * command
```

For better understanding, go https://crontab.guru/.

## Handling Errors:
```bash
* * * * * echo "Another minute! Date is $(date)" >> ~/time.log 2>&1
```

## More Cron Syntax:
**Run a job at midnight every weekday (monday-friday)**
```bash
0 0 * * 1-5 command
```

**Run a job every 5 minutes**
```bash
*/5 * * * * command
```

## Backup Cron:
### First show demos:
Create some folder with different files have to compress. To do
```bash
tar -cvzf backup.tar.gz Folder/  # Create a backup file of folder named Folder
rm -rf Folder/  # You can delete the folder but be very serious
tar -xvzf backup.tar.gz  # Uncompress the tar.gz file and done! Folder and files come back
date +%d  # output the day only
date +%Y  # output the year only, y - gives last 2 digits, Y - gives 4 digits
date +%m  # output the month
date +%M  # Output the minute
date +%m-%d-%Y  # Output like 04-30-2021
```

Now inside home directory create,
```bash
mkdir ~/backups
touch my-backup
nano my-backup
```
Create the bash script that will be executed for backup.

```bash
#!/bin/bash
DATE=$(date +%m-%d-%Y)
BACKUP_DIR="/home/sayan/backups"

# ~/backups/backup-04-30-2021.tar.gz  will be the name
tar -cvzf $BACKUP_DIR/backup-$DATE.tar.gz /home/sayan/Desktop
```

Give permission to be able executable
```bash
chmod +x ~/backups/my-backup
```

Now setup the cronjob

```bash
crontab -e
* * * * * /home/sayan/bin/my-backup # if you set the bash executable file as global 
```


