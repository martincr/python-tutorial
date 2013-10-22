https://docs.djangoproject.com/en/1.5/intro/tutorial01/

python -c "import django; print(django.get_version())"

django-admin.py startproject mysite

python manage.py runserver

http://127.0.0.1:8000/

edit mysite/settings.py

SQLite

https://docs.djangoproject.com/en/1.5/ref/settings/#std:setting-DATABASES

https://devcenter.heroku.com/articles/django
(virtualenv 1.9.1)[https://pypi.python.org/pypi/virtualenv]
mkdir hellodjango && cd hellodjango
sudo pip install virtualenv
virtualenv venv --distribute
source venv/bin/activate

pip install Django psycopg2 gunicorn dj-database-url
django-admin.py startproject hellodjango .

foreman start
http://0.0.0.0:5000

pip freeze > requirements.txt

.gitignore
git init
git add .
git commit -m "my django app"
heroku create
Creating warm-wave-5887... done, stack is cedar
http://warm-wave-5887.herokuapp.com/ | git@heroku.com:warm-wave-5887.git
Git remote heroku added
git push heroku master

heroku run python manage.py syncdb

http://www.moncefbelyamani.com/how-to-install-postgresql-on-a-mac-with-homebrew-and-lunchy/
brew update
brew install postgresql
initdb /usr/local/var/postgres -E utf8
gem install lunchy
mkdir -p ~/Library/LaunchAgents

# Build Notes

If builds of PostgreSQL 9 are failing and you have version 8.x installed,
you may need to remove the previous version first. See:
  https://github.com/mxcl/homebrew/issues/issue/2510

# Create/Upgrade a Database

If this is your first install, create a database with:
  initdb /usr/local/var/postgres -E utf8

To migrate existing data from a previous major version (pre-9.2) of PostgreSQL, see:
  http://www.postgresql.org/docs/9.2/static/upgrading.html

# Loading Extensions

By default, Homebrew builds all available Contrib extensions. To see a list of all
available extensions, from the psql command line, run:
  SELECT * FROM pg_available_extensions;

To load any of the extension names, navigate to the desired database and run:
  CREATE EXTENSION [extension name];

For instance, to load the tablefunc extension in the current database, run:
  CREATE EXTENSION tablefunc;

For more information on the CREATE EXTENSION command, see:
  http://www.postgresql.org/docs/9.2/static/sql-createextension.html
For more information on extensions, see:
  http://www.postgresql.org/docs/9.2/static/contrib.html

# Other

Some machines may require provisioning of shared memory:
  http://www.postgresql.org/docs/9.2/static/kernel-resources.html#SYSVIPC
When installing the postgres gem, including ARCHFLAGS is recommended:
  ARCHFLAGS="-arch x86_64" gem install pg

To install gems without sudo, see the Homebrew wiki.

To have launchd start postgresql at login:
    ln -sfv /usr/local/opt/postgresql/*.plist ~/Library/LaunchAgents
Then to load postgresql now:
    launchctl load ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist
Or, if you don't want/need launchctl, you can just run:
    pg_ctl -D /usr/local/var/postgres -l /usr/local/var/postgres/server.log start
==> Summary
🍺  /usr/local/Cellar/postgresql/9.2.4: 2831 files, 39M, built in 2.0 minutes

The files belonging to this database system will be owned by user "Martin".
This user must also own the server process.

The database cluster will be initialized with locale "en_US.UTF-8".
The default text search configuration will be set to "english".

creating directory /usr/local/var/postgres ... ok
creating subdirectories ... ok
selecting default max_connections ... 20
selecting default shared_buffers ... 1600kB
creating configuration files ... ok
creating template1 database in /usr/local/var/postgres/base/1 ... ok
initializing pg_authid ... ok
initializing dependencies ... ok
creating system views ... ok
loading system objects' descriptions ... ok
creating collations ... ok
creating conversions ... ok
creating dictionaries ... ok
setting privileges on built-in objects ... ok
creating information schema ... ok
loading PL/pgSQL server-side language ... ok
vacuuming database template1 ... ok
copying template1 to template0 ... ok
copying template1 to postgres ... ok

WARNING: enabling "trust" authentication for local connections
You can change this by editing pg_hba.conf or using the option -A, or
--auth-local and --auth-host, the next time you run initdb.

Success. You can now start the database server using:

    postgres -D /usr/local/var/postgres
or
    pg_ctl -D /usr/local/var/postgres -l logfile start

cp /usr/local/Cellar/postgresql/9.2.4/homebrew.mxcl.postgresql.plist ~/Library/LaunchAgents/

lunchy start postgres

ps auxwww | grep postgres

createuser martin

lunchy stop postgres

which psql
brew doctor

exec bash
touch .bash_profile
export PATH=/usr/local/bin:$PATH
source ~/.bash_profile

https://github.com/mxcl/homebrew/issues/5004
https://github.com/mxcl/homebrew/issues/13660
http://stackoverflow.com/questions/11335908/brew-doctor-says-error-usr-bin-occurs-before-usr-local-bin-how-to-fix
http://stackoverflow.com/questions/11025980/how-to-add-usr-local-bin-in-path-on-mac
http://stackoverflow.com/questions/6770649/repairing-postgresql-after-upgrading-to-osx-10-7-lion?rq=1