independent.mysql_sql57_v1
==========================

Description
-----------

The independent.mysql_sql57_v1 is used to check information stored in a
database. It is often the case that applications store configuration
settings in a database as opposed to a file. This test has been designed
to enable those settings to be tested. It extends the standard TestType
as defined in the oval-definitions-schema and one should refer to the
TestType description for more information. The object element
references a wmi_object and the state element specifies the
metadata to check.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| engine                              | string      | The engine       |
|                                     |             | entity defines a |
|                                     |             | specific         |
|                                     |             | database engine. |
+-------------------------------------+-------------+------------------+
| sql                                 | string      | The sql entity   |
|                                     |             | defines a query  |
|                                     |             | used to identify |
|                                     |             | the object(s) to |
|                                     |             | test against.    |
+-------------------------------------+-------------+------------------+
| version                             | string      | The version      |
|                                     |             | entity defines   |
|                                     |             | the specific     |
|                                     |             | version of the   |
|                                     |             | database engine  |
|                                     |             | to use. This is  |
|                                     |             | also important   |
|                                     |             | in determining   |
|                                     |             | the correct      |
|                                     |             | driver to use    |
|                                     |             | for establishing |
|                                     |             | a connection.    |
+-------------------------------------+-------------+------------------+
| prepend_str                         | string      | String to be     |
|                                     |             | prepended to     |
|                                     |             | either the SQL   |
|                                     |             | query or the     |
|                                     |             | result of the    |
|                                     |             | SQL query. Leave |
|                                     |             | empty if no      |
|                                     |             | string is to be  |
|                                     |             | appended.        |
+-------------------------------------+-------------+------------------+
| append_str                          | string      | String to be     |
|                                     |             | appended to the  |
|                                     |             | result of the    |
|                                     |             | SQL query. Leave |
|                                     |             | empty if no      |
|                                     |             | string is to be  |
|                                     |             | appended.        |
+-------------------------------------+-------------+------------------+
| prepend_type                        | string      | Select ‘string’  |
|                                     |             | if the prepend   |
|                                     |             | string is        |
|                                     |             | straight text to |
|                                     |             | be prepended to  |
|                                     |             | the result.      |
|                                     |             | Select ‘SQL’ if  |
|                                     |             | it is a query    |
|                                     |             | from which the   |
|                                     |             | result should be |
|                                     |             | prepended.       |
|                                     |             | Otherwise leave  |
|                                     |             | empty.           |
+-------------------------------------+-------------+------------------+
| append_type                         | string      | Select ‘string’  |
|                                     |             | if the append    |
|                                     |             | string is        |
|                                     |             | straight text to |
|                                     |             | be appended to   |
|                                     |             | the result of    |
|                                     |             | the SQL query.   |
|                                     |             | Select ‘SQL’ if  |
|                                     |             | it is a query    |
|                                     |             | from which the   |
|                                     |             | result should be |
|                                     |             | appended to the  |
|                                     |             | result of the    |
|                                     |             | SQL query.       |
|                                     |             | Otherwise leave  |
|                                     |             | empty.           |
+-------------------------------------+-------------+------------------+

engine NOTE: This parameter is governed by a constraint allowing only
the following values: 
  - access 
  - db2 
  - cache 
  - firebird 
  - firstsql 
  - foxpro 
  - informix 
  - ingres 
  - interbase 
  - lightbase 
  - maxdb 
  - monetdb 
  - mimer 
  - mysql 
  - oracle 
  - paradox 
  - pervasive 
  - postgre 
  - sqlbase 
  - sqlite 
  - sqlserver 
  - sybase

prepend_type NOTE: This parameter is governed by a constraint allowing
only the following values:
  - String
  - SQL

append_type NOTE: This parameter is governed by a constraint allowing
only the following values:
  - String
  - SQL

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - independent.sql57_v1
  - existence_test
  - SQL-Unix_File_or_Directory_Permissions_v1
  - SQL-Unix_File_or_Directory_Permissions_v2
  - SQL-Unix_File_or_Directory_Basename_Permissions_v2
  - SQL-Unix_File_or_Directory_Permissions_sql57_object_v2

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

independent.sql57_v1
^^^^^^^^^^^^^^^^^^^^

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| check_existence                     | string      | Specifies how    |
|                                     |             | many items in    |
|                                     |             | the set must     |
|                                     |             | exist for the    |
|                                     |             | test to evaluate |
|                                     |             | to true.         |
+-------------------------------------+-------------+------------------+
| check                               | string      | Defines how many |
|                                     |             | items must       |
|                                     |             | evaluate to true |
|                                     |             | for the entity   |
|                                     |             | to return true.  |
+-------------------------------------+-------------+------------------+
| value                               | string      | A simple         |
|                                     |             | (number, string, |
|                                     |             | or boolean)      |
|                                     |             | value to be used |
|                                     |             | in determining   |
|                                     |             | the result, i.e. |
|                                     |             | pass/fail.       |
+-------------------------------------+-------------+------------------+
| value_data_type                     | string      | The optional     |
|                                     |             | datatype         |
|                                     |             | attribute        |
|                                     |             | specifies how    |
|                                     |             | the given        |
|                                     |             | operation should |
|                                     |             | be applied to    |
|                                     |             | the data.        |
+-------------------------------------+-------------+------------------+
| field_name                          | string      | A string         |
|                                     |             | restricted to    |
|                                     |             | disallow upper   |
|                                     |             | case characters. |
+-------------------------------------+-------------+------------------+
| field_operation                     | string      | The optional     |
|                                     |             | operation        |
|                                     |             | attribute        |
|                                     |             | determines how   |
|                                     |             | the individual   |
|                                     |             | entities should  |
|                                     |             | be evaluated     |
|                                     |             | (the default     |
|                                     |             | operation is     |
|                                     |             | 'equals').       |
+-------------------------------------+-------------+------------------+

check_existence NOTE: This parameter is governed by a constraint
allowing only the following values: 
  - all_exist 
  - any_exist 
  - at_least_one_exists 
  - none_satisfy 
  - none_exist 
  - only_one_exists

check NOTE: This parameter is governed by a constraint allowing only the
following values: 
  - all 
  - at least one 
  - none satisfy 
  - only one

existence_test
^^^^^^^^^^^^^^

===== ====== ==============
Name  Type   Description
===== ====== ==============
value string Value to test.
===== ====== ==============

