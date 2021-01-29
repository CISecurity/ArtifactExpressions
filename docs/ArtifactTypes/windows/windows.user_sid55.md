# windows.user_sid55

## Description
The user_sid55_test is used to check information about Windows users. When the user_sid55_test collects the user SIDs on the system, it should only include the local and built-in user SIDs and not domain user SIDs. However, it is important to note that domain user SIDs can still be looked up. Also, note that the collection of groups, for which a user is a member, is not recursive. The only groups that will be collected are those for which the user is a direct member. For example, if a user is a member of group A, and group A is a member of group B, the only group that will be collected is group A. It extends the standard TestType as defined in the oval-definitions-schema and one should refer to the TestType description for more information. 

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| sid | String | SID|
| sid_operation | String | Operation to match SIDs|
| state | String | SID State to test|

### Supported Test Types
- equals
- equal
- not equal
- less than
- less than or equal
- greater than
- greater than or equal 

### Test Type Parameters
####Equals 
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| data_type | String | datatype of the value |
| value | String | the value included within the set of results/ value to be tested |

####Equal
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
			<ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION_NUMBER]">
				<ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
				<ae:title>[RECOMMENDATION TITLE]</ae:title>
				<ae:artifact type="windows.user_sid55">
                <ae:parameters>
                    <ae:parameter dt="string" name="sid"
                        >[sid.value]</ae:parameter>
                    <ae:parameter dt="string" name="sid_operation">[sid_operation.value]</ae:parameter>
                    <ae:parameter dt="string" name="state"
                        >[state.value]</ae:parameter>
                </ae:parameters>
				</ae:artifact>
				<ae:test type="[TestType Name]">
					<ae:parameters>
						<ae:parameter dt="string" name="value">[TestType.value]</ae:parameter>
						<ae:parameter dt="string" name="data_type">[TestType.data_type]</ae:parameter>
					</ae:parameters>
				</ae:test>
			</ae:artifact_expression>
		</xccdf:check-content>
	</xccdf:check>
</xccdf:complex-check>
```

#### SCAP
##### XCCDF
For `windows.user_sid55` artifacts, an XCCDF Value element is generated:

```
<Value id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" 
       operator="[TestType Name]" type="[number|boolean]">
  <title>[RECOMMENDATION TITLE]</title>
  <description>This value is used in Rule: [RECOMMENDATION TITLE]</description>
  <value>[TestType.value.value]</value>
</Value>
```

##### OVAL
###### Test

```
 <user_sid55_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
             id="oval:org.cisecurity.benchmarks.windows_8.1:tst:ARTIFACT_OVAL_ID"
             check_existence="at_least_one_exists" check="all"
             comment="[RECOMMENDATION_TITLE]"
             version="1">
             <object object_ref="oval:org.cisecurity.benchmarks.windows_8.1:obj:ARTIFACT_OVAL_ID"/>
             <state state_ref="oval:org.cisecurity.benchmarks.windows_8.1:ste:ARTIFACT_OVAL_ID"/>
         </user_sid55_test>
```

###### Object

```
<user_sid55_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
            id="oval:org.cisecurity.benchmarks.windows_8.1:obj:ARTIFACT_OVAL_ID"
            comment="[RECOMMENDATION_TITLE]"
            version="1">
           <user_sid operation="pattern match">^S\-1\-5\-21\-\d+\-\d+\-\d+\-500$</user_sid>
</user_sid55_object>
```

###### State

```
<user_sid55_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
            id="oval:org.cisecurity.benchmarks.windows_8.1:ste:ARTIFACT_OVAL_ID"
            comment="[RECOMMENDATION_TITLE]"
            version="1">
           <enabled operation="[testtype_name]" datatype="[testtype.datatype.value]"
                           var_ref="oval:org.cisecurity.benchmarks.windows_8.1:var:ARTIFACT_OVAL_ID"/>
</user_sid55_state>
```

#### YAML

```
- artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: windows.user_sid55
      parameters:
      - parameter: 
          name: sid
          type: string
          value: [ARTIFACT TYPE PARAMETER VALUE]
      - parameter: 
          name: sid_operation
          type: string
          value: [ARTIFACT TYPE PARAMETER VALUE]
      - parameter: 
          name: state
          type: string
          value: [ARTIFACT TYPE PARAMETER VALUE]
    test:
      type: [TestType Name]
      parameters:
      - parameter:
          name: value
          type: string
          value: [TestType.value.value]
      - parameter: 
          name: data_type
          type: string
          value: [TestType.data_type.value]
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
      "type": "windows.user_sid55",
      "parameters": [
        {
          "parameter": {
            "name": "sid",
            "type": "string",
            "value": [
              "ARTIFACT TYPE PARAMETER VALUE"
            ]
          }
        },
        {
          "parameter": {
            "name": "sid_operation",
            "type": "string",
            "value": [
              "ARTIFACT TYPE PARAMETER VALUE"
            ]
          }
        },
        {
          "parameter": {
            "name": "state",
            "type": "string",
            "value": [
              "ARTIFACT TYPE PARAMETER VALUE"
            ]
          }
        }
      ]
    },
    "test": {
      "type": [
        "TestType Name"
      ],
      "parameters": [
        {
          "parameter": {
            "name": "value",
            "type": "string",
            "value": [
              "TestType.value.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "data_type",
            "type": "string",
            "value": [
              "TestType.data_type.value"
            ]
          }
        }
      ]
    }
  }
}
``` 