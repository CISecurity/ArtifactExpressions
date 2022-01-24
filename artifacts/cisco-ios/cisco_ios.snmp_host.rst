Cisco ASA: SNMP Host Object
===========================

Description
-----------

The Cisco ASA: SNMP Host Object test is used to check the properties of specific output lines from an SNMP configuration.

The snmphost_object element is used by an snmphost test to define the host entity of the 'snmp host' IOS command to be tested.

The snmphost_state element defines the different information that can be used to evaluate the result of a specific 'snmp host' IOS command. This includes the host and the corresponding options. 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**cisco_asa.snmp_host_object**

+--------------------------+---------+---------------------------------------+
| Name                     | Type    | Description                           |
+==========================+=========+=======================================+
| cisco_ios.snmp_host_name | string  | The SNMP host address or hostname.    |
|                          |         | Cannot be blank.                      |
+--------------------------+---------+---------------------------------------+
| cisco_ios.snmp_host_op   | string  | SNMP Host Collection Operator.        |
+--------------------------+---------+---------------------------------------+

NOTE: The ``cisco_ios.snmp_host_op`` parameter is governed by a constraint allowing only the following values:
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

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Existence Test
  - Cisco IOS: SNMP Host Traps

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**existence_test**

===== ====== ===========
Name  Type   Description
===== ====== ===========
value string Value.
===== ====== ===========

**cisco_ios.snmp_host_traps**

======== ====== ==========================
Name     Type   Description
======== ====== ==========================
operator string Comparison Operator.
traps    string The SNMP Traps configured.
======== ====== ==========================

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

**existence_test**

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
              <ae:parameter dt="string" name="cisco_ios.snmp_host_name">[cisco_ios.snmp_host_name.value]</ae:parameter>
              <ae:parameter dt="string" name="cisco_ios.snmp_host_op">[cisco_ios.snmp_host_op.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
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

For ``cisco_ios.snmp_host existence_test`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-content-ref 
      href="[BENCHMARK-TITLE]"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
""

Test

::

  <snmphost_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#ios"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </snmphost_test>

Object

::

  <snmphost_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#ios"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <host operation="[operation.value]">[host.value]</host>
  </snmphost_object>

State

::

  N/A

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
            name: "cisco_ios.snmp_host_name"
            dt: "string"
            value: "[cisco_ios.snmp_host_name.value]"
        - parameter: 
            name: "cisco_ios.snmp_host_op"
            dt: "string"
            value: "[cisco_ios.snmp_host_op.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:   
        - parameter: 
            name: "value"
            dt: "string"
            value: "[value.value]"

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
              "name": "cisco_ios.snmp_host_name",
              "type": "string",
              "value": "[cisco_ios.snmp_host_name.value]"
            }
          },
          {
            "parameter": {
              "name": "cisco_ios.snmp_host_op",
              "type": "string",
              "value": "[cisco_ios.snmp_host_op.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "value",
              "type": "string",
              "value": "[value.value]"
            }
          }
        ]
      }
    }
  }

Generated Content
~~~~~~~~~~~~~~~~~

**cisco_ios.snmp_host_traps**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:complex-check operator="OR">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
        <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
          <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
          <ae:title>[ARTIFACT-TITLE]</ae:title>
          <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="cisco_ios.snmp_host_name">[cisco_ios.snmp_host_name.value]</ae:parameter>
              <ae:parameter dt="string" name="cisco_ios.snmp_host_op">[cisco_ios.snmp_host_op.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
              <ae:parameter dt="string" name="traps">[traps.value]</ae:parameter>
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

For ``cisco_ios.snmp_host cisco_ios.snmp_host_traps`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    type="string"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``cisco_ios.snmp_host cisco_ios.snmp_host_traps`` artifacts, the xccdf:check looks like this.

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
""

Test

::

  <snmphost_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#ios"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="any_exist"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </snmphost_test>

Object

::

  <snmphost_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#ios"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <host operation="[operation.value]">[host.value]</host>
  </snmphost_object>

State

::

  <snmphost_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#ios"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1"> 
      <traps 
        operation="[operation.value]"
        var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" /> 
  </snmphost_state>  

Variable

::

  <external_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="string"
    comment="This value is used in Rule: [RECOMMENDATION-TITLE]"
    version="1"> 

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
            name: "cisco_ios.snmp_host_name"
            dt: "string"
            value: "[cisco_ios.snmp_host_name.value]"
        - parameter: 
            name: "cisco_ios.snmp_host_op"
            dt: "string"
            value: "[cisco_ios.snmp_host_op.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:   
        - parameter: 
            name: "operator"
            dt: "string"
            value: "[operator.value]"
        - parameter: 
            name: "traps"
            dt: "string"
            value: "[traps.value]"              

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
              "name": "cisco_ios.snmp_host_name",
              "type": "string",
              "value": "[cisco_ios.snmp_host_name.value]"
            }
          },
          {
            "parameter": {
              "name": "cisco_ios.snmp_host_op",
              "type": "string",
              "value": "[cisco_ios.snmp_host_op.value]"
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
              "name": "traps",
              "type": "string",
              "value": "[traps.value]"
            }
          }
        ]
      }
    }
  }
