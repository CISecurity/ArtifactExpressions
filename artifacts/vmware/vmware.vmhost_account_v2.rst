vmware:vmhost_account
=====================

Description
-----------

The vmware:vmhost_account test is used to verify one or more local ESXi user accounts have been created for the specified ESXi host, and that the specified user account has been granted shell access. 

The vmhost_account_object element is used by the vmhost_account_test to define the name and connection string of the vmhost, and the user account to be evaluated.

The vmhost_account_state element holds information regarding the role and shell access settings of the specified user account.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**vmware.vmhost_account_v2**

+-------------------------------------+---------+----------------------------+
| Name                                | Type    | Description                |
+=====================================+=========+============================+
| check_existence                     | string  | Defines how many items     |
|                                     |         | should be collected.       |
+-------------------------------------+---------+----------------------------+
| vmhost_name                         | string  | The name of the ESXi host  |
|                                     |         | to limit collection to.    |
|                                     |         | Set to NA if not           |
|                                     |         | applicable. Cannot be      |
|                                     |         | blank.                     |
+-------------------------------------+---------+----------------------------+
| account_name                        | string  | Set to NA if not           |
|                                     |         | applicable. Cannot be      |
|                                     |         | blank.                     |
+-------------------------------------+---------+----------------------------+
| vmhost_name_operation               | string  | Comparison operation.      |
+-------------------------------------+---------+----------------------------+
| account_name_operation              | string  | Comparison operation.      |
+-------------------------------------+---------+----------------------------+

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_exist
  - only_one_exists

NOTE: The ``vmhost_name_operation`` and ``account_name_operation`` parameters are governed by a constraint allowing only the following values:
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

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - vmware:vmhost_account

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**vmware.vmhost_account_v2**

+-------------------------------------+---------+----------------------------+
| Name                                | Type    | Description                |
+=====================================+=========+============================+
| check                               | string  | Defines how many collected |
|                                     |         | items must match the       |
|                                     |         | expected state.            |
+-------------------------------------+---------+----------------------------+
| operation                           | string  | Comparison operation.      |
+-------------------------------------+---------+----------------------------+
| datatype                            | string  | Data type.                 |
+-------------------------------------+---------+----------------------------+
| shell_access_enabled_operator       | string  | The test to perform on the |
|                                     |         | Shell Access Enabled       |
|                                     |         | field. Enter NA if not     |
|                                     |         | applicable.                |
+-------------------------------------+---------+----------------------------+
| shell_access_enabled                | boolean | Shell Access Enabled?      |
+-------------------------------------+---------+----------------------------+
| role_operator                       | string  | Comparison operation.      |
+-------------------------------------+---------+----------------------------+
| role                                | string  | Enter NA if not            |
|                                     |         | applicable.Cannot be       |
|                                     |         | blank.                     |
+-------------------------------------+---------+----------------------------+

NOTE: The ``check`` parameter is governed by a constraint allowing only the following values:
  - all
  - at least one
  - none satisfy
  - only one

NOTE: The ``operation``, ``shell_access_enabled_operator``, and ``role_operator`` parameters are governed by a constraint allowing only the following values:
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

NOTE: The ``datatype`` parameter is governed by a constraint allowing only the following values:
  - boolean
  - float
  - int
  - string
  - version
  - set

Generated Content
~~~~~~~~~~~~~~~~~

