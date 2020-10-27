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
<xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
  <xccdf:check-content>
    <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION_NUMBER]">
      <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
      <ae:title>[RECOMMENDATION TITLE]</ae:title>
      <ae:artifact type="[ARTIFACTTYPE NAME]">
        <ae:parameters>
          <ae:parameter dt="string" name="gatekeeper"
            >[gatekeeper.value]</ae:parameter>
        </ae:parameters>
      </ae:artifact>
      <ae:test type="[TESTTYPE NAME]">
        <ae:parameters>
          <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
          <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
          <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
          <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
          <ae:parameter dt="boolean" name="enabled">[enabled.value]</ae:parameter>
        </ae:parameters>
      </ae:test>
      <ae:profiles>
        <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1"
        />
      </ae:profiles>
    </ae:artifact_expression>
  </xccdf:check-content>
</xccdf:check>
```

#### SCAP
##### XCCDF
For `macos.gatekeeper_v1` artifacts, the xccdf:check looks like this.  There is no Value in the xccdf for this Artifact.

```
<xccdf:check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
   <xccdf:check-content-ref xmlns:ae="http://benchmarks.cisecurity.org/ae/0.5"
      xmlns:cpe="http://cpe.mitre.org/language/2.0"
      xmlns:ecl="http://cisecurity.org/check"
      href="[BENCHMARK NAME]"
      name="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:def:[ARTIFACT-OVAL-ID]"/>
</xccdf:check>
```

##### OVAL
###### Test

```
<macos:gatekeeper_test check="[check.value]" check_existence="[check_existence.value]"
  comment="[RECOMMENDATION TITLE]"
  id="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:tst:ARTIFACT-OVAL-ID" version="1">
  <macos:object object_ref="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:obj:ARTIFACT-OVAL-ID"/>
  <macos:state state_ref="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:ste:ARTIFACT-OVAL-ID"/>
</macos:gatekeeper_test>
```

###### Object

```
<macos:gatekeeper_object
  comment="[RECOMMENDATION TITLE]"
  id="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:obj:ARTIFACT-OVAL-ID" version="1"> 
</macos:gatekeeper_object>    
```
###### State

```
<macos:gatekeeper_state
  comment="[RECOMMENDATION TITLE]"
  id="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:ste:ARTIFACT-OVAL-ID" version="1">
  <macos:enabled datatype="[datatype.value]" operation="[operation.value]">[enabled.value]</macos:enabled>
</macos:gatekeeper_state>    
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
          name: gatekeeper
          type: string
          value: [gatekeeper.value]
    test:
      type: [TESTTYPE NAME]
      parameters:
      - parameter:
          name: check_existence
          type: string
          value: [check_existence.value]
      - parameter: 
          name: check
          type: string
          value: [check.value]
      - parameter:
          name: operation
          type: string
          value: [operation.value]
      - parameter: 
          name: datatype
          type: string
          value: [datatype.value]  
      - parameter: 
          name: enabled
          type: string
          value: [enabled.value]      
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
          "name": "gatekeeper",
          "type": "string",
          "value": [gatekeeper.value]
        }
      }
    ]
  },
  "test": {
    "type": [TESTTYPE NAME],
    "parameters": [
      {
        "parameter": {
          "name": "check_existence",
          "type": "string",
          "value": [check_existence.value]
        }
      },
      {
        "parameter": {
          "name": "check",
          "type": "string",
          "value": [check.value]
        }
      },
      {
        "parameter": {
          "name": "operation",
          "type": "string",
          "value": [operation.value]
        }
      },
      {
        "parameter": {
          "name": "datetype",
          "type": "string",
          "value": [datatype.value]
        }
      },
      {
        "parameter": {
          "name": "enabled",
          "type": "string",
          "value": [enabled.value]
        }
      }
    ]
  }
}
``` 