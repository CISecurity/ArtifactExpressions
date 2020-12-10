# independent.sql57_sqlserver_query_each_database_v1

## Description
The independent.sql57_sqlserver_query_each_database_v1 is used by a sql test to define specific databases and queries to be evaluated. 

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| sql | String | The sql entity defines a query used to identify the object(s) to test against. |
| version | String | The version entity defines the specific version of the database engine to use. This is also important in determining the correct driver to use for establishing a connection. |
| exclude_system_db | Boolean | n/a |
| check_existence | String | n/a |

check_existence
NOTE: This parameter is governed by a constraint allowing only the following values:
- all_exist
- any_exist
- at_least_one_exists
- none_satisfy
- none_exist
- only_one_exists

### Supported Test Types
- independent.sql57_v2

### Test Type Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| check | String | Defines how many items must evaluate to true for the entity to return true. |
| field_value | String | A simple (number, string, or boolean) value to be used in determining the result, i.e. pass/fail. |
| field_value_datatype | String | The datatype of the expected/required value. |
| field_name | String | The name of the field to which collected items are compared, restricted to only lowercase letters. |
| field_operation | String | The optional operation attribute determines how the individual entities should be evaluated (the default operation is 'equals'). |

check
NOTE: This parameter is governed by a constraint allowing only the following values:
- all
- at least one
- none satisfy
- only one 

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
                    <ae:parameter dt="string" name="sql">[sql.value]</ae:parameter>
                    <ae:parameter dt="string" name="version">[version.value]</ae:parameter>
                    <ae:parameter dt="string" name="exclude_system_db">[exclude_system_db.value]</ae:parameter>
                    <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
                </ae:parameters>
            </ae:artifact>
            <ae:test type="[TESTTYPE NAME]">
                <ae:parameters>
                    <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
                    <ae:parameter dt="string" name="field_value">[field_value.value]</ae:parameter>
                    <ae:parameter dt="string" name="field_value_datatype">[field_value_datatype.value]</ae:parameter>
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
For `independent.sql57_sqlserver_query_each_database_v1` artifacts, the xccdf:check looks like this. 

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
<sql57_test
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]'
    check_existence='[check_existence.value]' 
    check='[check.value]' 
    comment='[RECOMMENDATION TITLE]'
    version='[version.value]'>
    <object object_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
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
n/a
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
           name: sql
           type: string
           value: [sql.value]
      - parameter: 
           name: version
           type: string
           value: [version.value]
      - parameter: 
           name: exclude_system_db
           type: string
           value: exclude_system_db.value]
      - parameter: 
           name: check_existence
           type: string
           value: [check_existence.value]
    test:
      type: [TESTTYPE NAME]
      parameters:   
      - parameter: 
           name: check
           type: string
           value: [check.value]
      - parameter: 
           name: field_value
           type: string
           value: field_value.value]
      - parameter: 
           name: field_value_datatype
           type: string
           value: [field_value_datatype.value]
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
              "name": "sql",
              "type": "string",
              "value": [
                "sql.value"
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
          },
          {
            "parameter": {
              "name": "exclude_system_db",
              "type": "string",
              "value": "exclude_system_db.value]"
            }
          },
          {
            "parameter": {
              "name": "check_existence",
              "type": "string",
              "value": [
                "check_existence.value"
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
              "name": "check",
              "type": "string",
              "value": [
                "check.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "field_value",
              "type": "string",
              "value": "field_value.value]"
            }
          },
          {
            "parameter": {
              "name": "field_value_datatype",
              "type": "string",
              "value": [
                "field_value_datatype.value"
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