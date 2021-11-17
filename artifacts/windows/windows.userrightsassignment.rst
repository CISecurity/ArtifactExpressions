windows.userrightsassignment
============================

Description
  -----------

The userright_test is used to enumerate all of the trustees/SIDs that
have been granted a specific user right/privilege.

Technical Details
  -----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

========= ====== =====================================
Name      Type   Description
========= ====== =====================================
userright String The user right setting to be audited.
========= ====== =====================================

| NOTE: This parameter is governed by a constraint allowing only the
  following values: - SE_ASSIGNPRIMARYTOKEN_NAME
| - SE_AUDIT_NAME - SE_BACKUP_NAME
| - SE_CHANGE_NOTIFY_NAME - SE_CREATE_GLOBAL_NAME -
  SE_CREATE_PAGEFILE_NAME
| - SE_CREATE_PERMANENT_NAME
| - SE_CREATE_SYMBOLIC_LINK_NAME
| - SE_CREATE_TOKEN_NAME
| - SE_DEBUG_NAME - SE_ENABLE_DELEGATION_NAME - SE_IMPERSONATE_NAME
| - SE_INC_BASE_PRIORITY_NAME - SE_INCREASE_QUOTA_NAME
| - SE_INC_WORKING_SET_NAME
| - SE_LOAD_DRIVER_NAME
| - SE_LOCK_MEMORY_NAME
| - SE_MACHINE_ACCOUNT_NAME
| - SE_MANAGE_VOLUME_NAME - SE_PROF_SINGLE_PROCESS_NAME
| - SE_RELABEL_NAME
| - SE_REMOTE_SHUTDOWN_NAME
| - SE_RESTORE_NAME
| - SE_SECURITY_NAME
| - SE_SHUTDOWN_NAME
| - SE_SYNC_AGENT_NAME
| - SE_SYSTEM_ENVIRONMENT_NAME
| - SE_SYSTEM_PROFILE_NAME
| - SE_SYSTEMTIME_NAME
| - SE_TAKE_OWNERSHIP_NAME
| - SE_TCB_NAME
| - SE_TIME_ZONE_NAME - SE_TRUSTED_CREDMAN_ACCESS_NAME
| - SE_UNDOCK_NAME
| - SE_UNSOLICITED_INPUT_NAME - SE_BATCH_LOGON_NAME
| - SE_DENY_BATCH_LOGON_NAME
| - SE_DENY_INTERACTIVE_LOGON_NAME
| - SE_DENY_NETWORK_LOGON_NAME
| - SE_DENY_REMOTE_INTERACTIVE_LOGON_NAME - SE_DENY_SERVICE_LOGON_NAME
| - SE_INTERACTIVE_LOGON_NAME - SE_NETWORK_LOGON_NAME -
  SE_REMOTE_INTERACTIVE_LOGON_NAME
| - SE_SERVICE_LOGON_NAME - "" (empty string)

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - existence_test
  - equals
  - pattern match

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

existence_test
^^^^^^^^^^^^^^

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| value                               | String      | the value        |
|                                     |             | included within  |
|                                     |             | the set of       |
|                                     |             | results/ value   |
|                                     |             | to be tested     |
+-------------------------------------+-------------+------------------+

equals
^^^^^^

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| data_type                           | String      | datatype of the  |
|                                     |             | value            |
+-------------------------------------+-------------+------------------+
| value                               | String      | the value        |
|                                     |             | included within  |
|                                     |             | the set of       |
|                                     |             | results/ value   |
|                                     |             | to be tested     |
+-------------------------------------+-------------+------------------+

pattern match
^^^^^^^^^^^^^

========= ====== ================================
Name      Type   Description
========= ====== ================================
data_type String datatype of the value
value     String Regular expression to be matched
========= ====== ================================

data_type NOTE: This parameter is governed by a constraint allowing only
the following values: - boolean - float - int - string - version - set

