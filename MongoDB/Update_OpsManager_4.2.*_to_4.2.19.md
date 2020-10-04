
## How to update Ops Manager 4.2.* to a newer 4.2 version or the latest 4.2.19

### Prerequisites

- If you have running Backup Daemons, you need to stop Backup Daemons by
    1. Log into the first host that serves a Backup Daemon.
    1. Click the Start button.
    1. Click Administrative Tools.
    1. Click Services.
    1. Right-click the MongoDB Ops Manager Backup Daemon Service and select Stop.
    1. Repeat steps 2 to 5 with every other Backup Daemon host.



### Procedure

1. Stop your first running Ops Manager Service

```bash
systemctl stop mongodb-mms
```


2. Download and update Ops Manager Package

```bash
## Download mongodb-mms-4.2.19
wget https://downloads.mongodb.com/on-prem-mms/rpm/mongodb-mms-4.2.19.57005.20200925T1733Z-1.x86_64.rpm
## update 
rpm -Uvh mongodb-mms-4.2.19.57005.20200925T1733Z-1.x86_64.rpm
```

3. Start Ops Manager service

```bash
systemctl start mongodb-mms
```
