---
description: Learn how to install MySql on Ubuntu
---

# Install MySql on Ubuntu

**MySQL** is an open-source relational database management system (RDBMS) where data is organized into one or more data tables in which data types may be related to each other.

The reference version used in this tutorial is Ubuntu 20.04.

> Update system packages (recommneded)

```bash
$ sudo apt update
```

> Install the `mysql-server` package

```bash
$ sudo apt install mysql-server
```

> Configure the MySql server (using `sudo)`

```bash
$ sudo mysql_secure_installation
```

This command will take the user through a series of prompts where you can make some changes to your MySQL installation’s security options.

The most important step in this setup is when we are asked for the password of the MySql root user.

```bash
Please set the password for root here.

New password: ******
Re-enter new password: ******
```


## Links & Resources

* [MySql](https://dev.mysql.com/) - the official website
* [How to install MySql on Ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-20-04) - a complete tutorial provided by Digital Ocean
