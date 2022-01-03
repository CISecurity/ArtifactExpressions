VMware: Virtual Machine: Device: Hard Disk
==========================================

Description
-----------

The VMware: Virtual Machine: Device: Hard Disk test is used to verify the configuration of virtual machine persistent memory settings.

The vm_harddiskdevice_object element is used by the vm_harddiskdevice_test to define the name and connection string of the vm to be evaluated.

the vm_harddiskdevice_state element holds information regarding the configuration of the virtual machine persistent memory settings.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**vmware.virtual_machine.device.harddisk**

+---------------+---------+--------------------------------------------------+
| Name          | Type    | Description                                      |
+===============+=========+==================================================+
| persistence   | string  | NA or acceptable persistence constraint value.   |
+---------------+---------+--------------------------------------------------+
| disktype      | string  | NA or acceptable disktype constraint value.      |
+---------------+---------+--------------------------------------------------+
| filename      | string  | i.e. hd1, hd2. Enter NA if not applicable.       |
+---------------+---------+--------------------------------------------------+
| capacitykb    | integer | i.e. 1000. Enter NA if not applicable.           |
+---------------+---------+--------------------------------------------------+
| capacitygb    | float   | i.e 1.6. Enter NA if not applicable.             |
+---------------+---------+--------------------------------------------------+
| vm_name       | string  | The name of the VM to scope collection to. Set   |
|               |         | to NA if not applicable.                         |
+---------------+---------+--------------------------------------------------+

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

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - VMware: Virtual Machine: Hard Disk Persistence Test

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**vmware.virtual_machine.hard_disk.persistence**

=========== ====== ===============================================
Name        Type   Description
=========== ====== ===============================================
operator    string Comparison operation.
persistence string NA or acceptable persistence constraint value.
=========== ====== ===============================================

NOTE: The ``operator`` parameter is governed by a constraint allowing only the following values:
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

NOTE: The ``persistence`` parameter is governed by a constraint allowing only the following values:
  - NA
  - Persistent
  - NonPersistent
  - Undoable
  - IndependentPersistent
  - IndependentNonPersistent
  - Unknown

Generated Content
~~~~~~~~~~~~~~~~~

**vmware.virtual_machine.hard_disk.persistence**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:complex-check operator="AND">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
        <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
          <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
          <ae:title>[ARTIFACT-TITLE]</ae:title>
          <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="persistence">[persistence.value]</ae:parameter>
              <ae:parameter dt="string" name="disktype">[disktype.value]</ae:parameter>
              <ae:parameter dt="string" name="filename">[filename.value]</ae:parameter>
              <ae:parameter dt="string" name="capacitykb">[capacitykb.value]</ae:parameter>
              <ae:parameter dt="string" name="capacitygb">[capacitygb.value]</ae:parameter>
              <ae:parameter dt="string" name="vm_name">[vm_name.value]</ae:parameter>                            
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
              <ae:parameter dt="string" name="persistence">[persistence.value]</ae:parameter>
            </ae:parameters>
          </ae:test>
          <ae:profiles>
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1" />
          </ae:profiles>
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  </xccdf:complex-check>

SCAP
^^^^

XCCDF
'''''

For ``vmware.virtual_machine.device_state`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    operator="[operator.value]"
    type="string">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``vmware.virtual_machine.device_state`` artifacts, the xccdf:check looks like this.

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

  <vm_harddiskdevice_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"    
    check_existence="any_exist"
    check="all"    
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </vm_harddiskdevice_test>

Object

::

  <vm_harddiskdevice_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <connection_string var_ref="oval:org.cisecurity.benchmarks[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <vm_name operation="pattern match">
      .*
    </vm_name>
  </vm_harddiskdevice_object>  

State

::

  <vm_harddiskdevice_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <persistence 
      datatype="string"
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </vm_harddiskdevice_state>

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
            dt: "string"
            value: "[capacitykb.value]"  
      - parameter: 
          name: "capacitygb"
            dt: "string"
            value: "[capacitygb.value]"
        - parameter: 
            name: "vm_name"
            dt: "string"
            value: "[vm_name.value]"                                
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "operator"
            dt: "string"
            value: "[operator.value]"
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
              "name": "persistence",
              "dt": "string",
              "value": "[persistence.value]"
            }
          },
          {
            "parameter": {
              "name": "disktype",
              "dt": "string",
              "value": "[disktype.value]"
            }
          },
          {
            "parameter": {
              "name": "filename",
              "dt": "string",
              "value": "[filename.value]"
            }
          },
          {
            "parameter": {
              "name": "capacitykb",
              "dt": "string",
              "value": "[capacitykb.value]"
            }
          },
          {
            "parameter": {
              "name": "capacitygb",
              "dt": "string",
              "value": "[capacitygb.value]"
            }
          },
          {
            "parameter": {
              "name": "vm_name",
              "dt": "string",
              "value": "[vm_name.value]"
            }
          }           
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "operator",
              "dt": "string",
              "value": "[operator.value]"
            }
          },
          {
            "parameter": {
              "name": "persistence",
              "dt": "string",
              "value": "[persistence.value]"
            }
          }
        ]
      }
    }
  }