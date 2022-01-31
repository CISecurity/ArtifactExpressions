macos:launchd
=============

Description
-----------

The macos:launchd_test is used to check the status of daemons/agents loaded via the launchd service.

The launchd_object element is used by a launchd_test to define the daemon/agent to be evaluated.

The launchd_state element defines a value used to evaluate the result of a specific launchd_object item.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**macos.launchd_v1**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| check_existence             | string  | Defines how many items should be   |
|                             |         | collected. Typically set to        |
|                             |         | 'at_least_one_exists'.             |
+-----------------------------+---------+------------------------------------+
| label                       | string  | Specifies the daemon to be         |
|                             |         | queried.                           |
+-----------------------------+---------+------------------------------------+

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_exist
  - only_one_exists

NOTE: The ``label`` parameter is governed by a constraint allowing only the following values:
  - ^.+$

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - macos:launchd

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**macos.launchd_v1**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| check                       | string  | Defines how many collected items   |
|                             |         | must match the expected state.     |
|                             |         | Typically set to 'all'.            |
+-----------------------------+---------+------------------------------------+
| label_operation             | string  | Comparison operation. Typically    |
|                             |         | set to 'equals'.                   |
+-----------------------------+---------+------------------------------------+
| label_datatype              | string  | The data type of the value.        |
|                             |         | Typically set to 'string'.         |
+-----------------------------+---------+------------------------------------+
| label                       | string  | Specifies the name of the          |
|                             |         | agent/daemon used to create the    |
|                             |         | object.                            |
+-----------------------------+---------+------------------------------------+
| pid                         | integer | Specifies the process ID of the    |
|                             |         | of the daemon (if any).            |
+-----------------------------+---------+------------------------------------+
| status                      | integer | Specifies the last exit code of    |
|                             |         | the daemon (if any), or if $lt; 0, |
|                             |         | indicates the negative of the      |
|                             |         | signal that interrupted            |
|                             |         | processing. For example, a value   |
|                             |         | of -15 would indicate that the job |
|                             |         | was terminated via a SIGTERM.      |
+-----------------------------+---------+------------------------------------+
| pid_operation               | string  | Comparison operation. Typically    |
|                             |         | set to 'equals'.                   |
+-----------------------------+---------+------------------------------------+
| pid_datatype                | string  | The data type of the value.        |
|                             |         | Typically set to 'string'.         |
+-----------------------------+---------+------------------------------------+
| status_operation            | string  | Comparison operation. Typically    |
|                             |         | set to 'equals'.                   |
+-----------------------------+---------+------------------------------------+
| status_datatype             | string  | The data type of the value.        |
|                             |         | Typically set to 'string'.         |
+-----------------------------+---------+------------------------------------+

NOTE: The ``check`` parameter is governed by a constraint allowing only the following values:
  - all
  - at least one
  - none satisfy
  - only one

NOTE: The ``label_operation``, ``pid_operation``, and ``status_operation`` parameters are governed by a constraint allowing only the following values:
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

NOTE: The ``label_datatype``, ``pid_datatype``, and ``status_datatype`` parameters are governed by a constraint allowing only the following values:
  - boolean
  - float
  - int
  - string
  - version
  - set

Generated Content
~~~~~~~~~~~~~~~~~

**macos.launchd_v1**

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
              <ae:parameter dt="string" name="label">[label.value]</ae:parameter>
              <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
              <ae:parameter dt="string" name="label_operation">[label_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="label_datatype">[label_datatype.value]</ae:parameter>
              <ae:parameter dt="boolean" name="label">[label.value]</ae:parameter>
              <ae:parameter dt="integer" name="pid">[pid.value]</ae:parameter>
              <ae:parameter dt="integer" name="status">[status.value]</ae:parameter>
              <ae:parameter dt="string" name="pid_operation">[pid_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="pid_datatype">[pid_datatype.value]</ae:parameter>
              <ae:parameter dt="string" name="status_operation">[status_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="status_datatype">[status_datatype.value]</ae:parameter>
            </ae:parameters>
          </ae:test>
          <ae:profiles>
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1" />
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

For ``macos.launchd_v1`` ``macos.launchd_v1`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-content-ref
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]">
    </check-content-ref>
  </check>

OVAL
''''

Test

::

  <launchd_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    check="[check.value]"
    check_existence="[check_existence.value]"
    comment="[ARTIFACT-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"></object>
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"></state>
  </launchd_test>

Object

::

  <launchd_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    comment="[ARTIFACT-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    version="1">
    <label>[label.value]</label>
  </launchd_object>

State

::

  <launchd_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    comment="[ARTIFACT-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    version="1">
    <label
      datatype="[datatype.value]"
      operation="[operation.value]">
        [label.value]
    </label>
    <pid
      datatype="[datatype.value]"
      operation="[operation.value]">
        [pid.value]
    </pid>
    <status
      datatype="[datatype.value]"
      operation="[operation.value]">
        [status.value]
    </status>
  </launchd_state>

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
            name: "label"
            dt: "string"
            value: "[label.value]"
        - parameter:
            name: "check_existence"
            dt: "string"
            value: "[check_existence.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "check"
            dt: "string"
            value: "[check.value]"
        - parameter:
            name: "label_operation"
            dt: "string"
            value: "[label_operation.value]"
        - parameter:
            name: "label_datatype"
            dt: "string"
            value: "[label_datatype.value]"
        - parameter:
            name: "label"
            dt: "string"
            value: "[label.value]"
        - parameter:
            name: "pid"
            dt: "integer"
            value: "[pid.value]"
        - parameter:
            name: "status"
            dt: "integer"
            value: "[status.value]"
        - parameter:
            name: "pid_operation"
            dt: "string"
            value: "[pid_operation.value]"
        - parameter:
            name: "pid_datatype"
            dt: "string"
            value: "[pid_datatype.value]"
        - parameter:
            name: "pid_operation"
            dt: "string"
            value: "[pid_operation.value]"
        - parameter:
            name: "status_operation"
            dt: "string"
            value: "[status_operation.value]"
        - parameter:
            name: "status_datatype"
            dt: "string"
            value: "[status_datatype.value]"

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
              "name": "label",
              "dt": "string",
              "value": "[label.value]"
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
              "name": "label_operation",
              "dt": "string",
              "value": "[label_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "label_datatype",
              "dt": "string",
              "value": "[label_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "label",
              "dt": "string",
              "value": "[label.value]"
            }
          },
          {
            "parameter": {
              "name": "pid",
              "dt": "integer",
              "value": "[pid.value]"
            }
          },
          {
            "parameter": {
              "name": "status",
              "dt": "integer",
              "value": "[status.value]"
            }
          },
          {
            "parameter": {
              "name": "pid_operation",
              "dt": "string",
              "value": "[pid_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "pid_datatype",
              "dt": "string",
              "value": "[pid_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "status_operation",
              "dt": "string",
              "value": "[status_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "status_datatype",
              "dt": "string",
              "value": "[status_datatype.value]"
            }
          }
        ]
      }
    }
  }