# unix.sshd_parameter_v1

## Description
The textfilecontent54_test element is used to check the contents of a text file (aka a configuration file) by looking at individual blocks of text. It extends the standard TestType as defined in the oval-definitions-schema and one should refer to the TestType description for more information. The required object element references a textfilecontent54_object and the optional state element specifies the metadata to check. The evaluation of the test is guided by the check attribute that is inherited from the TestType.

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| parameter | String | parameter to check |


### Supported Test Types
- equals
- not equal
- less than
- less than or equal
- greater than
- greater than or equal
- pattern match
- pattern not match
- existence_test

### Test Type Parameters

| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| value | String |Regular expression to be matched/ value to be tested			 |
| data_type | String |datatype	 |

data_type
NOTE: This parameter is governed by a constraint allowing only the following values:
- boolean
- float
- int
- string
- version
- set

existence_test
NOTE: This parameter is governed by a constraint allowing only the following values:
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
            <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_5.2.2.1">
                <ae:artifact_oval_id>[ARTIFACT_OVAL_ID]</ae:artifact_oval_id>
                <ae:title>[RECOMMENDATION_TTILE]</ae:title>
                <ae:artifact type="[ARTIFACT_TYPE]">
                    <ae:parameters>
                        <ae:parameter dt="string" name="parameter"
                            >[parameter.value]</ae:parameter>
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
For `unix.sshd_parameter_v1` artifacts, artifacts, an XCCDF Value element is generated:

```
<Values>
<Value id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT_OVAL_ID]_var" type="string"
    operator="equals">
    <title>Ensure SSH Protocol is set to 2</title>
    <description>This value is used in Rule: Ensure SSH Protocol is set to
        2</description>
    <value>2</value>
</Value>
</Values>
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
    <state state_ref="oval:org.cisecurity.benchmarks.centos_centos_7:ste:[ARTIFACT_OVAL_ID]"/>
</textfilecontent54_test>
```

###### Object

```<textfilecontent54_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks.centos_centos_7:obj:[ARTIFACT_OVAL_ID]"
    comment="[RECOMMENDATION_TITLE]"
    version="1">
    <filepath>/etc/ssh/sshd_config</filepath>
    <pattern operation="pattern match">^\s*Protocol\s+(\S+)\s*(?:#.*)?$</pattern>
    <instance datatype="int" operation="equals">1</instance>
</textfilecontent54_object>
```
###### State

```
<textfilecontent54_state
			xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
			id="oval:org.cisecurity.benchmarks.centos_centos_7:ste:[ARTIFACT_OVAL_ID]"
			comment="[RECOMMENDATION_TITLE]"
			version="1">
			<subexpression datatype="string" operation="equals"
				var_ref="oval:org.cisecurity.benchmarks.centos_centos_7:var:[ARTIFACT_OVAL_ID]"/>
</textfilecontent54_state>
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
      type: unix.sshd_parameter_v1
      parameters:
      - parameter:
          name: parameter
          type: string
          value: [parameter.value]
    test:
      type: [testType name]
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
      "type": "unix.sshd_parameter_v1",
      "parameters": [
        {
          "parameter": {
            "name": "parameter",
            "type": "string",
            "value": [
              "parameter.value"
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