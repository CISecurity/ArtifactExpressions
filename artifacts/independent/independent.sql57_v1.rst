Independent: SQL57
==================

Description
-----------

The Independent: SQL57 test is used to check information stored in a database. It is often the case that applications store configuration settings in a database as opposed to a file. This test has been designed to enable those settings to be tested.

The sql57_object element is used by a sql57_test to define the specific database and query to be evaluated. Connection information is supplied allowing the tool to connect to the desired database and a query is supplied to call out the desired setting.

The sql57_state element contains two entities that are used to check the name of the specified field and the value associated with it.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**independent.sql57_v1**

+------------------------+---------+-----------------------------------------+
| Name                   | Type    | Description                             |
+========================+=========+=========================================+
| engine                 | string  | The engine entity defines a specific    |
|                        |         | database engine.                        |
+------------------------+---------+-----------------------------------------+
| sql                    | string  | The sql entity defines a query used to  |
|                        |         | identify the object(s) to test against. |
+------------------------+---------+-----------------------------------------+
| version                | string  | The version entity defines the specific |
|                        |         | version of the database engine to use.  |
|                        |         | This is also important in determining   |
|                        |         | the correct driver to use for           |
|                        |         | establishing a connection.              |
+------------------------+---------+-----------------------------------------+
| prepend_str            | string  | string to be prepended to either the    |
|                        |         | SQL query or the result of the SQL      |
|                        |         | query. Leave empty if no string is to   |
|                        |         | be appended.                            |
+------------------------+---------+-----------------------------------------+
| append_str             | string  | string to be appended to the result of  |
|                        |         | the SQL query. Leave empty if no string |
|                        |         | is to be appended.                      |
+------------------------+---------+-----------------------------------------+
| prepend_type           | string  | Select 'string' if the prepend string   |
|                        |         | is straight text to be prepended to     |
|                        |         | the result. Select 'SQL' if  it is a    |
|                        |         | query from which the result should be   |
|                        |         | prepended. Otherwise leave  empty.      |
+------------------------+---------+-----------------------------------------+
| append_type            | string  | Select 'string'  if the append string   |
|                        |         | is straight text to be appended to the  |
|                        |         | result of the SQL query. Select 'SQL'   |
|                        |         | if it is a query from which the result  |
|                        |         | should be appended to the  result of    |
|                        |         | the SQL query. Otherwise leave  empty.  |
+------------------------+---------+-----------------------------------------+

NOTE: The ``engine`` parameter is governed by a constraint allowing only the following values:  - access 
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

NOTE: The ``prepend_type`` and ``append_type`` parameters are governed by a constraint allowing only the following values:
  - String
  - SQL

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Existence Test
  - Independent: SQL57
  - SQL-Unix_File_or_Directory_Permissions_v1
  - SQL-Unix_File_or_Directory_Permissions_v2

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**existence_test**

===== ====== ==============
Name  Type   Description
===== ====== ==============
value string Value to test.
===== ====== ==============

**independent.sql57_v1**

+------------------------+---------+-----------------------------------------+
| Name                   | Type    | Description                             |
+========================+=========+=========================================+
| check_existence        | string  | Specifies how many items in the set     |
|                        |         | must exist for the test to evaluate to  |
|                        |         | true.                                   |
+------------------------+---------+-----------------------------------------+
| check                  | string  | Defines how many items must evaluate to |
|                        |         | true for the entity to return true.     |
+------------------------+---------+-----------------------------------------+
| value                  | string  | A simple (number, string, or boolean)   |
|                        |         | value to be used in determining the     |
|                        |         | result, i.e. pass/fail.                 |
+------------------------+---------+-----------------------------------------+
| value_data_type        | string  | The optional datatype attribute         |
|                        |         | specifies how the given operation       |
|                        |         | should be applied to the data.          |
+------------------------+---------+-----------------------------------------+
| field_name             | string  | A string restricted to disallow upper   |
|                        |         | case characters.                        |
+------------------------+---------+-----------------------------------------+
| field_operation        | string  | The optional operation attribute        |
|                        |         | determines how the individual entities  |
|                        |         | should be evaluated (the default        |
|                        |         | operation is 'equals').                 |
+------------------------+---------+-----------------------------------------+

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values: 
  - all_exist 
  - any_exist 
  - at_least_one_exists 
  - none_exist 
  - only_one_exists

