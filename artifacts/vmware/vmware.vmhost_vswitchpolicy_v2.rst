vmware:vmhost_vswitchpolicy
===========================

Description
-----------

The vmware:vmhost_vswitchpolicy test is used to verify the vSwitch Forged Transmits policy is set to reject forged transmissions.

The vmhost_vswitchpolicy_object element is used by a vmhost_vswitchpolicy_test to define the vmhost name and connection string, and name of the vSwitch to be evaluated.

The vmhost_service_state element holds information regarding the vSwitch Forged Transmits policy of the specified vSwitch. 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**vmware.vmhost_vswitchpolicy_v2**

+-------------------------------------+---------+----------------------------+
| Name                                | Type    | Description                |
+=====================================+=========+============================+
| check_existence                     | string  | Defines how many items     |
|                                     |         | should be collected.       |
+-------------------------------------+---------+----------------------------+
| vswitch_name                        | string  | The name of a target       |
|                                     |         | vswitch. Set to NA if not  |
|                                     |         | applicable. Cannot be      |
|                                     |         | blank.                     |
+-------------------------------------+---------+----------------------------+
| vmhost_name                         | string  | The ESXi host to scope     |
|                                     |         | results to. Set it NA if   |
|                                     |         | not applicable. Cannot be  |
|                                     |         | blank.                     |
+-------------------------------------+---------+----------------------------+
| vswitch_name_operation              | string  | Comparison operation.      |
+-------------------------------------+---------+----------------------------+
| vmhost_name_operation               | string  | Comparison operation.      |
+-------------------------------------+---------+----------------------------+

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_exist
  - only_one_exists

NOTE: The ``vswitch_name_operation`` and ``vmhost_name_operation`` parameters are governed by a constraint allowing only the following values:
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

  - vmware:vmhost_vswitchpolicy

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**vmware.vmhost_vswitchpolicy_v2**

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
| policy_name                         | string  | The vSwitch policy         |
|                                     |         | attribute to test.         |
+-------------------------------------+---------+----------------------------+
| policy_state                        | string  | The state of the vSwitch   |
|                                     |         | policy.                    |
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

NOTE: The ``policy_name`` parameter is governed by a constraint allowing only the following values:
  - mac_changes
  - promiscuous_mode 
  - forged_transmits

NOTE: The ``policy_state`` parameter is governed by a constraint allowing only the following values:
  - NA
  - Accept
  - Reject

Generated Content
~~~~~~~~~~~~~~~~~

**vmware.vmhost_vswitchpolicy_v2**

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
            <ae:parameter dt="string" name="vmhost_name_operation">[vmhost_name_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="vswitch_name">[vswitch_name.value]</ae:parameter>
            <ae:parameter dt="string" name="vswitch_name_operation">[vswitch_name_operation.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
            <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
            <ae:parameter dt="set" name="policy_name">[policy_name.value]</ae:parameter>
            <ae:parameter dt="string" name="policy_state">[policy_state.value]</ae:parameter>
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

For ``vmware.vmhost_vswitchpolicy_v2`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

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

  <vmhost_vswitchpolicy_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </vmhost_vswitchpolicy_test>

Object

::

  <vmhost_vswitchpolicy_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <connection_string var_ref="oval:org.cisecurity.benchmarks[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <vmhost_name operation="[operation.value]">
      [vmhost_name.value]
    </vmhost_name>
    <vswitch_name operation="[operation.value]">
      [vswitch_name.value]
    </vswitch_name>
  </vmhost_vswitchpolicy_object>      

State

::

  <vmhost_vswitchpolicy_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <[testPolicyName.value] 
      datatype="[datatype.value]"
      operation="[operation.value]">
        [testPolicyState.value]
    </[testPolicyName.value]>
  </vmhost_vswitchpolicy_state> 

Variable

::

  <external_variable 
    id="oval:org.cisecurity.benchmarks[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
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
            name: "vmhost_name_operation"
            dt: "string"
            value: "[vmhost_name_operation.value]"
        - parameter: 
            name: "vswitch_name"
            dt: "string"
            value: "[vswitch_name.value]"
        - parameter: 
            name: "vswitch_name_operation"
            dt: "string"
            value: "[vswitch_name_operation.value]"
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
            name: "policy_name"
            dt: "set"
            value: "[policy_name.value]"
        - parameter: 
            name: "policy_state"
            dt: "string"
            value: "[policy_state.value]"

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
              "name": "vmhost_name_operation",
              "dt": "string",
              "value": "[vmhost_name_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "vswitch_name",
              "dt": "string",
              "value": "[vswitch_name.value]"
            }
          },
          {
            "parameter": {
              "name": "vswitch_name_operation",
              "dt": "string",
              "value": "[vswitch_name_operation.value]"
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
              "name": "policy_name",
              "dt": "string",
              "value": "[policy_name.value]"
            }
          },
          {
            "parameter": {
              "name": "policy_state",
              "dt": "string",
              "value": "[policy_state.value]"
            }
          }
        ]
      }
    }
  }
