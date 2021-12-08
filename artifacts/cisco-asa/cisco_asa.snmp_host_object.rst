Cisco ASA: SNMP Host Object
===========================

Description
-----------

The Cisco ASA: SNMP Host Object test is used to check the properties of
specific output lines from an SNMP configuration.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**cisco_asa.snmp_host_object**

======== ====== ====================================================
Name     Type   Description
======== ====== ====================================================
host     string The SNMP host address or host name. Cannot be blank.
operator string Comparison operator.
======== ====== ====================================================

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

  - Cisco ASA: SNMP Host Version

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**cisco_asa.snmp_host_version**

============ ====== ====================
Name         Type   Description
============ ====== ====================
operator     string Comparison operator.
snmp_version string SNMP Version.
============ ====== ====================

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

NOTE: The ``snmp_version`` parameter is governed by a constraint allowing only the following values:
  - 1
  - 2C
  - 3  

Generated Content
~~~~~~~~~~~~~~~~~

**cisco_asa.snmp_host_version**

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
            <ae:parameter dt="string" name="host">[host.value]</ae:parameter>
            <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
            <ae:parameter dt="string" name="snmp_version">[snmp_version.value]</ae:parameter>
          </ae:parameters>
        </ae:test>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``cisco_asa.snmp_host_object`` artifacts, the xccdf:check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"/>
    <check-content-ref 
      href="[BENCHMARK-NAME]" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]"/>
  </check>

OVAL
''''

Test

::

  <snmp_host_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
    check_existence="[check_existence.value]" 
    check="[check.value]" 
    comment="[RECOMMENDATION-TITLE]" 
    version="[version.value]">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"/>
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"/>
  </snmp_host_test>

Object

::

  <snmp_host_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]" 
    version="[version.value]">
    <host
      operation="[operation.value]">
      [host.value]
    </host>
  </snmp_host_object>

State

::

  <snmp_host_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]" 
    version="[version.value]">
    <version 
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"/>
  </snmp_host_state>

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
            name: "host"
            dt: "string"
            value: "[host.value]"
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
            name: "snmp_version"
            dt: "string"
            value: "[snmp_version.value]"

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
              "name": "host",
              "type": "string",
              "value": "[host.value]"
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
              "name": "snmp_version",
              "type": "string",
              "value": "[snmp_version.value]"
            }
          }
        ]
      }
    }
  }
