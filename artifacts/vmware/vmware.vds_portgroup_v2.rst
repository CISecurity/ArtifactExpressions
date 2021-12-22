vmware:vds_portgroup
====================

Description
-----------

The vmware:vds_portgroup test is used to verify override port policies are disabled for vSphere distributed portgroups on the specified vSphere Distributed Switch.

The vds_portgroup_object element is used by a vds_portgroup_test to define the name and connection string of the specific vSphere Distributed Switch, and the portgroup to be evaluated.

The vds_portgroup_state element holds information regarding whether or not override port policies are disabled for the specified portgroup, on the specified vSphere Distributed Switch.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**vmware.vds_portgroup_v2**

+---------------------------------------+---------+--------------------------+
| Name                                  | Type    | Description              |
+=======================================+=========+==========================+
| check_existence                       | string  | Defines how many items   |
|                                       |         | should be collected.     |
|                                       |         | Cannot be blank.         |
+---------------------------------------+---------+--------------------------+
| portgroup_name                        | string  | The name of a vSphere    |
|                                       |         | Distributed port group.  |
|                                       |         | Cannot be blank.         |
+---------------------------------------+---------+--------------------------+
| vds_name                              | string  | The name of a vSphere    |
|                                       |         | Distributed Switch.      |
|                                       |         | Cannot be blank.         |
+---------------------------------------+---------+--------------------------+
| vds_name_operation                    | string  | Comparison operation.    |
+---------------------------------------+---------+--------------------------+
| portgroup_name_operation              | string  | Comparison operation.    |
+---------------------------------------+---------+--------------------------+

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_exist
  - only_one_exists

NOTE: The ``vds_name_operation`` and ``portgroup_name_operation`` parameters are governed by a constraint allowing only the following values:
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

  - vmware:vds_portgroup_collector_ip_address
  - vmware:vds_portgroup_collector_port
  - vmware:vds_portgroup_override_port_policies

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**vmware.vds_portgroup_collector_ip_address_v2**

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
| collector_ip_address                  | string  | Authorized collector IP  |
|                                       |         | Address to which Virtual |
|                                       |         | Disributed Switch        |
|                                       |         | Netflow traffic is sent. |
|                                       |         | Cannot be blank.         |
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

**vmware.vds_portgroup_collector_port_v2**

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
| collector_port                        | string  | Authorized collector     |
|                                       |         | Port to which Virtual    |
|                                       |         | Disributed Switch        |
|                                       |         | Netflow traffic is sent. |
|                                       |         | Cannot be blank.         |
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

**vmware.vds_portgroup_override_port_policies_v2**

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
| override_port_policies_enabled        | boolean | Port-level configuration |
|                                       |         | overrides enabled?       |
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

