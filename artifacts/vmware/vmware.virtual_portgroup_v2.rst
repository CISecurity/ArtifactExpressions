vmware:virtual_portgroup
========================

Description
-----------

The VMware: Virtual Port Group test is used to verify the ESXi Server virtual switch port groups configuration in relation to the VLAN ID in use. 

The virtual_portgroup_object element is used by the virtual_portgroup_test to define the name and connection string of the specific virtual switch, and the portgroup to be evaluated.

The virtual_portgroup_state element holds the ID of the VLAN in use.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**vmware.virtual_portgroup_v2**

+-------------------------------+---------+----------------------------------+
| Name                          | Type    | Description                      |
+===============================+=========+==================================+
| check_existence               | string  | Defines how many items should be |
|                               |         | collected.                       |
+-------------------------------+---------+----------------------------------+
| port_group_name               | string  | The name of the port group.      |
|                               |         | Enter NA if not applicable.      |
+-------------------------------+---------+----------------------------------+
| virtual_switch_name           | string  | The name of the virtual switch.  |
|                               |         | Enter NA if not applicable.      |
+-------------------------------+---------+----------------------------------+
| portgroup_name_operation      | string  | Comparison operation.            |
+-------------------------------+---------+----------------------------------+
| virtual_switch_name_operation | string  | Comparison operation.            |
+-------------------------------+---------+----------------------------------+

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_exist
  - only_one_exists

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - vmware:virtual_portgroup_vlan

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**vmware.virtual_portgroup_vlan_v2**

+-------------------------------+---------+----------------------------------+
| Name                          | Type    | Description                      |
+===============================+=========+==================================+
| check                         | string  | Defines how many collected items |
|                               |         | must match the expected state.   |
+-------------------------------+---------+----------------------------------+
| operation                     | string  | Comparison operation.            |
+-------------------------------+---------+----------------------------------+
| datatype                      | string  | Datatype.                        |
+-------------------------------+---------+----------------------------------+
| vlan_id                       | integer | The ID of the VLAN.              |
+-------------------------------+---------+----------------------------------+

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

**vmware.virtual_portgroup_vlan_v2**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
        <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
          <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
          <ae:title>[ARTIFACT-TITLE]</ae:title>
          <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
              <ae:parameter dt="string" name="port_group_name">[port_group_name.value]</ae:parameter>
              <ae:parameter dt="string" name="virtual_switch_name">[virtual_switch_name.value]</ae:parameter>
              <ae:parameter dt="string" name="portgroup_name_operation">[portgroup_name_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="virtual_switch_name_operation">[virtual_switch_name_operation.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
            <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
            <ae:parameter dt="integer" name="vlan_id">[vlan_id.value]</ae:parameter>
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

For ``vmware:virtual_portgroup`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

::

  <xccdf:check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:100000"
      value-id="xccdf_org.cisecurity.benchmarks_value_esxi.connection" />
    <check-content-ref 
      href="[BENCHMARK-NAME]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </xccdf:check>

OVAL
''''

Test

::

  <virtual_portgroup_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </virtual_portgroup_test>

Object

::

  <virtual_portgroup_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <connection_string var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <port_group_name operation="[operation.value]">
      .*
    </port_group_name>
    <virtual_switch_name operation="[operation.value]">
      .*
    </virtual_switch_name>
  </virtual_portgroup_object>   

State

::

  <virtual_portgroup_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <vlan_id 
      datatype="[datatype.value]"
      operation="[operation.value]">
        [vlan_id.value]
    </vlan_id>
  </virtual_portgroup_state>  

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
            dt "string"
            value: "[check_existence.value]"
        - parameter: 
            name: "port_group_name"
            dt "string"
            value: "[port_group_name.value]"
        - parameter: 
            name: "virtual_switch_name"
            dt "string"
            value: "[virtual_switch_name.value]"
        - parameter: 
            name: "portgroup_name_operation"
            dt "string"
            value: "[portgroup_name_operation.value]"
        - parameter: 
            name: "virtual_switch_name_operation"
            dt "string"
            value: "[virtual_switch_name_operation.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter: 
            name: "check"
            dt "string"
            value: "[check.value]"
        - parameter:
            name: "operation"
            dt "string"
            value: "[operation.value]"
        - parameter: 
            name: "datatype"
            dt "string"
            value: "[datatype.value]"
        - parameter: 
            name: "vlan_id"
            dt "integer"
            value: "[vlan_id.value]"

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
              "name": "port_group_name",
              "dt": "string",
              "value": "[port_group_name.value]"
            }
          },
          {
            "parameter": {
              "name": "virtual_switch_name",
              "dt": "string",
              "value": "[virtual_switch_name.value]"
            }
          },
          {
            "parameter": {
              "name": "portgroup_name_operation",
              "dt": "string",
              "value": "[portgroup_name_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "virtual_switch_name_operation",
              "dt": "string",
              "value": "[virtual_switch_name_operation.value]"
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
              "name": "vlan_id",
              "dt": "integer",
              "value": "[vlan_id.value]"
            }
          }
        ]
      }
    }
  }
