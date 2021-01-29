# windows.rsop.security_setting_boolean

## Description
The wmi57 test is used to check information accessed by WMI. It extends the standard TestType as defined in the oval-definitions-schema and one should refer to the TestType description for more information. The required object element references a wmi57_object and the optional state element specifies the metadata to check.
## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| keyname | String | RSOP Security Setting Boolean Key Name		|

### Supported Test Types
- equals
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
        <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_5.1.2">
            <ae:artifact_oval_id>[ARTIFACT_OVAL_ID]</ae:artifact_oval_id>
            <ae:title>[RECOMMENDATION_TITLE]</ae:title>
            <ae:artifact type="[ARTIFACT_TYPE.name]">
                <ae:parameters>
                    <ae:parameter dt="string" name="keyname"
                        >[keyname.value]</ae:parameter>
                </ae:parameters>
            </ae:artifact>
            <ae:test type="[TESTTYPE_NAME]">
                <ae:parameters>
                    <ae:parameter dt="string" name="value">[testype.value.value]</ae:parameter>
                    <ae:parameter dt="string" name="data_type">[testype.data_type.value]</ae:parameter>
                </ae:parameters>
            </ae:test>
        </ae:artifact_expression>
    </xccdf:check-content>
    </xccdf:check>
</xccdf:complex-check>
```

#### SCAP
##### XCCDF
For `windows.rsop.security_setting_boolean` artifacts, an XCCDF Value element is generated:

```
<Values>
			<Value id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT_OVAL_ID]_var1" type="string"
				operator="equals">
				<title>[RECOMMENDATION_TITLE]</title>
				<description>This value is used in Rule: [RECOMMENDATION_TITLE]</description>
				<value>[TestType.value.value]</value>
			</Value>
		</Values>
```

##### OVAL
###### Test

```
<wmi57_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
        id="oval:org.cisecurity.benchmarks.windows_8.1:tst:[ARTIFACT_OVAL_ID]"
        check_existence="at_least_one_exists" check="all"
        comment="[RECOMMENDATION_TITLE]"
        version="1">
        <object object_ref="oval:org.cisecurity.benchmarks.windows_8.1:obj:[ARTIFACT_OVAL_ID]"/>
        <state state_ref="oval:org.cisecurity.benchmarks.windows_8.1:ste:[ARTIFACT_OVAL_ID]"/>
    </wmi57_test>
```

###### Object

```
<wmi57_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.windows_8.1:ste:[ARTIFACT_OVAL_ID]"
    comment="[RECOMMENDATION_TITLE]"
    version="1">
    <result datatype="record" entity_check="all">
        <field xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5" name="setting"
            operation="equals" datatype="boolean"
            var_ref="oval:org.cisecurity.benchmarks.windows_8.1:var:[ARTIFACT_OVAL_ID]"/>
    </result>
</wmi57_state>
```

###### State

```
<wmi57_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.windows_8.1:ste:[ARTIFACT_OVAL_ID]"
    comment="[RECOMMENDATION_TITLE]"
    version="1">
    <result datatype="record" entity_check="all">
        <field xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5" name="setting"
            operation="[testType.name]" datatype="[testType.datatype.value]"
            var_ref="oval:org.cisecurity.benchmarks.windows_8.1:var:[ARTIFACT_OVAL_ID]"/>
    </result>
</wmi57_state>
```

###### Variable

```
<external_variable id="oval:org.cisecurity.benchmarks.windows_8.1:var:[ARTIFACT_OVAL_ID]1"
			datatype="string" version="1"
			comment="This value is used in Rule: [RECOMMENDATION_TITLE]/?
/>
```


#### YAML

```
- artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: windows.rsop.security_setting_boolean
      parameters:
      - parameter: 
          name: keyname
          type: string
          value: [ARTIFACT TYPE PARAMETER VALUE]     
test:
      type: [TestType Name]
      parameters:
      - parameter:
          name: value
          type: string
          value: [TestType.value.value]
```

#### JSON

```
"artifact-expression": {
  "artifact-unique-id": [ARTIFACT-OVAL-ID],
  "artifact-title": [RECOMMENDATION TITLE],
  "artifact": {
    "type": "windows.rsop.security_setting_boolean",
    "parameters": [
      {
        "parameter": {
          "name": "keyname",
          "type": "string",
          "value": [ARTIFACT TYPE PARAMETER VALUE]
        }
      }]
  },
  "test": {
    "type": [TestType Name],
    "parameters": [
      {
        "parameter": {
          "name": "value",
          "type": "string",
          "value": [TestType.value.value]
        }
      }, 
   {
      "parameter": {
        "name": "data_type",
        "type": "string",
        "value": [TestType.data_type.value]
      }
    }
    ]
  }
}
``` 