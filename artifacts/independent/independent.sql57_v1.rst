independent.sql57_v1
====================

Description
-----------

The independent.sql57_v1 is used to check information stored in a
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
| prepend_type                        | string      | Select 'string'  |
|                                     |             | if the prepend   |
|                                     |             | string is        |
|                                     |             | straight text to |
|                                     |             | be prepended to  |
|                                     |             | the result.      |
|                                     |             | Select 'SQL' if  |
|                                     |             | it is a query    |
|                                     |             | from which the   |
|                                     |             | result should be |
|                                     |             | prepended.       |
|                                     |             | Otherwise leave  |
|                                     |             | empty.           |
+-------------------------------------+-------------+------------------+
| append_type                         | string      | Select 'string'  |
|                                     |             | if the append    |
|                                     |             | string is        |
|                                     |             | straight text to |
|                                     |             | be appended to   |
|                                     |             | the result of    |
|                                     |             | the SQL query.   |
|                                     |             | Select 'SQL' if  |
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
value String Value to test.
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
| uread                               | string      | Determines       |
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

Generated Content
~~~~~~~~~~~~~~~~~

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION_NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[RECOMMENDATION TITLE]</ae:title>
        <ae:artifact type="[ARTIFACTTYPE NAME]">
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
        <ae:test type="[TESTTYPE NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
            <ae:parameter dt="string" name="value_data_type">[value_data_type.value]</ae:parameter>
            <ae:parameter dt="string" name="field_name">[field_name.value]</ae:parameter>
            <ae:parameter dt="string" name="field_operation">[field_operation.value]</ae:parameter>
          </ae:parameters>
        </ae:test>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``independent.sql57_v1`` artifacts, the xccdf:check looks like this.

::

  <check system='http://oval.mitre.org/XMLSchema/oval-definitions-5'>
    <check-export 
      export-name='oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]' 
      value-id='xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var' />
    <check-export 
      export-name='oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]' 
      value-id='xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var' />
    <check-content-ref 
      href='[BENCHMARK NAME]' 
      name='oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]' />
  </check>

OVAL
''''

Test

::

  <sql57_test
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]'
    check_existence='[check_existence.value]' 
    check='[check.value]' 
    comment='[RECOMMENDATION TITLE]'
    version='[version.value]'>
    <object object_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]' />
    <state state_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]' />
  </sql57_test>

Object

::

  <sql57_object 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
    comment='[RECOMMENDATION TITLE]'
    version='[version.value]'>
    <engine>[engine.value]</engine>
    <version>[version.value]</version>
    <connection_string var_ref='oval:org.cisecurity.benchmarks:var:[ID]' />
    <sql>[sql.value]</sql>
  </sql57_object>

State

::

  <sql57_state 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
    comment='[RECOMMENDATION TITLE]'
    version='[version.value]'>
    <result 
      datatype='[result.value]' 
      entity_check='[entity_check.value]'>
      <field 
        xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5' 
        name='[name.value]' 
        datatype='[datatype.value]'
        operation='[operation.value]'
        var_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]' />
    </result>
  </sql57_state>

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: [ARTIFACTTYPE NAME]
      parameters:
        - parameter: 
            name: engine
            type: string
            value: [engine.value]
        - parameter: 
            name: sql
            type: string
            value: [sql.value]
        - parameter: 
            name: version
            type: string
            value: [version.value]
        - parameter: 
            name: prepend_str
            type: string
            value: prepend_str.value]
        - parameter: 
            name: append_str
            type: string
            value: [append_str.value]
        - parameter: 
            name: prepend_type
            type: string
            value: [prepend_type.value]
        - parameter: 
            name: append_type
            type: string
            value: append_type.value]
    test:
      type: [TESTTYPE NAME]
      parameters:   
        - parameter: 
            name: check_existence
            type: string
            value: [check_existence.value]
        - parameter: 
            name: check
            type: string
            value: [check.value]
        - parameter: 
            name: value
            type: string
            value: value.value]
        - parameter: 
            name: value_data_type
            type: string
            value: [value_data_type.value]
        - parameter: 
            name: field_name
            type: string
            value: [field_name.value]
        - parameter: 
            name: field_operation
            type: string
            value: field_operation.value]

JSON
^^^^

::

    {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact-title": "[RECOMMENDATION TITLE]",
      "artifact": {
        "type": "[ARTIFACTTYPE NAME]",
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
        "type": "[TESTTYPE NAME]",
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