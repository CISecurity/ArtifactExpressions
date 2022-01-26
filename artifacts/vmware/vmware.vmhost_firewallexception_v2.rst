vmware:vmhost_firewallexception
===============================

Description
-----------

The vmware:vmhost_firewallexception test is used to verify the ESXi host firewall is configured to restrict access to services running on the host.

The vmhost_firewallexception_object element is used by a vmhost_firewallexception_test to define the vmhost name and connection string, and name of the firewall exception to be evaluated.

The vmhost_firewallexception_state element holds information regarding the firewall exception, services, and allowed hosts to be evaluated. 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**vmware.vmhost_firewallexception_v2**

+-------------------------------------+---------+----------------------------+
| Name                                | Type    | Description                |
+=====================================+=========+============================+
| check_existence                     | string  | Defines how many items     |
|                                     |         | should be collected.       |
+-------------------------------------+---------+----------------------------+
| vmhost_name                         | string  | The ESXi host to scope     |
|                                     |         | results to. Set it NA if   |
|                                     |         | not applicable. Cannot be  |
|                                     |         | blank.                     |
+-------------------------------------+---------+----------------------------+
| firewall_exception_name             | string  | The firewall exceptions to |
|                                     |         | scope collection to. Set   |
|                                     |         | to NA if not applicable.   |
|                                     |         | Cannot be blank.           |
+-------------------------------------+---------+----------------------------+
| vmhost_name_operation               | string  | Comparison operation.      |
+-------------------------------------+---------+----------------------------+
| firewall_exception_name_operation   | string  | Comparison operation.      |
+-------------------------------------+---------+----------------------------+

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_exist
  - only_one_exists

NOTE: The ``exception_enabled_operation`` and ``service_running_operation`` parameters are governed by a constraint allowing only the following values:
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

  - vmware:vmhost_firewallexception

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**vmware.vmhost_firewallexception**

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
| allowed_hosts_all_ip                | boolean | Allowed Hosts All IP?      |
+-------------------------------------+---------+----------------------------+
| exception_enabled_datatype          | string  | Data type.                 |
+-------------------------------------+---------+----------------------------+
| exception_enabled                   | boolean | Exception Enabled?         |
+-------------------------------------+---------+----------------------------+
| service_running_datatype            | string  | Data type.                 |
+-------------------------------------+---------+----------------------------+
| service_running                     | boolean | Service Running?           |
+-------------------------------------+---------+----------------------------+
| exception_enabled_operation         | string  | Comparison operation.      |
+-------------------------------------+---------+----------------------------+
| service_running_operation           | string  | Comparison operation.      |
+-------------------------------------+---------+----------------------------+

NOTE: The ``exception_enabled_datatype`` parameter is governed by a constraint allowing only the following values:
  - boolean
  - float
  - int 
  - string
  - version
  - set

NOTE: The ``datatype`` and ``service_running_datatype`` parameters are governed by a constraint allowing only the following values:
  - boolean
  - float
  - int 
  - string
  - version
  - set

NOTE: The ``check`` parameter is governed by a constraint allowing only the following values:
  - all
  - at least one
  - none satisfy
  - only one

NOTE: The ``exception_enabled_operation`` and ``service_running_operation`` parameters are governed by a constraint allowing only the following values:
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

Generated Content
~~~~~~~~~~~~~~~~~

