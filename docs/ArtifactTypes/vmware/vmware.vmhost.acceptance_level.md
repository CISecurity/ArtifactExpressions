# vmware.vmhost.acceptance_level

## Description
The vmhost_acceptancelevel_test is used to determine if the software installed for the VMHost represents untested code. It extends the standard TestType as defined in the oval-definitions-schema and one should refer to the TestType description for more information. The required object element references a vmhost_acceptancelevel_object and the optional state element specifies the data to check.

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| vmhost_name | String | The name of the ESXi server to scope objects to. Set to NA if not applicable |


### Supported Test Types
- vmware.vmhost.acceptance_level

### Test Type Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| operator | String | comparison operator |
| acceptance_level | String | NA or values defined by Acceptance Level constraint|

acceptance_level
NOTE: This parameter is governed by a constraint allowing only the following values
- NA
- VMwareCertified
- VMwareAccepted
- PartnerSupported
- CommunitySupported

operator
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
<xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
  <xccdf:check-content>
    <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION_NUMBER]">
      <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
      <ae:title>[RECOMMENDATION TITLE]</ae:title>
      <ae:artifact type="[ARTIFACTTYPE NAME]">
        <ae:parameters>
          <ae:parameter dt="string" name="gatekeeper"
            >[gatekeeper.value]</ae:parameter>
        </ae:parameters>
      </ae:artifact>
      <ae:test type="[TESTTYPE NAME]">
        <ae:parameters>
          <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
          <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
          <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
          <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
          <ae:parameter dt="boolean" name="enabled">[enabled.value]</ae:parameter>
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
For `macos.gatekeeper_v1` artifacts, the xccdf:check looks like this.  There is no Value in the xccdf for this Artifact.

```
<xccdf:check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
   <xccdf:check-content-ref xmlns:ae="http://benchmarks.cisecurity.org/ae/0.5"
      xmlns:cpe="http://cpe.mitre.org/language/2.0"
      xmlns:ecl="http://cisecurity.org/check"
      href="[BENCHMARK NAME]"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]"/>
</xccdf:check>
```

##### OVAL
###### Test

```
<macos:gatekeeper_test check="[check.value]" check_existence="[check_existence.value]"
  comment="[RECOMMENDATION TITLE]"
  id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:ARTIFACT-OVAL-ID" version="1">
  <macos:object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:ARTIFACT-OVAL-ID"/>
  <macos:state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:ARTIFACT-OVAL-ID"/>
</macos:gatekeeper_test>
```

###### Object

```
<macos:gatekeeper_object
  comment="[RECOMMENDATION TITLE]"
  id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:ARTIFACT-OVAL-ID" version="1"> 
</macos:gatekeeper_object>    
```
###### State

```
<macos:gatekeeper_state
  comment="[RECOMMENDATION TITLE]"
  id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:ARTIFACT-OVAL-ID" version="1">
  <macos:enabled datatype="[datatype.value]" operation="[operation.value]">[enabled.value]</macos:enabled>
</macos:gatekeeper_state>    
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
          name: gatekeeper
          type: string
          value: [gatekeeper.value]
    test:
      type: [TESTTYPE NAME]
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
          name: datatype
          type: string
          value: [datatype.value]  
      - parameter: 
          name: enabled
          type: string
          value: [enabled.value]      
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
          "name": "gatekeeper",
          "type": "string",
          "value": [gatekeeper.value]
        }
      }
    ]
  },
  "test": {
    "type": [TESTTYPE NAME],
    "parameters": [
      {
        "parameter": {
          "name": "check_existence",
          "type": "string",
          "value": [check_existence.value]
        }
      },
      {
        "parameter": {
          "name": "check",
          "type": "string",
          "value": [check.value]
        }
      },
      {
        "parameter": {
          "name": "operation",
          "type": "string",
          "value": [operation.value]
        }
      },
      {
        "parameter": {
          "name": "datetype",
          "type": "string",
          "value": [datatype.value]
        }
      },
      {
        "parameter": {
          "name": "enabled",
          "type": "string",
          "value": [enabled.value]
        }
      }
    ]
  }
}
``` 