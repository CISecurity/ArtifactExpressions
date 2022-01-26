vmware:vmhost_advancedsetting
=============================

Description
-----------

The vmware:vmhost_advancedsetting test is used to check the value of a specified advanced system setting on an VMware ESXi Host Client.

The vmhost_advancedsetting_object element is used by a vmhost_advancedsetting_test to define the vmhost name, connection string, and the name of the advanced setting to be evaluated.

The vmhost_advancedsetting_state element holds information regarding the value of the specified advanced setting in the vmhost configuration file. 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**vmware.vmhost_advancedsetting_v2**

+---------------------------------+---------+--------------------------------+
| Name                            | Type    | Description                    |
+=================================+=========+================================+
| check_existence                 | string  | Defines how many items should  |
|                                 |         | be collected.                  |
+---------------------------------+---------+--------------------------------+
| vmhost_name                     | string  | The ESXi host to scope VIB     |
|                                 |         | acceptance collection to. Set  |
|                                 |         | to NA if not applicable.       |
|                                 |         | Cannot be blank.               |
+---------------------------------+---------+--------------------------------+
| advanced_setting_name           | string  | The name of the setting.       |
|                                 |         | i.e. User                      |
|                                 |         | Vars.ESXiShell                 |
|                                 |         | InteractiveTimeOut. Cannot be  |
|                                 |         | blank.                         |
+---------------------------------+---------+--------------------------------+
| vmhost_name_operation           | string  | Comparison operation.          |
+---------------------------------+---------+--------------------------------+
| advanced_setting_name_operation | string  | Comparison operation.          |
+---------------------------------+---------+--------------------------------+

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_exist
  - only_one_exists

NOTE: The ``vmhost_name_operation`` and ``advanced_setting_name_operation`` parameters are  governed by a constraint allowing only the following values:
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

  - vmware:vmhost_advancedsetting_value

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**vmware:vmhost_advancedsetting_value_v2**

+---------------------------------+---------+--------------------------------+
| Name                            | Type    | Description                    |
+=================================+=========+================================+
| check                           | string  | Defines how many collected     |
|                                 |         | items must match the expected  |
|                                 |         | state.                         |
+---------------------------------+---------+--------------------------------+
| operation                       | string  | Comparison operation.          |
+---------------------------------+---------+--------------------------------+
| datatype                        | string  | Data type.                     |
+---------------------------------+---------+--------------------------------+
| advanced_setting_value          | integer | The advanced_setting_value     |
|                                 |         | element details the value of   | 
|                                 |         | the VMHost’s advanced          |
|                                 |         | configuration setting that was |
|                                 |         | collected.                     |
+---------------------------------+---------+--------------------------------+

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

**vmware:vmhost_advancedsetting_value_v2**

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
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
            <ae:parameter dt="string" name="vmhost_name">[vmhost_name.value]</ae:parameter>
            <ae:parameter dt="string" name="advanced_setting_name">[advanced_setting_name.value]</ae:parameter>
            <ae:parameter dt="string" name="vmhost_name_operation">[vmhost_name_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="advanced_setting_name_operation">[advanced_setting_name_operation.value]</ae:parameter>                                                
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

For ``vmware.vmhost_advancedsetting_v2`` ``vmware:vmhost_advancedsetting_value_v2`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    operator="[operator.value]"
    type="[type.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>  

For ``vmware.vmhost_advancedsetting_v2`` ``vmware:vmhost_advancedsetting_value_v2`` artifacts, the XCCDF check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />    
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

  <vmhost_advancedsetting_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </vmhost_advancedsetting_test>

Object

::

  <vmhost_advancedsetting_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <connection_string var_ref="oval:org.cisecurity.benchmarks:var:100000" />
    <vmhost_name operation="[operation.value]">[vmhost_name.value]</vmhost_name>
    <advanced_setting_name operation="[operation.value]">
      [advanced_setting_name.value]
    </advanced_setting_name>
  </vmhost_advancedsetting_object>  

State

::

  <vmhost_advancedsetting_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <advanced_setting_name 
      datatype="string"
      operation="[operation.value]">
        [advanced_setting_name.value]
    </advanced_setting_name>
    <advanced_setting_value 
      datatype="[datatype.value]"
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </vmhost_advancedsetting_state>

Variable

::

  <external_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="[datatype.value]"
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
            name: "advanced_setting_name"
            dt: "string"
            value: "[advanced_setting_name.value]"
        - parameter: 
            name: "vmhost_name_operation"
            dt: "string"
            value: "[vmhost_name_operation.value]"
        - parameter: 
            name: "advanced_setting_name_operation"
            dt: "string"
            value: "[advanced_setting_name_operation.value]"
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
            name: "advanced_setting_value"
            dt: "string"
            value: "[advanced_setting_value.value]"

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
              "name": "advanced_setting_name",
              "dt": "string",
              "value": "[advanced_setting_name.value]"
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
              "name": "advanced_setting_name_operation",
              "dt": "string",
              "value": "[advanced_setting_name_operation.value]"
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
              "name": "advanced_setting_value",
              "dt": "string",
              "value": "[advanced_setting_value.value]"
            }
          }
        ]
      }
    }
  }
