# sce_check_v1

## Description

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| script  | String | The SCE script to run  |
| export_variable_value |string |TBD	|
| export_variable_type|string | TBD |
| export_variable_value | string | TBD |

### Supported Test Types
- null_test_v1

### Generated Content
#### XCCDF+AE
This is what the AE check looks like, inside a Rule, in the XCCDF

```
<xccdf:complex-check operator="AND">
   <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
        <xccdf:check-content>
            <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_1.1.20.1">
                <ae:artifact_oval_id>[ARTIFACT_OVAL_ID]</ae:artifact_oval_id>
                <ae:title>[RECOMMENDATION_TITLE]</ae:title>
                <ae:artifact type="[ARTIFACT_TYPE]">
                    <ae:parameters>
                        <ae:parameter dt="string" name="script"
                            >[script.value]</ae:parameter>
                        <ae:parameter dt="string" name="export_variable_value"
                            >[export_variable_value.value]</ae:parameter>
                            <ae:parameter dt="string" name="export_variable_type"
                            >[export_variable_type.value]</ae:parameter>
                         <ae:parameter dt="string" name="export_variable_name"
                            >[export_variable_name.value]</ae:parameter>
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
For `linux.sce_check_v1` artifacts, an XCCDF Value element is generated:


```
<Value id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT_OVAL_ID]_var" type="string"
				operator="not equal">
				<title>[RECOMMENDATION_TITLE]</title>
				<description>This value is used in Rule: [RECOMMENDATION_TITLE]</description>
				<value>enabled</value>
			</Value>
```


##### OVAL 
There are no tests, objects or states generated.

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
    "type": "sce_check_v1
",
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