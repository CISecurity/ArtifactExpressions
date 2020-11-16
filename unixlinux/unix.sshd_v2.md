# unix.sshd_v2

## Description
TBD

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| name | String | The name element specifies the name(s) of the sshd parameter(s) that should be collected from the local system.|


### Supported Test Types
- unix.sshd_v2

### Test Type Parameters

| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| check_existence | String |Defines how many items should be collected		 |
| check | String | Defines how many collected items must match the expected state	 |	
| operation | String | string comparison operation |
| value | String |The value element contains a string that represents the value(s) associated with the specified sshd parameter.			 |
| datatype  | String |datatype	 |

datatype
NOTE: This parameter is governed by a constraint allowing only the following values:
- boolean
- float
- int
- string
- version
- set

operation
NOTE: This parameter is governed by a constraint allowing only the following values:
- equals
- not equal
- case insensitive equals
- case insensitive not equal
- greater than
- less than
- greater than or equal
- less than or equal
- bitwise and
- bitwise or
- pattern match
- subset of
- superset of 

check_existence
NOTE: This parameter is governed by a constraint allowing only the following values:
- all_exist
- any_exist
- at_least_one_exists
- none_satisfy
- none_exist
- only_one_exists

check
NOTE: This parameter is governed by a constraint allowing only the following values:
- all
- at least one 
- none satisfy
- only one 

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
                        <ae:parameter dt="string" name="name">[name.value]</ae:parameter>
                    </ae:parameters>
                </ae:artifact>
                <ae:test type="[TEST_TYPE]">
                    <ae:parameters>
                        <ae:parameter dt="string" name="check_existence"
                            >[check_existence.value]</ae:parameter>
                        <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
                        <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
                        <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
                        <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
                    </ae:parameters>
                </ae:test>
            </ae:artifact_expression>
        </xccdf:check-content>
    </xccdf:check>
</xccdf:complex-check>
```

#### SCAP
##### XCCDF
For `unix.sshd_v2` artifacts, artifacts, an XCCDF Check element is generated:

```
check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
			<check-content-ref href="[BENCHMARK_NAME]"
				name="oval:org.cisecurity.benchmarks.centos_centos_7:def:[ARTIFACT_OVAL_ID]"/>
</check>
```

##### OVAL
###### Test

```
<sshd_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
			id="oval:org.cisecurity.benchmarks.centos_centos_7:tst:[ARTIFACT_OVAL_ID]"
			check_existence="at_least_one_exists" check="all"
			comment="[RECOMMENDATION_TITLE]"
			version="1">
			<object object_ref="oval:org.cisecurity.benchmarks.centos_centos_7:obj:[ARTIFACT_OVAL_ID]"/>
			<state state_ref="oval:org.cisecurity.benchmarks.centos_centos_7:ste:[ARTIFACT_OVAL_ID]"/>
</sshd_test>
```

###### Object

```
<sshd_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
			id="oval:org.cisecurity.benchmarks.centos_centos_7:obj:[ARTIFACT_OVAL_ID]"
			comment="[RECOMMENDATION_TITLE]"
			version="1">
			<name>Protocol</name>
</sshd_object>
```
###### State

```
<sshd_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
			id="oval:org.cisecurity.benchmarks.centos_centos_7:ste:[ARTIFACT_OVAL_ID]"
			comment="[RECOMMENDATION_TITLE]"
			version="1">
			<value datatype="string" operation="equals">2</value>
</sshd_state>
```

#### YAML

```
- artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: unix.sshd_v2
      parameters:
      - parameter: 
          name: command
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
    "type": "unix_command_output_v1",
    "parameters": [
      {
        "parameter": {
          "name": "command",
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