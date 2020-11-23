# linux.debian_package_v1

## Description
The dpkginfo test is used to check information for a given DPKG package. It extends the standard TestType as defined in the oval-definitions-schema and one should refer to the TestType description for more information. The required object element references a dpkginfo_object and the optional state element specifies the data to check.


## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| name  | String | The name of the package being checked.  |

### Supported Test Types
- existence_test

### Test Type Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| value | String | Regular expression to be matched |


### Generated Content
#### XCCDF+AE
This is what the AE check looks like, inside a Rule, in the XCCDF

```
<xccdf:complex-check operator="AND">
   <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
        <xccdf:check-content>
            <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_9.1.1">
                <ae:artifact_oval_id>[ARTIFACT_OVAL_ID]</ae:artifact_oval_id>
                <ae:title>[RECOMMENDATION_TITLE]</ae:title>
                <ae:artifact type="[ARTIFACT_TYPE]">
                    <ae:parameters>
                        <ae:parameter dt="string" name="name">[name.name]</ae:parameter>
                    </ae:parameters>
                </ae:artifact>
                <ae:test type="[TEST_TYPE]">
                    <ae:parameters>
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
For `linux.debian_package_v1` artifacts, the xccdf:check looks like this.  There is no Value in the xccdf for this Artifact.

```
<check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
            <check-content-ref href="[BENCHMARK_TITLE]"
                name="oval:org.cisecurity.benchmarks.debian_debian_linux_7:def:[ARTIFACT_OVAL_ID]"/>
        </check>
```

##### OVAL
###### Test

```
<dpkginfo_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
			id="oval:org.cisecurity.benchmarks.debian_debian_linux_7:tst:[ARTIFACT_OVAL_ID]"
			check_existence="none_exist" check="all"
			comment="[RECOMMENDATION_TITLE]" version="1">
			<object object_ref="oval:org.cisecurity.benchmarks.debian_debian_linux_7:obj:[ARTIFACT_OVAL_ID]"/>
</dpkginfo_test>
```

###### Object

```
<dpkginfo_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
			id="oval:org.cisecurity.benchmarks.debian_debian_linux_7:obj:[ARTIFACT_OVAL_ID]"
			comment="[RECOMMENDATION_TITLE]" version="1">
			<name>[name.value]</name>
</dpkginfo_object>
```

#### YAML


```
artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: linux.debian_package_v1
      parameters:
      - parameter: 
          name: name
          type: string
          value: [name.value]
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
{
  "artifact-expression": {
    "artifact-unique-id": [
      "ARTIFACT-OVAL-ID"
    ],
    "artifact-title": [
      "RECOMMENDATION TITLE"
    ],
    "artifact": {
      "type": "linux.debian_package_v1",
      "parameters": [
        {
          "parameter": {
            "name": "name",
            "type": "string",
            "value": [
              "name.value"
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
        }
      ]
    }
  }
}
``` 