macos.authorizationdb_v1
=================

Description
-----------

The authorizationdb_test is used to check the properties of the
plist-style XML output from the “security authorizationdb read >right-name<”
command, for reading information about rights authorizations on MacOSX.
It extends the standard TestType as defined in the oval-definitions-schema
and one should refer to the TestType description for more information. The
required object element references an authorizationdb_object and the optional
state element specifies the data to check.


Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

+-------------------------------------+-------------+--------------------------+
| Name                                | Type        | Description              |
+=====================================+=============+==========================+
| right_name                          | string      | Specifies the right name |
|                                     |             | to be queried (read)     |
|                                     |             | from the authorization   |
|                                     |             | database.                |
|                                     |             |                          |
|                                     |             |                          |
+-------------------------------------+-------------+--------------------------+
| xpath                               | string      | Specifies an expression  |
|                                     |             | Xpath describing the     |
|                                     |             | text node(s) or          |
|                                     |             | attribute(s) to look at. |
|                                     |             | Any valid Xpath 1.0      |
|                                     |             | statement is usable with |
|                                     |             | one exception, at most   |
|                                     |             | one field may be         |
|                                     |             | identified in the Xpath. |
|                                     |             | This is because the      |
|                                     |             | value_of element in the  |
|                                     |             | data section is only     |
|                                     |             | designed to work against |
|                                     |             | a single field. The only |
|                                     |             | valid operator for xpath |
|                                     |             | is equals since there is |
|                                     |             | an infinite number of    |
|                                     |             | possible xpaths and      |
|                                     |             | determining all those    |
|                                     |             | that do not equal a given|
|                                     |             | given xpath would be     |
|                                     |             | impossible.              |
+-------------------------------------+-------------+--------------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - macos.authorizationdb_v1

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| check_existence                     | string      | Define how many  |
|                                     |             | items should be  |
|                                     |             | collected        |
+-------------------------------------+-------------+------------------+
| check                               | string      | Defines how many |
|                                     |             | collected items  |
|                                     |             | must match the   |
|                                     |             | expected state   |
+-------------------------------------+-------------+------------------+
| operation                           | string      | comparison       |
|                                     |             | operation        |
+-------------------------------------+-------------+------------------+
| datatype                            | string      | datatype         |
+-------------------------------------+-------------+------------------+
| value_of                            | string      | The value_of     |
|                                     |             | element checks   |
|                                     |             | the value(s) of  |
|                                     |             | the text node(s) |
|                                     |             | or attribute(s)  |
|                                     |             | found.           |
+-------------------------------------+-------------+------------------+

check_existence NOTE: This parameter is governed by a constraint
allowing only the following values: 
  - all_exist 
  - any_exist 
  - at_least_one_exists 
  - none_satisfy 
  - none_exist 
  - only_one_exists

check NOTE: This parameter is governed by a constraint allowing only the
following values: - all - at least one - none satisfy - only one

operation NOTE: This parameter is governed by a constraint allowing only
the following values: 
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

datatype NOTE: This parameter is governed by a constraint allowing only
the following values: - boolean - float - int - string - version - set

Generated Content
~~~~~~~~~~~~~~~~~

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION_NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[RECOMMENDATION TITLE]</ae:title>
        <ae:artifact type="[ARTIFACTTYPE NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="right_name">[right_name.value]</ae:parameter>
            <ae:parameter dt="string" name="xpath">[xpath.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TESTTYPE NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
            <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
            <ae:parameter dt="string" name="value_of">[value_of.value]</ae:parameter>
          </ae:parameters>
        </ae:test>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``macos.authorizationdb_v1`` artifacts, the xccdf:check looks like this. There is no Value in the xccdf for this Artifact.

::

  <xccdf:check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <xccdf:check-content-ref
      href="[BENCHMARK NAME]"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </xccdf:check>


OVAL
''''

Test

::

  <authorizationdb_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM_ID]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[RECOMMENDATION TITLE]"
    version="[version.value]">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </authorizationdb_test>

Object

::

  <authorizationdb_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM_ID]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[RECOMMENDATION TITLE]"
    version="[version.value]">
    <right_name>[right_name.value]</right_name>
    <xpath>[xpath.value]</xpath>
  </authorizationdb_object>

State

::

  <authorizationdb_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM_ID]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[RECOMMENDATION TITLE]"
    version="[version.value]">
    <value_of 
      datatype="[datatype.value]" 
      operation="[operation.value]">
      [value_of.value]
    </value_of>
  </authorizationdb_state>

YAML
^^^^

::

  - artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact-title: "[RECOMMENDATION TITLE]"
    artifact:
      type: "[ARTIFACTTYPE NAME]"
      parameters:
        - parameter: 
          name: "right_name"
          type: "string"
          value: "[right_name.value]"
        - parameter: 
        name: "xpath"
          type: "string"
        value: "[xpath.value]"  
    test:
      type: "[TESTTYPE NAME]"
      parameters:
        - parameter:
          name: "check_existence"
          type: "string"
          value: "[check_existence.value]"
        - parameter: 
          name: "check"
          type: "string"
          value: "[check.value]"
        - parameter:
          name: "operation"
          type: "string"
          value: "[operation.value]"
        - parameter: 
          name: "datatype"
          type: "string"
          value: "[datatype.value] " 
        - parameter: 
          name: "value_of"
          type: "string"
          value: "[value_of.value]"    

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact-title": "[RECOMMENDATION TITLE]",
      "artifact": {
        "type": "[ARTIFACTTYPE NAME]",
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
        "type": "[TESTTYPE NAME]",
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