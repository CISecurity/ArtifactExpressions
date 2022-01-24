windows:userright_v2
====================

Description
-----------

The windows:userright_v2 test is used to enumerate all of the trustees/SIDs that have been granted a specific user right/privilege.

The userright_object is used to collect the trustees/SIDs that have been granted a specific user right/privilege.

The userright_state element includes the name of a particular user right/privilege, the unique name and ID associated with the SID that has been granted the specified user right/privilege. 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**windows.userright_v2**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| userright                   | string  | The userright entity holds a       |
|                             |         | string that represents the name of |
|                             |         | a particular user right/privilege. |
+-----------------------------+---------+------------------------------------+
| check_existence             | string  | Defines how many items should be   |
|                             |         | collected.                         |
+-----------------------------+---------+------------------------------------+

NOTE: The ``userright`` parameter is governed by a constraint allowing only the following values:
  - SE_ASSIGNPRIMARYTOKEN_NAME
  - SE_AUDIT_NAME 
  - SE_BACKUP_NAME
  - SE_CHANGE_NOTIFY_NAME 
  - SE_CREATE_GLOBAL_NAME 
  - SE_CREATE_PAGEFILE_NAME
  - SE_CREATE_PERMANENT_NAME
  - SE_CREATE_SYMBOLIC_LINK_NAME
  - SE_CREATE_TOKEN_NAME
  - SE_DEBUG_NAME 
  - SE_ENABLE_DELEGATION_NAME 
  - SE_IMPERSONATE_NAME
  - SE_INC_BASE_PRIORITY_NAME 
  - SE_INCREASE_QUOTA_NAME
  - SE_INC_WORKING_SET_NAME
  - SE_LOAD_DRIVER_NAME
  - SE_LOCK_MEMORY_NAME
  - SE_MACHINE_ACCOUNT_NAME
  - SE_MANAGE_VOLUME_NAME 
  - SE_PROF_SINGLE_PROCESS_NAME
  - SE_RELABEL_NAME
  - SE_REMOTE_SHUTDOWN_NAME
  - SE_RESTORE_NAME
  - SE_SECURITY_NAME
  - SE_SHUTDOWN_NAME
  - SE_SYNC_AGENT_NAME
  - SE_SYSTEM_ENVIRONMENT_NAME
  - SE_SYSTEM_PROFILE_NAME
  - SE_SYSTEMTIME_NAME
  - SE_TAKE_OWNERSHIP_NAME
  - SE_TCB_NAME
  - SE_TIME_ZONE_NAME
  - SE_TRUSTED_CREDMAN_ACCESS_NAME
  - SE_UNDOCK_NAME
  - SE_UNSOLICITED_INPUT_NAME 
  - SE_BATCH_LOGON_NAME
  - SE_DENY_BATCH_LOGON_NAME
  - SE_DENY_INTERACTIVE_LOGON_NAME
  - SE_DENY_NETWORK_LOGON_NAME
  - SE_DENY_REMOTE_INTERACTIVE_LOGON_NAME 
  - SE_DENY_SERVICE_LOGON_NAME
  - SE_INTERACTIVE_LOGON_NAME 
  - SE_NETWORK_LOGON_NAME 
  - SE_REMOTE_INTERACTIVE_LOGON_NAME
  - SE_SERVICE_LOGON_NAME 
  - "" (empty string)

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - windows:userright_trustee_name_v2
  - windows:userright_trustee_sid_v2

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**windows.userright_trustee_name_v2**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| datatype                    | string  | datatype of the value.             |
+-----------------------------+---------+------------------------------------+
| operation                   | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+
| check                       | string  | Defines how many collected items   |
|                             |         | must match the expected state.     |
+-----------------------------+---------+------------------------------------+
| trustee_name                | string  | The trustee_name entity is the     |
|                             |         | unique name associated with the    |
|                             |         | SID that has been granted the      |
|                             |         | specified user right/privilege. A  |
|                             |         | trustee can be associated with a   |
|                             |         | user, group, or program (such as a |
|                             |         | Windows service). In Windows,      |
|                             |         | trustee names are                  |
|                             |         | case-insensitive. As a result, it  |
|                             |         | is recommended that the            |
|                             |         | case-insensitive operations are    |
|                             |         | used for this entity.              |
+-----------------------------+---------+------------------------------------+

