# unix.process58_v2

## Description
The process58_test is used to check information found in the UNIX processes. It is equivalent to parsing the output of the ps command. It extends the standard TestType as defined in the oval-definitions-schema and one should refer to the TestType description for more information. The required object element references a process58_object and the optional state element references a process58_state that specifies the process information to check.

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| command_line | String | The command entity is the string used to start the process. This includes any parameters that are part of the command line.	 |
| pid | String |The pid entity is the process ID of the process.	 |
| command_line_operation | String |  Specifies what operation is to be performed using the Command value.	|
| pid_operation | String | Specifies what operation is to be performed using the Process ID value.	|

### Supported Test Types
- unix.process58_command_line_v1

### Test Type Parameters

| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| check_existence | String |Defines how many items should be collected		 |
| check | String |Defines how many collected items must match the expected state		 |
| operation | String | comparison operation	|
| data_type | String | datatype	|
| command_line | String | This is the string used to start the process. This includes any parameters that are part of the command line.	 |


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


check_existence NOTE: This parameter is governed by a constraint allowing only the following values:
- all_exist
- any_exist
- at_least_one_exists
- none_satisfy
- none_exist
- only_one_exists

### Generated Content
#### XCCDF+AE
This is what the AE check looks like, inside a Rule, in the XCCDF

```
<xccdf:complex-check operator="AND">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
        <xccdf:check-content>
            <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_6.3.3.2">
                <ae:artifact_oval_id>[ARTIFACT_OVAL_ID]</ae:artifact_oval_id>
                <ae:title>[RECOMMENDATION_TITLE]</ae:title>
                <ae:artifact type="[ARTIFACT_TYPE]">
                    <ae:parameters>
                        <ae:parameter dt="string" name="command_line"
                            >[command_line.value]</ae:parameter>
                        <ae:parameter dt="string" name="command_line_operation"
                            >[command_line_operation.value]</ae:parameter>
                        <ae:parameter dt="integer" name="pid">[pid.value]</ae:parameter>
                        <ae:parameter dt="string" name="pid_operation">[pid_operation.value]
                            </ae:parameter>
                    </ae:parameters>
                </ae:artifact>
                <ae:test type="[TEST_TYPE]">
                    <ae:parameters>
                        <ae:parameter dt="string" name="check_existence"
                            >[check_existence.value]</ae:parameter>
                        <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
                        <ae:parameter dt="string" name="operation">
                            [operation.value]</ae:parameter>
                        <ae:parameter dt="string" name="datatype"
                            >[datatype.value]</ae:parameter>
                        <ae:parameter dt="string" name="command_line"
                            >[command_line.value]</ae:parameter>
                    </ae:parameters>
                </ae:test>
            </ae:artifact_expression>
        </xccdf:check-content>
    </xccdf:check>
</xccdf:complex-check>
```

#### SCAP
##### XCCDF
For `unix.process58_v2` artifacts, an XCCDF check element is generated:

```
<check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
        <check-content-ref href="{BENCHMARK_NAME]"
            name="oval:org.cisecurity.benchmarks.Kubernetes_Kubernetes_1:def:[ARTIFACT_OVAL_ID]"/>
</check>
```

##### OVAL
###### Test

```
<process58_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.Kubernetes_Kubernetes_1:tst:[ARTIFACT_OVAL_ID]"
    check_existence="all_exist" check="none satisfy"
    comment="[RECOMMENDATION_TITLE]" version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.Kubernetes_Kubernetes_1:obj:[ARTIFACT_OVAL_ID]"/>
    <state state_ref="oval:org.cisecurity.benchmarks.Kubernetes_Kubernetes_1:ste:[ARTIFACT_OVAL_ID]"/>
</process58_test>
```

###### Object

```
<process58_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.Kubernetes_Kubernetes_1:obj:[ARTIFACT_OVAL_ID]"
    comment="[RECOMMENDATION_TITLE]" version="1">
    <command_line operation="pattern match">kube-apiserver</command_line>
    <pid datatype="int" operation="greater than">0</pid>
</process58_object>
```
###### State

```
<process58_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
        id="oval:org.cisecurity.benchmarks.Kubernetes_Kubernetes_1:ste:[ARTIFACT_OVAL_ID]"
        comment="[RECOMMENDATION_TITLE]" version="1">
        <command_line operation="pattern match" datatype="string"
            >--basic-auth-file</command_line>
</process58_state>
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
artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: unix.process58_v2
      parameters:
      - parameter: 
          name: command_line
          type: string
          value: [command_line.value]
      - parameter: 
          name: pid
          type: string
          value: [pid.value]
      - parameter: 
          name: command_line_operation
          type: string
          value: [command_line_operation.value]
      - parameter: 
          name: pid_operation
          type: string
          value: [pid_operation.value]
    test:
      type: [testType name]
      parameters:
      - parameter: 
          name: check_existence
          type: string
          value: [check_existence.value]
      - parameter: 
          name: check
          type: string
          value: [check.value]
      - parameter: 
          name: operation
          type: string
          value: [operation.value]
      - parameter: 
          name: data_type
          type: string
          value: [data_type.value]
      - parameter: 
          name: command_line
          type: string
          value: [command_line.value]
     
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
      "type": "unix.process58_v2",
      "parameters": [
        {
          "parameter": {
            "name": "command_line",
            "type": "string",
            "value": [
              "command_line.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "pid",
            "type": "string",
            "value": [
              "pid.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "command_line_operation",
            "type": "string",
            "value": [
              "command_line_operation.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "pid_operation",
            "type": "string",
            "value": [
              "pid_operation.value"
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
            "name": "check_existence",
            "type": "string",
            "value": [
              "check_existence.value"
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
        },
        {
          "parameter": {
            "name": "operation",
            "type": "string",
            "value": [
              "operation.value"
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
            "name": "command_line",
            "type": "string",
            "value": [
              "command_line.value"
            ]
          }
        }
      ]
    }
  }
}
```