---
title: "Remote Access PostgreSQL on Arch Linux"
categories: linux
---

1. Install the **postgresql** package.

2. Switch to the PostgreSQL user.
```shell
$ sudo -iu postgres
```

3. Initialize database.
```shell
[postgres]$ initdb --locale=en_US.UTF-8 -E UTF8 -D _var_lib_postgres_data
```

4. Start and enable the postgresql.service.
```shell
$ sudo systemctl start postgresql.server
$ sudo systemctl enable postgresql.server
```

5. Access the database shell.
```shell
[postgres]$ psql postgres
```

6. Configure PostgreSQL to be accessible from remote hosts. Edit the file **postgresql.conf**and replace this line

> listen_address=‘localhost’
> with:

> listen_addresses = '*'

7. The defaults **pg_hba.conf** allow any local user to connect as any database user, add the following at the end, then save the file:

> host all all all md5

8. Open port 5432 in the server firewall 

9. Inside the psql shell you can give the DB user postgres a password:
```sql
ALTER USER postgres PASSWORD 'newPassword';
```

10. The pgAdmin4 part will be easy.
