##### Install PostgreSQL
Mac OS X,  I used the [Graphical Installer](http://www.postgresql.org/download/macosx/), recommended on the download page of PostgreSQL. It includes PostgreSQL, pgAdmin and the StackBuilder utility, for installation of additional packages.
 try to run
```
$ pg_config
```
If you get a not found error, you will need to first find the path of this command with:
```
$ sudo find / -name pg_config
```
This should be something like `/Library/PostgreSQL/9.3/bin`. You need to add it to the `$PATH` variable, so open the `.bash_profile` file and add the line:
```
export PATH=/Library/PostgreSQL/9.3/bin:$PATH
```
Restart your terminal and try again to type pg_config. 😉
##### Create a PostgreSQL Database
On mac, the command
```
$ which psql
```
should point to the Postgres app. And this other command should start the Postgres command line utility:
```
$ psql -h localhost
```
If this command rises an error like psql: FATAL: password authentication falied for user “username”, and you’re sure you have entered your password correctly, you have to enter psql using the postgres user:

```
$sudo -u postgres psql
```
On the other hand, if you get an error like psql: FATAL: database <user> does not exist, it might be because your package manager failed to create the proper database, see this [post](http://stackoverflow.com/a/17936043) for more info. To solve this problem, try:
```
$ createdb
$ psql -h localhost
(or $ sudo -u postgres psql)
```
Or
Connects as a role with same name as the local user, i.e. "postgres", to the database called "postgres" (1st argument to psql).
```
$sudo -u postgres psql postgres
```
Then delete database:
```
DROP DATABASE dbname_db;
```
create database
```
CREATE DATABASE dbname_db;
CREATE USER  username;
ALTER ROLE username SET client_encoding TO 'utf8';
ALTER ROLE username SET default_transaction_isolation TO 'read committed';
ALTER ROLE username SET timezone TO 'UTC’;
GRANT ALL PRIVILEGES ON DATABASE dbname_db TO username;
```
Now, you should be in the command line of Postgres. You can exit this environment by typing
```
\q
```
Similarly, you can type `\?` for more help, `\list` to list your databases and `\du` to list your users.

Next, we will create a new database for our project and a new user to whom you will give access to the database:
```
$ createdb dbname_db
(or $ sudo -u postgres createdb dbname_db)
$ psql
(or $ sudo -u postgres psql)
CREATE ROLE myusername WITH LOGIN PASSWORD 'mypassword';
GRANT ALL PRIVILEGES ON DATABASE dbname_db TO myusername;
ALTER USER myusername CREATEDB;
```
Where you should change `myusername` to the user’s name you want, and `mypassword` to whatever you want. And don’t forget the ; at the end of each statement! 
##### Install the PostgreSQL Django adapter, psycopg2
we need to install a PostgreSQL database adapter for Python: the [psycopg2](https://pypi.python.org/pypi/psycopg2) package:
```
$ pip install psycopg2
```
Finally, add it into your requirements/base.txt file, and install it into your working environments (testing and developing).


reference
http://www.marinamele.com/taskbuster-django-tutorial/install-and-configure-posgresql-for-django
