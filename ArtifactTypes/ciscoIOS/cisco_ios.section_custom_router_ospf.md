# cisco_ios.section_custom_router_ospf

## Description
The cisco_ios.section_custom_router_ospf is used to check section custom router ospf authentication

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |


### Supported Test Types
- cisco_ios.section_custom_router_ospf_line

### Test Type Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| entity_check | String | The number of section configuration lines which must match the expected state. |
| operation | String | Comparison Operator. |
| section_config_line | String | One config line of the collected configuration section. |
  
entity_check
NOTE: This parameter is governed by a constraint allowing only the following values:
- all_exist
- any_exist
- at_least_one_exists
- none_exist
- only_one_exists

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
                <ae:parameters/>
            </ae:artifact>
            <ae:test type="[TESTTYPE NAME]">
                <ae:parameters>
                    <ae:parameter dt="string" name="entity_check">[entity_check.value]</ae:parameter>
                    <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
                    <ae:parameter dt="string" name="section_config_line">[section_config_line.value]</ae:parameter>
                </ae:parameters>
            </ae:test>
        </ae:artifact_expression>
    </xccdf:check-content>
</xccdf:check>
```

#### SCAP
##### XCCDF
For `cisco_ios.section_custom_router_ospf` artifacts, the xccdf:check looks like this. 

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
<section_test 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#ios' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]'
    check_existence='[check_existence.value]' 
    check='[check.value]' 
    comment='[RECOMMENDATION TITLE]'
    version='[version.value]'>
    <object object_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
    <state state_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]'/>
</section_test>
```

###### Object

```
<section_object 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#ios' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
    comment='[RECOMMENDATION TITLE]'
    version='[version.value]'>
    <section_command>[section_command.value]</section_command>
</section_object>
<router_object 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#ios' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
    comment='[RECOMMENDATION TITLE]'
    version='[version.value]'>
    <protocol>OSPF</protocol>
    <id datatype='[datatype.value]' operation='[operation.value]'>0</id>
</router_object>
```
###### State

```
<section_state
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#ios' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
    comment='[RECOMMENDATION TITLE]'
    version='[version.value]'>
    <config_line entity_check='[entity_check.value]' operation='[operation.value]' 
        var_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]/>
</section_state>
```

#### YAML

```
- artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: [ARTIFACTTYPE NAME]
      parameters:
    test:
      type: [TESTTYPE NAME]
      parameters: 
      - parameter: 
          name: entity_check
          type: string
          value: [entity_check.value]
      - parameter: 
          name: operation
          type: string
          value: [operation.value]  
      - parameter: 
          name: section_config_line
          type: string
          value: [section_config_line.value] 
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
        "parameters": null
      },
      "test": {
        "type": [
          "TESTTYPE NAME"
        ],
        "parameters": [
          {
            "parameter": {
              "name": "entity_check",
              "type": "string",
              "value": [
                "entity_check.value"
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
              "name": "section_config_line",
              "type": "string",
              "value": [
                "section_config_line.value"
              ]
            }
          }
        ]
      }
    }
  }
``` 