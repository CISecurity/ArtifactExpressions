# linux.partition_v1

## Description
The partition_test is used to check the information associated with partitions on the local system. It extends the standard TestType as defined in the oval-definitions-schema and one should refer to the TestType description for more information. The required object element references a partition_object and the optional state element references a partition_state that specifies the information to check.


## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
|mount_point  | String | Filesystem mount point being tested  |
| existence | String | Specifies how many items in the set must exist for the test to evaluate to true.	| 
| check | String | Defines how many items must evaluate to true for the entity to return true.	|

existence 
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
### Supported Test Types
- null_test_v1
- linux.partition_option_v1

### Test Type Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| value | String | Regular expression to be matched |
| data_type | String | datatype |
| check | String  | Add in | 
| operation | String | Add in | 

data_type
NOTE: This parameter is governed by a constraint allowing only the following values:
- boolean
- float
- int
- string
- version
- set

check
NOTE: This parameter is governed by a constraint allowing only the following values:
- all
- at least one 
- none satisfy
- only one 

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


### Generated Content
#### XCCDF+AE
This is what the AE check looks like, inside a Rule, in the XCCDF

```
<xccdf:complex-check operator="AND">
   <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
        <xccdf:check-content>
            <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_1.1.3.1">
                <ae:artifact_oval_id>[ARTIFACT_OVAL_ID]</ae:artifact_oval_id>
                <ae:title>[RECOMMENDATION_TITLE]</ae:title>
                <ae:artifact type="[ARTIFACTTYPE">
                    <ae:parameters>
                        <ae:parameter dt="string" name="existence"
                            >[existence_value]</ae:parameter>
                        <ae:parameter dt="set" name="check">[check.value]</ae:parameter>
                        <ae:parameter dt="string" name="mount_point"
                            >[mount_point.value]</ae:parameter>
                    </ae:parameters>
                </ae:artifact>
                <ae:test type="[TESTTYPE]">
                    <ae:parameters>
                        <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
                        <ae:parameter dt="set" name="operation"
                            >[operation.value]</ae:parameter>
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
For `linux.partition_v1` artifacts, the xccdf:check looks like this.  There is no Value in the xccdf for this Artifact.

```
<check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
			<check-content-ref href="[BENCHMARK_NAME]"
				name="oval:org.cisecurity.benchmarks.centos_centos_7:def:[ARTIFACT_OVAL_ID]"/>
		</check>
```

##### OVAL
###### Test

```
<partition_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
  			id="oval:org.cisecurity.benchmarks.centos_centos_7:tst:[ARTIFACT_OVAL_ID]"
  			check_existence="at_least_one_exists" check="all"
  			comment="[RECOMMENDATION_TITLE]" version="1">
  			<object object_ref="oval:org.cisecurity.benchmarks.centos_centos_7:obj:[ARTIFACT_OVAL_ID]"/>
</partition_test>
```

###### Object

```
<partition_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
			id="oval:org.cisecurity.benchmarks.centos_centos_7:obj:[ARTIFACT_OVAL_ID]"
			comment="[RECOMMENDATION_TITLE]" version="1">
			<mount_point>/home</mount_point>
</partition_object>
```

#### YAML


```
artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: linux.partition_v1
      parameters:
      - parameter: 
          name: existence
          type: string
          value: [existence.value]
      - parameter: 
          name: check
          type: set
          value: [check.value]
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
      - parameter:
          name: operation
          type: set
          value: [operation.value]
      - parameter:
          name: check
          type: string
          value: [check.value]
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
      "type": "linux.partition_v1",
      "parameters": [
        {
          "parameter": {
            "name": "existence",
            "type": "string",
            "value": [
              "existence.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "check",
            "type": "set",
            "value": [
              "check.value"
            ]
          }
        },
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
        },
        {
          "parameter": {
            "name": "operation",
            "type": "set",
            "value": [
              "operation.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "check",
            "type": "string",
            "value": [
              "check.value"
            ]
          }
        }
      ]
    }
  }
}
``` 