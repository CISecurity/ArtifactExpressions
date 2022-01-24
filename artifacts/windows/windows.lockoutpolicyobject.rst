Windows: Lockout Policy Object
==============================

Description
-----------

The Windows: Lockout Policy Object test enumerates various attributes associated with lockout information for users and global groups in the security database. 

The lockoutpolicy_object element is used by a lockoutpolicy_test to define those objects to evaluated based on a specified state. There is actually only one object relating to lockout policy and this is the system as a whole. Therefore, there are no child entities defined.

The lockoutpolicy_state element specifies the various attributes associated with lockout information for users and global groups in the security database. A lockout policy test will reference a specific instance of this state that defines the exact settings that need to be evaluated.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**windows.lockoutpolicyobject**

============== ====== =========================================
Name           Type   Description
============== ====== =========================================
lockoutsetting string The lockout policy setting to be audited.
============== ====== =========================================

NOTE: The ``lockoutsetting`` parameter is governed by a constraint allowing only the following values:
  - Duration 
  - Observation Window 
  - Threshold 
  - Forced Logoff

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Equal
  - Equals
  - Not Equal
  - Equal To
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
| data_type                   | string  | Datatype of the  value.            |
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
              <ae:parameter dt="string" name="lockoutsetting">[lockoutsetting.value]</ae:parameter>
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

For ``windows.lockoutpolicyobject`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    operator="[operator.value]"
    type="[type.value]">
    <title>[RECOMMENDATION-TTILE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``windows.lockoutpolicyobject`` artifacts, the xccdf:check looks like this.

::

  <xccdf:complex-check operator="AND">
    <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
      <check-export 
        export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
        value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
      <check-content-ref 
        href="[BENCHMARK-TITLE]"
        name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
    </check>
  </xccdf:complex-check>

OVAL
''''

Test

::

  <lockoutpolicy_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </lockoutpolicy_test>

Object

::

  <lockoutpolicy_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1" />       

State

::

  <lockoutpolicy_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <[lockoutsetting.value] 
      operation="[operation.value]"
      datatype="[datatype.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </lockoutpolicy_state>

Variable

::

  <external_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    comment="This value is used in [RECOMMENDATION-TITLE]"
    datatype="[datatype.value]"
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
            name: "lockoutsetting"
            dt: "string"
            value: "[lockoutsetting.value]"
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
              "name": "lockoutsetting",
              "type": "string",
              "value": "[lockoutsetting.value]"
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
