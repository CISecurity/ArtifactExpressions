# independent.text_file_content_tomcat_v1

## Description
The independent.text_file_content_tomcat_v1 is used to check the contents of a text file (aka a configuration file) by looking at individual blocks of text.

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
| recurse | String | Should subdirectories be recursed through. |
| max_depth | Binary | Max depth for recursion. -1 for unlimited recursion |
| file_system | String | Filesystem limitation for recursion. All filesystems, restrict to local only, or restrict to filesystem defined by Path. |
| xpath | String |  Specifies an XPath 1.0 expression to evaluate against the XML file specified by the filename entity. This XPath 1.0 expression must evaluate to a list of zero or more text values which will be accessible in OVAL via instances of the value_of entity. Any results from evaluating the XPath 1.0 expression other than a list of text strings (e.g., a nodes set) is considered an error. The intention is that the text values be drawn from instances of a single, uniquely named element or attribute. However, an OVAL interpreter is not required to verify this, so the author should define the XPath expression carefully. |
| pattern | String |  	This defines a chunk of text in a file and is represented using a regular expression. A subexpression (using parentheses) can call out a piece of the text block to test. Must be a valid expression according to Perl 5's regular expression specification. |
| check | String | Defines how many collected items must match the expected state. |

check
NOTE: This parameter is governed by a constraint allowing only the following values:
- all
- at least one
- none satisfy
- only one

### Supported Test Types
- Txt-Unix_File_or_Directory_Permissions_v2
- existence_test
- independent.xmlfilecontent_v2

### Test Type Parameters
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

####existence_test
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| value | String | Value to test. |

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
                    <ae:parameter dt="string" name="recurse">[recurse.value]</ae:parameter>
                    <ae:parameter dt="binary" name="max_depth">[max_depth.value]</ae:parameter>
                    <ae:parameter dt="string" name="file_system">[file_system.value]</ae:parameter>
                    <ae:parameter dt="string" name="xpath">[xpath.value]</ae:parameter>
                    <ae:parameter dt="string" name="pattern">[pattern.value]</ae:parameter>
                    <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
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
For `independent.text_file_content_tomcat_v1` artifacts, the xccdf:check looks like this. 

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
<textfilecontent54_test 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]'
    check_existence='[check_existence.value]' 
    check='[check.value]' 
    comment='[RECOMMENDATION TITLE]'
    version='[version.value]'>
    <object object_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
</textfilecontent54_test>
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

<textfilecontent54_object 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
    comment='[RECOMMENDATION TITLE]'>
    version='[version.value]'>
    <path var_ref='oval:org.cisecurity.benchmarks:var:[ID]'/>
    <filename>[filename.value]</filename>
    <pattern operation='[operation.value]' datatype='[datatype.value]'>[pattern.value]</pattern>
    <instance datatype='[datatype.value]' operation='[operation.value]'>[instance.value]</instance>
</textfilecontent54_object>
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
           name: recurse
           type: string
           value: [recurse.value]
      - parameter: 
           name: max_depth
           type: binary
           value: [max_depth.value]
      - parameter: 
           name: file_system
           type: string
           value: file_system.value]
      - parameter: 
           name: xpath
           type: string
           value: [xpath.value]
      - parameter: 
           name: pattern
           type: string
           value: [pattern.value]
      - parameter: 
           name: check
           type: string
           value: [check.value]
    test:
      type: [TESTTYPE NAME]
      parameters:   
      - parameter: 
           name: value
           type: string
           value: [value.value]
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
              "name": "recurse",
              "type": "string",
              "value": [
                "recurse.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "max_depth",
              "type": "binary",
              "value": [
                "max_depth.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "file_system",
              "type": "string",
              "value": "file_system.value]"
            }
          },
          {
            "parameter": {
              "name": "xpath",
              "type": "string",
              "value": [
                "xpath.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "pattern",
              "type": "string",
              "value": [
                "pattern.value"
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
              "value": [
                "value.value"
              ]
            }
          }
        ]
      }
    }
  }
``` 