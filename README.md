mysql-kill
==========

This script let you find MySQL queries by patterns, execution time, or both  and kill them without restarting MySQL daemon.

Installation
============

Checkout the script:

```bash
$ wget https://raw.github.com/cperezcerrato/mysql-kill/master/mysql-kill /usr/local/bin/
```

Set permissions:
```bash
$ chmod +x /usr/local/bin/mysql-kill
```
Set user, password with administration privileges and path (if necesary), in the file /usr/local/bin/mysql-kill.

Variables:
```bash
MYSQL="" # Path to MySQL binary command. If not set, fill with 'which mysql'
USER="" # User with administration privileges.
PASS="" # Password for $USER.
```
Feel free to put the script in the path you want.

Usage
=====

Kill MySQL queries that execution time is above the time (in seconds) specified by command line arguments.

```bash    
mysql-kill [ -p PATTERN ] [ -t TIME(in seconds) ] [-l /path/to/file.log ].

    -p  PATTERN (optional) Find PATTERN in MySQL queries.
    -t  TIME (optional) time in seconds, default 15.
    -i  ID (optional) Query ID to kill (specifying -p or -t is not needed using this).
    -l  logfile (optional) File to log killed queries.
```
Examples:

Kill all queries that contains "exampledb"
```bash
$ mysql-kill -p exampledb
```

Kill all queries that contains "exampledb" and execution time is greater than 40 seconds and log in file /tmp/mysql-killed.log
```bash
$ mysql-kill -p exampledb -t 40 -l /tmp/mysql-killed.log
```

Kill all queries whose execution time highter 15 seconds (default)
```bash
$ mysql-kill
```
Kill all queries whose execution time is greater than 3 seconds:
```bash
$ mysql-kill -t 3
```

Kill query with id equal to XXXX:
```bash
$ mysql-kill -i XXXX
```
