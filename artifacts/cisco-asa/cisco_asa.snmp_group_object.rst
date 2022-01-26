Cisco ASA: SNMP Group Object
============================

Description
-----------

The Cisco ASA: SNMP Group Object test is used to check the properties of specific output lines from an SNMP group configuration.

The snmp_group_object element is used by an snmp_group test to define the name of the SNMP group to be tested.

The snmp_group_state element defines the different information that can be used to evaluate the result of a specific 'snmp-server group' ASA command. This includes the user name and the corresponding options. 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**cisco_asa.snmp_group_object**

======== ====== =====================================
Name     Type   Description
======== ====== =====================================
name     string The SNMP group name. Cannot be blank.
operator string Comparison operator.
======== ====== =====================================

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

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Cisco ASA: SNMP Groups Priv
  - Cisco ASA: Existence Check

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**cisco_asa.snmp_groups_priv**

================ ====== =============================================
Name             Type   Description
================ ====== =============================================
operator         string Comparison operator.
snmpv3_sec_level string The SNMPv3 security configured for the group.
================ ====== =============================================

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

NOTE: The ``snmpv3_sec_level`` parameter is governed by a constraint allowing only the following values:
  - PRIV
  - AUTH
  - NO_AUTH

**cisco_asa.existence_check**

=============== ====== =========================================
Name            Type   Description
=============== ====== =========================================
existence_check string Number of lines expected to be collected.
=============== ====== =========================================

NOTE: The ``existence_check`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_satisfy
  - none_exist
  - only_one_exists

Generated Content
~~~~~~~~~~~~~~~~~

**cisco_asa.snmp_groups_priv**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[ARTIFACT-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACT-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="name">[name.value]</ae:parameter>
            <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
            <ae:parameter dt="string" name="snmpv3_sec_level">[snmpv3_sec_level.value]</ae:parameter>
          </ae:parameters>
        </ae:test>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``cisco_asa.snmp_group_object`` ``cisco_asa.snmp_groups_priv`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    type="string"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``cisco_asa.snmp_group_object`` ``cisco_asa.snmp_groups_priv`` artifacts, the XCCDF check looks like this. 

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

  <snmp_group_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#asa"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </snmp_group_test>

Object

::

  <snmp_group_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#asa"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <name operation="[operation.value]">[name.value]</name>
  </snmp_group_object>

State

::

  <snmp_group_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#asa"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <snmpv3_sec_level 
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </snmp_group_state>

Variable

::

  <external_variable
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#asa"
    datatype="string"
    comment="This value is used in Rule: [RECOMMENDATION-TITLE]"
    version="1" />

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
            name: "name"
            dt: "string"
            value: "[name.value]"
        - parameter:
            name: "operator"
            dt: "string"
            value: "[operator.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "operator"
            dt: "string"
            value: "[operator.value]"
        - parameter:
            name: "snmpv3_sec_level"
            dt: "string"
            value: "[snmpv3_sec_level.value]"

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
              "name": "name",
              "type": "string",
              "value": "[name.value]"
            }
          },
          {
            "parameter": {
              "name": "operator",
              "type": "string",
              "value": "[operator.value]"
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
              "name": "snmpv3_sec_level",
              "type": "string",
              "value": "[snmpv3_sec_level.value]"
              ]
            }
          }
        ]
      }
    }
  }

Generated Content
~~~~~~~~~~~~~~~~~

**cisco_asa.existence_check**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[ARTIFACT-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACT-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="name">[name.value]</ae:parameter>
            <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="existence_check">[existence_check.value]</ae:parameter>
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

For ``cisco_asa.snmp_group_object`` ``cisco_asa.existence_check`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-content-ref 
      href="[BENCHMARK-TITLE]-oval.xml" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <snmp_group_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#asa"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </snmp_group_test>

Object

::

  <snmp_group_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#asa"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <name operation="[operation.value]">[name.value]</name>
  </snmp_group_object>

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
            name: "name"
            dt: "string"
            value: "[name.value]"
        - parameter:
            name: "operator"
            dt: "string"
            value: "[operator.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "existence_check"
            dt: "string"
            value: "[existence_check.value]"

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
              "name": "name",
              "type": "string",
              "value": "[name.value]"
            }
          },
          {
            "parameter": {
              "name": "operator",
              "type": "string",
              "value": "[operator.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "existence_check",
              "type": "string",
              "value": "[existence_check.value]"
            }
          }
        ]
      }
    }
  }  