SQL-Unix_File_or_Directory_Permissions_v1
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| username                            | string      | The name of the  |
|                                     |             | user that owns   |
|                                     |             | the file or      |
|                                     |             | directory.       |
+-------------------------------------+-------------+------------------+
| group                               | string      | The name of the  |
|                                     |             | group that owns  |
|                                     |             | the file or      |
|                                     |             | directory.       |
+-------------------------------------+-------------+------------------+
| uread                               | boolean     | Determines       |
|                                     |             | whether the user |
|                                     |             | that owns the    |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | read the         |
|                                     |             | contents of it.  |
+-------------------------------------+-------------+------------------+
| uwrite                              | boolean     | Determines       |
|                                     |             | whether the user |
|                                     |             | that owns the    |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | write to it.     |
+-------------------------------------+-------------+------------------+
| uexec                               | boolean     | Determines       |
|                                     |             | whether the user |
|                                     |             | that owns the    |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | execute the file |
|                                     |             | or change into   |
|                                     |             | the directory.   |
+-------------------------------------+-------------+------------------+
| gread                               | boolean     | Determines       |
|                                     |             | whether the      |
|                                     |             | group that owns  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | read the content |
|                                     |             | of it.           |
+-------------------------------------+-------------+------------------+
| gwrite                              | boolean     | Determines       |
|                                     |             | whether the      |
|                                     |             | group that owns  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | write to it.     |
+-------------------------------------+-------------+------------------+
| gexec                               | boolean     | Determines       |
|                                     |             | whether the      |
|                                     |             | group that owns  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | execute the file |
|                                     |             | or change into   |
|                                     |             | the directory.   |
+-------------------------------------+-------------+------------------+
| oread                               | boolean     | Determines       |
|                                     |             | whether other    |
|                                     |             | users/groups     |
|                                     |             | that do not own  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | are permitted to |
|                                     |             | read the         |
|                                     |             | contents of it.  |
+-------------------------------------+-------------+------------------+
| owrite                              | boolean     | Determines       |
|                                     |             | whether other    |
|                                     |             | users/groups     |
|                                     |             | that do not own  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | are permitted to |
|                                     |             | write to it.     |
+-------------------------------------+-------------+------------------+
| oexec                               | boolean     | Determines       |
|                                     |             | whether other    |
|                                     |             | users/groups     |
|                                     |             | that do not own  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | are permitted to |
|                                     |             | execute the file |
|                                     |             | or change into   |
|                                     |             | the directory.   |
+-------------------------------------+-------------+------------------+
| dir_only                            | boolean     | If this is       |
|                                     |             | checking a       |
|                                     |             | directory        |
|                                     |             | permissions and  |
|                                     |             | no file within a |
|                                     |             | directory then   |
|                                     |             | this should be   |
|                                     |             | set to true.     |
+-------------------------------------+-------------+------------------+

SQL-Unix_File_or_Directory_Permissions_v2
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| username                            | string      | The name of the  |
|                                     |             | user that owns   |
|                                     |             | the file or      |
|                                     |             | directory.       |
+-------------------------------------+-------------+------------------+
| group                               | string      | The name of the  |
|                                     |             | group that owns  |
|                                     |             | the file or      |
|                                     |             | directory.       |
+-------------------------------------+-------------+------------------+
| uread                               | string      | Determines       |
|                                     |             | whether the user |
|                                     |             | that owns the    |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | read the         |
|                                     |             | contents of it.  |
+-------------------------------------+-------------+------------------+
| uwrite                              | string      | Determines       |
|                                     |             | whether the user |
|                                     |             | that owns the    |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | write to it.     |
+-------------------------------------+-------------+------------------+
| uexec                               | string      | Determines       |
|                                     |             | whether the user |
|                                     |             | that owns the    |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | execute the file |
|                                     |             | or change into   |
|                                     |             | the directory.   |
+-------------------------------------+-------------+------------------+
| gread                               | string      | Determines       |
|                                     |             | whether the      |
|                                     |             | group that owns  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | read the content |
|                                     |             | of it.           |
+-------------------------------------+-------------+------------------+
| gwrite                              | string      | Determines       |
|                                     |             | whether the      |
|                                     |             | group that owns  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | write to it.     |
+-------------------------------------+-------------+------------------+
| gexec                               | string      | Determines       |
|                                     |             | whether the      |
|                                     |             | group that owns  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | execute the file |
|                                     |             | or change into   |
|                                     |             | the directory.   |
+-------------------------------------+-------------+------------------+
| oread                               | string      | Determines       |
|                                     |             | whether other    |
|                                     |             | users/groups     |
|                                     |             | that do not own  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | are permitted to |
|                                     |             | read the         |
|                                     |             | contents of it.  |
+-------------------------------------+-------------+------------------+
| owrite                              | string      | Determines       |
|                                     |             | whether other    |
|                                     |             | users/groups     |
|                                     |             | that do not own  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | are permitted to |
|                                     |             | write to it.     |
+-------------------------------------+-------------+------------------+
| oexec                               | string      | Determines       |
|                                     |             | whether other    |
|                                     |             | users/groups     |
|                                     |             | that do not own  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | are permitted to |
|                                     |             | execute the file |
|                                     |             | or change into   |
|                                     |             | the directory.   |
+-------------------------------------+-------------+------------------+
| dir_only                            | boolean     | If this is       |
|                                     |             | checking a       |
|                                     |             | directory        |
|                                     |             | permissions and  |
|                                     |             | no file within a |
|                                     |             | directory then   |
|                                     |             | this should be   |
|                                     |             | set to true.     |
+-------------------------------------+-------------+------------------+

uread NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

uwrite NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

uexec NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

gread NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

gwrite NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

gexec NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

oread NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

owrite NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

oexec NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

oexec NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