**vmware.vmhost_account_v2**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[ARTIFACT-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACT-TYPE-NAME]" />
          <ae:parameters>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
            <ae:parameter dt="string" name="vmhost_name">[vmhost_name.value]</ae:parameter>
            <ae:parameter dt="string" name="account_name">[account_name.value]</ae:parameter>
            <ae:parameter dt="string" name="vmhost_name_operation">[vmhost_name_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="account_name_operation">[account_name_operation.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
            <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
            <ae:parameter dt="string" name="shell_access_enabled_operator">[shell_access_enabled_operator.value]</ae:parameter>
             <ae:parameter dt="boolean" name="shell_access_enabled">[shell_access_enabled.value]</ae:parameter>
            <ae:parameter dt="string" name="role_operator">[role_operator.value]</ae:parameter>
            <ae:parameter dt="string" name="role">[role.value]</ae:parameter>
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

For ``vmware.vmhost_account_v2`` ``vmware.vmhost_account_v2`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:100000"
      value-id="xccdf_org.cisecurity.benchmarks_value_esxi.connection" />
    <check-content-ref 
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <vmhost_account_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </vmhost_account_test>

Object

::

  <vmhost_account_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <connection_string var_ref="oval:org.cisecurity.benchmarks:var:100000" />
    <vmhost_name operation="[operation.value]">[vmhost_name.value]</vmhost_name>
    <account_name operation="[operation.value]">[account_name.value]</account_name>
  </vmhost_account_object> 

State

::

  <vmhost_account_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <shell_access_enabled 
      datatype="boolean"
      operation="[operation.value]">
        [shell_access_enabled.value]
    </shell_access_enabled>
    <role 
      datatype="[datatype.value]"
      operation="[operation.value]">
        [role.value]
    </role>
  </vmhost_account_state>

Variable

::

  <external_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="boolean"
    version="1"
    comment="This value is used in Rule: [RECOMMENDATION-TITLE]" />

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
            name: "check_existence"
            dt: "string"
            value: "[check_existence.value]"
        - parameter: 
            name: "vmhost_name"
            dt: "string"
            value: "[vmhost_name.value]"
        - parameter: 
            name: "account_name"
            dt: "string"
            value: "[account_name.value]"
        - parameter: 
            name: "vmhost_name_operation"
            dt: "string"
            value: "[vmhost_name_operation.value]"
        - parameter: 
            name: "account_name_operation"
            dt: "string"
            value: "[account_name_operation.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter: 
            name: "check"
            dt: "string"
            value: "[check.value]"
        - parameter:
            name: "operation"
            dt: "string"
            value: "[operation.value]"
        - parameter: 
            name: "datatype"
            dt: "string"
            value: "[datatype.value]"
        - parameter: 
            name: "shell_access_enabled_operator"
            dt: "string"
            value: "[shell_access_enabled_operator.value]"
        - parameter: 
            name: "shell_access_enabled"
            dt: "boolean"
            value: "[shell_access_enabled.value]"
        - parameter:
            name: "role_operator"
            dt: "string"
            value: "[role_operator.value]"
        - parameter: 
            name: "role"
            dt: "string"
            value: "[role.value]"

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
              "name": "check_existence",
              "dt": "string",
              "value": "[check_existence.value]"
            }
          },
          {
            "parameter": {
              "name": "vmhost_name",
              "dt": "string",
              "value": "[vmhost_name.value]"
            }
          },
          {
            "parameter": {
              "name": "account_name",
              "dt": "string",
              "value": "[account_name.value]"
            }
          },
          {
            "parameter": {
              "name": "vmhost_name_operation",
              "dt": "string",
              "value": "[vmhost_name_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "account_name_operation",
              "dt": "string",
              "value": "[account_name_operation.value]"
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
              "dt": "string",
              "value": "[check.value]"
            }
          },
          {
            "parameter": {
              "name": "operation",
              "dt": "string",
              "value": "[operation.value]"
            }
          },
          {
            "parameter": {
              "name": "datetype",
              "dt": "string",
              "value": "[datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "shell_access_enabled_operator",
              "dt": "string",
              "value": "[shell_access_enabled_operator.value]"
            }
          },
          {
            "parameter": {
              "name": "shell_access_enabled",
              "dt": "boolean",
              "value": "[shell_access_enabled.value]"
            }
          },
          {
            "parameter": {
              "name": "role_operator",
              "dt": "string",
              "value": "[role_operator.value]"
            }
          },
          {
            "parameter": {
              "name": "role",
              "dt": "string",
              "value": "[role.value]"
            }
          }
        ]
      }
    }
  }
