# Sublime Text 3 package for editing Oracle SQL and PL/SQL 

Language definition and execution utilities for Oracle PL/SQL files.

It is based on the bundle http://code.google.com/p/oracle-textmate-bundle/ 

## Install

### Install with Package Control

Install and configure [Package Control](https://packagecontrol.io/installation), if you haven't already done so, then:

- **CTRL+SHIFT+P** → **Package Control: Add Repository**
- Add the following URL: `https://github.com/frenchesco/OracleSQL.git`
- **CTRL+SHIFT+P** → **Package Control: Install Package** → **OracleSQL**

### Manual Install

- Download and extract package. Rename folder from *Oracle-master* to *OracleSQL* and place in `%APPDATA%\Sublime Text 3\Packages` for a normal installation or `SublimeText3\Data\Packages` for a portable installation.
- Install keymaps for the commands (see Example.sublime-keymap for my preferred keys)

## Build

To execute your PL/SQL source on your schema with ST3 Build command, you have to create a .sublime-build in your ST3 Users folder file containing something like::

```json
{
    "target": "oracle_exec",
    "selector": "source.plsql.oracle",
    "variants":
    [
        {
            "name": "SCHEMA 1",
            "dsn": "USERNAME/PASSWORD@DATABASENAME1"
        },
        {
            "name": "SCHEMA 2",
            "dsn": "USERNAME/PASSWORD@DATABASENAME2"
        }
    ]
}
```

You can also specify what build system to use for a specific project. Just go **CTRL+SHIFT+P** (Windows) or **CMD+SHIFT+P** (Mac) → **Project: Edit**

```json
{
    "folders":
    [
        {
            "follow_symlinks": true,
            "name": "PROJECTNAME",
            "path": "C:\\path\\to\\project"
        }
    ],
    "build_systems":
    [
        {
            "name": "SCHEMANAME",
            "target": "oracle_exec",
            "selector": "source.plsql.oracle, source.sql",
            "dsn": "USERNAME/PASSWORD@DATABASENAME"
        }
    ]
}
```

## Other Settings

The following will allow you to setup Key Mappings in Sublime Text for Switching between the Package Spec and Package Body in PL/SQL:

```json
    { "keys": ["alt+o"], "command": "switch_file", "args": {"extensions": ["cpp", "cxx", "cc", "c", "hpp", "hxx", "h", "ipp", "inl", "m", "mm", "pkb", "pks"]} },
```