SQL-Unix_File_or_Directory_Basename_Permissions_v2
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| username                            | string      | The name of the  |
|                                     |             | user that owns   |
|                                     |             | the file or      |
|                                     |             | directory.       |
+-------------------------------------+-------------+------------------+
| group                               | string      | The name of the  |
|                                     |             | group that owns  |
|                                     |             | the file or      |
|                                     |             | directory.       |
+-------------------------------------+-------------+------------------+
| uread                               | string      | Determines       |
|                                     |             | whether the user |
|                                     |             | that owns the    |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | read the         |
|                                     |             | contents of it.  |
+-------------------------------------+-------------+------------------+
| uwrite                              | string      | Determines       |
|                                     |             | whether the user |
|                                     |             | that owns the    |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | write to it.     |
+-------------------------------------+-------------+------------------+
| uexec                               | string      | Determines       |
|                                     |             | whether the user |
|                                     |             | that owns the    |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | execute the file |
|                                     |             | or change into   |
|                                     |             | the directory.   |
+-------------------------------------+-------------+------------------+
| gread                               | string      | Determines       |
|                                     |             | whether the      |
|                                     |             | group that owns  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | read the content |
|                                     |             | of it.           |
+-------------------------------------+-------------+------------------+
| gwrite                              | string      | Determines       |
|                                     |             | whether the      |
|                                     |             | group that owns  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | write to it.     |
+-------------------------------------+-------------+------------------+
| gexec                               | string      | Determines       |
|                                     |             | whether the      |
|                                     |             | group that owns  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | execute the file |
|                                     |             | or change into   |
|                                     |             | the directory.   |
+-------------------------------------+-------------+------------------+
| oread                               | string      | Determines       |
|                                     |             | whether other    |
|                                     |             | users/groups     |
|                                     |             | that do not own  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | are permitted to |
|                                     |             | read the         |
|                                     |             | contents of it.  |
+-------------------------------------+-------------+------------------+
| owrite                              | string      | Determines       |
|                                     |             | whether other    |
|                                     |             | users/groups     |
|                                     |             | that do not own  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | are permitted to |
|                                     |             | write to it.     |
+-------------------------------------+-------------+------------------+
| oexec                               | string      | Determines       |
|                                     |             | whether other    |
|                                     |             | users/groups     |
|                                     |             | that do not own  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | are permitted to |
|                                     |             | execute the file |
|                                     |             | or change into   |
|                                     |             | the directory.   |
+-------------------------------------+-------------+------------------+
| dir_only                            | boolean     | If this is       |
|                                     |             | checking a       |
|                                     |             | directory        |
|                                     |             | permissions and  |
|                                     |             | no file within a |
|                                     |             | directory then   |
|                                     |             | this should be   |
|                                     |             | set to true.     |
+-------------------------------------+-------------+------------------+
| check_existence                     | string      | Defines how many |
|                                     |             | items should be  |
|                                     |             | collected        |
+-------------------------------------+-------------+------------------+
| check                               | string      | Defines how many |
|                                     |             | collected items  |
|                                     |             | must match the   |
|                                     |             | expected state   |
+-------------------------------------+-------------+------------------+

uread NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

uwrite NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

uexec NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

gread NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

gwrite NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

gexec NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

oread NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

owrite NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

oexec NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

oexec NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

check_existence NOTE: This parameter is governed by a constraint allowing only 
the following values: 
  - all_exist 
  - any_exist 
  - at_least_one_exists 
  - none_satisfy 
  - none_exist 
  - only_one_exists

check NOTE: This parameter is governed by a constraint allowing only the
following values: 
  - all 
  - at least one 
  - none satisfy 
  - only one

SQL-Unix_File_or_Directory_Permissions_sql57_object_v2
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| username                            | string      | The name of the  |
|                                     |             | user that owns   |
|                                     |             | the file or      |
|                                     |             | directory.       |
+-------------------------------------+-------------+------------------+
| group                               | string      | The name of the  |
|                                     |             | group that owns  |
|                                     |             | the file or      |
|                                     |             | directory.       |
+-------------------------------------+-------------+------------------+
| uread                               | string      | Determines       |
|                                     |             | whether the user |
|                                     |             | that owns the    |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | read the         |
|                                     |             | contents of it.  |
+-------------------------------------+-------------+------------------+
| uwrite                              | string      | Determines       |
|                                     |             | whether the user |
|                                     |             | that owns the    |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | write to it.     |
+-------------------------------------+-------------+------------------+
| uexec                               | string      | Determines       |
|                                     |             | whether the user |
|                                     |             | that owns the    |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | execute the file |
|                                     |             | or change into   |
|                                     |             | the directory.   |
+-------------------------------------+-------------+------------------+
| gread                               | string      | Determines       |
|                                     |             | whether the      |
|                                     |             | group that owns  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | read the content |
|                                     |             | of it.           |
+-------------------------------------+-------------+------------------+
| gwrite                              | string      | Determines       |
|                                     |             | whether the      |
|                                     |             | group that owns  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | write to it.     |
+-------------------------------------+-------------+------------------+
| gexec                               | string      | Determines       |
|                                     |             | whether the      |
|                                     |             | group that owns  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | execute the file |
|                                     |             | or change into   |
|                                     |             | the directory.   |
+-------------------------------------+-------------+------------------+
| oread                               | string      | Determines       |
|                                     |             | whether other    |
|                                     |             | users/groups     |
|                                     |             | that do not own  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | are permitted to |
|                                     |             | read the         |
|                                     |             | contents of it.  |
+-------------------------------------+-------------+------------------+
| owrite                              | string      | Determines       |
|                                     |             | whether other    |
|                                     |             | users/groups     |
|                                     |             | that do not own  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | are permitted to |
|                                     |             | write to it.     |
+-------------------------------------+-------------+------------------+
| oexec                               | string      | Determines       |
|                                     |             | whether other    |
|                                     |             | users/groups     |
|                                     |             | that do not own  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | are permitted to |
|                                     |             | execute the file |
|                                     |             | or change into   |
|                                     |             | the directory.   |
+-------------------------------------+-------------+------------------+
| dir_only                            | boolean     | If this is       |
|                                     |             | checking a       |
|                                     |             | directory        |
|                                     |             | permissions and  |
|                                     |             | no file within a |
|                                     |             | directory then   |
|                                     |             | this should be   |
|                                     |             | set to true.     |
+-------------------------------------+-------------+------------------+
| check_existence                     | string      | Defines how many |
|                                     |             | items should be  |
|                                     |             | collected        |
+-------------------------------------+-------------+------------------+
| check                               | string      | Defines how many |
|                                     |             | collected items  |
|                                     |             | must match the   |
|                                     |             | expected state   |
+-------------------------------------+-------------+------------------+

uread NOTE: This parameter is governed by a constraint
allowing only the following values: 
  - NA
  - set
  - unset

uwrite NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

uexec NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

gread NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

gwrite NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

gexec NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

oread NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

owrite NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

oexec NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

oexec NOTE: This parameter is governed by a constraint
allowing only the following values:
  - NA
  - set
  - unset

check_existence NOTE: This parameter is governed by a constraint allowing only 
the following values: 
  - all_exist 
  - any_exist 
  - at_least_one_exists 
  - none_satisfy 
  - none_exist 
  - only_one_exists

check NOTE: This parameter is governed by a constraint allowing only the
following values: 
  - all 
  - at least one 
  - none satisfy 
  - only one

Generated Content
~~~~~~~~~~~~~~~~~

