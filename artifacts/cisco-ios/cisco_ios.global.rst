Cisco IOS: Global Config
========================

Description
-----------

The Cisco IOS: Global Config test is used to check for the existence of a particular
line in the IOS-XE config file under the global context. 

The global_object element is used by a global test to define the object to be evaluated. For the most part this object checks for existence and is used without a state comparision. 

The global_state element defines the different information that can be found in the ios config file under the global context.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**cisco_ios.global**

+----------------------------+---------+-------------------------------------+
| Name                       | Type    | Description                         |
+============================+=========+=====================================+
| cisco_ios.global_command   | string  | The global command identifies a     |
|                            |         | specific line in the IOS config     |
|                            |         | file under the global context.      |
+----------------------------+---------+-------------------------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Cisco IOS: Global Command

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**cisco_ios.global_command**

+----------------------------+---------+-------------------------------------+
| Name                       | Type    | Description                         |
+============================+=========+=====================================+
| operator                   | string  | The comparison operator.            |
+----------------------------+---------+-------------------------------------+
| global_command             | string  | The global_command entity           |
|                            |         | identifies a specific line in the   |
|                            |         | ios config file under the global    |
|                            |         | context.                            |
+----------------------------+---------+-------------------------------------+
| existence_check            | string  | Number of global config lines       |
|                            |         | required in the result.             |
+----------------------------+---------+-------------------------------------+

NOTE: The ``operator`` parameter is governed by a constraint allowing only the following values:
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

NOTE: The ``existence_check`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_satisfy
  - none_exist
  - only_one_exists 

Generated Content
~~~~~~~~~~~~~~~~~

**cisco_ios.global_command**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:complex-check operator="AND">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
        <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
          <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
          <ae:title>[ARTIFACT-TITLE]</ae:title>
          <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="cisco_ios.global_command">[cisco_ios.global_command.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
              <ae:parameter dt="string" name="global_command">[global_command.value]</ae:parameter>
              <ae:parameter dt="string" name="existence_check">[existence_check.value]</ae:parameter>
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

For ``cisco_ios.global`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    type="string"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``cisco_ios.global`` artifacts, the xccdf:check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
    <check-content-ref 
      href="[BENCHMARK-NAME]"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <global_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iso"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </global_test>

Object

::

  <global_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iso"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <global_command operation="pattern match">[global_command.value]</global_command>
  </global_object>

State

::

  <global_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iso"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <global_command 
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </global_state>

Variable

::

  <external_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
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
            name: "cisco_ios.global_command"
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
            name: "global_command"
            dt: "string"
            value: "[global_command.value]"
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
              "name": "cisco_ios.global_command",
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
              "name": "global_command",
              "type": "string",
              "value": "[global_command.value]"
            }
          },
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
