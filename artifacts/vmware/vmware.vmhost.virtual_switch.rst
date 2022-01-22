VMware: VM Host: Virtual Switch
===============================

Description
-----------

The VMware: VM Host: Virtual Switch test is used to verify the vSwitch Forged Transmits policy is set to reject forged transmissions.

The vmhost_vswitchpolicy_object element is used by a vmhost_vswitchpolicy_test to define the vmhost name and connection string, and name of the vSwitch to be evaluated.

The vmhost_service_state element holds information regarding the vSwitch Forged Transmits policy of the specified vSwitch. 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**vmware.vmhost.virtual_switch**

+----------------------+---------+-------------------------------------------+
| Name                 | Type    | Description                               |
+======================+=========+===========================================+
| vswitch_name         | string  | The name of a target vswitch. Set to NA   |
|                      |         | if not applicable.                        |
+----------------------+---------+-------------------------------------------+
| vmhost_name          | string  | The ESXi host to scope results to. Set to |
|                      |         | NA if not applicable.                     |
+----------------------+---------+-------------------------------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - VMware: VM Host: Virtual Switch Policy

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**vmware.vmhost.virtual_switch.policy**

============ ====== ===================================
Name         Type   Description
============ ====== ===================================
policy_name  string Value from Policy Name constraint.
policy_state string Value from Policy State constraint.
============ ====== ===================================

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

**vmware.vmhost.virtual_switch.policy**

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
            <ae:parameter dt="string" name="vswitch_name">[vswitch_name.value]</ae:parameter>
            <ae:parameter dt="string" name="vmhost_name">[vmhost_name.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="policy_name">[policy_name.value]</ae:parameter>
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

For ``vmware.vmhost.virtual_switch`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

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
    check_existence="at_least_one_exists"
    check="all"
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
    <vmhost_name operation="pattern match">
      .*
    </vmhost_name>
    <vswitch_name operation="pattern match">
      .*
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
      datatype="string"
      operation="equals">
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
            name: "vswitch_name"
            dt: "string"
            value: "[vswitch_name.value]"
        - parameter: 
            name: "vmhost_name"
            dt: "string"
            value: "[vmhost_name.value]"            
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "policy_name"
            dt: "string"
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
              "name": "vswitch_name",
              "dt": "string",
              "value": "[vswitch_name.value]"
            }
          },
          {
            "parameter": {
              "name": "vmhost_name",
              "dt": "string",
              "value": "[vmhost_name.value]"
            }
          }          
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
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