**windows.userright_trustee_sid_v2**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| datatype                    | string  | datatype of the value.             |
+-----------------------------+---------+------------------------------------+
| operation                   | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+
| check                       | string  | Defines how many collected items   |
|                             |         | must match the expected state.     |
+-----------------------------+---------+------------------------------------+
| trustee_sid                 | string  | The trustee_sid entity identifies  |
|                             |         | the SID that has been granted the  |
|                             |         | specified user right/privilege.    |
+-----------------------------+---------+------------------------------------+

NOTE: The ``datatype`` parameter is governed by a constraint allowing only the following values:
	- boolean
	- float
	- int
	- string
	- version
	- set

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

**windows.userright_trustee_name_v2**

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
              <ae:parameter dt="string" name="userright">[userright.value]</ae:parameter>
              <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
              <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
              <ae:parameter dt="string" name="datatype">[datatype.data_type]</ae:parameter>
              <ae:parameter dt="string" name="trustee_name">[trustee_name.value]</ae:parameter>
            </ae:parameters>
          </ae:test>
          <ae:profiles>
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1" />
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_2" />
          </ae:profiles>
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  </xccdf:complex-check>

SCAP
^^^^

XCCDF
'''''

For ``windows.userright_v2 windows.userright_trustee_name_v2`` artifacts, the xccdf:check looks like this. There is no Value element in the xccdf for this Artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-content-ref 
      href="[BENCHMARK-TITLE]"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <userright_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </userright_test>

Object

::

  <userright_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <userright>[userright.value]</userright>
  </userright_object>

State

::

  <userright_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <userright>[userright.value]</userright>
    <trustee_name 
      operation="[operation.value]"
      datatype="[datatype.value]">
        [trustee_name.value]
    </trustee_name>
  </userright_state>

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
            name: "userright"
            dt: "string"
            value: "[userright.value]"
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
            name: "operation"
            dt: "string"
            value: "[operation.value]"
        - parameter: 
            name: "datatype"
            dt: "string"
            value: "[datatype.value]"
        - parameter:
            name: "trustee_name"
            dt: "string"
            value: "[trustee_name.value]"

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
              "name": "userright",
              "type": "string",
              "value": "[userright.value]"
            }
          },
          {
            "parameter": {
              "name": "check_existence",
              "type": "string",
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
              "type": "string",
              "value": "[check.value]"
            }
          },
          {
            "parameter": {
              "name": "operation",
              "type": "string",
              "value": "[operation.value]"
            }
          },
          {
            "parameter": {
              "name": "datatype",
              "type": "string",
              "value": "[datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "trustee_name",
              "type": "string",
              "value": "[trustee_name.value]"
            }
          }
        ]
      }
    }
  }

Generated Content
~~~~~~~~~~~~~~~~~

**windows.userright_trustee_sid_v2**

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
              <ae:parameter dt="string" name="userright">[userright.value]</ae:parameter>
              <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
              <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
              <ae:parameter dt="string" name="datatype">[datatype.data_type]</ae:parameter>
              <ae:parameter dt="string" name="trustee_sid">[trustee_sid.value]</ae:parameter>
            </ae:parameters>
          </ae:test>
          <ae:profiles>
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1" />
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_2" />
          </ae:profiles>
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  </xccdf:complex-check>

SCAP
^^^^

XCCDF
'''''

For ``windows.userright_v2 windows.userright_trustee_sid_v2`` artifacts, the xccdf:check looks like this. There is no Value element in the xccdf for this Artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-content-ref 
      href="[BENCHMARK-TITLE]"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <userright_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </userright_test>

Object

::

  <userright_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <userright>[userright.value]</userright>
  </userright_object>

State

::

  <userright_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <trustee_sid 
      operation="[operation.value]"
      datatype="[datatype.value]">
        [trustee_sid.value]
    </trustee_sid>
  </userright_state>

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
            name: "userright"
            dt: "string"
            value: "[userright.value]"
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
            name: "operation"
            dt: "string"
            value: "[operation.value]"
        - parameter: 
            name: "datatype"
            dt: "string"
            value: "[datatype.value]"
        - parameter:
            name: "trustee_sid"
            dt: "string"
            value: "[trustee_sid.value]"


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
              "name": "userright",
              "type": "string",
              "value": "[userright.value]"
            }
          },
          {
            "parameter": {
              "name": "check_existence",
              "type": "string",
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
              "type": "string",
              "value": "[check.value]"
            }
          },
          {
            "parameter": {
              "name": "operation",
              "type": "string",
              "value": "[operation.value]"
            }
          },
          {
            "parameter": {
              "name": "datatype",
              "type": "string",
              "value": "[datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "trustee_sid",
              "type": "string",
              "value": "[trustee_sid.value]"
            }
          }
        ]
      }
    }
  }  