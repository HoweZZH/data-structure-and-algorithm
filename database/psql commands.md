>**psql** is a terminal-based front-end to PostgreSQL. It enables you to type in queries interactively, issue them to PostgreSQL, and see the query results. Alternatively, input can be from a file.[1]

**Launch Interactive session**
`psql -h localhost -U postgres -d somedb`
connect to local database i.e.(username = `postgres`, database name = `postgres `)
`sudo -u postgres psql -d postgres`

**Connection options:**
```
 -h, --host=HOSTNAME database server host or socket directory
 -p, --port=PORT database server port number
 -U, --username=NAME connect as specified database user
 -W, --password force password prompt (should happen automatically)
 -e, --exit-on-error exit on error, default is to continue
 -d DBNAME some database
```
connect to database `dbname_db` with user name = `postgres`:
```
\c dbname_db postgres
```
change a user's password:
``` 
ALTER USER username WITH PASSWORD 'mypassword'; 
```
create db
```
CREATE DATABASE db_name;
```
grant privileges to user
```
GRANT ALL PRIVILEGES ON DATABASE db_name TO user_name;
```
##### reference:
[1]https://www.postgresql.org/docs/9.4/static/app-psql.html
[2]https://www.postgresql.org/docs/9.2/static/sql-alterrole.html
