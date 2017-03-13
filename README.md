## MongoDB-Installation on Amazon Linux

### Configure the package management system (yum).

Create a /etc/yum.repos.d/mongodb-org-3.4.repo file so that you can install MongoDB directly, using yum.
Use the following repository file:

```
[mongodb-org-3.4]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/amazon/2013.03/mongodb-org/3.4/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://www.mongodb.org/static/pgp/server-3.4.asc
```
### Install the MongoDB packages and associated tools.

To install the latest stable version of MongoDB, issue the following command:
<pre><code>
sudo yum install -y mongodb-org
</code></pre>

## Run MongoDB Community Edition

The MongoDB instance stores its data files in /var/lib/mongo and its log files in /var/log/mongodb by default, and runs using the mongod user account. You can specify alternate log and data file directories in /etc/mongod.conf. See systemLog.path and storage.dbPath for additional information.

If you change the user that runs the MongoDB process, you must modify the access control rights to the /var/lib/mongo and /var/log/mongodb directories to give this user access to these directories.

### Start MongoDB.
```
sudo service mongod start
```
### Verify that MongoDB has started successfully
You can verify that the mongod process has started successfully by checking the contents of the log file at /var/log/mongodb/mongod.log for a line reading
```
[initandlisten] waiting for connections on port <port>
```
where <port> is the port configured in /etc/mongod.conf, 27017 by default.

You can optionally ensure that MongoDB will start following a system reboot by issuing the following command:
```
sudo chkconfig mongod on
```

### Stop MongoDB.
As needed, you can stop the mongod process by issuing the following command:
```
sudo service mongod stop
```
### Restart MongoDB.
You can restart the mongod process by issuing the following command:
```
sudo service mongod restart
```

You can follow the state of the process for errors or important messages by watching the output in the /var/log/mongodb/mongod.log file.
