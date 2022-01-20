macos:nvram
===========

Description
-----------

The macos:nvram test pulls data from the 'nvram -p' output.

The nvram_object element is used by a nvram test to define the object to be evaluated. Each object extends the standard ObjectType as defined in the oval-definitions-schema and one should refer to the ObjectType description for more information. The common set element allows complex objects to be created using filters and set logic. Again, please refer to the description of the set element in the oval-definitions-schema.

The nvram state element pulls data from the 'nvram -p' output.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**macos.nvram_v1**

+-------------------------------------+-------------+-------------------------------------+
| Name                                | Type        | Description                         |
+=====================================+=============+=====================================+
| check_existence                     | string      | Defines how many items should be    |
|                                     |             | collected. Typically set to 'at     |
|                                     |             | least one_exists'.                  |
+-------------------------------------+-------------+-------------------------------------+
| nvram_var                           | string      | This specifies the nvram variable   |
|                                     |             | to check. Cannot be blank.          |
+-------------------------------------+-------------+-------------------------------------+

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values:
   -  all_exist
   -  any_exist
   -  at_least_one_exists
   -  none_exist
   -  only_one_exists

NOTE: The ``nvram_var`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

-  macos.nvram_v1

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**macos.nvram_v1**

+-------------------------------------+-------------+-----------------------------------+
| Name                                | Type        | Description                       |
+=====================================+=============+===================================+
| check                               | string      | Defines how many collected items  |
|                                     |             | must match the expected state.    |
|                                     |             | Typically set to 'all'.           |
+-------------------------------------+-------------+-----------------------------------+
| nvram_value_operation               | string      | Comparison operation. Typically   |
|                                     |             | set to 'equals'.                  |
+-------------------------------------+-------------+-----------------------------------+
| nvram_value_datatype                | string      | The data type of the value.       |
|                                     |             | Typically set to 'string'.        |
+-------------------------------------+-------------+-----------------------------------+
| nvram_value                         | string      | This is the value of the          |
|                                     |             | associated nvram variable.        |
+-------------------------------------+-------------+-----------------------------------+
| nvram_var                           | string      | This specifies the nvram variable |
|                                     |             | to check.                         |
+-------------------------------------+-------------+-----------------------------------+
| nvram_var_operation                 | string      | Comparison operation.             |
+-------------------------------------+-------------+-----------------------------------+
| nvram_var_datatype                  | string      | Datatype.                         |
+-------------------------------------+-------------+-----------------------------------+

NOTE: The ``check`` parameter is governed by a constraint allowing only the following values:
   -  all
   -  at least one
   -  none satisfy
   -  only one

NOTE: The ``nvram_value_operation`` and ``nvram_var_operation`` parameters are governed by a constraint allowing only the following values:
   -  equals
   -  not equal
   -  case insensitive equals
   -  case insensitive not equal
   -  greater than
   -  less than
   -  greater than or equal
   -  less than or equal
   -  bitwise and
   -  bitwise or
   -  pattern match
   -  subset of
   -  superset of

NOTE: The ``nvram_value_datatype`` and ``nvram_var_datatype`` parameters are governed by a constraint allowing only the following values:
   -  boolean
   -  float
   -  int
   -  string
   -  version
   -  set

Generated Content
~~~~~~~~~~~~~~~~~

**macos.nvram_v1**

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
              <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
              <ae:parameter dt="string" name="nvram_var">[nvram_var.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
              <ae:parameter dt="string" name="nvram_value_operation">equals</ae:parameter>
              <ae:parameter dt="string" name="nvram_value_datatype">string</ae:parameter>
              <ae:parameter dt="string" name="nvram_value">This is the value of the associated nvram variable.</ae:parameter>
              <ae:parameter dt="string" name="nvram_var">This specifies the nvram variable to check.</ae:parameter>
              <ae:parameter dt="string" name="nvram_var_operation">equals</ae:parameter>
              <ae:parameter dt="string" name="nvram_var_datatype">string</ae:parameter>
            </ae:parameters>
          </ae:test>
          <ae:profiles>
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1"/>
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_2"/>
          </ae:profiles>
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  </xccdf:complex-check>

SCAP
^^^^

XCCDF
'''''

For ``macos.nvram_v1`` artifacts, the xccdf:check looks like this. There is no Value in the xccdf for this Artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-content-ref
      href="[BENCHMARK-NAME]"
        name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]">
    </check-content-ref>
  </check>

OVAL
''''

Test

::

  <nvram_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    check="[check.value]"
    check_existence="[check_existence.value]"
    comment="[ARTIFACT-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </nvram_test>

Object

::

  <nvram_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    comment="[ARTIFACT-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    version="1">
    <nvram_var>
        [nvram_var.value]
    </nvram_var>
  </nvram_object>

State

::

  <nvram_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    comment="[ARTIFACT-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    version="1">
    <nvram_var
      datatype="[datatype.value]"
      operation="[operation.value]">
        [nvram_var.value]
    </nvram_var>
    <nvram_value
      datatype="[datatype.value]"
      operation="[operation.value]">
        [nvram_value.value]
    </nvram_value>
  </nvram_state>

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
            name: "nvram_var"
            dt: "string"
            value: "[nvram_var.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "check"
            dt: "string"
            value: "[check.value]"
        - parameter:
            name: "nvram_value_operation"
            dt: "string"
            value: "[nvram_value_operation.value]"
        - parameter:
            name: "nvram_value_datatype"
            dt: "string"
            value: "[nvram_value_datatype.value]"
        - parameter:
            name: "nvram_value"
            dt: "string"
            value: "[nvram_value.value]"
        - parameter:
            name: "nvram_var"
            dt: "string"
            value: "[nvram_var.value]"
        - parameter:
            name: "nvram_var_operation"
            dt: "string"
            value: "[nvram_var_operation.value]"
        - parameter:
            name: "nvram_var_datatype"
            dt: "string"
            value: "[nvram_var_datatype.value]"
  
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
              "name": "nvram_var",
              "dt": "string",
              "value": "[nvram_var.value]"
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
              "name": "nvram_value_operation",
              "dt": "string",
              "value": "[nvram_value_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "nvram_value_datatype",
              "dt": "string",
              "value": "[nvram_value_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "nvram_value",
              "dt": "string",
              "value": "[nvram_value.value]"
            }
          },
          {
            "parameter": {
              "name": "nvram_var",
              "dt": "string",
              "value": "[nvram_var.value]"
            }
          },
          {
            "parameter": {
              "name": "nvram_var_operation",
              "dt": "string",
              "value": "[nvram_var_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "nvram_var_datatype",
              "dt": "string",
              "value": "[nvram_var_datatype.value]"
            }
          }
        ]
      }
    }
  }