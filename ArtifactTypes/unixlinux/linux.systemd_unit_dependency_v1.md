# linux.systemd_unit_dependency_v1

## Description
The systemdunitdependency_test is used to retrieve information about dependencies of a single systemd unit in the form of a list. This list contains all dependencies, including transitive dependencies. For more information see the output generated by systemctl list-dependencies --plain $unit. It extends the standard TestType as defined in the oval-definitions-schema and one should refer to the TestType description for more information. The required object element references a systemdunitdependency_object and the optional state element specifies the data to check.


## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| unit | String | The full systemd unit name which is usually also the filename of the unit configuration file located in the /etc/systemd/ and /usr/lib/systemd/ directories.	  |
|operation |string | Determines how the unit name should be evaluated (the default operation is 'equals').	|

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
### Supported Test Types
- linux.systemd_unit_dependency_v1 

### Test Type Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| unit | String | The full systemd unit name which is usually also the filename of the unit configuration file located in the /etc/systemd/ and /usr/lib/systemd/ directories |
| unit_operation | String | Determines how the unit name should be evaluated (the default operation is 'equals').	 |
| dependency | String | The name of a unit which is to be confirmed as a dependency of the given unit.	 |
| dependency_operation | String | Determines how the dependency name should be evaluated (the default operation is 'equals').	 |

unit_operation/dependency_operation
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
            <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_23.1.1">
                <ae:artifact_oval_id>[ARTIFACT_OVAL_ID]</ae:artifact_oval_id>
                <ae:title>[RECOMMENDATION_TITLE]</ae:title>
                <ae:artifact type="[ARTIFACT_TYPE]">
                    <ae:parameters>
                        <ae:parameter dt="string" name="unit">[unit.value]</ae:parameter>
                        <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
                    </ae:parameters>
                </ae:artifact>
                <ae:test type="[TEST_TYPE]">
                    <ae:parameters>
                        <ae:parameter dt="string" name="unit"
                            >[unit.value]</ae:parameter>
                        <ae:parameter dt="string" name="unit_operation"
                            >[unit_operation.value]</ae:parameter>
                        <ae:parameter dt="string" name="dependency"
                            >[dependency.value]</ae:parameter>
                        <ae:parameter dt="string" name="dependency_operation">[dependency_operation.value]
                            </ae:parameter>
                    </ae:parameters>
                </ae:test>
            </ae:artifact_expression>
        </xccdf:check-content>
    </xccdf:check>
</xccdf:complex-check>
```

#### SCAP
##### XCCDF
For ` linux.systemd_unit_property_v1` artifacts, the xccdf:check looks like this.  There is no Value in the xccdf for this Artifact.

```
<check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
			<check-content-ref href="[BENCHMARK_NAME]"
				name="oval:org.cisecurity.benchmarks.postgresql_postgresql_11:def:[ARTIFACT_OVAL_ID]"/>
		</check>
```

##### OVAL
###### Test

```
<systemdunitdependency_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
			id="oval:org.cisecurity.benchmarks.postgresql_postgresql_11:tst:[ARTIFACT_OVAL_ID]"
			check_existence="any_exist" check="all"
			comment="[RECOMMENDATION_TITLE]" version="1">
			<object object_ref="oval:org.cisecurity.benchmarks.postgresql_postgresql_11:obj:[ARTIFACT_OVAL_ID]"/>
			<state state_ref="oval:org.cisecurity.benchmarks.postgresql_postgresql_11:ste:[ARTIFACT_OVAL_ID]"/>
		</systemdunitdependency_test>
```

###### Object

```
<systemdunitdependency_object
			xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
			id="oval:org.cisecurity.benchmarks.postgresql_postgresql_11:obj:[ARTIFACT_OVAL_ID]"
			comment="[RECOMMENDATION_TITLE]" version="1">
			<unit operation="equals">default.target</unit>
		</systemdunitdependency_object>
```
###### State

```
<systemdunitdependency_state
			xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
			id="oval:org.cisecurity.benchmarks.postgresql_postgresql_11:ste:[ARTIFACT_OVAL_ID]"
			comment="[RECOMMENDATION_TITLE]" version="1">
			<dependency entity_check="at least one" operation="pattern match"
				>^postgres.+$</dependency>
		</systemdunitdependency_state>
```

#### YAML


```
artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: linux.systemd_unit_dependency_v1
      parameters:
      - parameter: 
          name: unit
          type: string
          value: [unit.value]
      - parameter: 
          name: operation
          type: string
          value: [operation.value]
    test:
      type: [TestType Name]
      parameters:
      - parameter:
          name: dependency_operation
          type: string
          value: [dependency_operation.value]
      - parameter:
          name: unit
          type: string
          value: [unit.value]
      - parameter:
          name: unit_operation
          type: string
          value: [unit_operation.value]
      - parameter:
          name: dependency
          type: string
          value: [dependency.value]
                             
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
      "type": "linux.systemd_unit_dependency_v1",
      "parameters": [
        {
          "parameter": {
            "name": "unit",
            "type": "string",
            "value": [
              "unit.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "operation",
            "type": "string",
            "value": [
              "operation.value"
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
            "name": "dependency_operation",
            "type": "string",
            "value": [
              "dependency_operation.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "unit",
            "type": "string",
            "value": [
              "unit.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "unit_operation",
            "type": "string",
            "value": [
              "unit_operation.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "dependency",
            "type": "string",
            "value": [
              "dependency.value"
            ]
          }
        }
      ]
    }
  }
}
``` 