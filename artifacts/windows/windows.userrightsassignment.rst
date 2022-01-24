Windows: User Rights Assignment
===============================

Description
-----------

The Windows: User Rights Assignment test is used to enumerate all of the trustees/SIDs that
have been granted a specific user right/privilege.

The userright_object element is used by a userright_test to collect the trustees/SIDs that have been granted a specific user right/privilege.

The userright_state element includes the name of a particular user right/privilege, the unique name and ID associated with the SID that has been granted the specified user right/privilege.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**windows.userrightsassignment**

========= ====== =====================================
Name      Type   Description
========= ====== =====================================
userright string The user right setting to be audited.
========= ====== =====================================

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

  - Existence Test
  - Equals
  - Pattern Match

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**existence_test**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| value                       | string  | The value included within the set  |
|                             |         | of results / value to be tested.   |
+-----------------------------+---------+------------------------------------+

| **equals**
| **pattern match**
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

**existence_test**

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
          <ae:artifact type="windows.userrightsassignment">
            <ae:parameters>
              <ae:parameter dt="string" name="userright">[userright.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
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

For ``windows.userrightsassignment existence_test`` artifacts, the xccdf:check looks like this. There is no Value element in the xccdf for this Artifact.

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
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </userright_test>

Object

::

  <userright_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT_OVAL_ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <userright operation="equals">[userright.value]</userright>
  </userright_object>

State

::

  N/A

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
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "value"
            dt: "string"
            value: "[value.value]"

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact-title": "[ARTIFACT-TITLE]",
      "artifact": {
        "type": "windows.userrightsassignment",
        "parameters": [
          {
            "parameter": {
              "name": "userright",
              "type": "string",
              "value": "[userright.value]"
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
          }
        ]
      }
    }
  }

Generated Content
~~~~~~~~~~~~~~~~~

| **equals**
| **pattern match**
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
          <ae:artifact type="windows.userrightsassignment">
            <ae:parameters>
              <ae:parameter dt="string" name="userright">[userright.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
              <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
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

For ``windows.userrightsassignment equals`` or ``pattern match`` artifacts, the xccdf:check looks like this. There is no Value element in the xccdf for this Artifact.

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
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </userright_test>

Object

::

  <userright_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT_OVAL_ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <userright operation="equals">[userright.value]</userright>
  </userright_object>

State

::

  <userright_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT_OVAL_ID]"
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
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "value"
            dt: "string"
            value: "[value.value]"
        - parameter:
            name: "datatype"
            dt: "string"
            value: "[datatype.value]"

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact-title": "[ARTIFACT-TITLE]",
      "artifact": {
        "type": "windows.userrightsassignment",
        "parameters": [
          {
            "parameter": {
              "name": "userright",
              "type": "string",
              "value": "[userright.value]"
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
              "name": "datatype",
              "type": "string",
              "value": "[datatype.value]"
            }
          }
        ]
      }
    }
  }