independent.sql57_v1

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[RECOMMENDATION-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACTTYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="engine">[engine.value]</ae:parameter>
            <ae:parameter dt="string" name="sql">[sql.value]</ae:parameter>
            <ae:parameter dt="string" name="version">[version.value]</ae:parameter>
            <ae:parameter dt="string" name="prepend_str"[prepend_str.value]</ae:parameter>
            <ae:parameter dt="string" name="append_str"[append_str.value]</ae:parameter>
            <ae:parameter dt="string" name="prepend_type"[prepend_type.value]</ae:parameter>
            <ae:parameter dt="string" name="append_type"[append_type.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TESTTYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
            <ae:parameter dt="string" name="value_data_type">[value_data_type.value]</ae:parameter>
            <ae:parameter dt="string" name="field_name">[field_name.value]</ae:parameter>
            <ae:parameter dt="string" name="field_operation">[field_operation.value]</ae:parameter>
          </ae:parameters>
        </ae:test>
        <ae:profiles>
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1" />
        </ae:profiles>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``independent.sql57_v1`` artifacts, the xccdf:check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity_value_[ARTIFACT-OVAL-ID]_var" />
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity_value_[ARTIFACT-OVAL-ID]_var " />
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity_value_[ARTIFACT-OVAL-ID]_var " />
    <check-content-ref 
      href="[BENCHMARK-TITLE]" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <sql57_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    check="[check.value]" 
    check_existence="[check_existence.value]" 
    comment="[RECOMMENDATION-TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
    version="[version.value]">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </sql57_test> 

Object

::

  <sql57_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    comment="[RECOMMENDATION-TITLE]"       
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    version="[version.value]">
    <engine>[engine.value]</engine>
    <version>[version.value]</version>
    <connection_string var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" />
    <sql>[sql.value]</sql>
  </sql57_object>

State

::

  <sql57_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    version="[version.value]">
    <result 
      datatype="[datatype.value]" 
      entity_check="[entity_check.value]">
      <field 
        xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5" 
        datatype="[datatype.value]" 
        name="[name.value]" 
        operation="[operation.value]" 
        var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    </result>
  </sql57_state>

External Variable

::

  <external_variable 
    comment="[RECOMMENDATION-TITLE]"
    datatype="[datatype.value]"  
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    version="[version.value]" />

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact-title: "[RECOMMENDATION-TITLE]"
    artifact:
      type: "[ARTIFACTTYPE-NAME]"
      parameters:
      - parameter: 
          name: "engine"
          dt: "string"
          value: "[engine.value]"
      - parameter: 
          name: "sql"
          dt: "string"
          value: "[sql.value]"
      - parameter: 
          name: "version"
          dt: "string"
          value: "[version.value]"
      - parameter: 
          name: "prepend_str"
          dt: "string"
          value: "[prepend_str.value]"
      - parameter: 
          name: "append_str"
          dt: "string"
          value: "[append_str.value]"
      - parameter: 
          name: "prepend_type"
          dt: "string"
          value: "[prepend_type.value]"
      - parameter: 
          name: "append_type"
          dt: "string"
          value: "[append_type.value]"
  test:
      type: "[TESTTYPE-NAME]"
      parameters:   
      - parameter: 
          name: "check_existence"
          dt: "string"
          value: "[check_existence.value]"
      - parameter: 
          name: "check"
          dt: "string"
          value: "[check.value]"
      - parameter: 
          name: "value"
          dt: "string"
          value: "[value.value]"
      - parameter: 
          name: "value_data_type"
          dt: "string"
          value: "[value_data_type.value]"
      - parameter: 
          name: "field_name"
          dt: "string"
          value: "[field_name.value]"
      - parameter: 
          name: "field_operation"
          dt: "string"
          value: "[field_operation.value]"

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact-title": "[RECOMMENDATION-TITLE]",
      "artifact": {
        "type": "[ARTIFACTTYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "engine",
              "type": "string",
              "value": "[engine.value]"
            }
          },
          {
            "parameter": {
              "name": "sql",
              "type": "string",
              "value": "[sql.value]"
            }
          },
          {
            "parameter": {
              "name": "version",
              "type": "string",
              "value": "[version.value]"
            }
          },
          {
            "parameter": {
              "name": "prepend_str",
              "type": "string",
              "value": "[prepend_str.value]"
            }
          },
          {
            "parameter": {
              "name": "append_str",
              "type": "string",
              "value": "[append_str.value]"
            }
          },
          {
            "parameter": {
              "name": "prepend_type",
              "type": "string",
              "value": "[prepend_type.value]"
            }
          },
          {
            "parameter": {
              "name": "append_type",
              "type": "string",
              "value": "[append_type.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TESTTYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "check_existence",
              "type": "string",
              "value": "[check_existence.value]"
            }
          },
          {
            "parameter": {
              "name": "check",
              "type": "string",
              "value": "[check.value]"
            }
          },
          {
            "parameter": {
              "name": "value",
              "type": "string",
              "value": "[value.value]"
            }
          },
          {
            "parameter": {
              "name": "value_data_type",
              "type": "string",
              "value": "[value_data_type.value]"
            }
          },
          {
            "parameter": {
              "name": "field_name",
              "type": "string",
              "value": "[field_name.value]"
            }
          },
          {
            "parameter": {
              "name": "field_operation",
              "type": "string",
              "value": "[field_operation.value]"
            }
          }
        ]
      }
    }
  }

Generated Content
~~~~~~~~~~~~~~~~~

