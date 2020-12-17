# independent.text_file_content_v1

## Description
The independent.text_file_content_v1 is used to check the contents of a text file (aka a configuration file) by looking at individual blocks of text.

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| non_multi_tenant_sql | String | This entity defines a query used to identify the object(s) to test against on a non-multi-tenant Oracle DB. |
| multi_tenant_sql | String | This entity defines a query used to identify the object(s) to test against on a multi-tenant Oracle DB. |
| version | String | The version entity defines the specific version of the database engine to use. This is also important in determining the correct driver to use for establishing a connection. |

### Supported Test Types
- pattern match
- pattern not match
- existence_test
- SQL-Unix_File_or_Directory_Permissions_v1
- independent.txt_file_content_v1
- Txt-Unix_File_or_Directory_Permissions_v1
- Txt-Unix_File_or_Directory_Permissions_v2

### Test Type Parameters
####pattern match
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| value | String | A simple (number, string, or boolean) value to be used in determining the result, i.e. pass/fail. |
| data_type | String | Data type. |

data_type
NOTE: This parameter is governed by a constraint allowing only the following values:
- boolean
- float
- int
- string
- version
- set

### Test Type Parameters
####pattern not match
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| value | String | A simple (number, string, or boolean) value to be used in determining the result, i.e. pass/fail. |
| data_type | String | Data type. |

data_type
NOTE: This parameter is governed by a constraint allowing only the following values:
- boolean
- float
- int
- string
- version
- set

####existence_test
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| value | String | Value to test. |

####SQL-Unix_File_or_Directory_Permissions_v1
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| username | String | The name of the user that owns the file or directory. |
| group | String | The name of the group that owns the file or directory. |
| uread | String | Determines whether the user that owns the file/directory is permitted to read the contents of it. |
| uwrite | boolean | Determines whether the user that owns the file/directory is permitted to write to it. |
| uexec | boolean | Determines whether the user that owns the file/directory is permitted to execute the file or change into the directory. |
| gread | boolean | Determines whether the group that owns the file/directory is permitted to read the content of it. |
| gwrite | boolean | Determines whether the group that owns the file/directory is permitted to write to it.|
| gexec | boolean | Determines whether the group that owns the file/directory is permitted to execute the file or change into the directory. |
| oread | boolean | Determines whether other users/groups that do not own the file/directory are permitted to read the contents of it. |
| owrite| boolean | Determines whether other users/groups that do not own the file/directory are permitted to write to it. |
| oexec | boolean | Determines whether other users/groups that do not own the file/directory are permitted to execute the file or change into the directory. |
| dir_only | boolean | If this is checking a directory permissions and no file within a directory then this should be set to true. |

####independent.txt_file_content_v1
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| subexpression | String | This represents a value to test against the subexpression in the specified pattern. If multiple subexpressions are specified in the pattern, this value is tested against all of them. |
| filepath | String | This specifies the absolute path for a file on the machine. A directory cannot be specified as a filepath. |
| path | String | This specifies the directory component of the absolute path to a file on the machine. |
| filename | String | This represents the name of a file. |
| pattern | binary | This represents a regular expression that is used to define a block of text. |
| instance | binary | This calls out a specific match of the pattern. This can only be a positive integer. |
| subexp_op | String | This specifies what operation to perform on the subexpression. |
| inst_op | String |  |
| text | String | This represents the block of text that matched the specified pattern. |
| text_op | String | This specifies what operation to perform on the text. |

####Txt-Unix_File_or_Directory_Permissions_v1
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| username | String | The name of the user that owns the file or directory. |
| group | String | The name of the group that owns the file or directory. |
| uread | String | Determines whether the user that owns the file/directory is permitted to read the contents of it. |
| uwrite | boolean | Determines whether the user that owns the file/directory is permitted to write to it. |
| uexec | boolean | Determines whether the user that owns the file/directory is permitted to execute the file or change into the directory. |
| gread | boolean | Determines whether the group that owns the file/directory is permitted to read the content of it. |
| gwrite | boolean | Determines whether the group that owns the file/directory is permitted to write to it.|
| gexec | boolean | Determines whether the group that owns the file/directory is permitted to execute the file or change into the directory. |
| oread | boolean | Determines whether other users/groups that do not own the file/directory are permitted to read the contents of it. |
| owrite| boolean | Determines whether other users/groups that do not own the file/directory are permitted to write to it. |
| oexec | boolean | Determines whether other users/groups that do not own the file/directory are permitted to execute the file or change into the directory. |
| dir_only | boolean | If this is checking a directory permissions and no file within a directory then this should be set to true. |

####Txt-Unix_File_or_Directory_Permissions_v2
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| username | String | The name of the user that owns the file or directory. |
| group | String | The name of the group that owns the file or directory. |
| uread | String | Determines whether the user that owns the file/directory is permitted to read the contents of it. |
| uwrite | boolean | Determines whether the user that owns the file/directory is permitted to write to it. |
| uexec | boolean | Determines whether the user that owns the file/directory is permitted to execute the file or change into the directory. |
| gread | boolean | Determines whether the group that owns the file/directory is permitted to read the content of it. |
| gwrite | boolean | Determines whether the group that owns the file/directory is permitted to write to it.|
| gexec | boolean | Determines whether the group that owns the file/directory is permitted to execute the file or change into the directory. |
| oread | boolean | Determines whether other users/groups that do not own the file/directory are permitted to read the contents of it. |
| owrite| boolean | Determines whether other users/groups that do not own the file/directory are permitted to write to it. |
| oexec | boolean | Determines whether other users/groups that do not own the file/directory are permitted to execute the file or change into the directory. |
| dir_only | boolean | If this is checking a directory permissions and no file within a directory then this should be set to true. |

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
                    <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
                    <ae:parameter dt="string" name="data_type">[data_type.value]</ae:parameter>
                </ae:parameters>
            </ae:test>
        </ae:artifact_expression>
    </xccdf:check-content>
</xccdf:check>
```

#### SCAP
##### XCCDF
For `independent.text_file_content_v1` artifacts, the xccdf:check looks like this. 

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
<textfilecontent54_test 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]'
    check_existence='[check_existence.value]' 
    check='[check.value]' 
    comment='[RECOMMENDATION TITLE]'
    version='[version.value]'>
    <object object_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
    <state state_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]'/>
</textfilecontent54_test>
```

###### Object

```
<textfilecontent54_object 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
    comment='[RECOMMENDATION TITLE]'>
    version='[version.value]'>
    <engine>[engine.value]</engine>
    <version>[version.value]</version>
    <path>[path.value]</path>
    <filename>[filename.value]</filename>
    <pattern operation='[pattern_operation.value]' datatype='[datatype.value]'>[pattern.value]</pattern>
    <instance datatype='[instance_datatype.value]' operation='[operation.value]'>[instance.value]</instance>
</textfilecontent54_object>
```
###### State

```
<textfilecontent54_state 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
    comment='[RECOMMENDATION TITLE]'>
    version='[version.value]'>
    <text operation='[text_operation.value]'
            var_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
</textfilecontent54_state>
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
           name: value
           type: string
           value: value.value]
      - parameter: 
           name: data_type
           type: string
           value: [data_type.value]
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
              "name": "value",
              "type": "string",
              "value": "value.value]"
            }
          },
          {
            "parameter": {
              "name": "data_type",
              "type": "string",
              "value": [
                "data_type.value"
              ]
            }
          }
        ]
      }
    }
  }
``` 