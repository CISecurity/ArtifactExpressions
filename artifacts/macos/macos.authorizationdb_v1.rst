macos:authorizationdb
=====================

Description
-----------

The macos:authorizationdb test is used to check the properties of the plist-style XML output from the “security authorizationdb read >right-name<” command, for reading information about rights authorizations on MacOSX.

The authorizationdb_object element is used by an authorizationdb_test to define the object to be evaluated, which contains the name of the right to be read from the authorization database. The resulting plist data can be queried using the xpath entity.

The authorizationdb_state element defines a value used to evaluate the result of a specific authorizationdb_object item.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**macos.authorizationdb_v1**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| right_name                  | string  | Specifies the right name to be     |
|                             |         | queried (read) from the            |
|                             |         | authorization database.            |
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

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - macos:authorizationdb

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**macos.authorizationdb_v1**

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
| value_of                    | string  | The value_of element checks the    |
|                             |         | value(s) of the text node(s) or    |
|                             |         | attribute(s) found. Cannot be      |
|                             |         | blank.                             |
+-----------------------------+---------+------------------------------------+

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
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

**macos.authorizationdb_v1**

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
            <ae:parameter dt="string" name="right_name">[right_name.value]</ae:parameter>
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

For ``macos.authorizationdb_v1`` ``macos.authorizationdb_v1`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this artifact.

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

  <authorizationdb_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </authorizationdb_test>

Object

::

  <authorizationdb_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <right_name>[right_name.value]</right_name>
    <xpath>[xpath.value]</xpath>
  </authorizationdb_object>

State

::

  <authorizationdb_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <value_of 
      datatype="[datatype.value]" 
      operation="[operation.value]">
        [value_of.value]
    </value_of>
  </authorizationdb_state>

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
            name: "right_name"
            dt: "string"
            value: "[right_name.value]"
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
              "name": "right_name",
              "type": "string",
              "value": "[right_name.value]"
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