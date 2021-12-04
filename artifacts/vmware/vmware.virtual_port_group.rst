VMware: Virtual Port Group
==========================

Description
-----------

The VMware: Virtual Port Group test is used to verify the ESXi Server virtual switch port groups configuration in relation to the VLAN ID in use. 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**vmware.virtual_port_group**

+---------------------+---------+--------------------------------------------+
| Name                | Type    | Description                                |
+=====================+=========+============================================+
| port_group_name     | string  | The name of the port group. Enter NA if    |
|                     |         | not applicable.                            |
+---------------------+---------+--------------------------------------------+
| virtual_switch_name | string  | The name of the virtual switch. Enter NA   |
|                     |         | if not applicable.                         |
+---------------------+---------+--------------------------------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - VMware: Virtual Port Group: VLAN Test

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**vmware.virtual_port_group.vlan**

======== ======= =====================
Name     Type    Description
======== ======= =====================
operator string Comparison operation.
vlan_id  integer VLAN ID
======== ======= =====================

NOTE: The ``operator`` parameter is governed by a constraint allowing only the following values:
  - bitwise and
  - bitwise or
  - case insensitive equals
  - case insensitive not equal
  - equals
  - greater than
  - greater than or equal
  - less than
  - less than or equal
  - pattern match
  - not equal
  - set white list
  - set is empty  

Generated Content
~~~~~~~~~~~~~~~~~

**vmware.virtual_port_group.vlan**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:complex-check operator="AND">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
        <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
          <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
          <ae:title>[RECOMMENDATION-TITLE]</ae:title>
          <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="port_group_name">NA</ae:parameter>
              <ae:parameter dt="string" name="virtual_switch_name">NA</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="operator">not equal</ae:parameter>
              <ae:parameter dt="int" name="vlan_id">4095</ae:parameter>
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

For ``vmware.virtual_port_group`` artifacts, the xccdf:check looks like this. There is no Value in the xccdf for this Artifact.

::

  <xccdf:complex-check operator="AND">
    <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
      <check-export 
        export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
        value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
      <check-content-ref href="[BENCHMARK-NAME]" name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"></check-content-ref>
    </check>
  </xccdf:complex-check>

OVAL
''''

Test

::

  <virtual_portgroup_test 
      xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi" 
      check="all" 
      check_existence="any_exist" 
      comment="[RECOMMENDATION-TITLE]"
      id="oval:org.cisecurity.benchmarks[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
      version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.vmware_esxi_6:obj:152623" />
    <state state_ref="oval:org.cisecurity.benchmarks.vmware_esxi_6:ste:152623" />
  </virtual_portgroup_test>

Object

::

  <virtual_portgroup_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    comment="[RECOMMENDATION-TITLE]"
    id="oval:org.cisecurity.benchmarks[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    version="1">
    <connection_string var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" />
    <port_group_name operation="pattern match">
        .*
    </port_group_name>
    <virtual_switch_name operation="pattern match">
        .*
    </virtual_switch_name>
  </virtual_portgroup_object> 

State

::

  <virtual_portgroup_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    comment="[RECOMMENDATION-TITLE]"
    id="oval:org.cisecurity.benchmarks[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    version="1">
    <vlan_id datatype="int"
      operation="[operation.value]">
        [vlan_id.value]
    </vlan_id>
  </virtual_portgroup_state>

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
          name: "port_group_name"
          type: "string"
          value: "[port_group_name.value]"
      - parameter: 
          name: "virtual_switch_name"
          type: "string"
          value: "[virtual_switch_name.value]"                      
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
      - parameter:
          name: "operator"
          type: "string"
          value: "[operator.value]"
      - parameter:
          name: "vlan_id"
          type: "int"
          value: "[vlan_id.value]"            

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
              "name": "port_group_name",
              "type": "string",
              "value": "[port_group_name.value]"
            }
          },
          {
            "parameter": {
              "name": "virtual_switch_name",
              "type": "string",
              "value": "[virtual_switch_name.value]"
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
              "type": "string",
              "value": "[operator.value]"
            }
          },
          {
            "parameter": {
              "name": "vlan_id",
              "type": "int",
              "value": "[vlan_id.value]"
            }
          }          
        ]
      }
    }
  }