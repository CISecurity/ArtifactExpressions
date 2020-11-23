# kubernetes.kubepsp_v1

## Description
The kubernetes.kubepsp_v1 is used to check the properties of the Pod Security Policy (PSP)

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| psp_name | String | Specifies the name of the PSP. Names are case-sensitive. |
| psp_operation | String | The operation of the pod security policy. |
| yaml_path | String | Specifies a dotted path substituting a colon for a dot to a particular Pod Security Policy setting's YAML configuration. |


### Supported Test Types
- kubernetes.kubepsp_v1

### Test Type Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| check_existence | String | Define how many items should be collected. |
| check | String | Defines how many collected items must match the expected state. |
| operation | String | comparison operation |
| datatype | String | datatype |
| result | String |  	The result entity specifies how to test objects in the result set of the specified. |


check_existence
NOTE: This parameter is governed by a constraint allowing only the following values:
- all_exist
- any_exist
- at_least_one_exists
- none_satisfy
- none_exist
- only_one_exists

check
NOTE: This parameter is governed by a constraint allowing only the following values:
- all
- at least one
- none satisfy
- only one

operation
NOTE: This parameter is governed by a constraint allowing only the following values:
- equals
- not equal
- case insensitive equals
- case insensitive not equal
- greater than
- less than
- greater than or equal
- less than or equal
- bitwise and
- bitwise or
- pattern match
- subset of
- superset of

datatype
NOTE: This parameter is governed by a constraint allowing only the following values:
- boolean
- float
- int
- string
- version
- set

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
                    <ae:parameter dt="string" name="psp_name">[psp_name.value]</ae:parameter>
                    <ae:parameter dt="string" name="psp_operation">[psp_operation.value]</ae:parameter>
                    <ae:parameter dt="string" name="yaml_path">[yaml_path.value]</ae:parameter>
                </ae:parameters>
            </ae:artifact>  
                <ae:test type="[TESTTYPE NAME]">
                    <ae:parameters>
                        <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
                        <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
                        <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
                        <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
                        <ae:parameter dt="string" name="result">[result.value]</ae:parameter>
                    </ae:parameters>
                </ae:test>
                <ae:profiles>
                    <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1"/>
                </ae:profiles>
            </ae:artifact_expression>
        </xccdf:check-content>
</xccdf:check>
```

#### SCAP
##### XCCDF
For `kubernetes.kubepsp_v1` artifacts, the xccdf:check looks like this. There is no Value in the xccdf for this Artifact.

```
<check system='http://oval.mitre.org/XMLSchema/oval-definitions-5'>
    <check-content-ref 
        href='[BENCHMARK NAME]' 
        name='oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]'/>
</check>
```

##### OVAL
###### Test

```
<kubepsp_test xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#kubernetes' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]' 
    check_existence='[check_existence.value]' 
    check='[check.value]' 
    comment='[RECOMMENDATION TITLE]'>
    <object object_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
    <state state_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]'/>
</kubepsp_test>
```

###### Object

```
<kubepsp_object xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#kubernetes' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
    comment='[RECOMMENDATION TITLE]'>
    <psp_name operation='[operation.value'>[psp_name.value]</psp_name>
    <yaml_path>[yaml_path.value]</yaml_path>
</kubepsp_object>  
```
###### State

```
<kubepsp_state 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#kubernetes' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
    comment='[RECOMMENDATION TITLE]'>
    <result datatype='record'>
        <field xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5' 
            name='[name.value]' entity_check='[entity_check.value]' operation='[operation.value]' datatype='string'>[datatype.value]
        </field>
    </result>
</kubepsp_state>
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
          name: psp_name
          type: string
          value: [psp_name.value]
      - parameter: 
          name: psp_operation
          type: string
          value: [psp_operation.value]
      - parameter: 
          name: yaml_path
          type: string
          value: [yaml_path.value]
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
          name: result
          type: string
          value: [result.value]      
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
              "name": "psp_name",
              "type": "string",
              "value": [
                "psp_name.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "psp_operation",
              "type": "string",
              "value": [
                "psp_operation.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "yaml_path",
              "type": "string",
              "value": [
                "yaml_path.value"
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
              "name": "check_existence",
              "type": "string",
              "value": [
                "check_existence.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "check",
              "type": "string",
              "value": [
                "check.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "operation",
              "type": "string",
              "value": [
                "operation.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "datatype",
              "type": "string",
              "value": [
                "datatype.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "result",
              "type": "string",
              "value": [
                "result.value"
              ]
            }
          }
        ]
      }
    }
  }
``` 