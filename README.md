# mysql-export
mysql-export is a tool for exporting a mysql database to an sql file using a portable and easy to read format. The output format will be UTF8 and all tables will be converted
to UTF8 even if one or more of the tables are in Latin1.

## Install
`wget https://raw.github.com/besherman/mysql-export/master/install --no-check-certificate -qO- | sudo bash`

The install script will download the shell script, put it in /usr/local/bin/mysql-export and make it executable.

## mysqldump
The script will call mysqldump with the following flags:
> --default-character-set utf8

Force the server to convert results to utf8.

> --skip-set-charset

Do not write SET NAMES statements.

> --hex-blob

Dump binary columns using hexadecimal notation. This is useful because if anyone tries to change the encoding of the file it will break.

> --single-transaction

Runs the entire dump in a single transation so that anything that changes
during the time that we dump the database will not be included in the
dump.

> --quick

Forces mysqldump to retrieve rows for a table from the server a row at a
time rather than retrieving the entire row set and buffering it in memory
before writing it out.
