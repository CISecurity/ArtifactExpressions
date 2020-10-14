# windows.passwordpolicyobject

## Description
The password policy test is used to check specific policy associated with passwords. It is important to note that these policies are specific to certain versions of Windows. As a result, the documentation for that version of Windows should be consulted for more information.

## Intent
The intent of the `windows.passwordpolicyobject` artifact type is to allow users to create specific checks against the Windows password policy.  The `passwordpolicysetting` parameter is constrained to the specific list of values, each representing one of the password policy attributes that can be collected.

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| passwordpolicysetting | String | The password policy setting to be audited.|

NOTE: This parameter is governed by a constraint allowing only the following values:
- Max Passwd Age
- Min Passwd Age
- Min Passwd Len
- Password Hist Len
- Password Complexity
- Reversible Encryption

### Supported Test Types
- Equals (value, data_type)
- Not Equal
- Less Than
- Less Than or Equal
- Greater Than
- Greater Than or Equal

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
				<ae:artifact type="windows.passwordpolicyobject">
					<ae:parameters>
						<ae:parameter dt="string" name="passwordpolicysetting">[SETTING CONSTRAINT VALUE]</ae:parameter>
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
For `windows.passwordpolicyobject` artifacts, an XCCDF Value element is generated:

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
<passwordpolicy_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows" 
                     check="all" 
           check_existence="at_least_one_exists" 
                   comment="[RECOMMENDATION TITLE]" 
                        id="oval:org.cisecurity.benchmarks.PLATFORM:tst:ARTIFACT-OVAL-ID" 
                   version="1">
   <object object_ref="oval:org.cisecurity.benchmarks.PLATFORM:obj:ARTIFACT-OVAL-ID"/>
   <state state_ref="oval:org.cisecurity.benchmarks.PLATFORM:ste:ARTIFACT-OVAL-ID"/>
</passwordpolicy_test>
```

###### Object

```
<passwordpolicy_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows" 
  comment="[RECOMMENDATION TITLE]" 
       id="oval:org.cisecurity.benchmarks.PLATFORM:obj:ARTIFACT-OVAL-ID" 
  version="1"/>
```

###### State

```
<passwordpolicy_state 
   xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows" 
 comment="[RECOMMENDATION TITLE]" 
      id="oval:org.cisecurity.benchmarks.PLATFORM:ste:ARTIFACT-OVAL-ID" version="1">
   <[passwordpolicysetting] datatype="[int|boolean]" 
      operation="[TestType Name]" 
        var_ref="oval:org.cisecurity.benchmarks.PLATFORM:var:ARTIFACT-OVAL-ID"/>
</passwordpolicy_state>
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
      type: windows.passwordpolicyobject
      parameters:
      - parameter: 
          name: passwordpolicysetting
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
    "type": "windows.passwordpolicyobject",
    "parameters": [
      {
        "parameter": {
          "name": "passwordpolicysetting",
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