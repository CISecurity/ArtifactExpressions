Windows: User Rights Assignment (Deny)
======================================

Description
-----------

The Windows: User Rights Assignment (Deny) test is used to enumerate all of the trustees/SIDs that
have been granted a specific user right/privilege.

The userright_object element is used by a userright_test to collect the trustees/SIDs that have been granted a specific user right/privilege.

The userright_state element includes the name of a particular user right/privilege, the unique name and ID associated with the SID that has been granted the specified user right/privilege.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**windows.userrightsassignmentdeny**

========= ====== =====================================
Name      Type   Description
========= ====== =====================================
userright String The user right setting to be audited.
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

  - Set White List

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**set.white_list_v1**

========= ====== =========================================
Name      Type   Description
========= ====== =========================================
data_type String datatype of the value.
values    String Comma separated list of permitted values.
========= ====== =========================================

NOTE: The ``data_type`` parameter is governed by a constraint allowing only the following values:
	- boolean
	- float
	- int
	- string
	- version
	- set

Generated Content
~~~~~~~~~~~~~~~~~

**set.white_list_v1**

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
          <ae:artifact type="windows.userrightsassignmentdeny">
            <ae:parameters>
              <ae:parameter dt="string" name="userright">[userright.value]</ae:parameter>
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

For ``windows.userrightsassignmentdeny`` ``set.white_list_v1`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this artifact. 

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-content-ref 
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

   <userright_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="at least one"
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
      operation="equals"
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
              "name": "data_type",
              "type": "string",
              "value": "[data_type.value]"
            }
          }
        ]
      }
    }
  }
