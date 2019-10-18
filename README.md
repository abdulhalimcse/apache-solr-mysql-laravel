# solr-mysql-laravel

[Apache Solr](https://lucene.apache.org/solr/) is the popular, blazing-fast, open source enterprise search platform built on Apache Lucene™. Solr provides full-text search, spell suggestions, custom document ordering and ranking, Snippet generation and highlighting. 

This tutorial will help you to install Apache Solr 8.2.0, import data from mysql and search using laravel 5/6 on CentOS 7 systems

## Step 1 – Prerequsities

Apache Solr 8 required Java 8 or greater to run. 

Install Java 11

## Step 2 - Install Apache Solr on CentOS 

Now you need to download solr from its official site or mirrors [Download](https://lucene.apache.org/solr/downloads.html). 
Choose your desired version. I chose 8.2.0 version. 

![Download Image](https://github.com/abdulhalimcse/solr-mysql-laravel/blob/master/img/solr-8.2.0-download-for-linx.PNG)

Click highlighted solr-8.2.0.tgz. 

![Donload Image 2](https://github.com/abdulhalimcse/solr-mysql-laravel/blob/master/img/click-after-taz-file.PNG)

Click highlighted link https://www-us.apache.org/dist/lucene/solr/8.2.0/solr-8.2.0.tgz and keep it in opt folder. 

OR 

```html

# cd /opt
# wget https://www-us.apache.org/dist/lucene/solr/8.2.0/solr-8.2.0.tgz  

```

https://www-us.apache.org/dist/lucene/solr/

After completing download, Please extract it.

```html
# tar -xvf solr-8.2.0.tgz
```

Open the limits.conf file

```html
# vi /etc/security/limits.conf
```
Add below text at last 

```html
solr soft nproc 65535
solr hard nproc 65535
solr soft nofile 65535
solr hard nofile 65535
```

Create a User and follow commond

```html
# useradd solr
# chown -R solr:solr solr-8.2.0
# su - solr
# cd /opt/solr-8.2.0/bin/
```

Create a solr collection or core

```html
# ./solr start
# ./solr status
# ./solr create -c testcollection -n data_driven_schema_configs
```

After creating collection

Sample output:

![CreatedCollectionSuccessfulMessage](https://github.com/abdulhalimcse/solr-mysql-laravel/blob/master/img/created-solr-successfull-message.PNG)


To access Solr Admin Panel from browser http://127.0.0.1:8983/solr/

![show solr admin panel](https://github.com/abdulhalimcse/solr-mysql-laravel/blob/master/img/solr-admin-panel-view.PNG)


## Step 3 - Importing/Indexing MySQL database in Solr using Data Import Handler 