Generated Content
~~~~~~~~~~~~~~~~~

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

   <xccdf:complex-check operator="AND">
       <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
           <xccdf:check-content>
               <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION_NUMBER]">
                   <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
                   <ae:title>[RECOMMENDATION TITLE]</ae:title>
                   <ae:artifact type="windows.userrightsassignment">
                       <ae:parameters>
                           <ae:parameter dt="string" name="userright">[SETTING CONSTRAINT VALUE]</ae:parameter>
                       </ae:parameters>
                   </ae:artifact>
                   <ae:test type="[TestType Name]">
                       <ae:parameters>
                           <ae:parameter dt="string" name="value">[TestType.value]</ae:parameter>
                           <ae:parameter dt="string" name="data_type">[TestType.data_type]</ae:parameter>
                       </ae:parameters>
                   </ae:test>
               </ae:artifact_expression>
           </xccdf:check-content>
       </xccdf:check>
   </xccdf:complex-check>

SCAP
^^^^

XCCDF
'''''

For ``windows.userrightsassignment`` artifacts, an XCCDF Value element
is generated:

::

   <Value id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" 
          operator="[TestType Name]" type="[number|boolean]">
     <title>[RECOMMENDATION TITLE]</title>
     <description>This value is used in Rule: [RECOMMENDATION TITLE]</description>
     <value>[TestType.value.value]</value>
   </Value>

OVAL
''''

Test

::

   <userright_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
               id="oval:org.cisecurity.benchmarks.windows_8.1:tst: <userright_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
                                                                              id="oval:org.cisecurity.benchmarks.windows_8.1:obj:73694"
                                                                              comment="Ensure &apos;sedenyinteractivelogonright&apos; is set to &apos;Guests&apos;"
                                                                              version="[version.value]">
                                                                              <userright operation="equals">SE_DENY_INTERACTIVE_LOGON_NAME</userright>
                                                                          </userright_object>"
               check_existence="at_least_one_exists" check="at least one"
               comment="[RECOMMENDATION_TITLE]"
               version="[version.value]">
               <object object_ref="oval:org.cisecurity.benchmarks.windows_8.1:obj:ARTIFACT-OVAL-ID"/>
               <state state_ref="oval:org.cisecurity.benchmarks.windows_8.1:ste:ARTIFACT-OVAL-ID"/>
   </userright_test>

Object

::

   <userright_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
               id="oval:org.cisecurity.benchmarks.windows_8.1:obj:ARTIFACT_OVAL_ID"
               comment="[RECOMMENDATION_TITLE]"
               version="[version.value]">
               <userright operation="[TestType Name]">[SETTING_CONSTRAINT_VALUE]</userright>
   </userright_object>

State

::

   <userright_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
               id="oval:org.cisecurity.benchmarks.windows_8.1:ste:ARTIFACT_OVAL_ID"
               comment="[RECOMMENDATION_TITLE]"
               version="[version.value]">
               <trustee_sid operation="[TestType Name]" datatype="[TestType.data_type]">[TestType.data_type.value]</trustee_sid>
   </userright_state>

YAML
^^^^

::

  - artifact-expression:
       artifact-unique-id: [ARTIFACT-OVAL-ID]
       artifact-title: [RECOMMENDATION TITLE]
       artifact:
         type: windows.userrightsassignment
         parameters:
         - parameter: 
             name: userright
             type: string
             value: [ARTIFACT TYPE PARAMETER VALUE]
       test:
         type: [TestType Name]
         parameters:
         - parameter:
             name: value
             type: string
             value: [TestType.value.value]
         - parameter: 
             name: data_type
             type: string
             value: [TestType.data_type.value]

JSON
^^^^

::

   "artifact-expression": {
     "artifact-unique-id": [ARTIFACT-OVAL-ID],
     "artifact-title": [RECOMMENDATION TITLE],
     "artifact": {
       "type": "windows.userrightsassignment",
       "parameters": [
         {
           "parameter": {
             "name": "userright",
             "type": "string",
             "value": [ARTIFACT TYPE PARAMETER VALUE]
           }
         }
       ]
     },
     "test": {
       "type": [TestType Name],
       "parameters": [
         {
           "parameter": {
             "name": "value",
             "type": "string",
             "value": [TestType.value.value]
           }
         },
         {
           "parameter": {
             "name": "data_type",
             "type": "string",
             "value": [TestType.data_type.value]
           }
         }
       ]
     }
   }
