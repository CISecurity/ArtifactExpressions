macos:nvram
===========

Description
-----------

The macos:nvram test pulls data from the 'nvram -p' output.

The nvram object element is used by a nvram test to define the object to be evaluated.

The nvram state element pulls data from the 'nvram -p' output.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**macos.nvram_v1**

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| check_existence                     | string      | Defines how many |
|                                     |             | items should be  |
|                                     |             | collected.       |
+-------------------------------------+-------------+------------------+
| nvram_var                           | string      | Specifies the    |
|                                     |             | nvram variable   |
|                                     |             | to check.        |
|                                     |             |                  |
+-------------------------------------+-------------+------------------+

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

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| check                               | string      | Defines how many |
|                                     |             | collected items  |
|                                     |             | must match the   |
|                                     |             | expected state.  |
+-------------------------------------+-------------+------------------+
| operation                           | string      | Comparison       |
|                                     |             | operation.       |
+-------------------------------------+-------------+------------------+
| datatype                            | string      | The data type of |
|                                     |             | the value.       |
+-------------------------------------+-------------+------------------+
| nvram_value                         | string      | This is the      |
|                                     |             | value of the     |
|                                     |             | associated       |
|                                     |             | nvram variable.  |
+-------------------------------------+-------------+------------------+

NOTE: The ``check`` parameter is governed by a constraint allowing only the following values:
   -  all
   -  at least one
   -  none satisfy
   -  only one

NOTE: The ``operation`` parameter is governed by a constraint allowing only the following values:
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

NOTE: The ``datatype`` parameter is governed by a constraint allowing only the following values:
   -  boolean
   -  float
   -  int
   -  string
   -  version
   -  set

NOTE: The ``nvram_value`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

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
          <ae:title>[RECOMMENDATION-TITLE]</ae:title>
          <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
              <ae:parameter dt="string" name="nvram_var">[nvram_var.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
              <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
              <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
              <ae:parameter dt="string" name="nvram_value">[nvram_value.value]</ae:parameter>
            </ae:parameters>
          </ae:test>
          <ae:profiles>
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

For ``macos.nvram_v1`` artifacts, the xccdf:check looks like this.
There is no Value in the xccdf for this Artifact.

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
    comment="[RECOMMENDATION-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    version="[version.value]">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </nvram_test>

Object

::

  <nvram_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    comment="[RECOMMENDATION-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    version="[version.value]">
    <nvram_var>
        [nvram_var.value]
    </nvram_var>
  </nvram_object>

State

::

  <nvram_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    comment="[RECOMMENDATION-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    version="[version.value]">
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
    artifact_title: "[RECOMMENDATION-TITLE]"
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
            name: "operation"
            dt: "string"
            value: "[operation.value]"
        - parameter:
            name: "datatype"
            dt: "string"
            value: "[datatype.value]"
        - parameter:
            name: "nvram_value"
            dt: "string"
            value: "[nvram_value.value]"
  
JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact_title": "[RECOMMENDATION-TITLE]",
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
              "name": "nvram_value",
              "dt": "string",
              "value": "[nvram_value.value]"
            }
          }
        ]
      }
    }
  }