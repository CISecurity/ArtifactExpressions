# unix.xinetd_service_v1

## Description
The xinetd test is used to check information associated with different Internet services. It extends the standard TestType as defined in the oval-definitions-schema and one should refer to the TestType description for more information. The required object element references an inetd_object and the optional state element specifies the information to check.
## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| service_name  | String | The name of the service that is enabled  |
| protocol | String | Protocol the service is on (tcp/udp) | 

### Supported Test Types
- unix.service_enabled_v1
- unix.xinetd_service_enabled_v1

### Test Type Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| enabled | String | Is the service enabled. |

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
                        <ae:parameter dt="string" name="service_name">[service_name.value]</ae:parameter>
                        <ae:parameter dt="string" name="protocol">[protocol.value]</ae:parameter>
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
For `linux.xinetd_service_v1` artifacts, the xccdf:check looks like this.  There is no Value in the xccdf for this Artifact.

```
	<check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
			<check-content-ref
				href="[BENCHMARK_NAME]"
				name="oval:org.cisecurity.benchmarks:def:[ARTIFACT_OVAL_ID]"/>
		</check>
```

##### OVAL
###### Test

```
<xinetd_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
			id="oval:org.cisecurity.benchmarks:tst:[ARTIFACT_OVAL_ID]" check_existence="any_exist" check="all"
			comment="[RECOMMENDATION_TITLE]" version="1">
			<object object_ref="oval:org.cisecurity.benchmarks:obj:[ARTIFACT_OVAL_ID]"/>
			<state state_ref="oval:org.cisecurity.benchmarks:ste:[ARTIFACT_OVAL_ID]"/>
		</xinetd_test>
```

###### Object

```
<xinetd_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
			id="oval:org.cisecurity.benchmarks:obj:[ARTIFACT_OVAL_ID]"
			comment="[RECOMMENDATION_TITLE]" version="1">
			<protocol/>
			<service_name>chargen-dgram</service_name>
</xinetd_object>
```

###### State

```
<xinetd_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
			id="oval:org.cisecurity.benchmarks:ste:[ARTIFACT_OVAL_ID]"
			comment="[RECOMMENDATION_TITLE]" version="1">
			<disabled datatype="boolean" operation="equals">true</disabled>
</xinetd_state>
```

#### YAML


```
artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: unix.uname_parameter_v1
      parameters:
      - parameter: 
          name: service_name
          type: string
          value: [service_name.value]
      - parameter: 
          name: protocol
          type: string
          value: [protocol.value]
    test:
      type: [testType name]
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
      "type": "unix.uname_parameter_v1",
      "parameters": [
        {
          "parameter": {
            "name": "service_name",
            "type": "string",
            "value": [
              "service_name.value"
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
        "testType name"
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