NOTE: The ``check`` parameter is governed by a constraint allowing only the following values:
  - all 
  - at least one 
  - none satisfy 
  - only one

NOTE: The ``value_data_type`` parameter is governed by a constraint allowing only the following values:
	- boolean
	- float
	- int
	- string
	- version
	- set

NOTE: The ``field_operation`` parameter is governed by a constraint allowing only the following values:
  - equals
  - not equal
  - case insensitive equals
  - case insensitive not equal
  - greater than
  - less than
  - greater than or equal
  - less than or equal
  - bitwise and
  - bitwise or
  - pattern match
  - subset of
  - superset of

**SQL-Unix_File_or_Directory_Permissions_v1**

+------------------------+---------+-----------------------------------------+
| Name                   | Type    | Description                             |
+========================+=========+=========================================+
| username               | string  | The name of the user that owns the      |
|                        |         | file or directory.                      |
+------------------------+---------+-----------------------------------------+
| group                  | string  | The name of the group that owns the     |
|                        |         | file or directory.                      |
+------------------------+---------+-----------------------------------------+
| uread                  | boolean | Determines whether the user that owns   |
|                        |         | the file/directory is permitted to      |
|                        |         | read the contents of it.                |
+------------------------+---------+-----------------------------------------+
| uwrite                 | boolean | Determines whether the user that owns   |
|                        |         | the file/directory is permitted to      |
|                        |         | write to it.                            |
+------------------------+---------+-----------------------------------------+
| uexec                  | boolean | Determines whether the user that owns   |
|                        |         | the file/directory is permitted to      |
|                        |         | execute the file or change into the     |
|                        |         | directory.                              |
+------------------------+---------+-----------------------------------------+
| gread                  | boolean | Determines whether the group that owns  |
|                        |         | the file/directory is permitted to      |
|                        |         | read the content of it.                 |
+------------------------+---------+-----------------------------------------+
| gwrite                 | boolean | Determines whether the group that owns  |
|                        |         | the file/directory is permitted to      |
|                        |         | write to it.                            |
+------------------------+---------+-----------------------------------------+
| gexec                  | boolean | Determines whether the group that owns  |
|                        |         | the file/directory is permitted to      |
|                        |         | execute the file or change into the     |
|                        |         | directory.                              |
+------------------------+---------+-----------------------------------------+
| oread                  | boolean | Determines whether other users/groups   |
|                        |         | that do not own the file/directory are  |
|                        |         | permitted to read the contents of it.   |
+------------------------+---------+-----------------------------------------+
| owrite                 | boolean | Determines whether other users/groups   |
|                        |         | that do not own the file/directory are  |
|                        |         | permitted to write to it.               |
+------------------------+---------+-----------------------------------------+
| oexec                  | boolean | Determines whether other users/groups   |
|                        |         | that do not own the file/directory are  |
|                        |         | permitted to execute the file or        |
|                        |         | change into thedirectory.               |
+------------------------+---------+-----------------------------------------+
| dir_only               | boolean | If this is checking a directory         |
|                        |         | permissions and no file within a        |
|                        |         | directory then this should be set to    |
|                        |         | true.                                   |
+------------------------+---------+-----------------------------------------+

**SQL-Unix_File_or_Directory_Permissions_v2**

