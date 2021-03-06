---
title: "Remote Access PostgreSQL on Arch Linux"
categories: linux
---

- Install the **postgresql** package.

- Switch to the PostgreSQL user.
```shell
$ sudo -iu postgres
```

- Initialize database.
```shell
[postgres]$ initdb --locale=en_US.UTF-8 -E UTF8 -D _var_lib_postgres_data
```

- Start and enable the postgresql.service.
```shell
$ sudo systemctl start postgresql.server
$ sudo systemctl enable postgresql.server
```

- Access the database shell.
```shell
[postgres]$ psql postgres
```

- Configure PostgreSQL to be accessible from remote hosts. Edit the file **postgresql.conf**and replace this line

> listen_address=‘localhost’
> with:

> listen_addresses = '*'

- The defaults **pg_hba.conf** allow any local user to connect as any database user, add the following at the end, then save the file:

> host all all all md5

- Open port 5432 in the server firewall 

- Inside the psql shell you can give the DB user postgres a password:
```sql
ALTER USER postgres PASSWORD 'newPassword';
```

- The pgAdmin4 part will be easy.
