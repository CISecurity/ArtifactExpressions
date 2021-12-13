vmware:vm_advancedsetting
=========================

Description
-----------

The vmware:vm_advancedsetting test is used to verify the status of specified advanced settings in the virtual machine configuration file.

The vm_advancedsetting_object element is used by a vm_advancedsetting_test to define the vm name, connection string, and the name of the advanced setting to be evaluated.

The vm_advancedsetting_state element holds information about the value of the specified advanced setting. 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**vmware.vm_advancedsetting_v2**

+-------------------------------------+---------+----------------------------+
| Name                                | Type    | Description                |
+=====================================+=========+============================+
| check_existence                     | string  | Defines how many items     |
|                                     |         | should be collected.       |
+-------------------------------------+---------+----------------------------+
| advanced_setting_name               | string  | The name of the VM’s       |
|                                     |         | setting.                   |
|                                     |         | i.e. RemoteDisplay.maxCon  |
|                                     |         | nections                   |
+-------------------------------------+---------+----------------------------+
| vm_name                             | string  | The name of the VM to      |
|                                     |         | scope the collection to.   |
|                                     |         | Set to NA if not           |
|                                     |         | applicable.                |
+-------------------------------------+---------+----------------------------+
| advanced_setting_name_operation     | string  | Comparison operation.      |
+-------------------------------------+---------+----------------------------+
| vm_name_operation                   | string  | Comparison operation.      |
+-------------------------------------+---------+----------------------------+

NOTE: The ``check_existence``  parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_exist
  - only_one_exists

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - vmware:vm_advancedsetting

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**vmware:vm_advancedsetting_value_v2**

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
| advanced_setting_value              | integer | The advanced_setting_value |
|                                     |         | element details the value  |
|                                     |         | of the VMHost’s advanced   |
|                                     |         | configuration setting that |
|                                     |         | was collected.             |
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

**vmware:vm_advancedsetting_value_v2**

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
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
            <ae:parameter dt="string" name="advanced_setting_name">[advanced_setting_name.value]</ae:parameter>
            <ae:parameter dt="string" name="vm_name">[vm_name.value]</ae:parameter>
            <ae:parameter dt="string" name="advanced_setting_name_operation">[advanced_setting_name_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="vm_name_operation">[vm_name_operation.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
            <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
            <ae:parameter dt="boolean" name="advanced_setting_value">[advanced_setting_value.value]</ae:parameter>
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

For ``vmware:vm_advancedsetting`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    operator="equals"
    type="[type.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>
        This value is used in Rule: [RECOMMENDATION-TITLE]
    </description>
    <value>[value.value]</value>
  </Value>  

For ``vmware:vm_advancedsetting`` artifacts, the xccdf:check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]"
      value-id="xccdf_org.cisecurity.benchmarks_value_[PLATFORM].connection" />
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]"
      value-id="xccdf_org.cisecurity.benchmarks_value_[PLATFORM].connection" />      
    <check-content-ref 
      href="[BENCHMARK-NAME]"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <vm_advancedsetting_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    check="[check.value]"
    check_existence="[check_existence.value]"
    comment="[RECOMMENDATION-TITLE]"
    id="oval:org.cisecurity.benchmarks[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </vm_advancedsetting_test>

Object

::

  <vm_advancedsetting_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    comment="[RECOMMENDATION-TITLE]"
    id="oval:org.cisecurity.benchmarks[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    version="1">
    <connection_string var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" />
    <vm_name operation="pattern match">
        [vm_name.value]
    </vm_name>
    <advanced_setting_name>[vmsafe.enable.value]</advanced_setting_name>
  </vm_advancedsetting_object>     

State

::

  <vm_advancedsetting_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    comment="[RECOMMENDATION-TITLE]"
    id="oval:org.cisecurity.benchmarks[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    version="1">
    <advanced_setting_name 
      datatype="string"
      operation="equals">
        [advanced_setting_name.value]
    </advanced_setting_name>
    <advanced_setting_value 
      datatype="[datatype.value]"
      operation="equals"
      var_ref="oval:org.cisecurity.benchmarks[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </vm_advancedsetting_state>

External Variable

::

  <external_variable 
    id="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]"
    datatype="boolean"
    version="1"
    comment="This value is used in Rule: [RECOMMENDATION-TITLE]" />     

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
            name: "check_existence"
            type: "string"
            value: "[check_existence.value]"
        - parameter: 
            name: "advanced_setting_name"
            type: "string"
            value: "[advanced_setting_name.value]"
        - parameter: 
            name: "vm_name"
            type: "string"
            value: "[vm_name.value]"
        - parameter: 
            name: "advanced_setting_name_operation"
            type: "string"
            value: "[advanced_setting_name_operation.value]"
        - parameter: 
            name: "vm_name_operation"
            type: "string"
            value: "[vm_name_operation.value]"                                
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
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
            name: "advanced_setting_value"
            type: "string"
            value: "[advanced_setting_value.value]"            

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
              "name": "check_existence",
              "type": "string",
              "value": "[check_existence.value]"
            }
          },
          {
            "parameter": {
              "name": "advanced_setting_name",
              "type": "string",
              "value": "[advanced_setting_name.value]"
            }
          },
          {
            "parameter": {
              "name": "vm_name",
              "type": "string",
              "value": "[vm_name.value]"
            }
          },
          {
            "parameter": {
              "name": "advanced_setting_name_operation",
              "type": "string",
              "value": "[advanced_setting_name_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "vm_name_operation",
              "type": "string",
              "value": "[vm_name_operation.value]"
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
              "name": "advanced_setting_value",
              "type": "string",
              "value": "[advanced_setting_value.value]"
            }
          }
        ]
      }
    }
  }
