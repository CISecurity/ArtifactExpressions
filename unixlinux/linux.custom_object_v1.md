# linux.custom_object_v1

## Description
The webconfig_test is used to check the status of Gatekeeper and any unsigned applications that have been granted execute permission.

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| object | String | The custom object being implemented |

object
NOTE: This parameter is governed by a constraint allowing only the following values:

- N/A
- All World Writable Directories Have Sticky Bit Set
- No World Writable Files Exist|There Are No Unconfined Daemons
- No Servers Listening On Port 25
- System Accounts Disabled|System Accounts Locked
- Default Group Set For root User
- No Un-owned Files and Directories|No Un-grouped Files and Directories
- systemd Does Not Default To graphical.target
- rsyslog Log Files Have Correct Permissions
- syslog Log Files Have Correct Permissions
- auditd Collects Privileged Command Use
- Check For Duplicate UIDs
- Check For Duplicate GIDs
- Check For Duplicate User Names
- Check For Duplicate Group Names
- No User Home Directories Have Permissions ----w-rwx
- No User Dot Files Have Permissions ----w--w-
- No User .netrc Files Have Permissions ---rwxrwx
- No User Home Directories Contain .rhost Files
- No User Home Directories Contain .netrc Files
- No User Home Directories Contain .forward Files
- All Groups In /etc/passwd Exist In /etc/group
- All User Home Directories Exist
- /etc/profile.d/* contains "umask 077"
- Check That Reserved UIDs Are Assigned to System Accounts
- Root Path Does Not Include ""
- Root Path Does Not Include "."
- Root Path Directories Are Owned By UID 0 And Not Writable By Group Or Other
- Check User Home Directory Ownership
- AppArmor has loaded profiles
- No AppArmor Profiles Are In Complain Mode
- No AppArmor Processes Are Unconfined
- Shadow Group is Empty
- No Users Have Shadow Group as Primary Group
- Ensure the X Window system is not installed
- Ensure no users with a Password have password expiration over 90 days
- Ensure no users with a Password have password expiration over 365 days
- Ensure no users with a Password have password change minimum under 7 days
- Ensure no users with a Password have password expiration warning under 7 days
- Ensure no users with a Password have password inactivation over 30 days
- chronyd is running as chrony user
- Firewall Rule Exists For All Open Ports
- Ensure all users with a Password have password change date in the past


### Supported Test Types
- null_test_v1

### Generated Content
#### XCCDF+AE
This is what the AE check looks like, inside a Rule, in the XCCDF

```
<xccdf:complex-check operator="AND">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
        <xccdf:check-content>
            <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_2.2.15.1">
                <ae:artifact_oval_id>[ARTIFACT_OVAL_ID]</ae:artifact_oval_id>
                <ae:title>[RECOMMENDATION_TITLE]"</ae:title>
                <ae:artifact type="[ARTIFACTTYPE_NAME]">
                    <ae:parameters>
                        <ae:parameter dt="string" name="object">[object.value]</ae:parameter>
                    </ae:parameters>
                </ae:artifact>
                <ae:test type="[TESTTYPE_NAME]">
            <ae:parameters/>
                </ae:test>
            </ae:artifact_expression>
        </xccdf:check-content>
    </xccdf:check>
</xccdf:complex-check>
```

#### SCAP
##### XCCDF
For `linux.custom_object_v1.md` artifacts, the xccdf:check looks like this.  There is no Value in the xccdf for this Artifact.

```
<check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
<check-content-ref href="[BENCHMARK_TITLE]"
    name="oval:org.cisecurity.benchmarks.suse_suse_linux_enterprise_server_12:def:[ARTIFACT_OVAL_ID]"
/>
</check>
```

##### OVAL
###### Test

```
<shadow_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
            id="oval:org.cisecurity.benchmarks.suse_suse_linux_enterprise_server_12:tst:[ARTIFACT_OVAL_ID]"
            check_existence="any_exist" check="none satisfy"
            comment='[RECOMMENDATION_TITLE]'
            version="1">
            <object
                object_ref="oval:org.cisecurity.benchmarks.suse_suse_linux_enterprise_server_12:obj:[ARTIFACT_OVAL_ID]"/>
            <state
                state_ref="oval:org.cisecurity.benchmarks.suse_suse_linux_enterprise_server_12:ste:[ARTIFACT_OVAL_ID]"
            />
        </shadow_test>
```

###### Object

```
<shadow_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
            id="oval:org.cisecurity.benchmarks.suse_suse_linux_enterprise_server_12:obj:[ARTIFACT_OVAL_ID]"
            comment='[RECOMMENDATION_TITLE]'
            version="1">
            <username operation="[testType_name]">[testType_name.value]</username>
</shadow_object>   
```
###### State

```
<shadow_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
            id="oval:org.cisecurity.benchmarks.suse_suse_linux_enterprise_server_12:ste:[ARTIFACT_OVAL_ID]"
            comment='[RECOMMENDATION_TITLE]'
            version="1">
            <password datatype="string" operation="pattern match">^[^!*]</password>
            <chg_req datatype="int" operation="[testtype_name]">[testType_name.value]</chg_req>
</shadow_state>  
```

#### YAML

```
- artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: [ARTIFACTTYPE NAME]
      parameters:
      - parameter: 
          name: object
          type: string
          value: [object.value]
    test:
      type: [TESTTYPE NAME]
      parameters:
      - parameter:
          name: [TEST_PARAMETER_NAME]
          type: string
          value: [TestParameter.name.value]    
```

#### JSON

```
"artifact-expression": {
  "artifact-unique-id": [ARTIFACT-OVAL-ID],
  "artifact-title": [RECOMMENDATION TITLE],
  "artifact": {
    "type": "[ARTIFACTTYPE NAME]",
    "parameters": [
      {
        "parameter": {
          "name": "objecrt",
          "type": "string",
          "value": [object.value]
        }
      }
    ]
  },
  "test": {
    "type": [TESTTYPE NAME],
    "parameters": [
      {
        "parameter": {
          "name": "[testType.name]",
          "type": "string",
          "value": [testType.value]
        }
      }
``` 