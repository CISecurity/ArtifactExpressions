# windows.sid_sid_v1

## Description
The sid_sid_test is used to check properties associated with the specified SID. It extends the standard TestType as defined in the oval-definitions-schema and one should refer to the TestType description for more information. The required object element references a sid_sid_object and the optional state element specifies the metadata to check.
## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| trustee_sid | String | The trustee_sid entity identifies a unique SID associated with a user, group, system, or program (such as a Windows service).	|
| trustee_sid_operator | String |  The operator used to qualify the Trustee SID. This is typically 'pattern match' or 'equals'	|

### Supported Test Types
- windows.sid_sid_trustee_name_v1

### Test Type Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| check_existence | String | Define how many items should be collected|
| check | String | Defines how many collected items must match the expected state |
| operation | String | comparison operation |
| datatype | String | datatype |
| trustee_name | String | This element specifies the trustee name associated with a particular SID. In Windows, trustee names are case-insensitive. As a result, it is recommended that the case-insensitive operations are used for this entity.|


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
				<ae:artifact type="windows.sid_sid_v1">
                <ae:parameters>
                 <ae:parameter dt="string" name="trustee_sid"
                    >[trustee_sid.value]</ae:parameter>
                <ae:parameter dt="string" name="trustee_sid_operator">
                    [trustee_sid_operator.value]</ae:parameter>
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
For `windows.sid_sid_v1` artifacts, an XCCDF Value element is generated:

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
 <sid_sid_v1_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
             id="oval:org.cisecurity.benchmarks.windows_8.1:tst:ARTIFACT_OVAL_ID"
             check_existence="at_least_one_exists" check="all"
             comment="[RECOMMENDATION_TITLE]"
             version="1">
             <object object_ref="oval:org.cisecurity.benchmarks.windows_8.1:obj:ARTIFACT_OVAL_ID"/>
             <state state_ref="oval:org.cisecurity.benchmarks.windows_8.1:ste:ARTIFACT_OVAL_ID"/>
         </sid_sid_v1_test>
```

###### Object

```
<sid_sid_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
            id="oval:org.cisecurity.benchmarks.windows_8.1:obj:231103"
            comment="[RECOMMENDATION_TITLE]"
            version="1">
            <trustee_sid operation="pattern match">[trustee_sid.value]</trustee_sid>
        </sid_sid_object>
```

###### State

```
 <sid_sid_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
            id="oval:org.cisecurity.benchmarks.windows_8.1:ste:231103"
            comment="Ensure &apos;^S\-1\-5\-21\-\d+\-\d+\-\d+\-500$&apos; is &apos;case insensitive not equal&apos; &apos;Administrator&apos;"
            version="1">
            <[testParameter.name] operation="[testType.name]" datatype="[testType.datatype]">[testParameter.value]</[testParameter.name]>
        </sid_sid_state>
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
      type: windows.sid_sid_v1
      parameters:
      - parameter: 
          name: trustee_sid
          type: string
          value: [ARTIFACT TYPE PARAMETER VALUE]
      - parameter: 
            name: trustee_sid_operator
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
    "type": "windows.sid_sid_v1",
    "parameters": [
      {
        "parameter": {
          "name": "trustee_sid",
          "type": "string",
          "value": [ARTIFACT TYPE PARAMETER VALUE]
        }
      }, 
       {
          "parameter": {
            "name": "trustee_sid_operator",
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