existence_test

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[RECOMMENDATION-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACTTYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="engine">[engine.value]</ae:parameter>
            <ae:parameter dt="string" name="sql">[sql.value]</ae:parameter>
            <ae:parameter dt="string" name="version">[version.value]</ae:parameter>
            <ae:parameter dt="string" name="prepend_str"[prepend_str.value]</ae:parameter>
            <ae:parameter dt="string" name="append_str"[append_str.value]</ae:parameter>
            <ae:parameter dt="string" name="prepend_type"[prepend_type.value]</ae:parameter>
            <ae:parameter dt="string" name="append_type"[append_type.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TESTTYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
          </ae:parameters>
        </ae:test>
        <ae:profiles>
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1" />
        </ae:profiles>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``existence_test`` artifacts, the xccdf:check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-content-ref 
      href="[BENCHMARK-TITLE]" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <sql57_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    check="[check.value]" 
    check_existence="[check_existence.value]" 
    comment="[RECOMMENDATION-TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
    version="[version.value]">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"/>
  </sql57_test> 

Object

::

  <sql57_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    comment="[RECOMMENDATION-TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    version="[version.value]">
    <engine>[engine.value]</engine>
    <version>[version.value]</version>
    <connection_string var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" />
    <sql>[sql.value]</sql>
  </sql57_object>

State

::

  N/A 

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact_title: "[RECOMMENDATION-TITLE]" 
    artifact:
      type: "[ARTIFACTTYPE-NAME]"
      parameters:
      - parameter:
          name: "engine"
          dt: "string"
          value: "[engine.value]"
      - parameter:
          name: "sql"
          dt: "string"
          value: "[sql.value]"
      - parameter:
          name: "version"
          dt: "string"
          value: "[version.value]"
      - parameter:
          name: "prepend_str"
          dt: "string"
          value: "[prepend_str.value]"
      - parameter:
          name: "append_str"
          dt: "string"
          value: "[append_str.value]"
      - parameter:
          name: "prepend_type"
          dt: "string"
          value: "[prepend_type.value]"
      - parameter:
          name: "append_type"
          dt: "string"
          value: "[append_type.value]"
    test:
      type: "[TESTTYPE-NAME]"
      parameters:
      - parameter:
          name: "value"
          dt: "string"
          value: "[value.value]"

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact-title": "[RECOMMENDATION-TITLE]",
      "artifact": {
        "type": "[ARTIFACTTYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "engine",
              "dt": "string",
              "value": "[engine.value]"
            }
          },
          {
            "parameter": {
              "name": "sql",
              "dt": "string",
              "value": "[sql.value]"
            }
          },
          {
            "parameter": {
              "name": "version",
              "dt": "string",
              "value": "[version.value]"
            }
          },
          {
            "parameter": {
              "name": "prepend_str",
              "dt": "string",
              "value": "[prepend_str.value]"
            }
          },
          {
            "parameter": {
              "name": "append_str",
              "dt": "string",
              "value": "[append_str.value]"
            }
          },
          {
            "parameter": {
              "name": "prepend_type",
              "dt": "string",
              "value": "[prepend_type.value]"
            }
          },
          {
            "parameter": {
              "name": "append_type",
              "dt": "string",
              "value": "[append_type.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TESTTYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "value",
              "dt": "string",
              "value": "[value.value]"
            }
          }
        ]
      }
    }
  }

Generated Content
~~~~~~~~~~~~~~~~~

