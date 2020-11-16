# linux.rpm_package_v1

## Description
The rpminfo_test is used to check the RPM header information for a given RPM package. It extends the standard TestType as defined in the oval-definitions-schema and one should refer to the TestType description for more information. The required object element references a rpminfo_object and the optional state element specifies the data to check.


## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| name  | String | The name of the package being checked  |

### Supported Test Types
- existence_test

### Test Type Parameters
####existence_test
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| value | String | the value included within the set of results/ value to be tested |

### Generated Content
#### XCCDF+AE
This is what the AE check looks like, inside a Rule, in the XCCDF

```
<xccdf:complex-check operator="AND">
  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
        <xccdf:check-content>
            <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_12.1.1">
                <ae:artifact_oval_id>[ARTIFACT_OVAL_ID]</ae:artifact_oval_id>
                <ae:title>[RECOMMENDATION_TITLE]</ae:title>
                <ae:artifact type="[ARTIFACT_TYPE]">
                    <ae:parameters>
                        <ae:parameter dt="string" name="name">[name.value]</ae:parameter>
                    </ae:parameters>
                </ae:artifact>
                <ae:test type="[TEST_TYPE]">
                    <ae:parameters>
                        <ae:parameter dt="string" name="value"
                            >[value.value]</ae:parameter>
                    </ae:parameters>
                </ae:test>
            </ae:artifact_expression>
        </xccdf:check-content>
    </xccdf:check>
</xccdf:complex-check>
```

#### SCAP
##### XCCDF
For `linux.rpm_package_v1` artifacts, the xccdf:check looks like this.  There is no Value in the xccdf for this Artifact.

```
	<check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
			<check-content-ref
				href="[BENCHMARK_NAME]"
				name="oval:org.cisecurity.benchmarks.redhat_redhat_enterprise_linux_5:def:[ARTIFACT_OVAL_ID]"/>
		</check>
```

##### OVAL
###### Test

```
<rpminfo_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
			id="oval:org.cisecurity.benchmarks.redhat_redhat_enterprise_linux_5:tst:[ARTIFACT_OVAL_ID]"
			check_existence="at_least_one_exists" check="all"
			comment="[RECOMMENDATION_TITLE]" version="1">
			<object
				object_ref="oval:org.cisecurity.benchmarks.redhat_redhat_enterprise_linux_5:obj:[ARTIFACT_OVAL_ID]"
			/>
</rpminfo_test>
```

###### Object

```
<rpminfo_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
        id="oval:org.cisecurity.benchmarks.redhat_redhat_enterprise_linux_5:obj:[ARTIFACT_OVAL_ID]"
        comment="[RECOMMENDATION_TITLE]" version="1">
        <name>gpg-pubkey</name>
</rpminfo_object>
```

#### YAML


```
- artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: unix.command_output_v1
      parameters:
      - parameter: 
          name: loadable
          type: string
          value: [ARTIFACT TYPE PARAMETER VALUE]
    test:
      type: [TestType Name]
      parameters:
      - parameter:
          name: loaded
          type: string
          value: [TestType.value.value]
```

#### JSON

```
"artifact-expression": {
  "artifact-unique-id": [ARTIFACT-OVAL-ID],
  "artifact-title": [RECOMMENDATION TITLE],
  "artifact": {
    "type": "linux.rpm_package_v1",
    "parameters": [
      {
        "parameter": {
          "name": "loadable",
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
          "name": "loaded",
          "type": "string",
          "value": [TestType.value.value]
        }
      }
    ]
  }
}
``` 