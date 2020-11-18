# unix.kernel_parameter_v1

## Description
TBD

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| parameter | String | kernel parameter to be checked |

### Supported Test Types
- equals
- not equal
- less than
- less than or equal,
- greater than
- greater than or equal
- pattern match
- pattern not match

### Test Type Parameters

####Equals
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| data_type | String | datatype of the value |
| value | String | the value included within the set of results/ value to be tested |

####Not Equal
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| data_type | String | datatype of the value |
| value | String | the value included within the set of results/ value to be tested |

####Less Than 
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| data_type | String | datatype of the value |
| value | String | the value included within the set of results/ value to be tested |

####Less Than or Equal 
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| data_type | String | datatype of the value |
| value | String | the value included within the set of results/ value to be tested |

####Greater Than
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| data_type | String | datatype of the value |
| value | String | the value included within the set of results/ value to be tested |

####Greater Than or Equal 
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| data_type | String | datatype of the value |
| value | String | the value included within the set of results/ value to be tested |

####Pattern Match
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| data_type | String | datatype of the value |
| value | String | regex to be matched |

####Pattern not match
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| data_type | String | datatype of the value |
| value | String |regex to be matched  |

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
            <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_1.5.1.3">
                <ae:artifact_oval_id>[ARTIFACT_OVAL_ID]</ae:artifact_oval_id>
                <ae:title>[RECOMMENDATION_TITLE]</ae:title>
                <ae:artifact type="[ARTIFACT_TYPE]">
                    <ae:parameters>
                        <ae:parameter dt="string" name="parameter"
                            >[parameter.value]</ae:parameter>
                    </ae:parameters>
                </ae:artifact>
                <ae:test type="[TEST_TYPE]">
                    <ae:parameters>
                        <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
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
For `unix.kernel_parameter_v1` artifacts, an XCCDF Check element is generated:

```
<check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-content-ref href="[BENCHMARK_NAME]"
        name="oval:org.cisecurity.benchmarks.centos_centos_7:def:[ARTIFACT_OVAL_ID]"/>
</check>
```

##### OVAL
###### Test

```
<shellcommand_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#cmd"
			id="oval:org.cisecurity.benchmarks.centos_centos_7:tst:[ARTIFACT_OVAL_ID]"
			check_existence="at_least_one_exists" check="at least one"
			comment="[RECOMMENDATION_TITLE]" version="1">
			<object object_ref="oval:org.cisecurity.benchmarks.centos_centos_7:obj:[ARTIFACT_OVAL_ID]"/>
			<state state_ref="oval:org.cisecurity.benchmarks.centos_centos_7:ste:[ARTIFACT_OVAL_ID]"/>
		</shellcommand_test>
```

###### Object

```
<shellcommand_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#cmd"
			id="oval:org.cisecurity.benchmarks.centos_centos_7:obj:[ARTIFACT_OVAL_ID]"
			comment="[RECOMMENDATION_TITLE]" version="1">
			<command>modprobe -n -v dccp</command>
			<line_selection operation="pattern match">.+</line_selection>
		</shellcommand_object>
```
###### State

```
<shellcommand_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#cmd"
			id="oval:org.cisecurity.benchmarks.centos_centos_7:ste:[ARTIFACT_OVAL_ID]"
			comment="[RECOMMENDATION_TITLE]" version="1">
			<stdout_line entity_check="at least one" operation="pattern match"
				>^install\s+/bin/true\s*$</stdout_line>
		</shellcommand_state>
```

#### YAML

```
artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: unix.kernel_parameter_v1
      parameters:
      - parameter: 
          name: parameter
          type: string
          value: [parameter.value]
    test:
      type: [Testtype name]
      parameters:
      - parameter: 
          name: data_type
          type: string
          value: [enabled.value]
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
      "type": "unix.kernel_parameter_v1",
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
        "Testtype name"
      ],
      "parameters": [
        {
          "parameter": {
            "name": "data_type",
            "type": "string",
            "value": [
              "enabled.value"
            ]
          }
        },
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