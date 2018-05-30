## MySqlDumpAllDatabases.sh

This script backups all your client's MySQL databases in individual files.
After the first copy, only modified databases will be copied.

[Download URL](https://github.com/elkarbackup/elkarbackup-scripts/raw/master/MySqlDumpAllDatabases/MySqlDumpAllDatabases.sh)

### Configuration

Script level configuration:

```
CLIENT PRE-SCRIPT:    NO
CLIENT POST-SCRIPT:   NO
JOB PRE-SCRIPT:       YES
JOB POST-SCRIPT:      NO
```


Create a New Job:

```
Name: mysql
Path: /root/backups/mysql
Description: MySQL dumps
Pre-script: MySqlDumpAllDatabases.sh

```

MySQL dumps will be copied to the "Path" field (example: /root/backups/mysql) and ElkarBackup will save this directory. If "Path" directory doesn't exist, it will be created on first execution.


### In non-debian based distributions


This script logs in MySQL thanks to /etc/mysql/debian.cnf file. In non-debian based distributions follow next steps.

Generate file /root/.my.cnf:

```
[mysql]
user=root
password=1234

[mysqldump]
user=root
password=1234
```

Important: this file must have 400 permissions:

`chmod 0400 /root/.my.cnf`
