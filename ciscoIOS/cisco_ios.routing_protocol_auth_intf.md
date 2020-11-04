# cisco_ios.routing_protocol_auth_intf

## Description
The cisco_ios.routing_protocol_auth_intf is used to TBD

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| interface_operator | String | Interface Operator. |
| interface | String | The name of the interface(s) to collect. |
| protocol_operator | String | Protocol Operator. |
| routing_protocol | String | The name of the routing protocol(s) to collect. |

### Supported Test Types
- cisco_ios.routing_protocol_auth_keychain
- cisco_ios.routing_protocol_auth_type

### Test Type Parameters
#### cisco_ios.routing_protocol_auth_keychain
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| operator | String | Comparison Operator. |
| keychain | String | Authentication Key Chain. |

#### cisco_ios.routing_protocol_auth_type
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| auth_type | String | The routing protocol authentication type. |
   

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
                    <ae:parameter dt="string" name="interface_operator>[interface_operator.value]</ae:parameter>
                    <ae:parameter dt="string" name="interface>[interface.value]</ae:parameter>
                    <ae:parameter dt="string" name="protocol_operator>[protocol_operator.value]</ae:parameter>
                    <ae:parameter dt="string" name="routing_protocol>[routing_protocol.value]</ae:parameter>
                </ae:parameters>
            </ae:artifact>
            <ae:test type="[TESTTYPE NAME]">
                <ae:parameters>
                    <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
                    <ae:parameter dt="string" name="keychain">[keychain.value]</ae:parameter>
                </ae:parameters>
            </ae:test>
        </ae:artifact_expression>
    </xccdf:check-content>
</xccdf:check>
```

#### SCAP
##### XCCDF
For `cisco_ios.routing_protocol_auth_intf` artifacts, the xccdf:check looks like this. 

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
<routingprotocolauthintf_test 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#ios' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]'
    check_existence='[check_existence.value]' 
    check='[check.value]' 
    comment='[RECOMMENDATION TITLE]'
    version='[version.value]'>
    <object object_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
    <state state_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]'/>
</routingprotocolauthintf_test>
```

###### Object

```
<routingprotocolauthintf_object 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#ios' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
    comment='[RECOMMENDATION TITLE]'
    version='[version.value]'>
    <interface operation='[operation.value]'>[interface.value]</interface>
    <protocol operation='[operation.value]'>[protocol.value]</protocol>
</routingprotocolauthintf_object>
```
###### State

```
<routingprotocolauthintf_state 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#ios' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
    comment='[RECOMMENDATION TITLE]' 
    version='[version.value]'>
    <key_chain operation='[operation.value]' var_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
</routingprotocolauthintf_state>

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
          name: interface_operator
          type: string
          value: [interface_operator.value]
      - parameter: 
          name: interface
          type: string
          value: [interface.value]
      - parameter: 
          name: protocol_operator
          type: string
          value: [protocol_operator.value]
      - parameter: 
          name: routing_protocol
          type: string
          value: [routing_protocol.value]
    test:
      type: [TESTTYPE NAME]
      parameters:   
      - parameter: 
          name: operator
          type: string
          value: [operator.value]
      - parameter: 
          name: keychain
          type: string
          value: [keychain.value]
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
              "name": "interface_operator",
              "type": "string",
              "value": [
                "interface_operator.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "interface",
              "type": "string",
              "value": [
                "interface.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "protocol_operator",
              "type": "string",
              "value": [
                "protocol_operator.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "routing_protocol",
              "type": "string",
              "value": [
                "routing_protocol.value"
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
              "name": "keychain",
              "type": "string",
              "value": [
                "keychain.value"
              ]
            }
          }
        ]
      }
    }
  }
``` 