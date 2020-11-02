# cisco_ios.snmp_host

## Description
The cisco_ios.snmp_host is used to TBD

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| cisco_ios.snmp_host_name | String | The SNMP host address or hostname. |
| cisco_ios.snmp_host_op | String | SNMP Host Collection Operator. |

### Supported Test Types
- existence_test
- cisco_ios.snmp_host_traps

### Test Type Parameters
#### existence_test
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| value | String | Value. |

#### cisco_ios.snmp_host_traps
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| operator | String | Comparison Operator. |
| traps | String | The SNMP Traps configured. |


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
                    <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
                    <ae:parameter dt="string" name="neighbor">[neighbor.value]</ae:parameter>
                </ae:parameters>
            </ae:artifact>
            <ae:test type="[TESTTYPE NAME]">
                <ae:parameters/>
            </ae:test>
            <ae:profiles>
                <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_2"/>
            </ae:profiles>
        </ae:artifact_expression>
    </xccdf:check-content>
</xccdf:check>
```

#### SCAP
##### XCCDF
For `cisco_ios.snmp_host` artifacts, the xccdf:check looks like this. 

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
<bgpneighbor_test xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#ios' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]'
    check_existence='[check_existence.value]' 
    check='[check.value]' 
    comment='[RECOMMENDATION TITLE]'>
    <object object_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
    <state state_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]'/>
</bgpneighbor_test>
```

###### Object

```
<bgpneighbor_object xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#ios' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
    comment='[RECOMMENDATION TITLE]'>
    <neighbor operation='[operation.value]'>[neighbor.value]</neighbor>
</bgpneighbor_object>
```
###### State

```
<bgpneighbor_state xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#ios' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
    comment='[RECOMMENDATION TITLE]'>
    <password operation='[operation.value]' 
    var_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID'/>
</bgpneighbor_state>
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
          name: operator
          type: string
          value: [operator.value]
      - parameter: 
          name: neighbor
          type: string
          value: [neighbor.value]
    test:
      type: [TESTTYPE NAME]
      parameters:   
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
              "name": "operator",
              "type": "string",
              "value": [
                "operator.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "neighbor",
              "type": "string",
              "value": [
                "neighbor.value"
              ]
            }
          }
        ]
      },
      "test": {
        "type": [
          "TESTTYPE NAME"
        ],
        "parameters": null
      }
    }
  }
``` 