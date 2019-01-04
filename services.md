# Backend services

Things like databases, webservers, etc. nice to have

## [PostgresQL](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-18-04)

Install:

```shell
sudo apt install postgresql postgresql-contrib
```

Set up user:

```shell
sudo -i -u postgres
psql
```

**TODO**

Set up Database:

(Include stuff like C-type for quick LIKE queries)

**TODO**

Add extensions???

## [MongoDB](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/)

Install:

```shell
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 9DA31620334BD75D9DCB49F368818C72E52529D4
sudo apt-add-repository "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.0 multiverse"
sudo apt update
sudo apt install mongodb-org
```

Configure (xfs and permissions to remove warnings):

**TODO**

Starting:
```shell
sudo service mongod start
sudo service mongod status
mongo
```