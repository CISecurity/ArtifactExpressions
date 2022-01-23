macos:softwareupdate
====================

Description
-----------

The macos:softwareupdate_test is used to check the status of automatic software updates on MacOSX.

The softwareupdate_object element is used by a softwareupdate_test to access automatic software update information.

The softwareupdate_state element makes it possible to make assertions about the state of automatic software updates.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**macos.softwareupdate_v1**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| check_existence             | string  | Defines how many items should be   |
|                             |         | collected. Typically set to        |
|                             |         | 'at_least_one_exists'.             |
+-----------------------------+---------+------------------------------------+

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_exist
  - only_one_exists

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - macos:softwareupdate

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**macos.softwareupdate_v1**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| check                       | string  | Defines how many collected items   |
|                             |         | must match the expected state.     |
|                             |         | Typically set to 'all'.            |
+-----------------------------+---------+------------------------------------+
| schedule_operation          | string  | Comparison operation. Typically    |
|                             |         | set to 'equals'.                   |
+-----------------------------+---------+------------------------------------+
| schedule_datatype           | string  | The data type of the value.        |
|                             |         | Typically set to 'string'.         |
+-----------------------------+---------+------------------------------------+
| schedule                    | boolean | Specifies whether automatic        |
|                             |         | checking is enabled (true).        |
+-----------------------------+---------+------------------------------------+
| software_title              | string  | Specifies the title string for an  |
|                             |         | available (not installed) software |
|                             |         | update. Cannot be blank.           |
+-----------------------------+---------+------------------------------------+
| software_title_operation    | string  | Specifies the title string for an  |
|                             |         | available (not installed) software |
|                             |         | update. Typically set to 'equals'. |
+-----------------------------+---------+------------------------------------+
| software_title_datatype     | string  | The data type of the value.        |
|                             |         | Typically set to 'string'.         |
+-----------------------------+---------+------------------------------------+

NOTE: The ``check`` parameter is governed by a constraint allowing only the following values:
  - all
  - at least one
  - none satisfy
  - only one

NOTE: The ``schedule_operation`` and ``software_title_operation`` parameters are governed by a constraint allowing only the following values:
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

NOTE: The ``schedule_datatype`` and ``software_title_datatype`` parameters are governed by a constraint allowing only the following values:
  - boolean
  - float
  - int
  - string
  - version
  - set

NOTE: The ``schedule`` parameter is governed by a constraint allowing only the following values:
  - true
  - false

NOTE: The ``software_title`` parameter is governed by a constraint allowing only the following values:
  - ^.+$

Generated Content
~~~~~~~~~~~~~~~~~

**macos.softwareupdate_v1**

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
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
              <ae:parameter dt="string" name="schedule_operation">[schedule_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="schedule_datatype">[schedule_datatype.value]</ae:parameter>
              <ae:parameter dt="boolean" name="schedule">[schedule.value]</ae:parameter>
              <ae:parameter dt="string" name="software_title">[software_title.value]</ae:parameter>
              <ae:parameter dt="string" name="software_title_operation">[software_title_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="software_title_datatype">[software_title_datatype.value]</ae:parameter>
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

For ``macos.softwareupdate_v1`` artifacts, the xccdf:check looks like this. There is no Value in the xccdf for this Artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-content-ref 
      href="[BENCHMARK-TITLE]"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]">
    </check-content-ref>
  </check>

OVAL
''''

Test

::

  <softwareupdate_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    check="[check.value]"
    check_existence="[check_existence.value]"
    comment="[ARTIFACT-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </softwareupdate_test>

Object

::

  <softwareupdate_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    comment="[ARTIFACT-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    version="1" />

State

::

  <softwareupdate_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    comment="[ARTIFACT-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    version="1">
    <schedule 
      datatype="[datatype.value]"
      operation="[operation.value]">
        [schedule.value]
    </schedule>
    <software_title 
      datatype="[datatype.value]"
      operation="[operation.value]">
        [software_title.value]
    </software_title>
  </softwareupdate_state>

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
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "check"
            dt: "string"
            value: "[check.value]"
        - parameter:
            name: "schedule_operation"
            dt: "string"
            value: "[schedule_operation.value]"
        - parameter:
            name: "schedule_datatype"
            dt: "string"
            value: "[schedule_datatype.value]"
        - parameter:
            name: "schedule"
            dt: "boolean"
            value: "[schedule.value]"
        - parameter:
            name: "software_title"
            dt: "string"
            value: "[software_title.value]"
        - parameter:
            name: "software_title_operation"
            dt: "string"
            value: "[software_title_operation.value]"
        - parameter:
            name: "software_title_datatype"
            dt: "string"
            value: "[software_title_datatype.value]"

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
              "name": "schedule_operation",
              "dt": "string",
              "value": "[schedule_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "schedule_datatype",
              "dt": "string",
              "value": "[schedule_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "schedule",
              "dt": "boolean",
              "value": "[schedule.value]"
            }
          },
          {
            "parameter": {
              "name": "software_title",
              "dt": "string",
              "value": "[software_title.value]"
            }
          },
          {
            "parameter": {
              "name": "software_title_operation",
              "dt": "string",
              "value": "[software_title_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "software_title_datatype",
              "dt": "string",
              "value": "[software_title_datatype.value]"
            }
          }
        ]
      }
    }
  }