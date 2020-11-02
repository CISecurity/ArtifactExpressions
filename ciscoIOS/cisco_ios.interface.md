# cisco_ios.interface

## Description
The cisco_ios.interface is used to TBD

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| cisco_ios.interface_name | String | The name of the IOS interface to be tested. |
| operation | String | The operator defining how to collect the IOS interface(s). |


### Supported Test Types
- cisco_ios.interface_existence_test
- cisco_ios.interface_proxy_arp
- cisco_ios.interface_urpf

### Test Type Parameters
#### cisco_ios.interface_existence_test
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| existence_check | String | Number of interfaces expected to be collected. |
| operator | String | Interface Name comparison operator. |
| interface_name | String | The interface name. |

#### cisco_ios.interface_proxy_arp
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| operation | String | Comparison Operator. |
| proxy_arp_enabled | String | True if the proxy_arp command is enabled on the interface. The default is true. |

#### cisco_ios.interface_urpf
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| operator | String | Interface Name comparison operator. |
| urpf_command | String | The uRPF commands expected value. |
   

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
For `cisco_ios.interface` artifacts, the xccdf:check looks like this. 

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