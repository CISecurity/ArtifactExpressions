# linux.audit_rule_v1

## Description
The textfilecontent54_test element is used to check the contents of a text file (aka a configuration file) by looking at individual blocks of text. It extends the standard TestType as defined in the oval-definitions-schema and one should refer to the TestType description for more information. The required object element references a textfilecontent54_object and the optional state element specifies the metadata to check. The evaluation of the test is guided by the check attribute that is inherited from the TestType.

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| check_existence | String | 	Typically set to 'at least one'.  |

check_existence
NOTE: This parameter is governed by a constraint allowing only the following values:
- all_exist
- any_exist
- at_least_one_exists
- none_satisfy
- none_exist
- only_one_exists

### Supported Test Types
- set.includes_v1

### Test Type Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| value | String | Regular expression to be matched |
| data_type | String | datatype |

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
            <ae:artifact_expression
                id="xccdf_org.cisecurity.benchmarks_ae_16.1.1">
                <ae:artifact_oval_id>[ARTIFACT_OVAL_ID]</ae:artifact_oval_id>
                <ae:title>[RECOMMENDATION_TITLE]</ae:title>
                <ae:artifact type="[ARTIFACT_TYPE]">
                    <ae:parameters>
                        <ae:parameter dt="string" name="check_existence"
                            >[check_existence.value]</ae:parameter>
                    </ae:parameters>
                </ae:artifact>
                <ae:test type="[TEST_TYPE]">
                    <ae:parameters>
                        <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
                        <ae:parameter dt="string" name="data_type"
                            >[data_type.value]</ae:parameter>
                    </ae:parameters>
                </ae:test>
            </ae:artifact_expression>
        </xccdf:check-content>
    </xccdf:check>
</xccdf:complex-check>
```

#### SCAP
##### XCCDF
For ` linux.auditd_rule_v1` artifacts, the xccdf:check looks like this.  There is no Value in the xccdf for this Artifact.

```
<check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
			<check-content-ref
				href="[BENCHMARK_TITLE]"
				name="oval:org.cisecurity.benchmarks.suse_suse_linux_enterprise_server_12:def:[ARTIFACT_OVAL_ID]"
			/>
		</check>
```

##### OVAL
###### Test

```
<textfilecontent54_test
			xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
			id="oval:org.cisecurity.benchmarks.suse_suse_linux_enterprise_server_12:tst:[ARTIFACT_OVAL_ID]"
			check_existence="at_least_one_exists" check="all"
			comment="[RECOMMENDATION_TITLE]"
			version="1">
			<object
				object_ref="oval:org.cisecurity.benchmarks.suse_suse_linux_enterprise_server_12:obj:[ARTIFACT_OVAL_ID]"
			/>
</textfilecontent54_test>
```

###### Object

```
<textfilecontent54_object
        xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
        id="oval:org.cisecurity.benchmarks.suse_suse_linux_enterprise_server_12:obj:[ARTIFACT_OVAL_ID]"
        comment="[RECOMMENDATION_TITLE]"
        version="1">
        <path>[path.value]</path>
        <filename>[filename.value]</filename>
        <pattern operation="pattern match" datatype="string"
            >[pattern.value]</pattern>
        <instance datatype="int" operation="equals">[datatype.value.value]</instance>
</textfilecontent54_object>
```

#### YAML


```
artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: unix.auditd_rule_v1
      parameters:
      - parameter: 
          name: check_existence
          type: string
          value: [check_existence.value]
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
  {
    "artifact-expression": {
      "artifact-unique-id": [
        "ARTIFACT-OVAL-ID"
      ],
      "artifact-title": [
        "RECOMMENDATION TITLE"
      ],
      "artifact": {
        "type": "linux.auditd_rule_v1",
        "parameters": [
          {
            "parameter": {
              "name": "check_existence",
              "type": "string",
              "value": [
                "check_existence.value"
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
                "TestType.value.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "data_type",
              "type": "string",
              "value": [
                "TestType.data_type.value"
              ]
            }
          }
        ]
      }
    }
  }

``` 