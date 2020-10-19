# macos.plist511_v1

## Description
The plist511_test is used to check the value(s) associated with property list preference keys. It can be used to represent any plist file in XML form (whether its native format is ASCII text, binary, or XML), permitting the use of the XPATH query language to explore its contents. It extends the standard TestType as defined in the oval-definitions-schema and one should refer to the TestType description for more information. The required object element references a plist511_object and the optional plist511_state element specifies the data to check.

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| filepath | String |   The absolute path to a plist file (e.g. ~/Library/Preferences/com.apple.Safari.plist). A directory cannot be specified as a filepath.|
| xpath | String | The preference key to check. If the xsi:nil attribute is set to 'true', the plist does not have any keys associated with it (i.e. it is not a CFDictionary) and the default value of the plist will be collected.|


### Supported Test Types
- macos.plist511_v1

### Test Type Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| check_existence | String | Define how many items should be collected|
| check | String | Defines how many collected items must match the expected state |
| operation | String | comparison operation |
| datatype | String | datatype |
| value_of | String | The value of the preference key.|


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
				<ae:artifact type="windows.lockoutpolicyobject">
					<ae:parameters>
						<ae:parameter dt="string" name="lockoutsetting">[SETTING CONSTRAINT VALUE]</ae:parameter>
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
For `windows.lockoutpolicyobject` artifacts, an XCCDF Value element is generated:

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
    <lockoutpolicy_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
            id="oval:org.cisecurity.benchmarks.windows_server_2012_r2:tst:ARTIFACT-OVAL-ID"
            check_existence="at_least_one_exists" check="all"
            comment="[RECOMMENDATION TITLE]"
            version="1">
            <object object_ref="oval:org.cisecurity.benchmarks.windows_server_2012_r2:obj:ARTIFACT-OVAL-ID"/>
            <state state_ref="oval:org.cisecurity.benchmarks.windows_server_2012_r2:ste:ARTIFACT-OVAL-ID"/>
    </lockoutpolicy_test>
```

###### Object

```
   <lockoutpolicy_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
            id="oval:org.cisecurity.benchmarks.windows_server_2012_r2:obj:ARTIFACT-OVAL-ID"
            comment="[RECOMMENDATION TITLE]"
    version="1"/>
```
###### State

```
    <lockoutpolicy_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
            id="oval:org.cisecurity.benchmarks.windows_server_2012_r2:ste:ARTIFACT-OVAL-ID"
            comment="[RECOMMENDATION TITLE]"
            version="1">
            <lockout_duration operation="greater than or equal" datatype="int"
                var_ref="oval:org.cisecurity.benchmarks.windows_server_2012_r2:var:ARTIFACT-OVAL-ID"/>
    </lockoutpolicy_state>
```

###### Variable

```
<external_variable comment="This value is used in [RECOMMENDATION TITLE]" 
                  datatype="[int|boolean]" 
                        id="oval:org.cisecurity.benchmarks.PLATFORM:var:ARTIFACT-OVAL-ID" 
                   version="1"/>
```

#### YAML

```
- artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: windows.lockoutpolicyobject
      parameters:
      - parameter: 
          name: lockoutpolicyobject
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
"artifact-expression": {
  "artifact-unique-id": [ARTIFACT-OVAL-ID],
  "artifact-title": [RECOMMENDATION TITLE],
  "artifact": {
    "type": "windows.lockoutpolicyobject",
    "parameters": [
      {
        "parameter": {
          "name": "lockoutpolicyobject",
          "type": "string",
          "value": [ARTIFACT TYPE PARAMETER VALUE]
        }
      }
    ]
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