SQL-Unix_File_or_Directory_Permissions_v1

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[RECOMMENDATION-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACTTYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="engine">[engine.value]</ae:parameter>
            <ae:parameter dt="string" name="sql">[sql.value]</ae:parameter>
            <ae:parameter dt="string" name="version">[version.value]</ae:parameter>
            <ae:parameter dt="string" name="prepend_str">[prepend_str.value]</ae:parameter>
            <ae:parameter dt="string" name="append_str">[append_str.value]</ae:parameter>
            <ae:parameter dt="string" name="prepend_type">[prepend_type.value]</ae:parameter>
            <ae:parameter dt="string" name="append_type">[append_type.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TESTTYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="username">[username.value]</ae:parameter>
            <ae:parameter dt="string" name="group">[group.value]</ae:parameter>
            <ae:parameter dt="boolean" name="uread">[uread.value]</ae:parameter>
            <ae:parameter dt="boolean" name="uwrite">[uwrite.value]</ae:parameter>
            <ae:parameter dt="boolean" name="uexec">[uexec.value]</ae:parameter>
            <ae:parameter dt="boolean" name="gread">[gread.value]</ae:parameter>
            <ae:parameter dt="boolean" name="gwrite">[gwrite.value]</ae:parameter>
            <ae:parameter dt="boolean" name="gexec">[gexec.value]</ae:parameter>
            <ae:parameter dt="boolean" name="oread">[oread.value]</ae:parameter>
            <ae:parameter dt="boolean" name="owrite">[owrite.value]</ae:parameter>
            <ae:parameter dt="boolean" name="oexec">[oexec.value]</ae:parameter>
            <ae:parameter dt="boolean" name="dir_only">[dir_only.value]</ae:parameter>
          </ae:parameters>
        </ae:test>
        <ae:profiles>
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1"/>
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_2"/>
        </ae:profiles>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>
  
SCAP
^^^^

XCCDF
'''''

For ``SQL-Unix_File_or_Directory_Permissions_v1`` artifacts, the xccdf:check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity_value_[ARTIFACT-OVAL-ID]_var " />
    <check-content-ref 
      href="[BENCHMARK-TITLE]" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <file_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    check="[check.value]" 
    check_existence="[check_existence.value]" 
    comment="[RECOMMENDATION-TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
    version="[version.value]">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"> />
  </file_test> 

Test

::

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    comment="[RECOMMENDATION-TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    version="[version.value]">
    <path 
      datatype="[datatype.value]" 
      operation="[operation.value]" 
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <filename xsi:nil="[xsi:nil.value]" />
  </file_object>

State

::

  <file_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    comment="[RECOMMENDATION-TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    version="[version.value]">
    <group_id 
      datatype="[datatype.value]" 
      var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" />
    <user_id 
      datatype="[datatype.value]" 
      var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" />
    <uread datatype="boolean">[uread.value]</uread>
    <uwrite datatype="boolean">[uwrite.value]</uwrite>
    <uexec datatype="boolean">[uexec.value]</uexec>
    <gread datatype="boolean">[gread.value]</gread>
    <gwrite datatype="boolean">[gwrite.value]</gwrite>
    <gexec datatype="boolean">[gexec.value]</gexec>
    <oread datatype="boolean">[oread.value]</oread>
    <owrite datatype="boolean">[owrite.value]</owrite>
    <oexec datatype="boolean">[oexec.value]</oexec>
  </file_state>
  
Local Variable

::

  <local_variable 
    comment="[RECOMMENDATION-TITLE]" 
    datatype="[datatype.value]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    version="[version.value]">
    <object_component 
      item_field="[item_field.value]" 
      object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
      record_field="[record_field.value]" />
  </local_variable>

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact_title: "[RECOMMENDATION-TITLE]" 
    artifact:
      type: "[ARTIFACTTYPE-NAME]"
      parameters:
      - parameter:
          name: "engine"
          dt: "string"
          value: "[engine.value]"
      - parameter:
          name: "sql"
          dt: "string"
          value: "[sql.value]"
      - parameter:
          name: "version"
          dt: "string"
          value: "[version.value]"
      - parameter:
          name: "prepend_str"
          dt: "string"
          value: "[prepend_str.value]"
      - parameter:
          name: "append_str"
          dt: "string"
          value: "[append_str.value]"
      - parameter:
          name: "prepend_type"
          dt: "string"
          value: "[prepend_type.value]"
      - parameter:
          name: "append_type"
          dt: "string"
          value: "[append_type.value]"
    test:
      type: "[TESTTYPE-NAME]"
      parameters:
      - parameter:
          name: "username"
          dt: "string"
          value: "[username.value]"
      - parameter:
          name: "group"
          dt: "string"
          value: "[group.value]"
      - parameter:
          name: "uread"
          dt: "boolean"
          value: "[uread.value]"
      - parameter:
          name: "uwrite"
          dt: "boolean"
          value: "[uwrite.value]"
      - parameter:
          name: "uexec"
          dt: "boolean"
          value: "[uexec.value]"
      - parameter:
          name: "gread"
          dt: "boolean"
          value: "[gread.value]"
      - parameter:
          name: "gwrite"
          dt: "boolean"
          value: "[gwrite.value]"
      - parameter:
          name: "gexec"
          dt: "boolean"
          value: "[gexec.value]"
      - parameter:
          name: "oread"
          dt: "boolean"
          value: "[oread.value]"
      - parameter:
          name: "owrite"
          dt: "boolean"
          value: "[owrite.value]"
      - parameter:
          name: "oexec"
          dt: "boolean"
          value: "[oexec.value]"
      - parameter:
          name: "dir_only"
          dt: "boolean"
          value: "[dir_only.value]"

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact-title": "[RECOMMENDATION-TITLE]",
      "artifact": {
        "type": "[ARTIFACTTYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "engine",
              "dt": "string",
              "value": "[engine.value]"
            }
          },
          {
            "parameter": {
              "name": "sql",
              "dt": "string",
              "value": "[sql.value]"
            }
          },
          {
            "parameter": {
              "name": "version",
              "dt": "string",
              "value": "[version.value]"
            }
          },
          {
            "parameter": {
              "name": "prepend_str",
              "dt": "string",
              "value": "[prepend_str.value]"
            }
          },
          {
            "parameter": {
              "name": "append_str",
              "dt": "string",
              "value": "[append_str.value]"
            }
          },
          {
            "parameter": {
              "name": "prepend_type",
              "dt": "string",
              "value": "[prepend_type.value]"
            }
          },
          {
            "parameter": {
              "name": "append_type",
              "dt": "string",
              "value": "[append_type.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TESTTYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "username",
              "dt": "string",
              "value": "[username.value]"
            }
          },
          {
            "parameter": {
              "name": "group",
              "dt": "string",
              "value": "[group.value]"
            }
          },
          {
            "parameter": {
              "name": "uread",
              "dt": "boolean",
              "value": "[uread.value]"
            }
          },
          {
            "parameter": {
              "name": "uwrite",
              "dt": "boolean",
              "value": "[uwrite.value]"
            }
          },
          {
            "parameter": {
              "name": "uexec",
              "dt": "boolean",
              "value": "[uexec.value]"
            }
          },
          {
            "parameter": {
              "name": "gread",
              "dt": "boolean",
              "value": "[gread.value]"
            }
          },
          {
            "parameter": {
              "name": "gwrite",
              "dt": "boolean",
              "value": "[gwrite.value]"
            }
          },
          {
            "parameter": {
              "name": "gexec",
              "dt": "boolean",
              "value": "[gexec.value]"
            }
          },
          {
            "parameter": {
              "name": "oread",
              "dt": "boolean",
              "value": "[oread.value]"
            }
          },
          {
            "parameter": {
              "name": "owrite",
              "dt": "boolean",
              "value": "[owrite.value]"
            }
          },
          {
            "parameter": {
              "name": "oexec",
              "dt": "boolean",
              "value": "[oexec.value]"
            }
          },
          {
            "parameter": {
              "name": "dir_only",
              "dt": "boolean",
              "value": "[dir_only.value]"
            }
          }
        ]
      }
    }
  }

Generated Content
~~~~~~~~~~~~~~~~~

SQL-Unix_File_or_Directory_Permissions_v2

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[RECOMMENDATION-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACTTYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="engine">[engine.value]</ae:parameter>
            <ae:parameter dt="string" name="sql">[sql.value]</ae:parameter>
            <ae:parameter dt="string" name="version">[version.value]</ae:parameter>
            <ae:parameter dt="string" name="prepend_str">[prepend_str.value]</ae:parameter>
            <ae:parameter dt="string" name="append_str">[append_str.value]</ae:parameter>
            <ae:parameter dt="string" name="prepend_type">[prepend_type.value]</ae:parameter>
            <ae:parameter dt="string" name="append_type">[append_type.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TESTTYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="username">[username.value]</ae:parameter>
            <ae:parameter dt="string" name="group">[group.value]</ae:parameter>
            <ae:parameter dt="string" name="uread">[uread.value]</ae:parameter>
            <ae:parameter dt="string" name="uwrite">[uwrite.value]</ae:parameter>
            <ae:parameter dt="string" name="uexec">[uexec.value]</ae:parameter>
            <ae:parameter dt="string" name="gread">[gread.value]</ae:parameter>
            <ae:parameter dt="string" name="gwrite">[gwrite.value]</ae:parameter>
            <ae:parameter dt="string" name="gexec">[gexec.value]</ae:parameter>
            <ae:parameter dt="string" name="oread">[oread.value]</ae:parameter>
            <ae:parameter dt="string" name="owrite">[owrite.value]</ae:parameter>
            <ae:parameter dt="string" name="oexec">[oexec.value]</ae:parameter>
            <ae:parameter dt="boolean" name="dir_only">[dir_only.value]</ae:parameter>
          </ae:parameters>
        </ae:test>
        <ae:profiles>
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1"/>
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_2"/>
        </ae:profiles>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check> 

SCAP
^^^^

XCCDF
'''''

For ``SQL-Unix_File_or_Directory_Permissions_v2`` artifacts, the xccdf:check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity_value_[ARTIFACT-OVAL-ID]_var " />
    <check-content-ref 
      href="[BENCHMARK-TITLE]" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <file_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    check="[check.value]" 
    check_existence="[check_existence.value]" 
    comment="[RECOMMENDATION-TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
    version="[version.value]">  
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </file_test>  

Object

::

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    comment="[RECOMMENDATION-TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
    version="[version.value]">  
    <path 
      datatype="[datatype.value]" 
      operation="[operation.value]" 
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"  />
    <filename 
      datatype="[datatype.value]" 
      operation="[operation.value]" 
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </file_object>

State

::

  <file_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    comment="[RECOMMENDATION-TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
    version="[version.value]">  
    <group_id 
      datatype="[datatype.value]" 
      var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" />
    <user_id 
      datatype="[datatype.value]" 
      var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" />
    <uread datatype="boolean">[uread.value]</uread>
    <uwrite datatype="boolean">[uread.value]</uwrite>
    <uexec datatype="boolean">[uread.value]</uexec>
    <gread datatype="boolean">[uread.value]</gread>
    <gwrite datatype="boolean">[uread.value]</gwrite>
    <gexec datatype="boolean">[uread.value]</gexec>
    <oread datatype="boolean">[uread.value]</oread>
    <owrite datatype="boolean">[uread.value]</owrite>
    <oexec datatype="boolean">[uread.value]</oexec>
  </file_state>

Local Variable

::

  <local_variable 
    comment="[RECOMMENDATION-TITLE]" 
    datatype="[datatype.value]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
    version="[version.value]"> 
    <object_component 
      item_field="[item_field.value]" 
      object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
      record_field="[record_field.value]" />
  </local_variable>

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact_title: "[RECOMMENDATION-TITLE]" 
    artifact:
      type: "[ARTIFACTTYPE-NAME]"
      parameters:
      - parameter:
          name: "engine"
          dt: "string"
          value: "[engine.value]"
      - parameter:
          name: "sql"
          dt: "string"
          value: "[sql.value]"
      - parameter:
          name: "version"
          dt: "string"
          value: "[version.value]"
      - parameter:
          name: "prepend_str"
          dt: "string"
          value: "[prepend_str.value]"
      - parameter:
          name: "append_str"
          dt: "string"
          value: "[append_str.value]"
      - parameter:
          name: "prepend_type"
          dt: "string"
          value: "[prepend_type.value]"
      - parameter:
          name: "append_type"
          dt: "string"
          value: "[append_type.value]"
    test:
      type: "[TESTTYPE-NAME]"
      parameters:
      - parameter:
          name: "username"
          dt: "string"
          value: "[username.value]"
      - parameter:
          name: "group"
          dt: "string"
          value: "[group.value]"
      - parameter:
          name: "uread"
          dt: "string"
          value: "[uread.value]"
      - parameter:
          name: "uwrite"
          dt: "string"
          value: "[uwrite.value]"
      - parameter:
          name: "uexec"
          dt: "string"
          value: "[uexec.value]"
      - parameter:
          name: "gread"
          dt: "string"
          value: "[gread.value]"
      - parameter:
          name: "gwrite"
          dt: "string"
          value: "[gwrite.value]"
      - parameter:
          name: "gexec"
          dt: "string"
          value: "[gexec.value]"
      - parameter:
          name: "oread"
          dt: "string"
          value: "[oread.value]"
      - parameter:
          name: "owrite"
          dt: "string"
          value: "[owrite.value]"
      - parameter:
          name: "oexec"
          dt: "string"
          value: "[oexec.value]"
      - parameter:
          name: "dir_only"
          dt: "boolean"
          value: "[dir_only.value]"  

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact-title": "[RECOMMENDATION-TITLE]",
      "artifact": {
        "type": "[ARTIFACTTYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "engine",
              "dt": "string",
              "value": "[engine.value]"
            }
          },
          {
            "parameter": {
              "name": "sql",
              "dt": "string",
              "value": "[sql.value]"
            }
          },
          {
            "parameter": {
              "name": "version",
              "dt": "string",
              "value": "[version.value]"
            }
          },
          {
            "parameter": {
              "name": "prepend_str",
              "dt": "string",
              "value": "[prepend_str.value]"
            }
          },
          {
            "parameter": {
              "name": "append_str",
              "dt": "string",
              "value": "[append_str.value]"
            }
          },
          {
            "parameter": {
              "name": "prepend_type",
              "dt": "string",
              "value": "[prepend_type.value]"
            }
          },
          {
            "parameter": {
              "name": "append_type",
              "dt": "string",
              "value": "[append_type.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TESTTYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "username",
              "dt": "string",
              "value": "[username.value]"
            }
          },
          {
            "parameter": {
              "name": "group",
              "dt": "string",
              "value": "[group.value]"
            }
          },
          {
            "parameter": {
              "name": "uread",
              "dt": "string",
              "value": "[uread.value]"
            }
          },
          {
            "parameter": {
              "name": "uwrite",
              "dt": "string",
              "value": "[uwrite.value]"
            }
          },
          {
            "parameter": {
              "name": "uexec",
              "dt": "string",
              "value": "[uexec.value]"
            }
          },
          {
            "parameter": {
              "name": "gread",
              "dt": "string",
              "value": "[gread.value]"
            }
          },
          {
            "parameter": {
              "name": "gwrite",
              "dt": "string",
              "value": "[gwrite.value]"
            }
          },
          {
            "parameter": {
              "name": "gexec",
              "dt": "string",
              "value": "[gexec.value]"
            }
          },
          {
            "parameter": {
              "name": "oread",
              "dt": "string",
              "value": "[oread.value]"
            }
          },
          {
            "parameter": {
              "name": "owrite",
              "dt": "string",
              "value": "[owrite.value]"
            }
          },
          {
            "parameter": {
              "name": "oexec",
              "dt": "string",
              "value": "[oexec.value]"
            }
          },
          {
            "parameter": {
              "name": "dir_only",
              "dt": "boolean",
              "value": "[dir_only.value]"
            }
          }
        ]
      }
    }
  }           
     
