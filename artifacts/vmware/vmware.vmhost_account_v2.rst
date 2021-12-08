vmware:vmhost_account
=====================

Description
-----------

The vmware:vmhost_account test is used to verify one or more local ESXi user accounts have been created for the specified ESXi host, and that the specified user account has been granted shell access. 

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
|                                     |         | applicable.                |
+-------------------------------------+---------+----------------------------+
| account_name                        | string  | Set to NA if not           |
|                                     |         | applicable.                |
+-------------------------------------+---------+----------------------------+
| vmhost_name_operation               | string  | Comparison operation.      |
+-------------------------------------+---------+----------------------------+
| account_name_operation              | string  | Comparison operation.      |
+-------------------------------------+---------+----------------------------+

NOTE: The ``check_existence``  parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_exist
  - only_one_exists

NOTE: The ``account_name_operation`` parameter is governed by a constraint allowing only the following values:
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
| datatype                            | string  | Datatype.                  |
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
|                                     |         | applicable.                |
+-------------------------------------+---------+----------------------------+

NOTE: The ``check`` parameter is governed by a constraint allowing only the following values:
  - all
  - at least one
  - none satisfy
  - only one

NOTE: The ``operation`` parameter is governed by a constraint allowing only the following values:
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

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[RECOMMENDATION-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACT-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="gatekeeper">[gatekeeper.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
            <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
            <ae:parameter dt="boolean" name="enabled">[enabled.value]</ae:parameter>
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

For ``macos.gatekeeper_v1`` artifacts, the xccdf:check looks like this. There is no Value in the xccdf for this Artifact.

::

  <xccdf:check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <xccdf:check-content-ref 
      xmlns:ae="http://benchmarks.cisecurity.org/ae/0.5"
      xmlns:cpe="http://cpe.mitre.org/language/2.0"
      xmlns:ecl="http://cisecurity.org/check"
      href="[BENCHMARK-NAME]"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </xccdf:check>

OVAL
''''

Test

::

  <macos:gatekeeper_test 
    check="[check.value]"
    check_existence="[check_existence.value]"
    comment="[RECOMMENDATION-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    version="1">
    <macos:object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <macos:state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </macos:gatekeeper_test>

Object

::

  <macos:gatekeeper_object 
    comment="[RECOMMENDATION-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    version="1" />
   

State

::

  <macos:gatekeeper_state 
    comment="[RECOMMENDATION-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    version="1">
    <macos:enabled 
      datatype="[datatype.value]"
      operation="[operation.value]">
        [enabled.value]
    </macos:enabled>
  </macos:gatekeeper_state>  

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact-title: "[RECOMMENDATION-TITLE]"
    artifact:
      type: "[ARTIFACT-TYPE-NAME]"
      parameters:
        - parameter: 
            name: "gatekeeper"
            type: "string"
            value: "[gatekeeper.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "check_existence"
            type: "string"
            value: "[check_existence.value]"
        - parameter: 
            name: "check"
            type: "string"
            value: "[check.value]"
        - parameter:
            name: "operation"
            type: "string"
            value: "[operation.value]"
        - parameter: 
            name: "datatype"
            type: "string"
            value: "[datatype.value]"
        - parameter: 
            name: "enabled"
            type: "string"
            value: "[enabled.value]"

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact-title": "[RECOMMENDATION-TITLE]",
      "artifact": {
        "type": "[ARTIFACT-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "gatekeeper",
              "type": "string",
              "value": "[gatekeeper.value]"
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
              "name": "operation",
              "type": "string",
              "value": "[operation.value]"
            }
          },
          {
            "parameter": {
              "name": "datetype",
              "type": "string",
              "value": "[datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "enabled",
              "type": "string",
              "value": "[enabled.value]"
            }
          }
        ]
      }
    }
  }
