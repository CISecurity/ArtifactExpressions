Cisco IOS: SNMP Group Config
============================

Description
-----------

The Cisco IOS: SNMP Group Config test is used to check the properties of specific output lines from an SNMP group configuration.

The snmpgroup_object element is used by an snmpgroup test to define the name of the SNMP group to be tested.

The snmpgroup_state element defines the different information that can be used to evaluate the result of a specific 'snmp-server group' IOS command. This includes the user name and the corresponding options. 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

========================= ======= =========================================
Name                      Type    Description
========================= ======= =========================================
cisco_ios.snmp_group_name string  The SNMP group name. Cannot be blank.
cisco_ios.snmp_group_op   string  The SNMP group op.
cisco_ios.snmpv3_filter   boolean Collect only SNMP v3 Groups?
========================= ======= =========================================

NOTE: The ``snmp_group_op`` parameter is governed by a constraint allowing only the following values:
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

  - cisco_ios.snmp_groups_priv

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

================ ====== =============================================
Name             Type   Description
================ ====== =============================================
operator         string Comparison Operator.
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

Generated Content
~~~~~~~~~~~~~~~~~

**cisco_ios.snmp_groups_priv**

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
            <ae:parameter dt="string" name="cisco_ios.snmp_group_name">[cisco_ios.snmp_group_name.value]</ae:parameter>
            <ae:parameter dt="string" name="cisco_ios.snmp_group_op">[cisco_ios.snmp_group_op.value]</ae:parameter>
            <ae:parameter dt="boolean" name="cisco_ios.snmpv3_filter">[cisco_ios.snmpv3_filter.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
            <ae:parameter dt="string" name="snmpv3_sec_level">[snmpv3_sec_level.value]</ae:parameter>
          </ae:parameters>
        </ae:test>
        <ae:profiles>
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_2" />
        </ae:profiles>        
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``cisco_ios.snmp_group`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    type="string"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``cisco_ios.snmp_group`` artifacts, the xccdf:check looks like this.

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

  <snmpgroup_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#ios"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="any_exist"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </snmpgroup_test>

Object

::

  <snmpgroup_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#ios"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <name 
      operation="[operation.value]"
      action=".+">
        oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]
    </name>
    <filter 
      xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#"
      action="include">
        oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]
    </filter>    
  </snmpgroup_object>

State

::

  <snmpgroup_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#ios"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]2"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <snmpv3_sec_level 
      operation="pattern match"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2" />
  </snmpgroup_state>

  <snmpgroup_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#ios"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]2"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <snmpv3_sec_level 
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </snmpgroup_state>

Variable

::

  <external_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="string"
    comment="This value is used in Rule: [RECOMMENDATION-TITLE]"
    version="1" />

  <constant_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="string"
    comment="This value is used in Rule: [RECOMMENDATION-TITLE]"
    version="1">
    <value>.+</value>

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
            name: "cisco_ios.snmp_group_name"
            dt: "string"
            value: "[cisco_ios.snmp_group_name.value]"
        - parameter: 
            name: "cisco_ios.snmp_group_op"
            dt: "string"
            value: "[cisco_ios.snmp_group_op.value]"
        - parameter: 
            name: "cisco_ios.snmpv3_filter"
            dt: "boolean"
            value: "[cisco_ios.snmpv3_filter.value]"
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
              "name": "cisco_ios.snmp_group_name",
              "type": "string",
              "value": "[cisco_ios.snmp_group_name.value]"
            }
          },
          {
            "parameter": {
              "name": "cisco_ios.snmp_group_op",
              "type": "string",
              "value": "[cisco_ios.snmp_group_op.value]"
            }
          },
          {
            "parameter": {
              "name": "cisco_ios.snmpv3_filter",
              "type": "boolean",
              "value": "[cisco_ios.snmpv3_filter.value]"
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
            }
          }
        ]
      }
    }
  }
