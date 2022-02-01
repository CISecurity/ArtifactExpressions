Windows: User Registry Value
============================

Description
-----------

The Windows: User Registry Value test is used to check metadata associated with a Windows
registry key. 

The registry_object element is used by an registry_test to define those objects to evaluate based on a specified state. A registry_object consists of the hive that the registry key belongs to, the registry key to be collected, and the name of the registry key to be evaluated.

The registry_state element defines the different metadata associate with a Windows registry key. This includes the hive, key, name, type, and value. 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**windows.user_registry_value_v1**

============= ====== ==========================================
Name          Type   Description
============= ====== ==========================================
key           string The registry sub-key under HKEY_USERS/SID.
name          string The name of the registry key to collect.
registry_view string The windows view parameter for collection.
============= ====== ==========================================
 
NOTE: The ``registry_view`` parameter is governed by a constraint allowing only the following values:
  - default 
  - 32_bit 
  - 64_bit

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Windows: User Registry Value

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**windows.user_registry_value_v1**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| existence_check             | string  | The existence check determines a   |
|                             |         | required number of items to be     |
|                             |         | collected from the target endpoint.|
+-----------------------------+---------+------------------------------------+
| check                       | string  | The check element describes how    |
|                             |         | many collected items must match    |
|                             |         | the expected state.                |
+-----------------------------+---------+------------------------------------+
| registry_type               | string  | The datatype of the collected      |
|                             |         | registry value .                   |
+-----------------------------+---------+------------------------------------+
| registry_type_operator      | string  | The registry type operator         |
|                             |         | describes the comparison operation |
|                             |         | for the registry type field.       |
+-----------------------------+---------+------------------------------------+
| registry_value              | string  | The registry value.                |
+-----------------------------+---------+------------------------------------+
| registry_value_datatype     | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| registry_value_operator     | string  | The registry value comparison      |
|                             |         | operation.                         |
+-----------------------------+---------+------------------------------------+

NOTE: The ``registry_type`` parameter is governed by a constraint allowing only the following values:
  - reg_dword
  - reg_sz
  - reg_dword_little_endian
  - reg_dword_big_endian
  - reg_expand_sz
  - reg_multi_sz
  - reg_binary
  - reg_link
  - reg_none
  - reg_qword_little_endian

NOTE: The ``check`` parameter is governed by a constraint allowing only the following values:
  - all
  - at least one
  - none satisfy
  - only one

NOTE: The ``existence_check `` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_exist
  - only_one_exists

NOTE: The ``registry_value_datatype`` parameter is governed by a constraint allowing only the following values:
    - boolean
    - float
    - int
    - string
    - version
    - set

NOTE: The ``registry_value_operator`` parameter is governed by a constraint allowing only the following values:
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

