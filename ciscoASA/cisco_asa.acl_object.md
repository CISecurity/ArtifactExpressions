# cisco_asa.acl_object

## Description
The cisco_asa.acl_object is used to check the properties of specific output lines from an ACL configuration.

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| name | String | The name of the ACL. |
| ip_version | String | The IP Version of the ACL. |
| name_operator | String | Operation used to collect appropriate Name values. |
| ip_version_operator | String | Operation used to collect appropriate IP Version values. |

ip_version
NOTE: This parameter is governed by a constraint allowing only the following values:
- IPV4
- IPV6
- IPV4_V6
- ALL

### Supported Test Types
- cisco_asa.acl_config_line_with_entity_check

### Test Type Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| operation | String | Comparison Operator. |
| config_line | String | ACL configuration line. |
| entity_check | String | Number of Config Lines which must match. |
  
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
                    <ae:parameter dt="string" name="name">[name.value]</ae:parameter>
                    <ae:parameter dt="string" name="ip_version">[ip_version.value]</ae:parameter>
                    <ae:parameter dt="string" name="name_operator">[name_operator.value]</ae:parameter>
                    <ae:parameter dt="string" name="ip_version_operator">[ip_version_operator.value]</ae:parameter>
                </ae:parameters>
            </ae:artifact>
            <ae:test type="[TESTTYPE NAME]">
                <ae:parameters>
                    <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
                    <ae:parameter dt="string" name="config_line">[config_line.value]</ae:parameter>
                    <ae:parameter dt="string" name="entity_check">[entity_check.value]</ae:parameter>
                </ae:parameters>
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
For `cisco_asa.acl_object` artifacts, the xccdf:check looks like this. 

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
<acl_test 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#ios' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]'
    check_existence='[check_existence.value]' 
    check='[check.value]' 
    comment='[RECOMMENDATION TITLE]'
    version='[version.value]'>
    <object object_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
    <state state_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]'/>
</acl_test>
```

###### Object

```
<acl_object 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#ios' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
    comment='[RECOMMENDATION TITLE]'>
    version='[version.value]'>
    <name operation='[operation.value]'>[name.value]</name>
    <ip_version operation='[operation.value]' 
        var_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]'/>
</acl_object>
```
###### State

```
<acl_state 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#ios' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
    comment='[RECOMMENDATION TITLE]'>
    version='[version.value]'>
    <config_line operation='[operation.value]' 
        entity_check='[entity_check.value]' 
        var_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]
</acl_state>
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
          name: name
          type: string
          value: [name.value]
      - parameter: 
          name: ip_version
          type: string
          value: [ip_version.value]
      - parameter: 
          name: name_operator
          type: string
          value: [name_operator.value]
      - parameter: 
          name: ip_version_operator
          type: string
          value: [ip_version_operator.value]
    test:
      type: [TESTTYPE NAME]
      parameters:   
      - parameter: 
           name: operation
           type: string
           value: [operation.value]
      - parameter: 
           name: config_line
           type: string
           value: [config_line.value]
      - parameter: 
          name: entity_check
          type: string
          value: [entity_check.value]
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
              "name": "name",
              "type": "string",
              "value": [
                "name.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "ip_version",
              "type": "string",
              "value": [
                "ip_version.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "name_operator",
              "type": "string",
              "value": [
                "name_operator.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "ip_version_operator",
              "type": "string",
              "value": [
                "ip_version_operator.value"
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
              "name": "operation",
              "type": "string",
              "value": [
                "operation.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "config_line",
              "type": "string",
              "value": [
                "config_line.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "entity_check",
              "type": "string",
              "value": [
                "entity_check.value"
              ]
            }
          }
        ]
      }
    }
  }
``` 