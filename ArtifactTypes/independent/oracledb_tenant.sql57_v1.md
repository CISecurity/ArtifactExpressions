# oracledb_tenant.sql57_v1

## Description
The oracledb_tenant.sql57_v1 is used to check information stored in a database. 

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| non_multi_tenant_sql | String | This entity defines a query used to identify the object(s) to test against on a non-multi-tenant Oracle DB. |
| multi_tenant_sql | String | This entity defines a query used to identify the object(s) to test against on a multi-tenant Oracle DB. |
| version | String | This entity defines the specific version of the database engine to use. This is also important in determining the correct driver to use for establishing a connection. |

### Supported Test Types
- independent.sql57_v1
- existence_test

### Test Type Parameters
####independent.sql57_v1
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| check_existence | String | Specifies how many items in the set must exist for the test to evaluate to true. |
| check | String | Defines how many items must evaluate to true for the entity to return true. |
| value | String | A simple (number, string, or boolean) value to be used in determining the result, i.e. pass/fail. |
| value_data_type | String | The optional datatype attribute specifies how the given operation should be applied to the data. |
| field_name | String | A string restricted to disallow upper case characters. |
| field_operation | String | The optional operation attribute determines how the individual entities should be evaluated (the default operation is 'equals'). |

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

####existence_test
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| value | String | Value to test. |


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
                    <ae:parameter dt="string" name="non_multi_tenant_sql">[non_multi_tenant_sql.value]</ae:parameter>
                    <ae:parameter dt="string" name="multi_tenant_sql">[multi_tenant_sql.value]</ae:parameter>
                    <ae:parameter dt="string" name="version">[version.value]</ae:parameter>
                </ae:parameters>
            </ae:artifact>
            <ae:test type="[TESTTYPE NAME]">
                <ae:parameters>
                    <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
                    <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
                    <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
                    <ae:parameter dt="string" name="value_data_type">[value_data_type.value]</ae:parameter>
                    <ae:parameter dt="string" name="field_name">[field_name.value]</ae:parameter>
                    <ae:parameter dt="string" name="field_operation">[field_operation.value]</ae:parameter>
                </ae:parameters>
            </ae:test>
        </ae:artifact_expression>
    </xccdf:check-content>
</xccdf:check>
```

#### SCAP
##### XCCDF
For `oracledb_tenant.sql57_v1` artifacts, the xccdf:check looks like this. 

```
<check system='http://oval.mitre.org/XMLSchema/oval-definitions-5'>
    <check-export 
         export-name='oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]' 
         value-id='xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var'/>
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
<sql57_test
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]'
    check_existence='[check_existence.value]' 
    check='[check.value]' 
    comment='[RECOMMENDATION TITLE]'
    version='[version.value]'>
    <object object_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
    <state state_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]'/>
</sql57_test>
```

###### Object

```
<sql57_object 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
    comment='[RECOMMENDATION TITLE]'>
    version='[version.value]'>
    <engine>[engine.value]</engine>
    <version>[version.value]</version>
    <connection_string var_ref='oval:org.cisecurity.benchmarks:var:[ID]]'/>
    <sql>[sql.value]</sql>
</sql57_object>
```
###### State

```
<sql57_state 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
    comment='[RECOMMENDATION TITLE]'>
    version='[version.value]'>
    <result datatype='[result.value]' entity_check='[entity_check.value]'>
    <field xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5' 
        name='[name.value]' 
        datatype='[datatype.value]'
        operation='[operation.value]'
        var_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
    </result>
</sql57_state>
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
          name: non_multi_tenant_sql
          type: string
          value: [non_multi_tenant_sql.value]
      - parameter: 
           name: multi_tenant_sql
           type: string
           value: [multi_tenant_sql.value]
      - parameter: 
           name: version
           type: string
           value: [version.value]
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
           name: value
           type: string
           value: value.value]
      - parameter: 
           name: value_data_type
           type: string
           value: [value_data_type.value]
      - parameter: 
           name: field_name
           type: string
           value: [field_name.value]
      - parameter: 
           name: field_operation
           type: string
           value: field_operation.value]
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
              "name": "non_multi_tenant_sql",
              "type": "string",
              "value": [
                "non_multi_tenant_sql.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "multi_tenant_sql",
              "type": "string",
              "value": [
                "multi_tenant_sql.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "version",
              "type": "string",
              "value": [
                "version.value"
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
              "name": "value",
              "type": "string",
              "value": "value.value]"
            }
          },
          {
            "parameter": {
              "name": "value_data_type",
              "type": "string",
              "value": [
                "value_data_type.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "field_name",
              "type": "string",
              "value": [
                "field_name.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "field_operation",
              "type": "string",
              "value": "field_operation.value]"
            }
          }
        ]
      }
    }
  }
``` 