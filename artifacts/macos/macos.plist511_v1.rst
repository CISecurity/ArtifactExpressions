macos:plist511
=================

Description
-----------

The macos:plist511 test is used to check the value(s) associated with property list preference keys. It can be used to represent any plist file in XML form (whether its native format is ASCII text, binary, or XML), permitting the use of the XPATH query language to explore its contents.

The plist511_object element is used by a plist511_test to define the preference keys to collect and where to look for them. 

The plist511_state element defines the different information that can be used to evaluate the specified property list preference key. This includes the preference key, application identifier, filepath, type, as well as the preference key's value. Please refer to the individual elements in the schema for more details about what each represents.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**macos.plist511_v1**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| filepath                    | string  | The absolute path to a plist file  |
|                             |         | (e.g.                              |
|                             |         | ~/Library/Preferences/com.apple.   |
|                             |         | Safari.plist). A directory cannot  |
|                             |         | be specified as a filepath.        |
+-----------------------------+---------+------------------------------------+
| xpath                       | string  | Specifies an expression Xpath      |
|                             |         | describing the text node(s) or     |
|                             |         | attribute(s) to look at. Any valid |
|                             |         | Xpath 1.0 statement is usable with |
|                             |         | one exception, at most one field   |
|                             |         | may be identified in the Xpath.    |
|                             |         | This is because the value_of       |
|                             |         | element in the data section is     |
|                             |         | only designed to work against a    |
|                             |         | single field. The only valid       |
|                             |         | operator for xpath is equals since |
|                             |         | there is an infinite number of     |
|                             |         | possible xpaths and determining    |
|                             |         | all those that do not equal a      |
|                             |         | given xpath would be impossible.   |
+-----------------------------+---------+------------------------------------+
| app_id                      | string  | The unique application identifier  |
|                             |         | that specifies the application to  |
|                             |         | use when looking up the preference |
|                             |         | key (e.g. com.apple.Safari).	     |
+-----------------------------+---------+------------------------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - macos:plist511

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**macos.plist511_v1**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| check_existence             | string  | Defines how many items should be   |
|                             |         | collected.                         |
+-----------------------------+---------+------------------------------------+
| check                       | string  | Defines how many collected items   |
|                             |         | must match the expected state.     |
+-----------------------------+---------+------------------------------------+
| operation                   | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+
| datatype                    | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| value_of                    | string  | The value of the preference key.   |
+-----------------------------+---------+------------------------------------+

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_satisfy
  - none_exist
  - only_one_exists

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

**macos.plist511_v1**

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
            <ae:parameter dt="string" name="filepath">[filepath.value]</ae:parameter>
            <ae:parameter dt="string" name="xpath">[xpath.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
            <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
            <ae:parameter dt="string" name="value_of">[value_of.value]</ae:parameter>
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

For ``macos.plist511_v1`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

::

  <xccdf:check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <xccdf:check-content-ref 
      href="[BENCHMARK-TITLE]"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </xccdf:check>

OVAL
''''

Test

::

  <plist511_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[ARTIFACT-TTILE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </plist511_test>

Object

::

  <plist511_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TTILE]"
    version="1">
    <filepath operation="case insensitive equals">[filepath.value]</filepath>
    <xpath>[xpath.value]</xpath>
  </plist511_object>

State

::

  <plist511_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TTILE]"
    version="1">
    <value_of 
      datatype="[datatype.value]"
      operation="[operation.value]">
        [value_of.value]
    </value_of>
  </plist511_state>    

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
          name: "filepath"
          dt: "string"
          value: "[filepath.value]"
      - parameter: 
          name: "xpath"
          dt: "string"
          value: "[xpath.value]"  
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
      - parameter:
          name: "check_existence"
          dt: "string"
          value: "[check_existence.value]"
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
          name: "value_of"
          dt: "string"
          value: "[value_of.value]"

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
              "name": "filepath",
              "type": "string",
              "value": "[filepath.value]"
            }
          },
          {
            "parameter": {
              "name": "xpath",
              "type": "string",
              "value": "[xpath.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "check_existence",
              "type": "string",
              "value": "[check_existence.value]"
            }
          },
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
              "name": "value_of",
              "type": "string",
              "value": "[value_of.value]"
            }
          }
        ]
      }
    }
  }
