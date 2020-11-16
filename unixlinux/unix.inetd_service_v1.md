# unix.inetd_service_v1

## Description
TBD

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| service | String | service name |
| protocol | String | leave blank for any  |

### Supported Test Types
- unix.service_enabled_v1

### Test Type Parameters
####pattern match, pattern not match
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| enabled | String | is the service enabled |

### Generated Content
#### XCCDF+AE
This is what the AE check looks like, inside a Rule, in the XCCDF

```
<xccdf:complex-check operator="AND">
<xccdf:check-content>
            <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_2.1.2.1">
                <ae:artifact_oval_id>[ARTIFACT_OVAL_ID]</ae:artifact_oval_id>
                <ae:title>[RECOMMENDATION_TITLE]</ae:title>
                <ae:artifact type="[ARTIFACT_TYPE]">
                    <ae:parameters>
                        <ae:parameter dt="string" name="service"
                            >[service.value]</ae:parameter>
                        <ae:parameter dt="string" name="protocol">[protocol.value]</ae:parameter>
                    </ae:parameters>
                </ae:artifact>
                <ae:test type="[TEST_TYPE]">
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
For `unix.inetd_service_v1` artifacts, an XCCDF check element is generated:

```
<check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
			<check-content-ref href="[BENCHMARK_NAME]"
				name="oval:org.cisecurity.benchmarks.centos_centos_7:def:[ARTIFACT_OVAL_ID]"/>
</check>
```

##### OVAL
###### Test

```
<textfilecontent54_test
			xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
			id="oval:org.cisecurity.benchmarks.centos_centos_7:tst:[ARTIFACT_OVAL_ID]2"
			check_existence="none_exist" check="all"
			comment="[RECOMMENDATION_TITLE]" version="1">
			<object object_ref="oval:org.cisecurity.benchmarks.centos_centos_7:obj:[ARTIFACT_OVAL_ID]2"/>
		</textfilecontent54_test>
		<textfilecontent54_test
			xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
			id="oval:org.cisecurity.benchmarks.centos_centos_7:tst:[ARTIFACT_OVAL_ID]3"
			check_existence="none_exist" check="all"
			comment="[RECOMMENDATION_TITLE]" version="1">
			<object object_ref="oval:org.cisecurity.benchmarks.centos_centos_7:obj:[ARTIFACT_OVAL_ID]3"/>
		</textfilecontent54_test>
```

###### Object

```
<xinetd_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
			id="oval:org.cisecurity.benchmarks.centos_centos_7:obj:[ARTIFACT_OVAL_ID]1"
			comment="[RECOMMENDATION_TITLE]" version="1">
			<protocol operation="pattern match">.*</protocol>
			<service_name>chargen</service_name>
		</xinetd_object>
		<textfilecontent54_object
			xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
			id="oval:org.cisecurity.benchmarks.centos_centos_7:obj:[ARTIFACT_OVAL_ID]2"
			comment="[RECOMMENDATION_TITLE]" version="1">
			<filepath>/etc/inetd.conf</filepath>
			<pattern operation="pattern match" datatype="string">^chargen\s+</pattern>
			<instance datatype="int" operation="equals">1</instance>
		</textfilecontent54_object>
		<textfilecontent54_object
			xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
			id="oval:org.cisecurity.benchmarks.centos_centos_7:obj:[ARTIFACT_OVAL_ID]3"
			comment="[RECOMMENDATION_TITLE]" version="1">
			<path>/etc/inetd.d</path>
			<filename operation="pattern match">.+</filename>
			<pattern operation="pattern match" datatype="string">^chargen\s+</pattern>
			<instance datatype="int" operation="equals">1</instance>
		</textfilecontent54_object>
```
###### State

```
<xinetd_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
			id="oval:org.cisecurity.benchmarks.centos_centos_7:ste:[ARTIFACT_OVAL_ID]1"
			comment="[RECOMMENDATION_TITLE]" version="1">
			<disabled datatype="boolean" operation="equals">true</disabled>
		</xinetd_state>
```

#### YAML

```
- artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: unix.inetd_service_v1
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