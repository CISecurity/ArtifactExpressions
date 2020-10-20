# windows.userright_v2

## Description
The userright_test is used to enumerate all of the trustees/SIDs that have been granted a specific user right/privilege.

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| userright | String | The userright entity holds a string that represents the name of a particular user right/privilege.	|
| check_existence | String | Defines how many items should be collected.	|

NOTE: This parameter is governed by a constraint allowing only the following values:
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

### Supported Test Types
- windows.userright_trustee_name_v2
- windows.userright_trustee_sid_v2

### Generated Content
#### XCCDF+AE
This is what the AE check looks like, inside a Rule, in the XCCDF

```
<xccdf:complex-check operator="OR">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
        <xccdf:check-content>
            <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_14.1.1">
                <ae:artifact_oval_id>[ARTIFACT_OVAL_ID]</ae:artifact_oval_id>
                <ae:title>[RECOMMENDATION_TITLE]</ae:title>
                <ae:artifact type="windows.userright_v2">
                    <ae:parameters>
                        <ae:parameter dt="string" name="userright"
                            >[SETTING_CONSTRAINT_VALUE]</ae:parameter>
                        <ae:parameter dt="string" name="check_existence"
                            >at_least_one_exists</ae:parameter>
                    </ae:parameters>
                </ae:artifact>
                <ae:test type="[Testtype Name]">
                    <ae:parameters>
                        <ae:parameter dt="string" name="check">all</ae:parameter>
                        <ae:parameter dt="string" name="operation">[TestType.value]</ae:parameter>
                        <ae:parameter dt="string" name="datatype">[TestType.data_type]</ae:parameter>
                        <ae:parameter dt="string" name="[PARAMETER NAME]"
                            >[ARTIFACT TYPE PARAMETER VALUE]</ae:parameter>
                    </ae:parameters>
                </ae:test>
            </ae:artifact_expression>
        </xccdf:check-content>
    </xccdf:check>
</xccdf:complex-check>
```

#### SCAP

##### OVAL
###### Test

```
<userright_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
            id="oval:org.cisecurity.benchmarks.windows_8.1:tst:ARTIFACT-OVAL-ID"
            check_existence="at_least_one_exists" check="all"
            comment="[RECOMMENDATION_TITLE]"
            version="1">
            <object object_ref="oval:org.cisecurity.benchmarks.windows_8.1:obj:ARTIFACT-OVAL-ID"/>
            <state state_ref="oval:org.cisecurity.benchmarks.windows_8.1:ste:ARTIFACT-OVAL-ID"/>
</userright_test>
```

###### Object

```
<userright_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
      id="oval:org.cisecurity.benchmarks.windows_8.1:obj:ARTIFACT-OVAL-ID"
            comment="[RECOMMENDATION_TITLE]"
            version="1">
            <userright>[ARTIFACT_PARAMETER_NAME]</userright>
        </userright_object>
```
###### State

```
<userright_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
            id="oval:org.cisecurity.benchmarks.windows_8.1:ste:ARTIFACT-OVAL-ID"
            comment="[RECOMMENDATION TITLE]"
            version="1">
            <userright>[ARTIFACT_PARAMETER_NAME]</userright>
            <trustee_name operation="[TEST_TYPE_NAME]" datatype="string">[PARAMETER_VALUE]</trustee_name>
        </userright_state>
```

#### YAML

```
- artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: windows.userright_v2
      parameters:
      - parameter: 
          name: [PARAMETER_NAME]
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
```

#### JSON

```
"artifact-expression": {
  "artifact-unique-id": [ARTIFACT-OVAL-ID],
  "artifact-title": [RECOMMENDATION TITLE],
  "artifact": {
    "type": "windows.userright_v2",
    "parameters": [
      {
        "parameter": {
          "name": "[PARAMETER_NAME]",
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
``` 