panos:config v1
==================

Description
-----------

The panos:config v1 test is used to check the properties of a Palo Alto system.
It works by taking the XPath information specified and checks the value(s) of the text node(s)
or attribute(s) found.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**panos.config_v1**

+---------------------------------------+---------+--------------------------+
| Name                                  | Type    | Description              |
+=======================================+=========+==========================+
| check_existence                       | string  | Defines how many items   |
|                                       |         | should be collected.     |
+---------------------------------------+---------+--------------------------+
| xpath                                 | string  | Specifies an Xpath       |
|                                       |         | expression describing the|
|                                       |         | text node(s) or          |
|                                       |         | attribute(s) to look at. |
|                                       |         | Any valid XPath 1.0      |
|                                       |         | statement is usable with |
|                                       |         | one exception, at most   |
|                                       |         | one field may be         |
|                                       |         | identified in the XPath. |
|                                       |         | This is because the      |
|                                       |         | value_of element in the  |
|                                       |         | data section is only     |
|                                       |         | designed to work against |
|                                       |         | a single field. The only |
|                                       |         | valid operator for xpath |
|                                       |         | is equals since there is |
|                                       |         | an infinite number of    |
|                                       |         | possible XPaths and      |
|                                       |         | determining all those    |
|                                       |         | that do not equal a given|
|                                       |         | XPath would be           |
|                                       |         | impossible. The operation|
|                                       |         | of the pod security      |
|                                       |         | policy.                  |
+---------------------------------------+---------+--------------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - panos:config_v1

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**panos.config_v1**

+---------------------------------------+---------+--------------------------+
| Name                                  | Type    | Description              |
+=======================================+=========+==========================+
| check                                 | string  | Defines how many         |
|                                       |         | collected items must     |
|                                       |         | match the expected       |
|                                       |         | state.                   |
+---------------------------------------+---------+--------------------------+
| operation                             | string  | Comparison operation.    |
+---------------------------------------+---------+--------------------------+
| datatype                              | string  | Data type.               |
+---------------------------------------+---------+--------------------------+
| value_of                              | string  | The value_of element     |
|                                       |         | checks the value(s) of   |
|                                       |         | the text node(s) or      |
|                                       |         | attribute(s) found.The   |
|                                       |         | result entity specifies  |
|                                       |         | how to test objects in   |
|                                       |         | the result set of the    |
|                                       |         | specified.               |
+---------------------------------------+---------+--------------------------+

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

NOTE: The ``value_of`` parameter is governed by a constraint allowing only the following values:
  - ^.+$

Generated Content
~~~~~~~~~~~~~~~~~

**panos.config_v1**

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
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
            <ae:parameter dt="string" name="xpath">[xpath.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
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

For ``panos.config_v1`` ``panos.config_v1`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this artifact.

::

  <check system='http://oval.mitre.org/XMLSchema/oval-definitions-5'>
    <check-content-ref 
      href='[BENCHMARK-TITLE]'
      name='oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]' />
  </check>

OVAL
''''

Test

::

  <config_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#panos"
    check_existence="[check-existence.value]"
    check="[check.value]"
    comment="[ARTIFACT-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </config_test>

Object

::

  <config_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#panos"
    comment="[ARTIFACT-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    version="1">
  </config_object>

State

::

 <config_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#panos"
    comment="[ARTIFACT-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    version="1">
    <value_of
      datatype="[datatype.value]"
      operation="[operation.value]">
        [value_of.value]
    </value_of>
  </config_state>

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact_title: "[ARTIFACT-TITLE]"
    artifact:
      type: "[ARTIFACT-TYPE-NAME]"
      parameters:
        - parameter:
            name: "check_existence"
            dt: "string"
            value: "[check_existence.value]"
        - parameter:
            name: "xpath"
            dt: "string"
            value: "[xpath.value]"
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
            name: "value_of"
            dt: "string"
            value: "[value_of.value]"

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact_title": "[ARTIFACT-TITLE]",
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
              "name": "xpath",
              "dt": "string",
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
              "name": "datatype",
              "dt": "string",
              "value": "[datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "value_of",
              "dt": "string",
              "value": "[value_of.value]"
            }
          }
        ]
      }
    }
  }
