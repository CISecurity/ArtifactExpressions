vmware:vmhost_module
====================

Description
-----------

The vmware:vmhost_module test is used to verify no unauthorized kernel modules are loaded on the ESXi host.

The vmhost_module_object element is used by a vmhost_module_test to define the vmhost name and connection string, and name of the module to be evaluated.

The vmhost_module_state element holds information regarding the signed status of the specified module. 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**vmware.vmhost_module_v2**

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
| module_name                         | string  | The name of the module to  |
|                                     |         | collect. Set to NA if not  |
|                                     |         | applicable. Cannot be      |
|                                     |         | blank.                     |
+-------------------------------------+---------+----------------------------+
| vmhost_name_operation               | string  | CComparison operation.     |
+-------------------------------------+---------+----------------------------+
| module_name_operation               | string  | CComparison operation.     |
+-------------------------------------+---------+----------------------------+

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_exist
  - only_one_exists

NOTE: The ``vmhost_name_operation`` and ``module_name_operation`` parameters are governed by a constraint allowing only the following values:
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

  - vmware:vmhost_module_signed_status

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**vmware:vmhost_module_signed_status_v2**

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
| signed_status                       | string  | The digital signature      |
|                                     |         | status of the kernel       |
|                                     |         | module.                    |
+-------------------------------------+---------+----------------------------+

NOTE: The ``signed_status`` parameter is governed by a constraint allowing only the following values:
  - NA
  - VMware Signed
  - VMWare Certified

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

**vmware:vmhost_module_signed_status_v2**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

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
            <ae:parameter dt="string" name="module_name">[module_name.value]</ae:parameter>
            <ae:parameter dt="string" name="module_name_operation">[module_name_operation.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
            <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
            <ae:parameter dt="string" name="signed_status">[signed_status.value]</ae:parameter>
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

For ``vmware.vmhost_module_v2`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    operator="[operator.value]"
    type="[type.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>  

For ``vmware.vmhost_module_v2`` artifacts, the xccdf:check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />    
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:100000"
      value-id="xccdf_org.cisecurity.benchmarks_value_esxi.connection" />
    <check-content-ref 
      href="[BENCHMARK-NAME]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <vmhost_module_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </vmhost_module_test>

Object

::

  <vmhost_module_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <connection_string var_ref="oval:org.cisecurity.benchmarks[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <vmhost_name operation="[operation.value]">
      [vmhost_name.value]
    </vmhost_name>
    <module_name operation="[operation.value]">
      [module_name.value]
    </module_name>
  </vmhost_module_object>      

State

::

  <vmhost_module_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <signed_status 
      datatype="[datatype.value]"
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </vmhost_module_state> 

Variable

::

  <external_variable 
    id="oval:org.cisecurity.benchmarks[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="string"
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
            name: "module_name"
            dt: "string"
            value: "[module_name.value]"
        - parameter: 
            name: "module_name_operation"
            dt: "string"
            value: "[module_name_operation.value]"
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
            name: "signed_status"
            dt: "string"
            value: "[signed_status.value]"

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
              "name": "module_name",
              "dt": "string",
              "value": "[module_name.value]"
            }
          },
          {
            "parameter": {
              "name": "module_name_operation",
              "dt": "string",
              "value": "[module_name_operation.value]"
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
              "name": "signed_status",
              "dt": "string",
              "value": "[signed_status.value]"
            }
          }
        ]
      }
    }
  }
