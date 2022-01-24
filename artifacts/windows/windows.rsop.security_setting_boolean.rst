Windows: RSOP Security Setting Boolean
======================================

Description
-----------

The Windows: RSOP Security Setting Boolean test is used to check information accessed by WMI. 

The wmi57_object element is used by a wimi57_test to define the WMI namespace to look under, and a WQL query used to identify the object(s) to test against.

The wmi57_state element specifies the metadata to check, including which WMI namespace to look under, a WQL query used to identify the object(s) to test against, and the result element specifying how to test items in the result set of the specified WQL statement.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**windows.rsop.security_setting_boolean**

======= ====== =======================================
Name    Type   Description
======= ====== =======================================
keyname string RSOP Security Setting Boolean Key Name.
======= ====== =======================================

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Equal
  - Equals
  - Not Equal
  - Less Than
  - Less Than Or Equal
  - Greater Than
  - Greater Than Or Equal

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
              <ae:parameter dt="string" name="keyname">[keyname.value]</ae:parameter>
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

For ``windows.rsop.security_setting_boolean`` artifacts, an XCCDF Value element is generated:

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    type="string"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``windows.rsop.security_setting_boolean`` artifacts, the xccdf:check looks like this.

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

  <wmi57_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </wmi57_test>

Object

::

  <wmi57_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <namespace>root\rsop\computer</namespace>
    <wql>[wql.value]</wql>
  </wmi57_state>

State

::

  <wmi57_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <result 
      datatype="record"
      entity_check="all">
      <field 
        xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5"
        name="setting"
        operation="[operation.value]"
        datatype="[datatype.value]"
        var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    </result>
  </wmi57_state>

Variable

::

  <external_variable id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1"
    datatype="[datatype.value]"
    version="1"
    comment="This value is used in Rule: [RECOMMENDATION-TITLE]" />

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
          name: "keyname"
          dt: "string"
          value: "[keyname.value]"
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
              "name": "keyname",
              "type": "string",
              "value": "[keyname.value]"
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
