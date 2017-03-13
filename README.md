# MongoDB-Installation on Amazon Linux

## Configure the package management system (yum).

Create a /etc/yum.repos.d/mongodb-org-3.4.repo file so that you can install MongoDB directly, using yum.

Changed in version 3.0: MongoDB Linux packages are in a new repository beginning with 3.0.

*For the latest stable release of MongoDB*

Use the following repository file:

<pre><code>
[mongodb-org-3.4]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/amazon/2013.03/mongodb-org/3.4/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://www.mongodb.org/static/pgp/server-3.4.asc
</code></pre>

*For versions of MongoDB earlier than 3.0*


To install the packages from an earlier release series, such as 2.4 or 2.6, you can specify the release series in the repository configuration. For example, to restrict your system to the 2.6 release series, create a /etc/yum.repos.d/mongodb-org-2.6.repo file to hold the following configuration information for the MongoDB 2.6 repository:

<pre><code>
[mongodb-org-2.6]
name=MongoDB 2.6 Repository
baseurl=http://downloads-distro.mongodb.org/repo/redhat/os/x86_64/
gpgcheck=0
enabled=1
</code></pre>
You can find .repo files for each release in the repository itself. Remember that odd-numbered minor release versions (e.g. 2.5) are development versions and are unsuitable for production use.

## Install the MongoDB packages and associated tools.

To install the latest stable version of MongoDB, issue the following command:
<pre><code>
sudo yum install -y mongodb-org
</code></pre>
