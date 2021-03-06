# linux.partition_options_v1

## Description
The partition_test is used to check the information associated with partitions on the local system. It extends the standard TestType as defined in the oval-definitions-schema and one should refer to the TestType description for more information. The required object element references a partition_object and the optional state element references a partition_state that specifies the information to check.


## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
|mount_point  | String | Filesystem mount point being tested  |

### Supported Test Types
- set.includes_v1

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
            <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_11.1.1">
                <ae:artifact_oval_id>[ARTIFACT_OVAL_ID]</ae:artifact_oval_id>
                <ae:title>[RECOMMENDATION_TITLE]</ae:title>
                <ae:artifact type="[ARTIFACT_TYPE]">
                    <ae:parameters>
                        <ae:parameter dt="string" name="mount_point">[mount_point.value]</ae:parameter>
                    </ae:parameters>
                </ae:artifact>
                <ae:test type="[TEST_TYPE]">
                    <ae:parameters>
                        <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
                        <ae:parameter dt="string" name="data_type">[data_type.value]</ae:parameter>
                    </ae:parameters>
                </ae:test>
                <ae:profiles/>
            </ae:artifact_expression>
        </xccdf:check-content>
    </xccdf:check>
</xccdf:complex-check>
```

#### SCAP
##### XCCDF
For `linux.partition_options_v1` artifacts, the xccdf:check looks like this.  There is no Value in the xccdf for this Artifact.

```
<check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
			<check-content-ref
				href="[BENCHMARK_TITLE]"
				name="oval:org.cisecurity.benchmarks.redhat_redhat_enterprise_linux_5:def:[ARTIFACT_OVAL_ID]"/>
</check>
```

##### OVAL
###### Test

```
<partition_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
			id="oval:org.cisecurity.benchmarks.redhat_redhat_enterprise_linux_5:tst:[ARTIFACT_OVAL_ID]"
			check_existence="at_least_one_exists" check="all"
			comment="[RECOMMENDATION_TITLE]" version="1">
			<object
				object_ref="oval:org.cisecurity.benchmarks.redhat_redhat_enterprise_linux_5:obj:[ARTIFACT_OVAL_ID]"/>
			<state
				state_ref="oval:org.cisecurity.benchmarks.redhat_redhat_enterprise_linux_5:ste:[ARTIFACT_OVAL_ID]"
			/>
</partition_test>
```

###### Object

```
<partition_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
			id="oval:org.cisecurity.benchmarks.redhat_redhat_enterprise_linux_5:obj:[ARTIFACT_OVAL_ID]"
			comment="[RECOMMENDATION_TITLE]" version="1">
			<mount_point>[mount_point.value]</mount_point>
</partition_object>
```
###### State

```
<partition_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
			id="oval:org.cisecurity.benchmarks.redhat_redhat_enterprise_linux_5:ste:[ARTIFACT_OVAL_ID]"
			comment="[RECOMMENDATION_TITLE]" version="1">
			<mount_options entity_check="at least one" operation="equals" datatype="string"
				>nodev</mount_options>
</partition_state>
```

#### YAML


```
artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: linux.partition_options_v1
      parameters:
      - parameter: 
          name: mount_point
          type: string
          value: [mount_point.value]
    test:
      type: [TestType Name]
      parameters:
      - parameter:
          name: value
          type: string
          value: [value.value]
      - parameter:
          name: data_type
          type: string
          value: [data_type.value]
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
      "type": "linux.partition_options_v1",
      "parameters": [
        {
          "parameter": {
            "name": "mount_point",
            "type": "string",
            "value": [
              "mount_point.value"
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
            "name": "data_type",
            "type": "string",
            "value": [
              "data_type.value"
            ]
          }
        }
      ]
    }
  }
}
``` 