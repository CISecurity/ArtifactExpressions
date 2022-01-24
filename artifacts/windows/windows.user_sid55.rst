Windows: User Sid55
===================

Description
-----------

The Windows: User Sid55 test is used to check information about Windows users. When the user_sid55_test collects the user SIDs on the system, it should only include the local and built-in user SIDs and not domain user SIDs. However, it is important to note that domain user SIDs can still be looked up. Also, note that the collection of groups, for which a user is a member, is not recursive. The only groups that will be collected are those for which the user is a direct member. For example, if a user is a member of group A, and group A is a member of group B, the only group that will be collected is group A. 

The user_sid55_object element is used by a user_sid55_test represents a set of users on a Windows system. This set (which might contain only one user) is identified by a SID.

The user_sid55_state element enumerates the different groups (identified by SID) that a Windows user might belong to.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**windows.user_sid55**

============= ====== ========================
Name          Type   Description
============= ====== ========================
sid           string SID.
sid_operation string Operation to match SIDs.
state         string SID State to test.
============= ====== ========================

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Equals
  - Equal
  - Not Equal
  - Less Than
  - Less Than or Equal
  - Greater Than
  - Greater Than or Equal

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

| **equal**
| **equals**
| **not equal**
| **less than**
| **less than or equal**
| **greater than**
| **greater than or equal**
+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| data_type                   | string  | Datatype of the value.             |
+-----------------------------+---------+------------------------------------+
| value                       | string  | The value included within the set  |
|                             |         | of results / value to be tested.   |
+-----------------------------+---------+------------------------------------+

NOTE: The ``data_type`` parameter is governed by a constraint allowing only the following values:
  - boolean
  - float
  - int
  - string
  - version
  - set

Generated Content
~~~~~~~~~~~~~~~~~

| **equal**
| **equals**
| **not equal**
| **less than**
| **less than or equal**
| **greater than**
| **greater than or equal**
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
              <ae:parameter dt="string" name="sid">[sid.value]</ae:parameter>
              <ae:parameter dt="string" name="sid_operation">[sid_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="state">[state.value]</ae:parameter>
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

For ``windows.user_sid55`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    type="string"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``windows.user_sid55`` artifacts, the xccdf:check looks like this.

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

  <user_sid55_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </user_sid55_test>

Object

::

  <user_sid55_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <user_sid operation="[operation.value]">[user_sid.value]</user_sid>
  </user_sid55_object>

State

::

  <user_sid55_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <[sidState.value] 
      operation="[operation.value]"
      datatype="[datatype.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </user_sid55_state>

Variable

::

  <external_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="[datatype.value]"
    comment="This valueis used in Rule: [RECOMMENDATION-TITLE]"
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
            name: "sid"
            dt: "string"
            value: "[sid.value]"
        - parameter: 
            name: "sid_operation"
            dt: "string"
            value: "[sid_operation.value]"
        - parameter: 
            name: "state"
            dt: "string"
            value: "[state.value]"
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
      "artifact-title": "[RECOMMENDATION TITLE]",
      "artifact": {
        "type": "[ARTIFACT-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "sid",
              "type": "string",
              "value": "[sid.value]"
            }
          },
          {
            "parameter": {
              "name": "sid_operation",
              "type": "string",
              "value": "[sid_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "state",
              "type": "string",
              "value": "[state.value]"
            }
          }
        ]
      },
      "test": {
        "type": [
          "TestType Name"
        ],
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
