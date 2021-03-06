# windows.lockoutpolicyobject

## Description
The lockout policy test enumerates various attributes associated with lockout information for users and global groups in the security database. 

## Intent
The intent of the `windows.lockoutpolicyobject` artifact type is to allow users to create specific checks against the Windows lockout policy.  The `lockoutsetting` parameter is constrained to the specific list of values, each representing one of the lockout policy attributes that can be collected.

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| lockoutsetting | String | The lockout policy setting to be audited.|

NOTE: This parameter is governed by a constraint allowing only the following values:
- Duration
- Observation Window
- Threshold
- Forced Logoff

### Supported Test Types
- Equal 
- Equals 
- Not Equal
- Equal To
- Less Than
- Less Than or Equal
- Greater Than
- Greater Than or Equal

### Test Type Parameters
####Equal
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| data_type | String | datatype of the value |
| value | String | the value included within the set of results/ value to be tested |

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

####Equal to
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

data_type
NOTE: This parameter is governed by a constraint allowing only the following values:
- boolean
- float
- int
- string
- version
- set

### Generated Content
#### equal, equals, not equal, equal_to, less than, less than or equal, greater than, greater than or equal
#### XCCDF+AE
This is what the AE check looks like, inside a Rule, in the XCCDF

```
<xccdf:complex-check operator="AND">
	<xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
		<xccdf:check-content>
			<ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION_NUMBER]">
				<ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
				<ae:title>[RECOMMENDATION TITLE]</ae:title>
				<ae:artifact type="[ARTIFACTTYPE NAME]">
					<ae:parameters>
						<ae:parameter dt="string" name="lockoutsetting">[lockoutsetting.value]</ae:parameter>
					</ae:parameters>
				</ae:artifact>
				<ae:test type="[TESTTYPE NAME]">
					<ae:parameters>
						<ae:parameter dt="string" name="value">[value.value]</ae:parameter>
						<ae:parameter dt="string" name="data_type">[data_type.data_type]</ae:parameter>
					</ae:parameters>
				</ae:test>
			</ae:artifact_expression>
		</xccdf:check-content>
	</xccdf:check>
</xccdf:complex-check>
```

#### SCAP
##### XCCDF
For `windows.lockoutpolicyobject` artifacts, an XCCDF Value element is generated:

```

<xccdf:complex-check operator="AND">
  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export export-name="oval:org.cisecurity.benchmarks.windows_10:var:[ARTIFACT-OVAL-ID]"
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"/>
    <check-content-ref
      href="[BENCHMARK NAME]"
      name="oval:org.cisecurity.benchmarks.windows_10:def:[ARTIFACT-OVAL-ID]"/>
  </check>
</xccdf:complex-check>

<Value id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" 
       operator="test_type" type="data_type.value">
  <title>[RECOMMENDATION TITLE]</title>
  <description>This value is used in Rule: [RECOMMENDATION TITLE]</description>
  <value>[value.value]</value>
</Value>
```

##### OVAL
###### Test

```
    <lockoutpolicy_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
            id="oval:org.cisecurity.benchmarks.windows_server_2012_r2:tst:[ARTIFACT-OVAL-ID]"
            check_existence="at_least_one_exists" check="all"
            comment="[RECOMMENDATION TITLE]"
            version="1">
            <object object_ref="oval:org.cisecurity.benchmarks.windows_server_2012_r2:obj:[ARTIFACT-OVAL-ID]"/>
            <state state_ref="oval:org.cisecurity.benchmarks.windows_server_2012_r2:ste:[ARTIFACT-OVAL-ID]"/>
    </lockoutpolicy_test>
```

###### Object

```
   <lockoutpolicy_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
            id="oval:org.cisecurity.benchmarks.windows_server_2012_r2:obj:[ARTIFACT-OVAL-ID]"
            comment="[RECOMMENDATION TITLE]"
    version="1"/>
    
```
###### State

```
    <lockoutpolicy_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
            id="oval:org.cisecurity.benchmarks.windows_server_2012_r2:ste:[ARTIFACT-OVAL-ID]"
            comment="[RECOMMENDATION TITLE]"
            version="1">
            <[lockoutsetting.value] operation="[test_type]" datatype="[data_type.value]"
                var_ref="oval:org.cisecurity.benchmarks.windows_server_2012_r2:var:[ARTIFACT-OVAL-ID]"/>
    </lockoutpolicy_state>
```

###### Variable

```
<external_variable comment="This value is used in [RECOMMENDATION TITLE]" 
                  datatype="[data_type.value]" 
                        id="oval:org.cisecurity.benchmarks.PLATFORM:var:[ARTIFACT-OVAL-ID]" 
                   version="1"/>
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
          name: lockoutsetting
          type: string
          value: [lockoutsetting.value]
    test:
      type: [TESTTYPE NAME]
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
"artifact-expression": {
  "artifact-unique-id": [ARTIFACT-OVAL-ID],
  "artifact-title": [RECOMMENDATION TITLE],
  "artifact": {
    "type": "[ARTIFACTTYPE NAME]",
    "parameters": [
      {
        "parameter": {
          "name": "lockoutsetting",
          "type": "string",
          "value": "[lockoutsetting.value]"
        }
      }
    ]
  },
  "test": {
    "type": "[TESTTYPE NAME]",
    "parameters": [
      {
        "parameter": {
          "name": "value",
          "type": "string",
          "value": "[value.value]"
        }
      },
      {
        "parameter": {
          "name": "data_type",
          "type": "string",
          "value": "[data_type.value]"
        }
      }
    ]
  }
}
``` 