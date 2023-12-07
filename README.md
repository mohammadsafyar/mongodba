# MongoDB 7.0.2 Standalone Installation offline and Configuration on Ubuntu

This guide provides step-by-step instructions to install MongoDB 7.0.2 standalone version offline on Ubuntu. It also covers changing the `dbPath`, `logPath`, and `port number`.

## Server Details

- **Server Name:** ser01
- **IP Address:** 192.168.225.150

## Installation Steps

1. **Download MongoDB:**

   Download MongoDB 7.0.2 package on a machine with internet access.

   ```
   wget https://repo.mongodb.org/apt/ubuntu/dists/focal/mongodb-org/7.0/multiverse/binary-amd64/mongodb-org-server_7.0.2_amd64.deb

    ```

## 1. Copy to Main Server:

Copy the downloaded MongoDB package to the main server.

## 2. Install MongoDB:

Install MongoDB on the server.
```bash
sudo dpkg -i mongodb-org-server_7.0.2_amd64.deb 
```

 ## 3. Create Directories for Data and Log Files:

Create directories for MongoDB data and log files.

These directories will be used to store MongoDB data files (/var/mongodb/dbfile) and log files (/var/mongodb/logfile).

## 4. Set Permissions for New dbPath:

Set permissions for the new MongoDB data and log directories.
````
sudo chown -R mongodb:mongodb /var/mongodb/logfile/
sudo chown -R mongodb:mongodb /var/mongodb/dbfile/
``````


## 3. Check MongoDB Status:

Configure MongoDB:

Edit the MongoDB configuration file.
``````
sudo nano /etc/mongod.conf
``````

``````conf
# mongod.conf

# Where and how to store data.
storage:
  dbPath: /var/mongodb/dbfile

# Where to write logging data.
systemLog:
  destination: file
  logAppend: true
  path: /var/mongodb/logfile/mongod.log

# Network interfaces
net:
  port: 50433
  bindIp: 127.0.0.1

# How the process runs
processManagement:
  timeZoneInfo: /usr/share/zoneinfo
``````


Check the status of the MongoDB service

 ```bash
 systemctl status mongod.service
 ```

 In the net section, change the port value to your desired port (e.g., 27018).
 
## Conclusion
MongoDB 7.0.2 is now installed and configured as a standalone server on Ubuntu 20.04. Adjust paths and settings as needed for your specific setup.
