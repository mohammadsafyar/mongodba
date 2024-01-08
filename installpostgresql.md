# Installing PostgreSQL 16 on Ubuntu

## Prerequisites

##### Step 1: Add PostgreSQL Repository 
 we used local reposotory company 


 sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

sudo apt update

##### Step 2: Install PostgreSQL 16
Install PostgreSQL 16 and the necessary packages:

```bash
sudo apt install postgresql-16 postgresql-client-16  
```
####     Open the PostgreSQL Configuration File:
Open the PostgreSQL configuration file in a text editor. The default configuration file is usually located at /etc/postgresql/16/main/postgresql.conf

```bash
sudo nano /etc/postgresql/16/main/postgresql.conf
``````
Locate the Listen Addresses:
Look for the listen_addresses configuration parameter. By default, it may be commented out or set to listen on all available addresses ('*'). Uncomment the line and set it to listen only on localhost:
```conf
listen_addresses = 'localhost,IPserver'
````
###### Save and Close the File:
Save the changes and close the text editor.
 #####   Step 3: Start and Enable PostgreSQL
Start the PostgreSQL service and enable it to start on boot:
```bash
sudo systemctl start postgresql@16-main
sudo systemctl enable postgresql@16-main
```
##### Restart PostgreSQL:

After modifying the configuration, restart the PostgreSQL service for the changes to take effect:
```bash
sudo systemctl restart postgresql@16-main
```

