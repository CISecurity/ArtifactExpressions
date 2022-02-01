Oracle DB: (Non-)Multi-Tenant SQL57 v1
======================================

Description
-----------

The Oracle DB: (Non-)Multi-Tenant SQL57 v1 test is used to check information stored in a database. It is often the case that applications store configuration settings in a database as opposed to a file. This test has been designed to enable those settings to be tested.

The sql57_object element is used by a sql57_test to define the specific database and query to be evaluated. Connection information is supplied allowing the tool to connect to the desired database and a query is supplied to call out the desired setting.

The sql57_state element contains two entities that are used to check the name of the specified field and the value associated with it.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**oracledb_tenant.sql57_v1**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| non_multi_tenant_sql        | string  | This entity defines a query used   |
|                             |         | to identify the object(s) to test  |
|                             |         | against on a non-multi-tenant      |
|                             |         | Oracle DB.                         |
+-----------------------------+---------+------------------------------------+
| multi_tenant_sql            | string  | This entity defines a query used   |
|                             |         | to identify the object(s) to test  |
|                             |         | against on a multi-tenant          |
|                             |         |  Oracle DB.                        |
+-----------------------------+---------+------------------------------------+
| version                     | string  | This entity defines the specific   |
|                             |         | version of the engine to use.      |
|                             |         | This is also important in          |
|                             |         | determining the correct driver     |
|                             |         | to use for establishing a          |
|                             |         |  connection.                       |
+-----------------------------+---------+------------------------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Existence Test
  - Independent: SQL57

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**existence_test**

===== ====== ==============
Name  Type   Description
===== ====== ==============
value string Value to test.
===== ====== ==============

**independent.sql57_v1**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| check_existence             | string  | Specifies how many items in the    |
|                             |         | set must exist for the test to     |
|                             |         | evaluate to true.                  |
+-----------------------------+---------+------------------------------------+
| check                       | string  | Defines how many items must        |
|                             |         | evaluate to true for the entity    |
|                             |         | to return true.                    |
+-----------------------------+---------+------------------------------------+
| value                       | string  | A simple (number, string, or       |
|                             |         | boolean) value to be used in       |
|                             |         | determining the result, i.e.       |
|                             |         | pass/fail.                         |
+-----------------------------+---------+------------------------------------+
| value_data_type             | string  | The optional datatype attribute    |
|                             |         | specifies how the given operation  |
|                             |         | should be applied to the data.     |
+-----------------------------+---------+------------------------------------+
| field_name                  | string  | A string restricted to disallow    |
|                             |         | upper case characters.             |
+-----------------------------+---------+------------------------------------+
| field_operation             | string  | The optional operation attribute   |
|                             |         | determines how the individual      |
|                             |         | entities should be evaluated (the  |
|                             |         | default operation is 'equals').    |
+-----------------------------+---------+------------------------------------+

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
            <ae:parameter dt="string" name="non_multi_tenant_sql">[non_multi_tenant_sql.value]</ae:parameter>
            <ae:parameter dt="string" name="multi_tenant_sql">[multi_tenant_sql.value]</ae:parameter>
            <ae:parameter dt="string" name="version">[version.value]</ae:parameter>
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

For ``oracledb_tenant.sql57_v1`` ``existence_test`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this artifact.

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
""""

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

  <sql57_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]1"
    check_existence="[check_existence.value]"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1" />
  </sql57_test>  

Object

::

  <sql57_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <engine>oracle</engine>
    <version>[version.value]</version>
    <connection_string var_ref="oval:org.cisecurity.benchmarks:var:2000000" />
    <sql>[sql.value]</sql>
  </sql57_object>

  <sql57_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <engine>oracle</engine>
    <version>[version.value]</version>
    <connection_string var_ref="xccdf_org.cisecurity_value_jdbc.url" />
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
            name: "non_multi_tenant_sql"
            dt: "string"
            value: "[non_multi_tenant_sql.value]"
        - parameter:
            name: "multi_tenant_sql"
            dt: "string"
            value: "[multi_tenant_sql.value]"
        - parameter:
            name: "version"
            dt: "string"
            value: "[version.value]"
    test:
      type: "[TEST-TYPE-NAME]"
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
              "name": "non_multi_tenant_sql",
              "type": "string",
              "value": "[non_multi_tenant_sql.value]"
            }
          },
          {
            "parameter": {
              "name": "multi_tenant_sql",
              "type": "string",
              "value": "[multi_tenant_sql.value]"
            }
          },
          {
            "parameter": {
              "name": "version",
              "type": "string",
              "value": "[version.value"
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
              "type": "string",
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
            <ae:parameter dt="string" name="non_multi_tenant_sql">[non_multi_tenant_sql.value]</ae:parameter>
            <ae:parameter dt="string" name="multi_tenant_sql">[multi_tenant_sql.value]</ae:parameter>
            <ae:parameter dt="string" name="version">[version.value]</ae:parameter>
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

For ``oracledb_tenant.sql57_v1`` ``independent.sql57_v1`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    type="string"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``oracledb_tenant.sql57_v1`` ``independent.sql57_v1`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this Artifact. 

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]1_var" />
    <check-export 
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:2000000" 
      value-id="xccdf_org.cisecurity_value_jdbc.url" />
    <check-content-ref 
      href="[BENCHMARK-NAME]"
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

  <sql57_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]1"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </sql57_test>  

Object

::

  <sql57_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <engine>oracle</engine>
    <version>[version.value]</version>
    <connection_string var_ref="oval:org.cisecurity.benchmarks:var:2000000" />
    <sql>[sql.value]</sql>
  </sql57_object>

  <sql57_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <engine>oracle</engine>
    <version>[version.value]</version>
    <connection_string var_ref="xccdf_org.cisecurity_value_jdbc.url" />
    <sql>[sql.value]</sql>
  </sql57_object>


State

::

  <sql57_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <result 
      datatype="record"
      entity_check="all">
      <field 
        xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5"
        name="[name.value]"
        datatype="[datatype.value]"
        operation="[operation.value]"
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
            name: "non_multi_tenant_sql"
            dt: "string"
            value: "[non_multi_tenant_sql.value]"
        - parameter:
            name: "multi_tenant_sql"
            dt: "string"
            value: "[multi_tenant_sql.value]"
        - parameter:
            name: "version"
            dt: "string"
            value: "[version.value]"
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
              "name": "non_multi_tenant_sql",
              "type": "string",
              "value": "[non_multi_tenant_sql.value]"
            }
          },
          {
            "parameter": {
              "name": "multi_tenant_sql",
              "type": "string",
              "value": "[multi_tenant_sql.value]"
            }
          },
          {
            "parameter": {
              "name": "version",
              "type": "string",
              "value": "[version.value"
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