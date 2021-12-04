vmware:vds
==========

Description
-----------

The vmware:vds test is used to verify vSphere Distributed Switch health checks are disabled.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**vmware.vds_v2**

================== ====== ===========================================
Name               Type   Description
================== ====== ===========================================
vds_name           string The name of a vSphere Distributed Switch.
check_existence    string Defines how many items should be collected.
vds_name_operation string Comparison operation.
================== ====== ===========================================

NOTE: The ``check_existence``  parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_exist
  - only_one_exists

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - vmware:vds_vlan_mtu
  - vmware:vds_teaming_failover

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**vmware:vds_teaming_failover**

+---------------------------------------+---------+--------------------------+
| Name                                  | Type    | Description              |
+=======================================+=========+==========================+
| check                                 | string  | Defines how many         |
|                                       |         | collected items must     |
|                                       |         | match the expected       |
|                                       |         | state.                   |
+---------------------------------------+---------+--------------------------+
| operation                             | string  | Comparison operation.    |
+---------------------------------------+---------+--------------------------+
| datatype                              | string  | Datatype.                |
+---------------------------------------+---------+--------------------------+
| teaming_failover_health_check_enabled | boolean | Teaming and Failover     |
|                                       |         | Health Check enabled?    |
+---------------------------------------+---------+--------------------------+

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

**vmware:vds_vlan_mtu**

+---------------------------------------+---------+--------------------------+
| Name                                  | Type    | Description              |
+=======================================+=========+==========================+
| check                                 | string  | Defines how many         |
|                                       |         | collected items must     |
|                                       |         | match the expected       |
|                                       |         | state.                   |
+---------------------------------------+---------+--------------------------+
| operation                             | string  | Comparison operation.    |
+---------------------------------------+---------+--------------------------+
| datatype                              | string  | Datatype.                |
+---------------------------------------+---------+--------------------------+
| vlan_mtu_health_check_enabled         | boolean | VLAN and MTU Health      |
|                                       |         | Check enabled?           |
+---------------------------------------+---------+--------------------------+

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

**vmware:vds_teaming_failover**

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
            <ae:parameter dt="string" name="vds_name">[vds_name.value]</ae:parameter>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
            <ae:parameter dt="string" name="vds_name_operation">[vds_name_operation.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
            <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
            <ae:parameter dt="string" name="teaming_failover_health_check_enabled"
              >[teaming_failover_health_check_enabled.value]</ae:parameter>
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

For ``vmware.vds_v2`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    abstract="false"
    hidden="false"
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    interactive="1"
    prohibitChanges="false"
    type="string">
    <title override="0">
        ESXi connection string
    </title>
    <description override="0">
        This value allows for user-supplied connection strings
    </description>
    <value selector="" />
    <default>[DEFAULT-VALUE]</default>
  </Value> 

For ``vmware.vds_v2`` artifacts, the xccdf:check looks like this.

::

  <xccdf:complex-check operator="AND">
    <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
      <check-export 
        export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
        value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
      <check-content-ref 
        href="[BENCHMARK-NAME]"
        name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
    </check>
  </xccdf:complex-check>  

OVAL
''''

Test

::

  <vds_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    check="[check.value]"
    check_existence="[check_existence.value]"
    comment="[RECOMMENDATION-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </vds_test>

Object

::

  <vds_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    comment="[RECOMMENDATION-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    version="1">
    <connection_string var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" />
    <vds_name operation="[operation.value]">
        [vds_name.value]
    </vds_name>
  </vds_object>    

State

::

  <vds_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    comment="[RECOMMENDATION-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    version="1">
    <teaming_failover_health_check_enabled 
      datatype="[datatype.value]"
      operation="[operation.value]">
        [teaming_failover_health_check_enabled.value]
    </teaming_failover_health_check_enabled>
  </vds_state>   

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
            name: "vds_name"
            type: "string"
            value: "[vds_name.value]"
        - parameter: 
            name: "check_existence"
            type: "string"
            value: "[check_existence.value]"   
        - parameter: 
            name: "ds_name_operation"
            type: "string"
            value: "[vds_name_operation.value]"  
    test:
      type: [TEST-TYPE-NAME]
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
          name: "teaming_failover_health_check_enabled"
          dt: "string"
          value: "[teaming_failover_health_check_enabled.value]"  

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
            "name": "vds_name",
            "type": "string",
            "value": "[vds_name.value]"
          }
        },
        {
          "parameter": {
            "name": "check_existence",
            "type": "string",
            "value": "[check_existence.value]"
          }
        },
        {
          "parameter": {
            "name": "vds_name_operation",
            "type": "string",
            "value": "[vds_name_operation.value]"
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
            "name": "teaming_failover_health_check_enabled",
            "type": "string",
            "value": "[teaming_failover_health_check_enabled.value]"
          }
        }
      ]
    }
  }
}