+------------------------+---------+-----------------------------------------+
| Name                   | Type    | Description                             |
+========================+=========+=========================================+
| username               | string  | The name of the user that owns the file |
|                        |         | or directory.                           |
+------------------------+---------+-----------------------------------------+
| group                  | string  | The name of the group that owns the     |
|                        |         | file or directory.                      |
+------------------------+---------+-----------------------------------------+
| uread                  | string  | Determines whether the user that owns   |
|                        |         | the file/directory is permitted to read |
|                        |         | the contents of it.                     |
+------------------------+---------+-----------------------------------------+
| uwrite                 | string  | Determines whether the user that owns   |
|                        |         | the file/directory is permitted to      |
|                        |         | write to it.                            |
+------------------------+---------+-----------------------------------------+
| uexec                  | string  | Determines whether the user that owns   |
|                        |         | the file/directory is permitted to      |
|                        |         | execute the file or change into the     |
|                        |         | directory.                              |
+------------------------+---------+-----------------------------------------+
| gread                  | string  | Determines whether the group that owns  |
|                        |         | the file/directory is permitted to      |
|                        |         | read the content of it.                 |
+------------------------+---------+-----------------------------------------+
| gwrite                 | string  | Determines whether the group that owns  |
|                        |         | the file/directory is permitted to      |
|                        |         | write to it.                            |
+------------------------+---------+-----------------------------------------+
| gexec                  | string  | Determines whether the group that owns  |
|                        |         | the file/directory is permitted to      |
|                        |         | execute the file or change into the     |
|                        |         | directory.                              |
+------------------------+---------+-----------------------------------------+
| oread                  | string  | Determines whether other users/groups   |
|                        |         | that do not own the file/directory are  |
|                        |         | permitted to read the contents of it.   |
+------------------------+---------+-----------------------------------------+
| owrite                 | string  | Determines whether other users/groups   |
|                        |         | that do not own the file/directory are  |
|                        |         | permitted to write to it.               |
+------------------------+---------+-----------------------------------------+
| oexec                  | string  | Determines whether other users/groups   |
|                        |         | that do not own the file/directory are  |
|                        |         | permitted to execute the file or change |
|                        |         | into the directory.                     |
+------------------------+---------+-----------------------------------------+
| dir_only               | boolean | If this is checking a directory         |
|                        |         | permissions and no file within a        |
|                        |         | directory then this should be set to    |
|                        |         | true.                                   |
+------------------------+---------+-----------------------------------------+

NOTE: The ``read``, ``write``, and ``exec`` parameters are governed by a constraint allowing only the following values:
  - NA
  - set
  - unset

Generated Content
~~~~~~~~~~~~~~~~~

**existence_test**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[ARTIFACT-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACT-TYPE-NAME]">
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
        <ae:test type="[TEST-TYPE-NAME]">
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

For ``independent.sql57_v1`` ``existence_test`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:2000000"
      value-id="xccdf_org.cisecurity_value_jdbc.url" />
    <check-content-ref
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <sql57_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"     
    check_existence="[check_existence.value]"
    check="all" 
    comment="[ARTIFACT-TITLE]" 
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </sql57_test> 

Object

::

  <sql57_object>
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"    
    comment="[ARTIFACT-TITLE]"  
    version="1">
    <engine>[engine.value]</engine>
    <version>[version.value]</version>
    <connection_string var_ref="oval:org.cisecurity.benchmarks:var:2000000" />
    <sql 
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]">
        [sql.value]
    </sql>
  </sql57_object>

State

::

  N/A

Variable

::

  <local_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    comment="[comment.value]"
    datatype="string"
    version="1">
    <literal_component datatype="string">[literal_component.value]</literal_component>
    <variable_component var_ref="oval:org.cisecurity.benchmarks:var:3000000" />
    <literal_component datatype="string">[literal_component.value]</literal_component>
  </local_variable>

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact_title: "[ARTIFACT-TITLE]" 
    artifact:
      type: "[ARTIFACT-TYPE-NAME]"
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
        - parameter: 
            name: "pattern"
            dt: "string"
            value: "[pattern.value]"
    test:
      type: "[TEST-TYPE-NAME]"
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
      "artifact-title": "[ARTIFACT-TITLE]",
      "artifact": {
        "type": "[ARTIFACT-TYPE-NAME]",
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
          },
          {
            "parameter": {
              "name": "pattern",
              "dt": "string",
              "value": "[pattern.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
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

**independent.sql57_v1**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[ARTIFACT-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACT-TYPE-NAME]">
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
        <ae:test type="[TEST-TYPE-NAME]">
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

For ``independent.sql57_v1`` ``independent.sql57_v1`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]1_var"
    type="[type.value]"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``independent.sql57_v1`` ``independent.sql57_v1`` artifacts, the XCCDF check looks like this.  

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]1_var" />
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:2000000"
      value-id="xccdf_org.cisecurity_value_jdbc.url" />         
    <check-content-ref
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <sql57_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"     
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[ARTIFACT-TITLE]" 
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </sql57_test> 

Object

::

  <sql57_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <engine>[engine.value]</engine>
    <version>[version.value]</version>
    <connection_string var_ref="oval:org.cisecurity.benchmarks:var:2000000" />
    <sql>[sql.value]</sql>
  </sql57_object>

State

