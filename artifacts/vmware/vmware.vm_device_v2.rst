vmware:vm_device
================

Description
-----------

The vmware:vm_device test is used to verify no device is connected to a virtual machine if it is not required.

The vm_device_object element is used by the vm_device_test to define the name and connection string of the vm, and the type of device being evaluated.

The vm_device_state element holds information regarding the connection state of the specified device.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**vmware.vm_device_v2**

+-------------------------------------+---------+----------------------------+
| Name                                | Type    | Description                |
+=====================================+=========+============================+
| check_existence                     | string  | Defines how many items     |
|                                     |         | should be collected.       |
+-------------------------------------+---------+----------------------------+
| vm_name                             | string  | The name of the VM to      |
|                                     |         | scope collection to. Set   |
|                                     |         | to NA if not applicable.   |
|                                     |         | Cannot be blank.           |
+-------------------------------------+---------+----------------------------+
| vm_name_operation                   | string  | Comparison operation.      |
+-------------------------------------+---------+----------------------------+
| device_type_operation               | string  | Comparison operation.      |
+-------------------------------------+---------+----------------------------+
| device_type                         | string  | The device type;one of the |
|                                     |         | values in the enumeration  |
|                                     |         | (floppy, cdrom, parallel,  |
|                                     |         | etc).                      |
+-------------------------------------+---------+----------------------------+

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_exist
  - only_one_exists

NOTE: The ``vm_name_operation`` and ``device_type_operation`` parameters are governed by a constraint allowing only the following values:
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

NOTE: The ``device_type`` parameter is governed by a constraint allowing only the following values:
  - floppy
  - cdrom
  - parallel_port 
  - serial_port
  - usb
  - hard_disk  

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - vmware:vm_device

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**vmware.vm_device_v2**

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
| connected                           | boolean | Connected?                 |
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

**vmware.vm_device_v2**

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
            <ae:parameter dt="string" name="vm_name">[vm_name.value]</ae:parameter>
            <ae:parameter dt="string" name="vm_name_operation">[vm_name_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="device_type_operation">[device_type_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="device_type">[device_type.value]</ae:parameter>                                                
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
            <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
            <ae:parameter dt="boolean" name="connected">[connected.value]</ae:parameter>
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

For ``vmware.vm_device_v2`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    operator="equals"
    type="number">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``vmware.vm_device_v2`` artifacts, the xccdf:check looks like this.

::

  <xccdf:complex-check operator="AND">
    <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
      <check-export 
        export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
        value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
      <check-export 
        export-name="oval:org.cisecurity.benchmarks:var:100000"
        value-id="xccdf_org.cisecurity.benchmarks_value_esxi.connection" />
      <check-content-ref 
        href="[BENCHMARK-NAME]-oval.xml"
        name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
    </check>
  </xccdf:complex-check> 

OVAL
''''

Test

::

  <vm_device_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </vm_device_test>

Object

::

  <vm_device_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    comment="[ARTIFACT-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    version="1">
    <connection_string var_ref="oval:org.cisecurity.benchmarks[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <vm_name operation="[operation.value]">
      [vm_name.value]
    </vm_name>
    <device_type operation="[operation.value]">
      [device_type.value]
    </device_type>
  </vm_device_object>   

State

::

  <vm_device_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <connected datatype="[datatype.value]"
      operation="[operation.value]">
        [connected.value]
    </connected>
  </vm_device_state>

Variable

::

  <external_variable 
    id="oval:org.cisecurity.benchmarks[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
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
            name: "vm_name"
            dt: "string"
            value: "[vm_name.value]"
        - parameter: 
            name: "vm_name_operation"
            dt: "string"
            value: "[vm_name_operation.value]"
        - parameter: 
            name: "device_type_operation"
            dt: "string"
            value: "[device_type_operation.value]"
        - parameter: 
            name: "device_type"
            dt: "string"
            value: "[device_type.value]"
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
            name: "connected"
            dt: "boolean"
            value: "[connected.value]"

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
              "name": "vm_name",
              "dt": "string",
              "value": "[vm_name.value]"
            }
          },
          {
            "parameter": {
              "name": "vm_name_operation",
              "dt": "string",
              "value": "[vm_name_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "device_type_operation",
              "dt": "string",
              "value": "[device_type_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "device_type",
              "dt": "string",
              "value": "[device_type.value]"
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
              "name": "connected",
              "dt": "boolean",
              "value": "[connected.value]"
            }
          }
        ]
      }
    }
  }
