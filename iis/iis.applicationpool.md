# iis.applicationpool

## Description
The applicationpool_test is used to check the status of Gatekeeper and any unsigned applications that have been granted execute permission.

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| applicationpool_name | String | The name of the application pool to collect. Can be a regex. |


### Supported Test Types
- iis.applicationpool

### Test Type Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| operator | String | comparison operation|
| value | String | |
| configuration_setting | String | The name of application pool property to test |
| data_type | String | The data type of the application pool property to test|

### Generated Content
#### XCCDF+AE
This is what the AE check looks like, inside a Rule, in the XCCDF

```
<xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
  <xccdf:check-content>
    <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION_NUMBER]">
      <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
      <ae:title>[RECOMMENDATION TITLE]</ae:title>
      <ae:artifact type="[ARTIFACTTYPE NAME]">
        <ae:parameters>
          <ae:parameter dt="string" name="applicationpool_name"
            >[applicationpool_name.value]</ae:parameter>
        </ae:parameters>
      </ae:artifact>
      <ae:test type="[TESTTYPE NAME]">
        <ae:parameters>
          <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
          <ae:parameter dt="string" name="configuration_setting"
            >[configuration_setting.value]</ae:parameter>
          <ae:parameter dt="string" name="data_type"
            >[data_type.value]</ae:parameter>
          <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
        </ae:parameters>
      </ae:test>
      <ae:profiles>
        <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1"
        />
      </ae:profiles>
    </ae:artifact_expression>
  </xccdf:check-content>
</xccdf:check>
```

#### SCAP
##### XCCDF

```
<xccdf:check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
  <xccdf:check-export
     export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
     value-id="[VALUE ID NAME]"/>
  <xccdf:check-content-ref href="CIS_Microsoft_IIS_10_Benchmark_v1.1.1-oval.xml"
     name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]"/>
</xccdf:check>

<xccdf:Value id="xccdf_org.cisecurity.benchmarks_value_4.9.1_var" operator="[operator.value]"
  type="[data_type.value]">
  <xccdf:title>[RECOMMENDATION TITLE]</xccdf:title>
  <xccdf:description>This variable is used in [RECOMMENDATION TITLE]</xccdf:description>
  <xccdf:value>[value.value]</xccdf:value>
</xccdf:Value>

```

##### OVAL
###### Test

```
<iis:applicationpool_test check="all" check_existence="at_least_one_exists"
   comment="[RECOMMENDATION TITLE]"
   id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" version="1">
   <iis:object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:"/>
   <iis:state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"/>
</iis:applicationpool_test>

```

###### Object

```
<iis:applicationpool_object id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
   version="1">
   <iis:applicationpool_name operation="[operator.value]">[applicationpool_name.value]</iis:applicationpool_name>
</iis:applicationpool_object>   
```

###### State

```
<iis:applicationhostconfig_state
   id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" version="1">
   <identity_type xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iis"
      datatype="[data_type.value]" operation="[operator.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"/>
</iis:applicationhostconfig_state>   

```

###### Variable

```
<external_variable
  comment="This value is used in [RECOMMENDATION TITLE]"
  datatype="[data_type.value]" id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" version="1"/>                   
```

#### YAML

```
- artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: [ARTIFACTTYPE NAME]
      parameters:
      - parameter: 
          name: applicationpool_name
          type: string
          value: [applicationpool_name.value]
    test:
      type: [TESTTYPE NAME]
      parameters:
      - parameter:
          name: operator
          type: string
          value: [operator.value]
      - parameter: 
          name: configuration_setting
          type: string
          value: [configuration_setting.value]
      - parameter:
          name: data_type
          type: string
          value: [data_type.value]
      - parameter: 
          name: value
          type: string
          value: [value.value]       
```

#### JSON

```
"artifact-expression": {
  "artifact-unique-id": [ARTIFACT-OVAL-ID],
  "artifact-title": [RECOMMENDATION TITLE],
  "artifact": {
    "type": "[ARTIFACTTYPE NAME]",
    "parameters": [
      {
        "parameter": {
          "name": "applicationpool_name",
          "type": "string",
          "value": [applicationpool_name.value]
        }
      }
    ]
  },
  "test": {
    "type": [TESTTYPE NAME],
    "parameters": [
      {
        "parameter": {
          "name": "operator",
          "type": "string",
          "value": [operator.value]
        }
      },
      {
        "parameter": {
          "name": "configuration_setting",
          "type": "string",
          "value": [configuration_setting.value]
        }
      },
      {
        "parameter": {
          "name": "data_type",
          "type": "string",
          "value": [data_type.value]
        }
      },
      {
        "parameter": {
          "name": "value",
          "type": "string",
          "value": [value.value]
        }
      }
    ]
  }
}
``` 