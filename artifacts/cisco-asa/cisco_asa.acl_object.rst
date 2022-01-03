Cisco ASA: ACL Object
=====================

Description
-----------

The Cisco ASA: ACL Object test is used to check the properties of specific
output lines from an ACL configuration.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**cisco_asa.acl_object**

+------------------------+---------+-----------------------------------------+
| Name                   | Type    | Description                             |
+========================+=========+=========================================+
| name                   | string  | The name of the ACL. Cannot be blank.   |
+------------------------+---------+-----------------------------------------+
| ip_version             | string  | The IP Version of the ACL.              |
+------------------------+---------+-----------------------------------------+
| name_operator          | string  | Operation used to collect appropriate   |
|                        |         | Name values.                            |
+------------------------+---------+-----------------------------------------+
| ip_version_operator    | string  | Operation used to collect appropriate   |
|                        |         | IP Version values.                      |
+------------------------+---------+-----------------------------------------+

NOTE: The ``ip_version`` parameter is governed by a constraint allowing only the following values:
  - IPV4
  - IPV6
  - IPV4_V6
  - ALL

NOTE: The ``name_operator`` and ``ip_version_operator`` parameters are governed by a constraint allowing only the following values:
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
  - Cisco ASA: ACL Config Line W/Entity Check

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**cisco_asa.acl_config_line_with_entity_check**

+------------------------+---------+-----------------------------------------+
| Name                   | Type    | Description                             |
+========================+=========+=========================================+
| operation              | string  | The operation to be used when           |
|                        |         | performing the comparison between the   |
|                        |         | collected configuration line and the    |
|                        |         | expected ``config_line``.               |
+------------------------+---------+-----------------------------------------+
| config_line            | string  | The expected value for the ACL          |
|                        |         | configuration line. This could be       |
|                        |         | represented as an exact match or a      |
|                        |         | regular expression.                     |
+------------------------+---------+-----------------------------------------+
| entity_check           | string  | This enumeration represents the         |
|                        |         | complement of collected configuration   |
|                        |         | lines which must successfully match the |
|                        |         | expected ``config_line``value in order  |
|                        |         | for this test to reach a positive       |
|                        |         | result.                                 |
+------------------------+---------+-----------------------------------------+


NOTE: The ``operation`` parameter is governed by a constraint allowing only the following values:
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

NOTE: The ``entity_check`` parameter is governed by a constraint allowing only the following values:
	- all
	- at least one
	- none satisfy
	- only one  

Generated Content
~~~~~~~~~~~~~~~~~

**cisco_asa.acl_config_line_with_entity_check**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[RECOMMENDATION-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACT-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="name">[name.value]</ae:parameter>
            <ae:parameter dt="string" name="ip_version">[ip_version.value]</ae:parameter>
            <ae:parameter dt="string" name="name_operator">[name_operator.value]</ae:parameter>
            <ae:parameter dt="string" name="ip_version_operator">[ip_version_operator.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
            <ae:parameter dt="string" name="config_line">[config_line.value]</ae:parameter>
            <ae:parameter dt="string" name="entity_check">[entity_check.value]</ae:parameter>
          </ae:parameters>
        </ae:test>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``cisco_asa.acl_object`` artifacts, the xccdf:check looks like this.

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

  <acl_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
    check_existence="[check_existence.value]" 
    check="[check.value]" 
    comment="[RECOMMENDATION-TITLE]" 
    version="[version.value]">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"/>
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"/>
  </acl_test>

Object

::

  <acl_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[RECOMMENDATION-TITLE]" 
    version="[version.value]">
    <name operation="[operation.value]">
      [name.value]
    </name>
    <ip_version 
      operation="[operation.value]" 
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </acl_object>

State

::

  <acl_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[RECOMMENDATION-TITLE]"
    version="[version.value]">
    <config_line 
      operation="[operation.value]"
      entity_check="[entity_check.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </acl_state>

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
            name: "name"
            dt: "string"
            value:" [name.value]"
        - parameter:
            name: "ip_version"
            dt: "string"
            value: "[ip_version.value]"
        - parameter:
            name: "name_operator"
            dt: "string"
            value: "[name_operator.value]"
        - parameter:
            name: "ip_version_operator"
            dt: "string"
            value: "[ip_version_operator.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "operation"
            dt: "string"
            value: "[operation.value]"
        - parameter:
            name: "config_line"
            dt: "string"
            value: "[config_line.value]"
        - parameter:
            name: "entity_check"
            dt: "string"
            value: "[entity_check.value]"

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
              "name": "name",
              "type": "string",
              "value": "[name.value]"
            }
          },
          {
            "parameter": {
              "name": "ip_version",
              "type": "string",
              "value": "[ip_version.value]"
            }
          },
          {
            "parameter": {
              "name": "name_operator",
              "type": "string",
              "value": "[name_operator.value]"
            }
          },
          {
            "parameter": {
              "name": "ip_version_operator",
              "type": "string",
              "value": "[ip_version_operator.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "operation",
              "type": "string",
              "value": "[operation.value]"
            }
          },
          {
            "parameter": {
              "name": "config_line",
              "type": "string",
              "value": "[config_line.value]"
            }
          },
          {
            "parameter": {
              "name": "entity_check",
              "type": "string",
              "value": "[entity_check.value]"
            }
          }
        ]
      }
    }
  }