**vmware.vmhost_firewallexception**

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
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
            <ae:parameter dt="string" name="vmhost_name">[vmhost_name.value]</ae:parameter>
            <ae:parameter dt="string" name="vmhost_name_operation">[vmhost_name_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="firewall_exception_name">[firewall_exception_name.value]</ae:parameter>
            <ae:parameter dt="string" name="firewall_exception_name_operation">[firewall_exception_name_operation.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
            <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
            <ae:parameter dt="string" name="allowed_hosts_all_ip">[allowed_hosts_all_ip.value]</ae:parameter>
            <ae:parameter dt="string" name="exception_enabled_datatype">[exception_enabled_datatype.value]</ae:parameter>
            <ae:parameter dt="boolean" name="exception_enabled">[exception_enabled.value]</ae:parameter>
            <ae:parameter dt="string" name="service_running_datatype">[service_running_datatype.value]</ae:parameter>
            <ae:parameter dt="boolean" name="service_running">[service_running.value]</ae:parameter>
            <ae:parameter dt="string" name="exception_enabled_operation">[exception_enabled_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="service_running_operation">[service_running_operation.value]</ae:parameter>  
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

For ``vmware.vmhost_firewallexception_v2`` ``vmware.vmhost_firewallexception``artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    operator="[operator.value]"
    type="[type.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>  

For ``vmware.vmhost_firewallexception_v2`` ``vmware.vmhost_firewallexception`` artifacts, the XCCDF check looks like this.

::

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

OVAL
''''

Test

::

  <vmhost_firewallexception_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </vmhost_firewallexception_test>

Object

::

  <vmhost_firewallexception_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <connection_string var_ref="oval:org.cisecurity.benchmarks:var:100000" />
    <vmhost_name operation="[operation.value]">[vmhost_name.value]</vmhost_name>
    <firewall_exception_name operation="[operation.value]">
      [firewall_exception_name.value]
    </firewall_exception_name>
  </vmhost_firewallexception_object>      

State

::

  <vmhost_firewallexception_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <exception_enabled 
      datatype="[datatype.value]"
      operation="[operation.value]">
        [exception_enabled.value]
    </exception_enabled>
    <service_running 
      datatype="[datatype.value]"
      operation="[operation.value]">
        [service_running.value]
    </service_running>
    <allowed_hosts_all_ip 
      datatype="[datatype.value]"
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </vmhost_firewallexception_state> 

Variable

::

  <external_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
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
            name: "firewall_exception_name"
            dt: "string"
            value: "[firewall_exception_name.value]"
        - parameter: 
            name: "firewall_exception_name_operation"
            dt: "string"
            value: "[firewall_exception_name_operation.value]"
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
            name: "allowed_hosts_all_ip"
            dt: "boolean"
            value: "[allowed_hosts_all_ip.value]"
        - parameter: 
            name: "exception_enabled_datatype"
            dt: "string"
            value: "[exception_enabled_datatype.value]"
        - parameter:
            name: "exception_enabled"
            dt: "boolean"
            value: "[exception_enabled.value]"
        - parameter: 
            name: "service_running_datatype"
            dt: "string"
            value: "[service_running_datatype.value]"
        - parameter: 
            name: "service_running"
            dt: "boolean"
            value: "[service_running.value]"
        - parameter: 
            name: "exception_enabled_operation"
            dt: "string"
            value: "[exception_enabled_operation.value]"
        - parameter:
            name: "service_running_operation"
            dt: "string"
            value: "[service_running_operation.value]"

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
              "name": "firewall_exception_name",
              "dt": "string",
              "value": "[firewall_exception_name.value]"
            }
          },
          {
            "parameter": {
              "name": "firewall_exception_name_operation",
              "dt": "string",
              "value": "[firewall_exception_name_operation.value]"
            }
          },
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
              "name": "allowed_hosts_all_ip",
              "dt": "boolean",
              "value": "[allowed_hosts_all_ip.value]"
            }
          },
          {
            "parameter": {
              "name": "exception_enabled_datatype",
              "dt": "string",
              "value": "[exception_enabled_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "exception_enabled",
              "dt": "boolean",
              "value": "[exception_enabled.value]"
            }
          },
          {
            "parameter": {
              "name": "service_running_datatype",
              "dt": "string",
              "value": "[service_running_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "service_running",
              "dt": "boolean",
              "value": "[service_running.value]"
            }
          },
          {
            "parameter": {
              "name": "exception_enabled_operation",
              "dt": "string",
              "value": "[exception_enabled_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "service_running_operation",
              "dt": "string",
              "value": "[service_running_operation.value]"
            }
          }
        ]
      }
    }
  }