::

  <sql57_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"   
    version="1">
    <result 
      datatype="record" 
      entity_check="all">
      <field 
        xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5" 
        name="[name.value]"
        operation="[operation.value]"
        datatype="[datatype.value]"
        var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    </result>
  </sql57_state>

Variable

::

  <external_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"  
    comment="[ARTIFACT-TITLE]"
    datatype="[datatype.value]"
    version="1" />

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact-title: "[ARTIFACT-TITLE]"
    artifact:
      type: "[ARTIFACT-TYPE-NAME]"
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
        type: "[TEST-TYPE-NAME]"            
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
      "artifact-title": "[ARTIFACT-TITLE]",
      "artifact": {
        "type": "[ARTIFACT-TYPE-NAME]",
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
        "type": "[TEST-TYPE-NAME]",
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

**SQL-Unix_File_or_Directory_Permissions_v1**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[ARTIFACT-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACT-TYPE-NAME]">
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
        <ae:test type="[TEST-TYPE-NAME]">
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
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1" />
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_2" />
        </ae:profiles>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>
  
SCAP
^^^^

XCCDF
'''''

For ``independent.sql57_v1`` ``SQL-Unix_File_or_Directory_Permissions_v1`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:2000000"
      value-id="xccdf_org.cisecurity_value_jdbc.url" />
    <check-content-ref
      href="[BENCHMARK-TITLE]-oval.xml" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <file_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"     
    check_existence="all_exist"    
    check="all" 
    comment="[ARTIFACT-TITLE]" 
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"> />
  </file_test> 

Test

::

  <file_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]" 
    version="1">
    <behaviors
      max_depth="0"
      recurse="symlinks and directories"
      recurse_direction="none"
      recurse_file_system="defined" />
    <filepath 
      datatype="string" 
      operation="equals" 
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </file_object>

  <sql57_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1"
    comment="[ARTIFACT-TITLE]" 
    version="1">
    <engine>[engine.value]</engine>
    <version>[version.value]</version>
    <connection_string
      var_ref="oval:org.cisecurity.benchmarks:var:2000000" />
    <sql>[sql.value]</sql>
  </sql57_object>

State

::

  <file_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[ARTIFACT-TITLE]" 
    version="1">
    <group_id 
      datatype="int"
      var_ref="oval:org.cisecurity.benchmarks:var:1000003" /> 
    <user_id 
      datatype="int" 
      var_ref="oval:org.cisecurity.benchmarks:var:1000002" />
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

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact_title: "[ARTIFACT-TITLE]" 
    artifact:
      type: "[ARTIFACT-TYPE-NAME]"
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
      type: "[TEST-TYPE-NAME]"
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
      "artifact-title": "[ARTIFACT-TITLE]",
      "artifact": {
        "type": "[ARTIFACT-TYPE-NAME]",
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
        "type": "[TEST-TYPE-NAME]",
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

**SQL-Unix_File_or_Directory_Permissions_v2**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[ARTIFACT-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACT-TYPE-NAME]">
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
        <ae:test type="[TEST-TYPE-NAME]">
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
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1" />
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_2" />
        </ae:profiles>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check> 

SCAP
^^^^

XCCDF
'''''

For ``independent.sql57_v1`` ``SQL-Unix_File_or_Directory_Permissions_v2`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this artifact.

::

  <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:2000000"
      value-id="xccdf_org.cisecurity_value_jdbc.url" />
    <check-content-ref
      href="[BENCHMARK-TITLE]-oval.xml" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <file_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="all_exist"    
    check="all" 
    comment="[ARTIFACT-TITLE]" 
    version="1">  
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </file_test>  

Object

::

  <file_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"  
    version="1">  
    <path 
      datatype="string" 
      operation="equals" 
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <filename xsi:nil="true" />
  </file_object>

State

::

  <file_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <group_id 
      datatype="int"
      var_ref="oval:org.cisecurity.benchmarks:var:1000003" />
    <user_id 
      datatype="int"
      var_ref="oval:org.cisecurity.benchmarks:var:1000002" />
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

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact_title: "[ARTIFACT-TITLE]"
    artifact:
      type: "[ARTIFACT-TYPE-NAME]"
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
      type: "[TEST-TYPE-NAME]"
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
      "artifact-title": "[ARTIFACT-TITLE]",
      "artifact": {
        "type": "[ARTIFACT-TYPE-NAME]",
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
        "type": "[TEST-TYPE-NAME]",
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