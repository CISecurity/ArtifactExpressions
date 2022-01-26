Cisco IOS: SNMP User Config
===========================

Description
-----------

The Cisco IOS: SNMP User Config test is used to check the properties of specific output lines from an SNMP user configuration.

The snmpuser_object element is used by an snmpuser test to define the name of the SNMP user to be tested.

The snmpuser_state element defines the different information that can be used to evaluate the result of a specific 'show snmp user' IOS command. This includes the user name and the corresponding options. 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**cisco_ios.snmp_user**

========================== ======= ===========================================
Name                       Type    Description
========================== ======= ===========================================
cisco_ios.snmp_user_name   string  The SNMP user name. Cannot be blank.
cisco_ios.snmp_user_op     string  SNMP User Comparison Operator.
cisco_ios.snmp_user_snmpv3 boolean Collect only SNMPv3 Users?
========================== ======= ===========================================

NOTE: The ``cisco_ios.snmp_user_op`` parameter is governed by a constraint allowing only the following values:
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

  - Cisco IOS: SNMP User Priv

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**cisco_ios.snmp_user_priv**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| operator                    | string  | Comparison operator.               |
+-----------------------------+---------+------------------------------------+
| snmp_encryption_type        | string  | The SNMP encryption type for the   |
|                             |         | user (for SNMPv3).                 |
+-----------------------------+---------+------------------------------------+

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
  
NOTE: The ``snmp_encryption_type`` parameter is governed by a constraint allowing only the following values:  
  - DES
  - 3DES
  - AES

Generated Content
~~~~~~~~~~~~~~~~~

**cisco_ios.snmp_user_priv**

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
              <ae:parameter dt="string" name="cisco_ios.snmp_user_name">[cisco_ios.snmp_user_name.value]</ae:parameter>
              <ae:parameter dt="string" name="cisco_ios.snmp_user_op">[cisco_ios.snmp_user_op.value]</ae:parameter>
              <ae:parameter dt="boolean" name="cisco_ios.snmp_user_snmpv3">[cisco_ios.snmp_user_snmpv3.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
              <ae:parameter dt="string" name="snmp_encryption_type">[snmp_encryption_type.value]</ae:parameter>
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

For ``cisco_ios.snmp_user`` ``cisco_ios.snmp_user_priv`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    type="string"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``cisco_ios.snmp_user`` ``cisco_ios.snmp_user_priv`` artifacts, the XCCDF check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
    <check-content-ref 
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <snmpuser_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#ios"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="any_exist"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </snmpuser_test>

Object

::

  <snmpuser_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#ios"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <name operation="[operation.value]">[name.value]</name>
    <filter 
      xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5"
      action="include">
        oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]2
    </filter>
  </snmpuser_object>

State

::

  <snmpuser_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#ios"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]2"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <version>3</version>
  </snmpuser_state>

  <snmpuser_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#ios"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <priv
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </snmpuser_state>

Variable

::

  <external_variable
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#ios"
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
            name: "cisco_ios.snmp_user_name"
            dt: "string"
            value: "[cisco_ios.snmp_user_name.value]"
        - parameter: 
            name: "cisco_ios.snmp_user_op"
            dt: "string"
            value: "[cisco_ios.snmp_user_op.value]"
        - parameter: 
            name: "cisco_ios.snmp_user_snmpv3"
            dt: boolean
            value: "[cisco_ios.snmp_user_snmpv3.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:   
        - parameter: 
            name: "operator"
            dt: "string"
            value: "[operator.value]"
        - parameter: 
            name: "snmp_encryption_type"
            dt: "string"
            value: "[snmp_encryption_type.value]"

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
              "name": "cisco_ios.snmp_user_name",
              "type": "string",
              "value": "[cisco_ios.snmp_user_name.value]"
            }
          },
          {
            "parameter": {
              "name": "cisco_ios.snmp_user_op",
              "type": "string",
              "value": "[cisco_ios.snmp_user_op.value]"
            }
          },
          {
            "parameter": {
              "name": "cisco_ios.snmp_user_snmpv3",
              "type": "boolean",
              "value": "[cisco_ios.snmp_user_snmpv3.value]"
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
              "name": "snmp_encryption_type",
              "type": "string",
              "value": "[snmp_encryption_type.value]"
            }
          }
        ]
      }
    }
  }
