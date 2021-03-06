# unix.command_output_v1

## Description
TBD

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| command | String | Command to run |


### Supported Test Types
- pattern match
- pattern not match
- equals
- null_test_v1

### Test Type Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| value | String | Regular expression to be matched |
| data_type | String | datatype |  datatype


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
						<ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_19.2.1">
							<ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
							<ae:title>[RECOMMENDATION_TITLE</ae:title>
							<ae:artifact type="[ARTIFACT_TYPE_NAME]">
								<ae:parameters>
									<ae:parameter dt="string" name="command">[command.value]</ae:parameter>
								</ae:parameters>
							</ae:artifact>
							<ae:test type="pattern not match">
								<ae:parameters>
									<ae:parameter dt="string" name="value">[value.value]</ae:parameter>
									<ae:parameter dt="string" name="data_type">[testParameter.data_type.value]</ae:parameter>
								</ae:parameters>
							</ae:test>
						</ae:artifact_expression>
					</xccdf:check-content>
				</xccdf:check>
			</xccdf:complex-check>
```

#### SCAP
##### XCCDF
For `unix.command_output_v1` artifacts, artifacts, an XCCDF Value element is generated:

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
<shellcommand_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#cmd"
            id="oval:org.cisecurity.benchmarks.canonical_ubuntu_linux_18:tst:ARTIFACT_OVAL_ID"
            check_existence="at_least_one_exists" check="all"
            comment="[RECOMMENDATION_TITLE]" version="1">
            <object object_ref="oval:org.cisecurity.benchmarks.canonical_ubuntu_linux_18:obj:ARTIFACT_OVAL_ID"
            />
</shellcommand_test>
```

###### Object

```
<shellcommand_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#cmd"
            id="oval:org.cisecurity.benchmarks.canonical_ubuntu_linux_18:obj:ARTIFACT_OVAL_ID"
            comment="[RECOMMENDATION_TITLE]" version="1">
            <command/>
            <line_selection operation="[TestType]">[TestType.value]</line_selection>
    </shellcommand_object>
```
###### State

```
<shellcommand_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#cmd"
            id="oval:org.cisecurity.benchmarks.centos_centos_7:ste:[ARTIFACT_OVAL_ID]"
            comment='[RECOMMENDATION_TITLE]'
            version="1">
            <stdout_line entity_check="at least one" operation="pattern match"
                var_ref="oval:org.cisecurity.benchmarks.centos_centos_7:var:[ARTIFACT_OVAL_ID]"/>
</shellcommand_state> 
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
      type: unix.command_output_v1
      parameters:
      - parameter: 
          name: command
          type: string
          value: [command.value]
    test:
      type: [TestType Name]
      parameters:
      - parameter: 
          name: value
          type: string
          value: [value.value]
      - parameter: 
          name: datatype
          type: string
          value: [datatype.value]                                     
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
      "type": "unix.command_output_v1",
      "parameters": [
        {
          "parameter": {
            "name": "command",
            "type": "string",
            "value": [
              "command.value"
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
              "value.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "datatype",
            "type": "string",
            "value": [
              "datatype.value"
            ]
          }
        }
      ]
    }
  }
}
```