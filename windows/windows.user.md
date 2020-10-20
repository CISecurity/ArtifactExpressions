# windows.user

## Description
The user_test is used to check information about Windows users.

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| user | String | username	|
| existence | String | existence of the user |

### Supported Test Types
- null_test_v1

### Generated Content
#### XCCDF+AE
This is what the AE check looks like, inside a Rule, in the XCCDF

```
<xccdf:complex-check operator="OR">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
        <xccdf:check-content>
            <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_14.1.1">
                <ae:artifact_oval_id>[ARTIFACT_OVAL_ID]</ae:artifact_oval_id>
                <ae:title>[RECOMMENDATION_TITLE]</ae:title>
                <ae:artifact type="windows.user">
                    <ae:parameters>
                        <ae:parameter dt="string" name="user"
                            >[parameter_value]</ae:parameter>
                        <ae:parameter dt="string" name="existence"
                            >at_least_one_exists</ae:parameter>
                    </ae:parameters>
                </ae:artifact>
                <ae:test type="[Testtype Name]">
                </ae:test>
            </ae:artifact_expression>
        </xccdf:check-content>
    </xccdf:check>
</xccdf:complex-check>
```

#### SCAP

##### OVAL
###### Test

```
<user_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
            id="oval:org.cisecurity.benchmarks.windows_8.1:tst:ARTIFACT-OVAL-ID"
            check_existence="at_least_one_exists" check="all"
            comment="[RECOMMENDATION_TITLE]"
            version="1">
            <object object_ref="oval:org.cisecurity.benchmarks.windows_8.1:obj:ARTIFACT-OVAL-ID"/>
            <state state_ref="oval:org.cisecurity.benchmarks.windows_8.1:ste:ARTIFACT-OVAL-ID"/>
</user_test>
```

###### Object

```
<user_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
      id="oval:org.cisecurity.benchmarks.windows_8.1:obj:ARTIFACT-OVAL-ID"
            comment="[RECOMMENDATION_TITLE]"
            version="1">
        <user datatype="string" operation="[TEST_TYPE_NAME]">[TestType.data_type.value]</user>       
 </user_object>
```

#### YAML

```
- artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: windows.user
      parameters:
      - parameter: 
          name: [PARAMETER_NAME]
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
    "type": "windows.user",
    "parameters": [
      {
        "parameter": {
          "name": "[PARAMETER_NAME]",
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
      }
    ]
  }
}
``` 