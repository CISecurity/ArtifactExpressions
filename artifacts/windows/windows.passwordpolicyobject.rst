Windows: Password Policy Object
===============================

Description
-----------

The Windows: Password Policy Object test is used to check specific policy associated with passwords. It is important to note that these policies are specific to certain versions of Windows.  As a result, the documentation for that version of Windows should be consulted for more information.

NOTE: This information is stored in the SAM or Active Directory but is encrypted or hidden so the registry_test and activedirectory57_test are of no use. If this can be figured out, then the password_policy test is not needed.

The passwordpolicy_object element is used by a passwordpolicy_test to define those objects to be evaluated based on a specified state. There is actually only one object relating to password policy and this is the system as a whole. Therefore, there are no child entities defined.

The passwordpolicy_state element specifies the various policies associated with passwords. A password policy test will reference a specific instance of this state that defines the exact settings that need to be evaluated.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**windows.passwordpolicyobject**

===================== ====== ==========================================
Name                  Type   Description
===================== ====== ==========================================
passwordpolicysetting string The password policy setting to be audited.
===================== ====== ==========================================

NOTE: The ``passwordpolicysetting`` parameter is governed by a constraint allowing only the following values:
  - Max Passwd Age 
  - Min Passwd Age 
  - Min Passwd Len 
  - Password Hist Len 
  - Password Complexity 
  - Reversible Encryption

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Equals
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
              <ae:parameter dt="string" name="passwordpolicysetting">[passwordpolicysetting.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
              <ae:parameter dt="string" name="data_type">[data_type.value]</ae:parameter>
            </ae:parameters>
          </ae:test>
          <ae:profiles>
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1"/>
          </ae:profiles>          
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  </xccdf:complex-check>

SCAP
^^^^

XCCDF
'''''

For ``windows.passwordpolicyobject`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    operator="[operator.value]"
    type="[type.value]">
    <title>[RECOMMENDATION-TTILE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``windows.passwordpolicyobject`` artifacts, the xccdf:check looks like this.

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

  <passwordpolicy_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </passwordpolicy_test>

Object

::

  <passwordpolicy_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1" />

State

::

  <passwordpolicy_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <[passwordpolicysetting.value] 
      datatype="[datatype.value]"
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </passwordpolicy_state>

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
            name: "passwordpolicysetting"
            dt: "string"
            value: "[passwordpolicysetting.value]"
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
              "name": "passwordpolicysetting",
              "type": "string",
              "value": "[passwordpolicysetting.value]"
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
