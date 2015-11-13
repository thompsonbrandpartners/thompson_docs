---
layout: post
title:  "Creating Databases"
date:   2015-11-13 13:52:54
categories: databases, rules
---

**This document advises on best practice for working with databases, from initial setup through to tracking changes with Git. It's important that we have naming conventions in order to provide consistency through the team and the wider business**

#### On this page:

* [Naming databases](#naming)
* [Naming database users](#usernaming)
* [Database user passwords](#passwords)
* [Table prefixing](#tables)
* [Exporting and tracking](#exporting)

{:#naming}
### Naming databases

When creating a new database, the naming convention is simple. Begin the name with the letters `db` to signify that we are dealing with a database file. Follow this with an abbreviation of the client or project name, such as `mmate` for MindMate, and finally add an abbreviation of the system that the website or application is running on. Each word should be separated by an underscore and should be in lowercase.

For example, if we need a new database for MindMate, and the website is going to be built on Wordpress, the name should be `db_mmate_wp`.

If the database is specifically for either a development or production environment then we should include either `_dev` or `_prod` on the end. If the database will be transferred between environments then don't add anything.

Other abbreviations might be:

* wp = WordPress
* lmnst = Lemonstand
* mgto = Magento

{:#usernaming}
### Naming database users

The naming convention for creating database users is equally as simple as for creating databases. We follow exactly the same principles, except we substitute `db` for `user`.

For example, if we need a new database user for MindMate, and the website is going to be built on Wordpress, the name should be `user_mmate_wp`.

If there are several types of user with different access, we should include the access level on the end. This descriptor should be obvious, but may vary from project to project.

{:#passwords}
### Database user passwords

As is the convention with all passwords, these should be random strings, at least 20 characters long including a mixture of uppercase and lowercase letters, with at least four numbers and without ambiguous symbols that may not be recognised by various systems.

{:#tables}
### Table prefixing

{:#exporting}
### Exporting and tracking



[tower]:    http://www.git-tower.com/
[tower-ignore]:    http://www.git-tower.com/help/mac/working-copy/ignore-files
[github]:   https://github.com/
[githubissues]: https://github.com/issues