**windows.user_registry_value_v1**

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
              <ae:parameter dt="string" name="key">[key.value]</ae:parameter>
              <ae:parameter dt="string" name="name">[name.value]</ae:parameter>
              <ae:parameter dt="string" name="registry_view">[registry_view.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="existence_check">[existence_check.value]</ae:parameter>
              <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
              <ae:parameter dt="string" name="registry_type">[registry_type.value]</ae:parameter>
              <ae:parameter dt="string" name="registry_type_operator">[registry_type_operator.value]</ae:parameter>
              <ae:parameter dt="string" name="registry_value">[registry_value.value]</ae:parameter>
              <ae:parameter dt="string" name="registry_value_datatype">[registry_value_datatype.value]</ae:parameter>
              <ae:parameter dt="string" name="registry_value_operator">[registry_value_operator.value]</ae:parameter>
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

For ``windows.user_registry_value_v1`` ``windows.user_registry_value_v1`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var2"
    type="[type.value]"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE] for the registry value</description>
    <value>[value.value]</value>
  </Value>

For ``windows.user_registry_value_v1`` ``windows.user_registry_value_v1`` artifacts, the XCCDF check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2"
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var2" />
    <check-content-ref 
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <registry_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </registry_test>

Object

::

  <registry_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <behaviors windows_view="[windows_view.value" />
    <hive>HKEY_USERS</hive>
    <key 
      operation="case insensitive equals"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1" />
    <name>[name.value]</name>
  </registry_object>

State

::

  <registry_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <type operation="[operation.value]">[type.value]</type>
    <value 
      datatype="[datatype.value]"
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2" />
  </registry_state>

Variable

::

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1"
    datatype="string"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <concat>
      <object_component
        item_field="key"
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:200000" />
      <literal_component>[literal_component.value]</literal_component>
    </concat> 
  </local_variable>

  <external_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2"
    datatype="[datatype.value]"
    version="1"
    comment="This value is used in Rule: [RECOMMENDATION-TITLE] for the registry value" />

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
            name: "hive"
            dt: "string"
            value: "[hive.value]"
        - parameter: 
            name: "key_operator"
            dt: "string"
            value: "[key_operator.value]"
        - parameter: 
            name: "key"
            dt: "string"
            value: "[key.value]"
        - parameter: 
            name: "name"
            dt: "string"
            value: "[name.value]"
        - parameter: 
            name: "check_existence"
            dt: "string"
            value: "[check_existence.value]"
        - parameter: 
            name: "registry_view"
            dt: "string"
            value: "[registry_view.value]"
        - parameter: 
            name: "registry_data_type"
            dt: "string"
            value: "[registry_data_type.value]"
        - parameter: 
            name: "name_operation"
            dt: "string"
            value: "[name_operation.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "existence_check"
            dt: "string"
            value: "[existence_check.value]"
        - parameter:
            name: "check"
            dt: "string"
            value: "[check.value]"
        - parameter:
            name: "registry_type"
            dt: "string"
            value: "[registry_type.value]"
        - parameter:
            name: "registry_type_operator"
            dt: "string"
            value: "[registry_type_operator.value]"
        - parameter:
            name: "registry_value"
            dt: "string"
            value: "[registry_value.value]"
        - parameter:
            name: "registry_value_datatype"
            dt: "string"
            value: "[registry_value_datatype.value]"
        - parameter:
            name: "registry_value_operator"
            dt: "string"
            value: "[registry_value_operator.value]"

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
              "name": "hive",
              "type": "string",
              "value": "[hive.value]"
            }
          },
          {
            "parameter": {
              "name": "key_operator",
              "type": "string",
              "value": "[key_operator.value]"
            }
          },
          {
            "parameter": {
              "name": "key",
              "type": "string",
              "value": "[key.value]"
            }
          },
          {
            "parameter": {
              "name": "name",
              "type": "string",
              "value": "[name.value]"
            }
          },
          {
            "parameter": {
              "name": "check_existence",
              "type": "string",
              "value": "[check_existence.value]"
            }
          },
          {
            "parameter": {
              "name": "registry_view",
              "type": "string",
              "value": "[registry_view.value]"
            }
          },
          {
            "parameter": {
              "name": "registry_data_type",
              "type": "string",
              "value": "[registry_data_type.value]"
            }
          },
          {
            "parameter": {
              "name": "name_operation",
              "type": "string",
              "value": "[name_operation.value]"
            }
          }
        ]
      }
    },
    "test": {
      "type": "[TEST-TYPE-NAME]",
      "parameters": [
        {
          "parameter": {
            "name": "existence_check",
            "type": "string",
            "value": "[existence_check.value]"
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
            "name": "registry_type",
            "type": "string",
            "value": "[registry_type.value]"
          }
        },
        {
          "parameter": {
            "name": "registry_type_operator",
            "type": "string",
            "value": "[registry_type_operator.value]"
          }
        },
        {
          "parameter": {
            "name": "registry_value",
            "type": "string",
            "value": "[registry_value.value]"
          }
        },
        {
          "parameter": {
            "name": "registry_value_datatype",
            "type": "string",
            "value": "[registry_value_datatype.value]"
          }
        },
        {
          "parameter": {
            "name": "registry_value_operator",
            "type": "string",
            "value": "[registry_value_operator.value]"
          }
        }
      ]
    }
  }