# linux.upstart_service_v1

## Description
TBD

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| service | String | Add in  |


### Supported Test Types
- unix.service_enabled_v1

### Test Type Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| enabled | String | Is the service enabled |


### Generated Content
#### XCCDF+AE
This is what the AE check looks like, inside a Rule, in the XCCDF

```
<xccdf:complex-check operator="AND">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
        <xccdf:check-content>
            <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_23.1.1">
                <ae:artifact_oval_id>[ARTIFACT_OVAL_ID]</ae:artifact_oval_id>
                <ae:title>[RECOMMENDATION_TITLE]</ae:title>
                <ae:artifact type="[ARTIFACT_TYPE_NAME]">
                    <ae:parameters>
                        <ae:parameter dt="string" name="service">chargen</ae:parameter>
                        <ae:parameter dt="string" name="protocol"/>
                    </ae:parameters>
                </ae:artifact>
                <ae:test type="[TESTTYPE_NAME]">
                    <ae:parameters>
                        <ae:parameter dt="string" name="enabled">[enabled.value]</ae:parameter>
                    </ae:parameters>
                </ae:test>
            </ae:artifact_expression>
        </xccdf:check-content>
    </xccdf:check>
</xccdf:complex-check>
```

#### SCAP
##### XCCDF
For `linux.upstart_service_v1` artifacts, the xccdf:check looks like this.  There is no Value in the xccdf for this Artifact.

```
<check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
			<check-content-ref href="CIS_Debian_Linux_7_Benchmark_v2.0.0.xml-oval.xml"
				name="oval:org.cisecurity.benchmarks.debian_debian_linux_7:def:[ARTIFACT_OVAL_ID]"/>
		</check>
```

##### OVAL
###### Test

```
<shellcommand_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#cmd"
			id="oval:org.cisecurity.benchmarks.debian_debian_linux_7:tst:[ARTIFACT_OVAL_ID]"
			check_existence="at_least_one_exists" check="all"
			comment="[RECOMMENDATION_TITLE]" version="1">
			<object object_ref="oval:org.cisecurity.benchmarks.debian_debian_linux_7:obj:[ARTIFACT_OVAL_ID]"/>
			<state state_ref="oval:org.cisecurity.benchmarks.debian_debian_linux_7:ste:[ARTIFACT_OVAL_ID]"/>
</shellcommand_test>
```

###### Object

```
<shellcommand_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#cmd"
			id="oval:org.cisecurity.benchmarks.debian_debian_linux_7:obj:[ARTIFACT_OVAL_ID]"
			comment="[RECOMMENDATION_TITLE]" version="1">
			<command>[artifactParameter.value]</command>
			<line_selection operation="[testType_name]">[testType_name.value]</line_selection>
</shellcommand_object>
```
###### State

```
<shellcommand_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#cmd"
    id="oval:org.cisecurity.benchmarks.debian_debian_linux_7:ste:[ARTIFACT_OVAL_ID]"
    comment="[RECOMMENDATION_TITLE]" version="1">
    <stdout_line entity_check="at least one" operation="testTypeParameter.name">testtypeParameter.name.value</stdout_line>
</shellcommand_state> 
```

#### YAML


```
artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: linux.upstart_service_v1
      parameters:
      - parameter: 
          name: service
          type: string
          value: [service.value]
      - parameter: 
          name: protocol
          type: string
          value: [protocol.value]
    test:
      type: [TestType Name]
      parameters:
      - parameter:
          name: enabled
          type: string
          value: [enabled.value]
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
      "type": "linux.upstart_service_v1",
      "parameters": [
        {
          "parameter": {
            "name": "service",
            "type": "string",
            "value": [
              "service.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "protocol",
            "type": "string",
            "value": [
              "protocol.value"
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
            "name": "enabled",
            "type": "string",
            "value": [
              "enabled.value"
            ]
          }
        }
      ]
    }
  }
}
```