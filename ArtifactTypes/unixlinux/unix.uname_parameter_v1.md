# unix.uname_parameter_v1

## Description
The uname test reveals information about the hardware the machine is running on. This information is the parsed equivalent of uname -a. 
## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| parameter | String | the uname parameter to be tested. |

parameter 
NOTE: This parameter is governed by a constraint allowing only the following values:
- machine_class
- node_name 
- os_name
- os_release
- os_version
- processor_type

### Supported Test Types
- equals
- not equal
- less than
- less than or equal
- greater than 
- greater than or equal 
- pattern match 
- pattern not match

### Test Type Parameters

| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| value | String |The value element contains a string that represents the value(s) associated with the specified sshd parameter.			 |
| data_type  | String |datatype |

data_type
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
<xccdf:complex-check operator="AND">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
            <xccdf:check-content>
                <ae:artifact_expression
                    id="xccdf_org.cisecurity.benchmarks_ae_4.1.4.10">
                    <ae:artifact_oval_id>[ARTIFACT_OVAL_ID]</ae:artifact_oval_id>
                    <ae:title>[RECOMMENDATION_TITLE]</ae:title>
                    <ae:artifact type="[ARTIFACT_TYPE]">
                        <ae:parameters>
                            <ae:parameter dt="string" name="parameter"
                                >[parameter.value]</ae:parameter>
                        </ae:parameters>
                    </ae:artifact>
                    <ae:test type="[TESTTYPE]">
                        <ae:parameters>
                            <ae:parameter dt="string" name="value"
                                >[value.value]</ae:parameter>
                            <ae:parameter dt="string" name="data_type"
                                >[data_type.value]</ae:parameter>
                        </ae:parameters>
                    </ae:test>
                </ae:artifact_expression>
            </xccdf:check-content>
        </xccdf:check>
</xccdf:complex-check>
```

#### SCAP
##### XCCDF
For `unix.uname_parameter_v1` artifacts, artifacts, an XCCDF Value element is generated:

```
 <Value id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" type="string"
            operator="[testTypeName]">
            <title>[RECOMMENDATION_TITLE]</title>
            <description>This value is used in Rule: [RECOMMENDATION TITLE]</description>
            <value>[TestType.value.value]</value>
</Value>
```

##### OVAL
###### Test

```
<uname_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.centos_centos_7:tst:[ARTIFACT_OVAL_ID]"
    check_existence="at_least_one_exists" check="all"
    comment="[RECOMMENDATION_TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.centos_centos_7:obj:[ARTIFACT_OVAL_ID]"/>
    <state state_ref="oval:org.cisecurity.benchmarks.centos_centos_7:ste:[ARTIFACT_OVAL_ID]"/>
</uname_test>
```

###### Object

```
<uname_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.centos_centos_7:obj:[ARTIFACT_OVAL_ID]"
    comment="[RECOMMENDATION_TITLE]"
    version="1"/>
```
###### State

```
<uname_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.centos_centos_7:ste:[ARTIFACT_OVAL_ID]"
    comment="[RECOMMENDATION_TITLE]"
    version="1">
    <processor_type datatype="string" operation="not equal"
        var_ref="oval:org.cisecurity.benchmarks.centos_centos_7:var:[ARTIFACT_OVAL_ID]"/>
</uname_state>
```

###### Variable

```
<external_variable comment="This value is used in [RECOMMENDATION TITLE]" 
                  datatype="[string]" 
                        id="oval:org.cisecurity.benchmarks.PLATFORM:var:ARTIFACT-OVAL-ID" 
                   version="1"/>
```

#### YAML

```
artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: unix.uname_parameter_v1
      parameters:
      - parameter: 
          name: parameter
          type: string
          value: [parameter.value]
    test:
      type: [testType name]
      parameters:
      - parameter: 
          name: value
          type: string
          value: [value.value]
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
      "type": "unix.uname_parameter_v1",
      "parameters": [
        {
          "parameter": {
            "name": "parameter",
            "type": "string",
            "value": [
              "parameter.value"
            ]
          }
        }
      ]
    },
    "test": {
      "type": [
        "testType name"
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