Generated Content
~~~~~~~~~~~~~~~~~

SQL-Unix_File_or_Directory_Basename_Permissions_v2
SQL-Unix_File_or_Directory_Permissions_sql57_object_v2

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[RECOMMENDATION-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACTTYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="engine">[engine.value]</ae:parameter>
            <ae:parameter dt="string" name="sql">[sql.value]</ae:parameter>
            <ae:parameter dt="string" name="version">[version.value]</ae:parameter>
            <ae:parameter dt="string" name="prepend_str">[prepend_str.value]</ae:parameter>
            <ae:parameter dt="string" name="append_str">[append_str.value]</ae:parameter>
            <ae:parameter dt="string" name="prepend_type">[prepend_type.value]</ae:parameter>
            <ae:parameter dt="string" name="append_type">[append_type.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TESTTYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="username">[username.value]</ae:parameter>
            <ae:parameter dt="string" name="group">[group.value]</ae:parameter>
            <ae:parameter dt="string" name="uread">[uread.value]</ae:parameter>
            <ae:parameter dt="string" name="uwrite">[uwrite.value]</ae:parameter>
            <ae:parameter dt="string" name="uexec">[uexec.value]</ae:parameter>
            <ae:parameter dt="string" name="gread">[gread.value]</ae:parameter>
            <ae:parameter dt="string" name="gwrite">[gwrite.value]</ae:parameter>
            <ae:parameter dt="string" name="gexec">[gexec.value]</ae:parameter>
            <ae:parameter dt="string" name="oread">[oread.value]</ae:parameter>
            <ae:parameter dt="string" name="owrite">[owrite.value]</ae:parameter>
            <ae:parameter dt="string" name="oexec">[oexec.value]</ae:parameter>
            <ae:parameter dt="boolean" name="dir_only">[dir_only.value]</ae:parameter>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
          </ae:parameters>
        </ae:test>
        <ae:profiles>
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1" />
        </ae:profiles>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check> 

SCAP
^^^^

XCCDF
'''''

For ``SQL-Unix_File_or_Directory_Basename_Permissions_v2`` or ``SQL-Unix_File_or_Directory_Permissions_sql57_object_v2`` artifacts, the xccdf:check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity_value_[ARTIFACT-OVAL-ID]_var " />
    <check-content-ref 
      href="[BENCHMARK-TITLE]" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <file_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    check="[check.value]" 
    check_existence="[check_existence.value]" 
    comment="[RECOMMENDATION-TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
    version="[version.value]">  
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </file_test>  

Object

::

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    comment="[RECOMMENDATION-TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
    version="[version.value]">  
    <path 
      datatype="[datatype.value]" 
      operation="[operation.value]" 
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"  />
    <filename 
      datatype="[datatype.value]" 
      operation="[operation.value]" 
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </file_object>

State

::

  <file_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    comment="[RECOMMENDATION-TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    version="[version.value]">
    <group_id 
      datatype="[datatype.value]" 
      var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" />
    <user_id 
      datatype="[datatype.value]" 
      var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" />
    <uread datatype="boolean">[uread.value]</uread>
    <uwrite datatype="boolean">[uwrite.value]</uwrite>
    <uexec datatype="boolean">[uexec.value]</uexec>
    <gread datatype="boolean">[gread.value]</gread>
    <gwrite datatype="boolean">[gwrite.value]</gwrite>
    <gexec datatype="boolean">[gexec.value]</gexec>
    <oread datatype="boolean">[oread.value]</oread>
    <owrite datatype="boolean">[owrite.value]</owrite>
    <oexec datatype="boolean">[oexec.value]</oexec>
  </file_state>

Local Variable

::

  <local_variable 
    comment="[RECOMMENDATION-TITLE]" 
    datatype="[datatype.value]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
    version="[version.value]"> 
    <object_component 
      item_field="[item_field.value]" 
      object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
      record_field="[record_field.value]" />
  </local_variable>

YAML
^^^^

::

  - artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact_title: "[RECOMMENDATION-TITLE]" 
    artifact:
      type: "[ARTIFACTTYPE-NAME]"
      parameters:
      - parameter:
          name: "engine"
          dt: "string"
          value: "[engine.value]"
      - parameter:
          name: "sql"
          dt: "string"
          value: "[sql.value]"
      - parameter:
          name: "version"
          dt: "string"
          value: "[version.value]"
      - parameter:
          name: "prepend_str"
          dt: "string"
          value: "[prepend_str.value]"
      - parameter:
          name: "append_str"
          dt: "string"
          value: "[append_str.value]"
      - parameter:
          name: "prepend_type"
          dt: "string"
          value: "[prepend_type.value]"
      - parameter:
          name: "append_type"
          dt: "string"
          value: "[append_type.value]"
    test:
      type: "[TESTTYPE-NAME]"
      parameters:
      - parameter:
          name: "username"
          dt: "string"
          value: "[username.value]"
      - parameter:
          name: "group"
          dt: "string"
          value: "[group.value]"
      - parameter:
          name: "uread"
          dt: "string"
          value: "[uread.value]"
      - parameter:
          name: "uwrite"
          dt: "string"
          value: "[uwrite.value]"
      - parameter:
          name: "uexec"
          dt: "string"
          value: "[uexec.value]"
      - parameter:
          name: "gread"
          dt: "string"
          value: "[gread.value]"
      - parameter:
          name: "gwrite"
          dt: "string"
          value: "[gwrite.value]"
      - parameter:
          name: "gexec"
          dt: "string"
          value: "[gexec.value]"
      - parameter:
          name: "oread"
          dt: "string"
          value: "[oread.value]"
      - parameter:
          name: "owrite"
          dt: "string"
          value: "[owrite.value]"
      - parameter:
          name: "oexec"
          dt: "string"
          value: "[oexec.value]"
      - parameter:
          name: "dir_only"
          dt: "boolean"
          value: "[dir_only.value]"
      - parameter:
          name: "check_existence"
          dt: "string"
          value: "[check_existence.value]"
      - parameter:
          name: "check"
          dt: "string"
          value: "[check.value]"     

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact-title": "[RECOMMENDATION-TITLE]",
      "artifact": {
        "type": "[ARTIFACTTYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "engine",
              "dt": "string",
              "value": "[engine.value]"
            }
          },
          {
            "parameter": {
              "name": "sql",
              "dt": "string",
              "value": "[sql.value]"
            }
          },
          {
            "parameter": {
              "name": "version",
              "dt": "string",
              "value": "[version.value]"
            }
          },
          {
            "parameter": {
              "name": "prepend_str",
              "dt": "string",
              "value": "[prepend_str.value]"
            }
          },
          {
            "parameter": {
              "name": "append_str",
              "dt": "string",
              "value": "[append_str.value]"
            }
          },
          {
            "parameter": {
              "name": "prepend_type",
              "dt": "string",
              "value": "[prepend_type.value]"
            }
          },
          {
            "parameter": {
              "name": "append_type",
              "dt": "string",
              "value": "[append_type.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TESTTYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "username",
              "dt": "string",
              "value": "[username.value]"
            }
          },
          {
            "parameter": {
              "name": "group",
              "dt": "string",
              "value": "[group.value]"
            }
          },
          {
            "parameter": {
              "name": "uread",
              "dt": "string",
              "value": "[uread.value]"
            }
          },
          {
            "parameter": {
              "name": "uwrite",
              "dt": "string",
              "value": "[uwrite.value]"
            }
          },
          {
            "parameter": {
              "name": "uexec",
              "dt": "string",
              "value": "[uexec.value]"
            }
          },
          {
            "parameter": {
              "name": "gread",
              "dt": "string",
              "value": "[gread.value]"
            }
          },
          {
            "parameter": {
              "name": "gwrite",
              "dt": "string",
              "value": "[gwrite.value]"
            }
          },
          {
            "parameter": {
              "name": "gexec",
              "dt": "string",
              "value": "[gexec.value]"
            }
          },
          {
            "parameter": {
              "name": "oread",
              "dt": "string",
              "value": "[oread.value]"
            }
          },
          {
            "parameter": {
              "name": "owrite",
              "dt": "string",
              "value": "[owrite.value]"
            }
          },
          {
            "parameter": {
              "name": "oexec",
              "dt": "string",
              "value": "[oexec.value]"
            }
          },
          {
            "parameter": {
              "name": "dir_only",
              "dt": "boolean",
              "value": "[dir_only.value]"
            }
          },
          {
              "parameter": {
                  "name": "check_existence",
                  "dt": "string",
                  "value": "[check_existence.value]"
              }
          },
          {
              "parameter": {
                  "name": "check",
                  "dt": "string",
                  "value": "[check.value]"
              }
          }
        ]
      }
    }
  }           
    