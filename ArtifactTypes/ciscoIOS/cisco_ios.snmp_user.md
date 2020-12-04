# cisco_ios.snmp_user

## Description
The cisco_ios.snmp_user is used to check the properties of specific output lines from an SNMP user configuration.

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| cisco_ios.snmp_user_name | String | The SNMP user name. |
| cisco_ios.snmp_user_op | String | SNMP User Comparison Operator. |
| cisco_ios.snmp_user_snmpv3 | boolean | Collect only SNMPv3 Users? |

### Supported Test Types
- cisco_ios.snmp_user_priv

### Test Type Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| operator | String | Comparison Operator. |
| snmp_encryption_type | String | The SNMP encryption type for the user (for SNMPv3). |


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
                    <ae:parameter dt="string" name="cisco_ios.snmp_user_name">[cisco_ios.snmp_user_name.value]</ae:parameter>
                    <ae:parameter dt="string" name="cisco_ios.snmp_user_op">[cisco_ios.snmp_user_op.value]</ae:parameter>
                    <ae:parameter dt="string" name="cisco_ios.snmp_user_snmpv3">[cisco_ios.snmp_user_snmpv3.value]</ae:parameter>
                </ae:parameters>
            </ae:artifact>
            <ae:test type="[TESTTYPE NAME]">
                <ae:parameters>
                    <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
                    <ae:parameter dt="string" name="snmp_encryption_type">[snmp_encryption_type.value]</ae:parameter>
                </ae:parameters>
            </ae:test>
        </ae:artifact_expression>
    </xccdf:check-content>
</xccdf:check>
```

#### SCAP
##### XCCDF
For `cisco_ios.snmp_user` artifacts, the xccdf:check looks like this. 

```
<check system='http://oval.mitre.org/XMLSchema/oval-definitions-5'>            
    <check-export 
        export-name='oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]' 
        value-id='xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var'/>
    <check-content-ref 
        href='[BENCHMARK NAME]' 
        name='oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]'/>
</check>
```

##### OVAL
###### Test

```
<snmpuser_test 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]'
    check_existence='[check_existence.value]' 
    check='[check.value]' 
    comment='[RECOMMENDATION TITLE]'
    version='1'>
    <object object_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
    <state state_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]'/>
</snmpuser_test>
```

###### Object

```
<snmpuser_object 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
    comment='[RECOMMENDATION TITLE]'
    version='1'>
    <name operation='[operation.value]'>[name.value]</name>
    <filter 
        xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5' 
        action='[action.value]]'>oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]</filter>
</snmpuser_object>
```
###### State

```
<snmpuser_state 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
    comment='[RECOMMENDATION TITLE]'
    version='[version.value]'>
    <version>[version.value]</version>
</snmpuser_state>
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
          name: cisco_ios.snmp_user_name
          type: string
          value: [cisco_ios.snmp_user_name.value]
      - parameter: 
          name: cisco_ios.snmp_user_op
          type: string
          value: [cisco_ios.snmp_user_op.value]
      - parameter: 
          name: cisco_ios.snmp_user_snmpv3
          type: string
          value: [cisco_ios.snmp_user_snmpv3.value]
    test:
      type: [TESTTYPE NAME]
      parameters:   
      - parameter: 
          name: operator
          type: string
          value: [operator.value]
      - parameter: 
          name: snmp_encryption_type
          type: string
          value: [snmp_encryption_type.value]
```

#### JSON

```
{
    "artifact-expression": {
      "artifact-unique-id": [
        "ARTIFACT-OVAL-ID"
      ],
      "artifact-title": [
        "RECOMMENDATION TITLE"
      ],
      "artifact": {
        "type": [
          "ARTIFACTTYPE NAME"
        ],
        "parameters": [
          {
            "parameter": {
              "name": "cisco_ios.snmp_user_name",
              "type": "string",
              "value": [
                "cisco_ios.snmp_user_name.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "cisco_ios.snmp_user_op",
              "type": "string",
              "value": [
                "cisco_ios.snmp_user_op.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "cisco_ios.snmp_user_snmpv3",
              "type": "string",
              "value": [
                "cisco_ios.snmp_user_snmpv3.value"
              ]
            }
          }
        ]
      },
      "test": {
        "type": [
          "TESTTYPE NAME"
        ],
        "parameters": [
          {
            "parameter": {
              "name": "operator",
              "type": "string",
              "value": [
                "operator.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "snmp_encryption_type",
              "type": "string",
              "value": [
                "snmp_encryption_type.value"
              ]
            }
          }
        ]
      }
    }
  }
``` 