**vmware.vds_portgroup_collector_ip_address_v2**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[RECOMMENDATION-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACT-TYPE-NAME]" />
          <ae:parameters>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
            <ae:parameter dt="string" name="portgroup_name">[portgroup_name.value]</ae:parameter>
            <ae:parameter dt="string" name="vds_name">[vds_name.value]</ae:parameter>
            <ae:parameter dt="string" name="vds_name_operation">[vds_name_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="portgroup_name_operation">[portgroup_name_operation.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
            <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
            <ae:parameter dt="string" name="collector_ip_address">[collector_ip_address.value]</ae:parameter>
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

For ``vmware.vds_portgroup_v2`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
    <check-content-ref 
      href="[BENCHMARK-TITLE]"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>    

OVAL
''''

Test

::

  <vds_portgroup_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
      <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
      <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </vds_portgroup_test>

Object

::

  <vds_portgroup_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <connection_string var_ref="oval:org.cisecurity.benchmarks[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <vds_name operation="[operation.value]">
        [vds_name.value]
    </vds_name>
    <portgroup_name operation="[operation.value]">
        [portgroup_name.value]
    </portgroup_name>
  </vds_portgroup_object>  

State

::

  <vds_portgroup_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <collector_ip_address 
      datatype="[datatype.value]"
      operation="[operation.value]">
        [collector_ip_address.value]
    </collector_ip_address>
  </vds_portgroup_state>  

Variable

::

  <external_variable 
    id="oval:org.cisecurity.benchmarks[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="boolean"
    version="1"
    comment="[ARTIFACT-TITLE]" />

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
            name: "check_existence"
            dt: "string"
            value: "[check_existence.value]"
        - parameter: 
            name: "portgroup_name"
            dt: "string"
            value: "[portgroup_name.value]"
        - parameter: 
            name: "vds_name"
            dt: "string"
            value: "[vds_name.value]"
        - parameter: 
            name: "vds_name_operation"
            dt: "string"
            value: "[vds_name_operation.value]"
        - parameter: 
            name: "portgroup_name_operation"
            dt: "string"
          value: "[portgroup_name_operation.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "check"
            dt: "string"
            value:"[check.value]"
        - parameter:
            name: "operation"
            dt: "string"
            value: "[operation.value]"
        - parameter:
            name: "datatype"
            dt: "string"
            value: "[datatype.value]"
        - parameter:
            name: "collector_ip_address"
            dt: "string"
            value: "[collector_ip_address.value]"

JSON
^^^^

::

   {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact_title": "[RECOMMENDATION-TITLE]",
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
              "name": "portgroup_name",
              "dt": "string",
              "value": "[portgroup_name.value]"
            }
          },
          {
            "parameter": {
              "name": "vds_name",
              "dt": "string",
              "value": "[vds_name.value]"
            }
          },
          {
            "parameter": {
              "name": "vds_name_operation",
              "dt": "string",
              "value": "[vds_name_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "portgroup_name_operation",
              "dt": "string",
              "value": "[portgroup_name_operation.value]"
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
              "name": "datatype",
              "dt": "string",
              "value": "[datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "collector_ip_address",
              "dt": "string",
              "value": "[collector_ip_address.value]"
            }
          }
        ]
      }
    }
  }

Generated Content
~~~~~~~~~~~~~~~~~

**vmware.vds_portgroup_collector_port_v2**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[RECOMMENDATION-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACT-TYPE-NAME]" />
          <ae:parameters>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
            <ae:parameter dt="string" name="portgroup_name">[portgroup_name.value]</ae:parameter>
            <ae:parameter dt="string" name="vds_name">[check_exivds_namestence.value]</ae:parameter>
            <ae:parameter dt="string" name="vds_name_operation">[vds_name_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="portgroup_name_operation">[portgroup_name_operation.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
            <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
            <ae:parameter dt="string" name="collector_port">[collector_port.value]</ae:parameter>
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

For ``vmware.vds_portgroup_v2`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
    <check-content-ref 
      href="[BENCHMARK-TITLE]"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>  

OVAL
''''

Test

::

  <vds_portgroup_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[ARTIFACT-TITLE]"
    id="oval:org.cisecurity.benchmarks:tst:[ARTIFACT-OVAL-ID]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks:ste:[ARTIFACT-OVAL-ID]" />
  </vds_portgroup_test>

Object

::

  <vds_portgroup_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <connection_string var_ref="oval:org.cisecurity.benchmarks[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <vds_name operation="[operation.value]">
        [vds_name.value]
    </vds_name>
    <portgroup_name operation="[operation.value]">
        [portgroup_name.value]
    </portgroup_name>
  </vds_portgroup_object>  

State

::

  <vds_portgroup_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <collector_port datatype="[datatype.value]"
      operation="[operation.value]">
        [collector_port.value]
    </collector_port>
  </vds_portgroup_state>

Variable

::

  <external_variable 
    id="oval:org.cisecurity.benchmarks:obj:[ARTIFACT-OVAL-ID]"
    datatype="boolean"
    version="1"
    comment="[ARTIFACT-TITLE]" />

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
            name: "check_existence"
            dt: "string"
            value: "[check_existence.value]"
        - parameter: 
            name: "portgroup_name"
            dt: "string"
            value: "[portgroup_name.value]"
        - parameter: 
            name: "vds_name"
            dt: "string"
            value: "[vds_name.value]"
        - parameter: 
            name: "vds_name_operation"
            dt: "string"
            value: "[vds_name_operation.value]"
        - parameter: 
            name: "portgroup_name_operation"
            dt: "string"
            value: "[portgroup_name_operation.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "check"
            dt: "string"
            value:"[check.value]"
        - parameter:
            name: "operation"
            dt: "string"
            value: "[operation.value]"
        - parameter:
            name: "datatype"
            dt: "string"
            value: "[datatype.value]"
        - parameter:
            name: "collector_port"
            dt: "string"
            value: "[collector_port.value]"

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact_title": "[RECOMMENDATION-TITLE]",
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
              "name": "portgroup_name",
              "dt": "string",
              "value": "[portgroup_name.value]"
            }
          },
          {
            "parameter": {
              "name": "vds_name",
              "dt": "string",
              "value": "[vds_name.value]"
            }
          },
          {
            "parameter": {
              "name": "vds_name_operation",
              "dt": "string",
              "value": "[vds_name_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "portgroup_name_operation",
              "dt": "string",
              "value": "[portgroup_name_operation.value]"
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
              "name": "datatype",
              "dt": "string",
              "value": "[datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "collector_port",
              "dt": "string",
              "value": "[collector_port.value]"
            }
          }
        ]
      }
    }
  }

Generated Content
~~~~~~~~~~~~~~~~~

**vmware.vds_portgroup_override_port_policies_v2**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[RECOMMENDATION-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACT-TYPE-NAME]" />
          <ae:parameters>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
            <ae:parameter dt="string" name="portgroup_name">[portgroup_name.value]</ae:parameter>
            <ae:parameter dt="string" name="vds_name">[check_exivds_namestence.value]</ae:parameter>
            <ae:parameter dt="string" name="vds_name_operation">[vds_name_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="portgroup_name_operation">[portgroup_name_operation.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
            <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
            <ae:parameter dt="string" name="override_port_policies_enabled">[override_port_policies_enabled.value]</ae:parameter>
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

For ``vmware.vds_portgroup_v2`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:100000"  
      value-id="xccdf_org.cisecurity.benchmarks_value_esxi.connection" />
    <check-content-ref 
      href="[BENCHMARK-TITLE]-oval.xml"" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>  

OVAL
''''

Test

::

  <vds_portgroup_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks:ste:[ARTIFACT-OVAL-ID]" />
  </vds_portgroup_test>

Object

::

  <vds_portgroup_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <connection_string var_ref="oval:org.cisecurity.benchmarks[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <vds_name operation="[operation.value]">
        [vds_name.value]
    </vds_name>
    <portgroup_name operation="[operation.value]">
        [portgroup_name.value]
    </portgroup_name>
  </vds_portgroup_object>  

State

::

  <vds_portgroup_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <override_port_policies_enabled datatype="[datatype.value]"
      operation="[operation.value]">
        [override_port_policies_enabled.value]
    </override_port_policies_enabled>
  </vds_portgroup_state>

Variable

::

  <external_variable 
    id="oval:org.cisecurity.benchmarks:obj:[ARTIFACT-OVAL-ID]"
    datatype="boolean"
    version="1"
    comment="[ARTIFACT-TITLE]" />

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
            name: "check_existence"
            dt: "string"
            value: "[check_existence.value]"
        - parameter: 
            name: "portgroup_name"
            dt: "string"
            value: "[portgroup_name.value]"
        - parameter: 
            name: "vds_name"
            dt: "string"
            value: "[vds_name.value]"
        - parameter: 
            name: "vds_name_operation"
            dt: "string"
            value: "[vds_name_operation.value]"
        - parameter: 
            name: "portgroup_name_operation"
            dt: "string"
            value: "[portgroup_name_operation.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "check"
            dt: "string"
            value:"[check.value]"
        - parameter:
            name: "operation"
            dt: "string"
            value: "[operation.value]"
        - parameter:
            name: "datatype"
            dt: "string"
            value: "[datatype.value]"
        - parameter:
            name: "override_port_policies_enabled"
            dt: "string"
            value: "[override_port_policies_enabled.value]"

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact_title": "[RECOMMENDATION-TITLE]",
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
              "name": "portgroup_name",
              "dt": "string",
              "value": "[portgroup_name.value]"
            }
          },
          {
            "parameter": {
              "name": "vds_name",
              "dt": "string",
              "value": "[vds_name.value]"
            }
          },
          {
            "parameter": {
              "name": "vds_name_operation",
              "dt": "string",
              "value": "[vds_name_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "portgroup_name_operation",
              "dt": "string",
              "value": "[portgroup_name_operation.value]"
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
              "name": "datatype",
              "dt": "string",
              "value": "[datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "override_port_policies_enabled",
              "dt": "string",
              "value": "[override_port_policies_enabled.value]"
            }
          }
        ]
      }
    }
  }