# cisco_ios.section

## Description
The cisco_ios.section is used to check the properties of specific output lines from a configuration section.

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| cisco_ios.section_name | String | The name of the section for which to collect configuration information. |

### Supported Test Types
- cisco_ios.section_existence_test
- cisco_ios.section_config_line

### Test Type Parameters
#### cisco_ios.section_existence_test
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| existence_check | String | Number of sections expected to be collected. |

existence_check
NOTE: This parameter is governed by a constraint allowing only the following values:
- all_exist
- any_exist
- at_least_one_exists
- none_satisfy
- none_exist
- only_one_exists

#### cisco_ios.section_config_line
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| section_config_line | String | One config line of the collected configuration section. |
| operation | String | Comparison Operator. |
| entity_check | String | The number of section configuration lines which must match the expected state. |

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
 
 entity_check
 NOTE: This parameter is governed by a constraint allowing only the following values:
- all_exist
- any_exist
- at_least_one_exists
- none_exist
- only_one_exists

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
                    <ae:parameter dt="string" name="cisco_ios.section_name">[cisco_ios.section_name.value]</ae:parameter>
                </ae:parameters>
            </ae:artifact>
            <ae:test type="[TESTTYPE NAME]">
                <ae:parameters>
                    <ae:parameter dt="string" name="existence_check">[existence_check.value]</ae:parameter>
                </ae:parameters>
            </ae:test>
        </ae:artifact_expression>
    </xccdf:check-content>
</xccdf:check>
```

#### SCAP
##### XCCDF
For `cisco_ios.section` artifacts, the xccdf:check looks like this. 

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
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
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
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
    comment='[RECOMMENDATION TITLE]'
    version='[version.value]'>
    <section_command>[section_command.value]</section_command>
</section_object>
```
###### State

```
<section_state
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
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
      - parameter: 
          name: cisco_ios.section_name
          type: string
          value: [cisco_ios.section_name.value]
    test:
      type: [TESTTYPE NAME]
      parameters:   
      - parameter: 
          name: existence_check
          type: string
          value: [existence_check.value]
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
              "name": "cisco_ios.section_name",
              "type": "string",
              "value": [
                "cisco_ios.section_name.value"
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
              "name": "existence_check",
              "type": "string",
              "value": [
                "existence_check.value"
              ]
            }
          }
        ]
      }
    }
  }
``` 