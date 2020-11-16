# unix.individual_file_v1

## Description
TBD

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| existence | String | existence requirement |
| filepath | String | path to the file  |
| check | string | check |

existence NOTE: This parameter is governed by a constraint allowing only the following values:
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
- pattern match
- unix_file_attributes_v1
- pattern not match
- null_test_v1

### Test Type Parameters
####pattern match, pattern not match
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| data_type | String | datatype |
| value | String | Regular expression to be matched  |

data_type
NOTE: This parameter is governed by a constraint allowing only the following values:
- boolean
- float
- int
- string
- version
- set

#### unix_file_attributes_v1
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| uread | String | Can the owner read the file |
| uwrite | String | Can the owner write the file |
| uexec | String | Can the owner execute the file |
| gread | String | Can the group read the file |
| gwrite | String | Can the group write the file |
| gexec | String | Can the group execute the file |
| oread | String | Can the world read the file |
| owrite | String | Can the world write the file |
| oexec | String | Can the world execute the file |
| suid | String | Can the file execute as the owner |
| sgid | String | Can the file execute as the group|
| sticky | String | Is the sticky bit set |
| uid | int | Owner UID (empty to ignore) |
| gid | int | owner GID (empty to ignore) | 


### Generated Content
#### XCCDF+AE
This is what the AE check looks like, inside a Rule, in the XCCDF

```
<xccdf:complex-check operator="AND">
<xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
        <xccdf:check-content>
            <ae:artifact_expression
                id="xccdf_org.cisecurity.benchmarks_ae_1.3.2.2">
                <ae:artifact_oval_id>[ARTIFACT_OVAL_ID]</ae:artifact_oval_id>
                <ae:title>[RECOMMENDATION_TITLE]</ae:title>
                <ae:artifact type="[ARTIFACT_TYPE]">
                    <ae:parameters>
                        <ae:parameter dt="string" name="filepath"
                            >[filepath.value]</ae:parameter>
                        <ae:parameter dt="string" name="existence"
                            >[existence.value]</ae:parameter>
                        <ae:parameter dt="string" name="check">
                            [check.value]</ae:parameter>
                    </ae:parameters>
                </ae:artifact>
                <ae:test type="[TEST_TYPE]">
                    <ae:parameters/>
                </ae:test>
            </ae:artifact_expression>
        </xccdf:check-content>
    </xccdf:check>
</xccdf:complex-check>
```

#### SCAP
##### XCCDF
For `unix.individual_file_v1` artifacts, an XCCDF check element is generated, an xccdf value is not generated.

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
			id="oval:org.cisecurity.benchmarks.centos_centos_7:tst:[ARTIFACT_OVAL_ID]"
			check_existence="at_least_one_exists" check="all"
			comment="[RECOMMENDATION_TITLE]"
			version="1">
			<object object_ref="oval:org.cisecurity.benchmarks.centos_centos_7:obj:[ARTIFACT_OVAL_ID]"/>
		</textfilecontent54_test>
```

###### Object

```
<textfilecontent54_object
			xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
			id="oval:org.cisecurity.benchmarks.centos_centos_7:obj:[ARTIFACT_OVAL_ID]"
			comment="[RECOMMENDATION_TITLE]"
			version="1">
			<filepath>/var/spool/cron/root</filepath>
			<pattern operation="pattern match" datatype="string"
				>^\S+\s+\S+\s+\S+\s+\S+\s+\S+\s+/usr/sbin/aide --check</pattern>
			<instance datatype="int" operation="equals">1</instance>
</textfilecontent54_object>
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
- artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: unix.individual_file_v1
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