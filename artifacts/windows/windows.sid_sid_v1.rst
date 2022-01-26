Windows: SID SID
================

Description
-----------

The Windows: SID SID test is used to check properties associated with the specified SID.

The sid_sid_object element is used by a sid_sid_test to define the object set, in this case a set of SIDs, to be evaluated. 

The sid_state element defines the different metadata associate with a Windows trustee (identified by the specified SID). 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**windows.sid_sid_v1**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| trustee_sid                 | string  | The trustee_sid entity identifies  |
|                             |         | a unique SID associated with a     |
|                             |         | user, group, system, or program    |
|                             |         | (such asa Windows service).        |
+-----------------------------+---------+------------------------------------+
| trustee_sid_operator        | string  | The operator used to qualify the   |
|                             |         | Trustee SID. This is typically     |
|                             |         | 'pattern match' or 'equals'.       |
+-----------------------------+---------+------------------------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Windows: SID SID Trustee Name

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**windows.sid_sid_trustee_name_v1**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| check_existence             | string  | Define how many items should be    |
|                             |         | collected.                         |
+-----------------------------+---------+------------------------------------+
| check                       | string  | Defines how many collected items   |
|                             |         | must match the expected state.     |
+-----------------------------+---------+------------------------------------+
| operation                   | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+
| datatype                    | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| trustee_name                | string  | This element specifies the trustee |
|                             |         | name associated with a particular  |
|                             |         | SID. In Windows, trustee names are |
|                             |         | case-insensitive. As a result, it  |
|                             |         | is recommended that the            |
|                             |         | case-insensitive operations are    |
|                             |         | used for this entity.              |
+-----------------------------+---------+------------------------------------+

NOTE: The ``datatype`` parameter is governed by a constraint allowing only the following values:
	- boolean
	- float
	- int
	- string
	- version
	- set

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

Generated Content
~~~~~~~~~~~~~~~~~

**windows.sid_sid_trustee_name_v1**

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
          <ae:artifact type="windows.sid_sid_v1">
            <ae:parameters>
              <ae:parameter dt="string" name="trustee_sid">[trustee_sid.value]</ae:parameter>
              <ae:parameter dt="string" name="trustee_sid_operator">[trustee_sid_operator.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
              <ae:parameter dt="string" name="data_type">[data_type.value]</ae:parameter>
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

For ``windows.sid_sid_v1`` ``windows.sid_sid_trustee_name_v1`` artifacts, an XCCDF Value element is generated:

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    type="string"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>string</value>
  </Value>

For ``windows.sid_sid_v1`` ``windows.sid_sid_trustee_name_v1`` artifacts, the XCCDF check looks like this.

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

  <sid_sid_v1_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </sid_sid_v1_test>

Object

::

  <sid_sid_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <trustee_sid operation="[operation.value]">[trustee_sid.value]</trustee_sid>
  </sid_sid_object>

State

::

  <sid_sid_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <trustee_name 
      operation="[operation.value]"
      datatype="[datatype.value]">
        [trustee_name.value]
    </trustee_name]>
  </sid_sid_state>

Variable

::

  <external_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="string"
    comment="This value is used in [RECOMMENDATION-TITLE]"
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
            name: "trustee_sid"
            dt: "string"
            value: "[trustee_sid.value]"
        - parameter: 
              name: "trustee_sid_operator"
              dt: "string"
              value: "[trustee_sid_operator.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "value"
            dt: "string"
            value: "[value.value]"
        - parameter: 
            name: "data_type"
            dt: "string"
            value: "[data_type.value]"

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
              "name": "trustee_sid",
              "type": "string",
              "value": "[trustee_sid.value]"
            }
          },
          {
            "parameter": {
              "name": "trustee_sid_operator",
              "type": "string",
              "value": "[trustee_sid_operator.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "value",
              "type": "string",
              "value": "[value.value]"
            }
          },
          {
            "parameter": {
              "name": "data_type",
              "type": "string",
              "value": "[data_type.value]"
            }
          }
        ]
      }
    }
  }
