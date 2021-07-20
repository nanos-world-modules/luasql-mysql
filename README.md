# LuaSQL
http://keplerproject.github.io/luasql

LuaSQL is a simple interface from Lua to a DBMS. It enables a Lua program to:

    * Connect to ODBC, ADO, Oracle, MySQL, SQLite, Firebird and PostgreSQL databases; 
    * Execute arbitrary SQL statements;
    * Retrieve results in a row-by-row cursor fashion.

LuaSQL is free software and uses the same license as Lua 5.1. 


Source code for LuaSQL can be downloaded from its GitHub repository.

## Building the module

### Windows

Download MySQL ZIP archive: https://dev.mysql.com/downloads/mysql/8.0.html

```
mkdir build
cd build
cmake -DMYSQL_DIR="PATH_TO_MYSQL-8.0.26-winx64" ..
cmake --build . --config Release
```

```
Modules
  luasql
    mysql.dll
  libcrypto-1_1-x64.dll
  libmysql.dll
  libssl-1_1-x64.dll
```

`libcrypto-1_1-x64.dll`, `libmysql.dll` and `libssl-1_1-x64.dll` can be obtained out of the mysql sdk folder.

### Linux

Download MySQL ZIP archive for generic linux: https://dev.mysql.com/downloads/mysql/8.0.html

```
mkdir build
cd build
cmake -DMYSQL_DIR="PATH_TO_MYSQL-8.0.26-linux-glibc2.12-x86_64" ..
cmake --build . --config Release
```

```
Modules
  luasql
    mysql.so
```
