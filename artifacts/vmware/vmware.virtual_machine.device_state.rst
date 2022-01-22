VMware: Virtual Machine: Device State
=====================================

Description
-----------

The VMware: Virtual Machine: Device State test is used to verify no device is 
connected to a virtual machine if it is not required.

The vm_device_object element is used by a vm_device_test to define the vm 
name, connection string, and the name of the device type to be evaluated.

The vm_device_state element holds information regarding the connection state of 
the specified device.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**vmware.virtual_machine.device_state**

=========== ====== =======================================
Name        Type   Description
=========== ====== =======================================
device_type string Value from device_type constraints.
vm_name     string The name of the VM to scope applicable.
=========== ====== =======================================

NOTE: The ``device_type`` parameter is governed by a constraint allowing only the following values:
  - floppy
  - cdrom
  - parallel_port
  - serial_port
  - usb
  - hard_disk

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - VMware: Virtual Machine: Device State Test

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**vmware.virtual_machine.device_state**

========= ======= ===========
Name      Type    Description
========= ======= ===========
connected boolean Connected?
========= ======= ===========

Generated Content
~~~~~~~~~~~~~~~~~

**vmware.virtual_machine.device_state**

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
              <ae:parameter dt="string" name="device_type">[device_type.value]</ae:parameter>
              <ae:parameter dt="string" name="vm_name">[vm_name.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="boolean" name="connected">[connected.value]</ae:parameter>
            </ae:parameters>
          </ae:test>
          <ae:profiles>
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_2" />
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
        href="[BENCHMARK-TITLE]-oval.xml"
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
    check_existence="any_exist" 
    check="all" 
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </vm_device_test>

Object

::

  <vm_device_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <connection_string var_ref="oval:org.cisecurity.benchmarks[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <vm_name operation="pattern match">
      .*
    </vm_name>
    <device_type>
      [device_type.value]
    </device_type>
  </vm_device_object>  

State

::

  <vm_device_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <connected 
      datatype="boolean"
      operation="equals"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </vm_device_state>

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
            name: "device_type"
            dt: "string"
            value: "[device_type.value]"
        - parameter: 
            name: "vm_name"
            dt: "string"
            value: "[vm_name.value]"          
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
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
              "name": "device_type",
              "dt": "string",
              "value": "[device_type.value]"
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
              "name": "connected",
              "dt": "boolean",
              "value": "[connected.value]"
            }
          }
        ]
      }
    }
  }