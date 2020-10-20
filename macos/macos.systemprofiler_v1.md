# macos.systemprofiler_v1

## Description
The systemprofiler_test is used to check the properties of the plist-style XML output from the “system_profiler -xml <data type>” command, for reading information about system inventory data on MacOSX. It extends the standard TestType as defined in the oval-definitions-schema and one should refer to the TestType description for more information. The required object element references an systemprofiler_object and the optional state element specifies the data to check.

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| data_type | String |The data_type entity provides the datatype value that is desired.|
| xpath | String |Specifies an Xpath expression describing the text node(s) or attribute(s) to look at. Any valid Xpath 1.0 statement is usable with one exception, at most one field may be identified in the Xpath. This is because the value_of element in the data section is only designed to work against a single field. The only valid operator for xpath is equals since there is an infinite number of possible xpaths and determinining all those that do not equal a given xpath would be impossible.|

### Supported Test Types
- macos.systemprofiler_v1

### Test Type Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| check_existence | String | Define how many items should be collected|
| check | String | Defines how many collected items must match the expected state |
| operation | String | comparison operation |
| datatype | String | datatype |
| value_of | String | The value_of element checks the value(s) of the text node(s) or attribute(s) found.|


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