Independent: SQL Server Query Each Database
============================================

Description
-----------

The Independent: SQL Server Query Each Database test is used to check information stored in a database. It is often the case that applications store configuration settings in a database as opposed to a file. This test has been designed to enable those settings to be tested.

The sql57_object element is used by a sql57_test to define the specific database and query to be evaluated. Connection information is supplied allowing the tool to connect to the desired database and a query is supplied to call out the desired setting.

The sql57_state element contains two entities that are used to check the name of the specified field and the value associated with it.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**independent.sql57_sqlserver_query_each_database_v1**

+---------------------------------------+---------+--------------------------+
| Name                                  | Type    | Description              |
+=======================================+=========+==========================+
| sql                                   | string  | The sql entity defines a |
|                                       |         | query used to identify   |
|                                       |         | the object(s) to test    |
|                                       |         | against.                 |
+---------------------------------------+---------+--------------------------+
| version                               | string  | The version entity       |
|                                       |         | defines the specific     |
|                                       |         | version of the database  |
|                                       |         | engine to use. This is   |
|                                       |         | also important in        |
|                                       |         | determining the correct  |
|                                       |         | driver to use for        |
|                                       |         | establishing a           |
|                                       |         | connection.              |
+---------------------------------------+---------+--------------------------+
| exclude_system_db                     | boolean |                          |
+---------------------------------------+---------+--------------------------+
| check_existence                       | string  |                          |
+---------------------------------------+---------+--------------------------+

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values: 
  - all_exist 
  - any_exist 
  - at_least_one_exists 
  - none_exist 
  - only_one_exists

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Independent: SQL57 V2

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**independent.sql57_v2**

+---------------------------------------+---------+--------------------------+
| Name                                  | Type    | Description              |
+=======================================+=========+==========================+
| check                                 | string  | Defines how many items   |
|                                       |         | must evaluate to true    |
|                                       |         | for the entity to return |
|                                       |         | true.                    |
+---------------------------------------+---------+--------------------------+
| field_value                           | string  | A simple (number,        |
|                                       |         | string, or boolean)      |
|                                       |         | value to be used in      |
|                                       |         | determining the result,  |
|                                       |         | i.e. pass/fail.          |
+---------------------------------------+---------+--------------------------+
| field_value_datatype                  | string  | The datatype of the      |
|                                       |         | expected/required value. |
+---------------------------------------+---------+--------------------------+
| field_name                            | string  | The name of the field to |
|                                       |         | which collected items    |
|                                       |         | are compared, restricted |
|                                       |         | to only lowercase        |
|                                       |         | letters.                 |
+---------------------------------------+---------+--------------------------+
| field_operation                       | string  | The optional operation   |
|                                       |         | attribute determines how |
|                                       |         | the individual entities  |
|                                       |         | should be evaluated (the |
|                                       |         | default operation is     |
|                                       |         | ‘equals’).               |
+---------------------------------------+---------+--------------------------+

NOTE: The ``check`` parameter is governed by a constraint allowing only the following values:
  - all
  - at least one
  - none satisfy
  - only one

Generated Content
~~~~~~~~~~~~~~~~~

**independent.sql57_v2**

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
            <ae:parameter dt="string" name="sql">[sql.value]</ae:parameter>
            <ae:parameter dt="string" name="version">[version.value]</ae:parameter>
            <ae:parameter dt="boolean" name="exclude_system_db">[exclude_system_db.value]</ae:parameter>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="field_value">[field_value.value]</ae:parameter>
            <ae:parameter dt="string" name="field_value_datatype">[field_value_datatype.value]</ae:parameter>
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

For ``independent.sql57_sqlserver_query_each_database_v1`` artifacts,
the XCCDF check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
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
    <connection_string var_ref="oval:org.cisecurity.benchmarks:var:[ID]" />
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
    artifact-title: "[ARTIFACT-TITLE]"
    artifact:
      type: "[ARTIFACT-TYPE-NAME]"
      parameters:
        - parameter: 
            name: "sql"
            dt: "string"
            value: "[sql.value]"
        - parameter: 
            name: "version"
            dt: "string"
            value: "[version.value]"
        - parameter: 
            name: "exclude_system_db"
            dt: "boolean"
            value: "[exclude_system_db.value]"
        - parameter: 
            name: "check_existence"
            dt: "string"
            value: "[check_existence.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter: 
            name: "check"
            dt: "string"
            value: "[check.value]"
        - parameter: 
            name: "field_value"
            dt: "string"
            value: "[field_value.value]"
        - parameter: 
            name: "field_value_datatype"
            dt: "string"
            value: "[field_value_datatype.value]"
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
              "name": "exclude_system_db",
              "type": "boolean",
              "value": "[exclude_system_db.value]"
            }
          },
          {
            "parameter": {
              "name": "check_existence",
              "type": "string",
              "value": "[check_existence.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "check",
              "type": "string",
              "value": "[check.value]"
            }
          },
          {
            "parameter": {
              "name": "field_value",
              "type": "string",
              "value": "[field_value.value]"
            }
          },
          {
            "parameter": {
              "name": "field_value_datatype",
              "type": "string",
              "value": "[field_value_datatype.value]"
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