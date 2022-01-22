vmware:vm_harddiskdevice
========================

Description
-----------

The vmware:vm_harddiskdevice test is used to verify the configuration of virtual machine persistent memory settings.

The vm_harddiskdevice_object element is used by the vm_harddiskdevice_test to define the name and connection string of the vm to be evaluated.

the vm_harddiskdevice_state element holds information regarding the configuration of the virtual machine persistent memory settings.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**vmware.vm_harddiskdevice_v2**

+-------------------------------------+---------+----------------------------+
| Name                                | Type    | Description                |
+=====================================+=========+============================+
| check_existence                     | string  | Defines how many items     |
|                                     |         | should be collected.       |
+-------------------------------------+---------+----------------------------+
| persistence                         | string  | NA or acceptable           |
|                                     |         | persistence constraint     |
|                                     |         | values.                    |
+-------------------------------------+---------+----------------------------+
| disktype                            | string  |                            |
+-------------------------------------+---------+----------------------------+
| filename                            | string  | i.e. hd1,hd2. Enter NA if  |
|                                     |         | not applicable.            |
+-------------------------------------+---------+----------------------------+
| capacitykb                          | binary  | i.e. 1000. Enter NA if not |
|                                     |         | applicable.                |
+-------------------------------------+---------+----------------------------+
| capacitygb                          | float   | i.e 1.6. Enter NA if not   |
|                                     |         | applicable.                |
+-------------------------------------+---------+----------------------------+
| vm_name                             | string  | The name of the VM to      |
|                                     |         | scope collection to. Set   |
|                                     |         | to NA if not applicable.   |
+-------------------------------------+---------+----------------------------+
| vm_name_operation                   | string  | Comparison operation.      |
+-------------------------------------+---------+----------------------------+

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_exist
  - only_one_exists

NOTE: The ``persistence`` parameter is governed by a constraint allowing only the following values:
  - NA
  - Persistent
  - NonPersistent
  - Undoable
  - IndependentPersistent
  - IndependentNonPersistent
  - Unknown

NOTE: The ``disktype`` parameter is governed by a constraint allowing only the following values:
  - NA
  - RawVirtual
  - RawPhysical
  - Flat
  - Unknown

NOTE: The ``vm_name_operation`` parameter is governed by a constraint allowing only the following values:
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

  - vmware:vm_harddiskdevice

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

vmware.vm_harddiskdevice_v2

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
| persistence                         | string  | The persistence policy     |
|                                     |         | (Persistent,               |
|                                     |         | NonPersistent, Undoable,   |
|                                     |         | IndependentPersistent,     |
|                                     |         | IndependentNonPersistent,  |
|                                     |         | or Unknown.                |
+-------------------------------------+---------+----------------------------+

NOTE: The ``persistence`` parameter is governed by a constraint allowing only the following values:
  - NA
  - Persistent
  - NonPersistent
  - Undoable
  - IndependentPersistent
  - IndependentNonPersistent
  - Unknown

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

**vmware.vm_harddiskdevice_v2**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:complex-check operator="AND">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
        <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
          <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
          <ae:title>[ARTIFACT-TITLE]</ae:title>
          <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
              <ae:parameter dt="string" name="persistence">[persistence.value]</ae:parameter>
              <ae:parameter dt="string" name="disktype">[disktype.value]</ae:parameter>
              <ae:parameter dt="string" name="filename">[filename.value]</ae:parameter>
              <ae:parameter dt="binary" name="capacitykb">[capacitykb.value]</ae:parameter>
              <ae:parameter dt="float" name="capacitygb">[capacitygb.value]</ae:parameter>
              <ae:parameter dt="string" name="vm_name">[vm_name.value]</ae:parameter>
              <ae:parameter dt="string" name="vm_name_operation">[vm_name_operation.value]</ae:parameter>          
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
              <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
              <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
              <ae:parameter dt="string" name="persistence">[persistence.value]</ae:parameter>
            </ae:parameters>
          </ae:test>
          <ae:profiles>
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_2" />
          </ae:profiles>
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  <xccdf:complex-check>

SCAP
^^^^

XCCDF
'''''

For ``vmware.vm_harddiskdevice_v2`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    operator="[operator.value]"
    type="[type.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``vmware.vm_harddiskdevice_v2`` artifacts, the xccdf:check looks like this.

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
        href="[BENCHMARK-TITLE]-oval.xml"
        name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
    </check>
  </xccdf:complex-check> 

OVAL
''''

Test

::

  <vm_harddiskdevice_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi" 
    id="oval:org.cisecurity.benchmarks[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </vm_harddiskdevice_test>

Object

::

  <vm_harddiskdevice_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <connection_string var_ref="oval:org.cisecurity.benchmarks[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <vm_name operation="[operation.value]">
      [vm_name.value]
    </vm_name>
  </vm_harddiskdevice_object>   

State

::

  <vm_harddiskdevice_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <persistence 
      datatype="[datatype.value]"
      operation="[operation.value]">
        [persistence.value]
    </persistence>
  </vm_harddiskdevice_state>  

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
            name: "persistence"
            dt: "string"
            value: "[persistence.value]"
        - parameter: 
            name: "disktype"
            dt: "string"
            value: "[disktype.value]"
        - parameter: 
            name: "filename"
            dt: "string"
            value: "[filename.value]"
        - parameter: 
            name: "capacitykb"
            dt: "binary"
            value: "[capacitykb.value]"
        - parameter: 
            name: "capacitygb"
            dt: "float"
            value: "[capacitygb.value]"
        - parameter: 
            name: "vm_name"
            dt: "string"
            value: "[vm_name.value]"
        - parameter: 
            name: "vm_name_operation"
            dt: "string"
            value: "[vm_name_operation.value]"
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
            name: "persistence"
            dt: "string"
            value: "[persistence.value]"

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
