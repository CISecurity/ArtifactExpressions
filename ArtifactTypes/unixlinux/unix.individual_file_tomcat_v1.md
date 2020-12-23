# unix.individual_file_tomcat_v1

## Description
The unix.individual_file_tomcat_v1 is used to check the contents of a file.

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| base_path | String | Base component of path either $CATALINA_HOME or $CATALINA_BASE. |
| path | String | Directory component of the absolute path to the file after $CATALINA_HOME or $CATALINA_BASE. |
| concat_path | String | Directory component after <appname>. |
| filename | String | Filename component of the absolute path to the file. |
| check | String | Defines how many collected items must match the expected state. |
| check_existence | String | Defines how many items should be collected. |

check
NOTE: This parameter is governed by a constraint allowing only the following values:
- all
- at least one
- none satisfy
- only one

check_existence
NOTE: This parameter is governed by a constraint allowing only the following values:
- all_exist
- any_exist
- at_least_one_exists
- none_satisfy
- none_exist
- only_one_exists

### Supported Test Types
- existence_test

### Test Type Parameters
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
                    <ae:parameter dt="string" name="base_path">[base_path.value]</ae:parameter>
                    <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
                    <ae:parameter dt="string" name="concat_path">[concat_path.value]</ae:parameter>
                    <ae:parameter dt="string" name="filename">[filename.value]</ae:parameter>
                    <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
                    <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
                </ae:parameters>
            </ae:artifact>
            <ae:test type="[TESTTYPE NAME]">
                <ae:parameters>
                    <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
                </ae:parameters>
            </ae:test>
        </ae:artifact_expression>
    </xccdf:check-content>
</xccdf:check>
```

#### SCAP
##### XCCDF
For `unix.individual_file_tomcat_v1` artifacts, the xccdf:check looks like this. 

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
<file_test
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]'
    check_existence='[check_existence.value]' 
    check='[check.value]' 
    comment='[RECOMMENDATION TITLE]'
    version='[version.value]'>
    <object object_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
</file_test>
```

###### Object

```
<file_object 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
    comment='[RECOMMENDATION TITLE]'>
    version='[version.value]'>
    <behaviors 
        max_depth='[max_depth.value]' 
        recurse='[recurse.value]' 
        recurse_direction='[recurse_direction.value]'/>
    <path var_ref='oval:org.cisecurity.benchmarks:var:[ID]'/>
    <filename xsi:nil='[filename.value]'/>
</file_object>
<file_object 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
    comment='[RECOMMENDATION TITLE]'>
    version='[version.value]'>
    <path var_ref='oval:org.cisecurity.benchmarks:var:[ID]'/>
    <filename>[filaename.value]</filename>
</file_object>
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
           name: base_path
           type: string
           value: [base_path.value]
      - parameter: 
           name: path
           type: string
           value: [path.value]
      - parameter: 
           name: concat_path
           type: string
           value: concat_path.value]
      - parameter: 
           name: filename
           type: string
           value: [filename.value]
      - parameter: 
           name: check
           type: string
           value: [check.value]
      - parameter: 
           name: check_existence
           type: string
           value: [check_existence.value]
    test:
      type: [TESTTYPE NAME]
      parameters:   
      - parameter: 
           name: value
           type: string
           value: value.value]
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
              "name": "base_path",
              "type": "string",
              "value": [
                "base_path.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "path",
              "type": "string",
              "value": [
                "path.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "concat_path",
              "type": "string",
              "value": "concat_path.value]"
            }
          },
          {
            "parameter": {
              "name": "filename",
              "type": "string",
              "value": [
                "filename.value"
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
              "name": "value",
              "type": "string",
              "value": "value.value]"
            }
          }
        ]
      }
    }
  }
``` 