# vmware.vds_v2

## Description
The gatekeeper_test is used to check the status of Gatekeeper and any unsigned applications that have been granted execute permission.

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| vds_name | String | The name of a vSphere Distributed Switch |
| check_existence | String | Defines how many items should be collected |
| vds_name_operation | String | comparison operation |


### Supported Test Types
- vmware:vds_vlan_mtu
- vmware:vds_teaming_failover

### Test Type Parameters
#### vmware:vds_teaming_failover
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| check | String | Defines how many collected items must match the expected state |
| operation | String | comparison operation |
| datatype | String | datatype |
| teaming_failover_health_check_enabled | Boolean |Teaming and Failover Health Check enabled? |

#### vmware:vds_vlan_mtu
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| check | String | Defines how many collected items must match the expected state |
| operation | String | comparison operation |
| datatype | String | datatype |
|   vlan_mtu_health_check_enabled | Boolean | VLAN and MTU Health Check enabled? |

check_existence
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

datatype
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
<xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
  <xccdf:check-content>
    <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION_NUMBER]">
      <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
      <ae:title>[RECOMMENDATION TITLE]</ae:title>
      <ae:artifact type="[ARTIFACTTYPE NAME]">
        <ae:parameters>
          <ae:parameter dt="string" name="vds_name">[vds_name.value]</ae:parameter>
          <ae:parameter dt="string" name="check_existence"
            >[check_existence.value]</ae:parameter>
          <ae:parameter dt="string" name="vds_name_operation">[vds_name_operation.value]</ae:parameter>
        </ae:parameters>
      </ae:artifact>
      <ae:test type="[TESTTYPE NAME]">
        <ae:parameters>
          <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
          <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
          <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
          <ae:parameter dt="string" name="vlan_mtu_health_check_enabled"
            >[vlan_mtu_health_check_enabled.value]</ae:parameter>
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
For `vmware.vds_v2` artifacts, the xccdf:check looks like this. An XCCDF Value element is generated.

```
<xccdf:complex-check operator="AND">
  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export export-name="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]"
      value-id="[VALUE ID NAME]"/>
    <check-content-ref href="[BENCHMARK NAME]"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]"/>
  </check>
</xccdf:complex-check>  

<Value abstract="false" hidden="false" id="[VALUE ID NAME]"
  interactive="1" prohibitChanges="false" type="string">
  <title override="0">[RECOMMENDATION TITLE]</title>
  <description override="0">[RECOMMENDATION TITLE]</description>
  <value selector=""/>
  <default>[DEFAULT VALUE]</default>
</Value>    

```

##### OVAL
###### Test

```
<vds_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi" check="[check.value]"
  check_existence="[check_existence.value]" comment="[RECOMMENDATION TITLE]"
  id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" version="1">
  <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"/>
  <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"/>
</vds_test>
```

###### Object

```
<vds_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
  comment="[RECOMMENDATION TITLE]"
  id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" version="1">
  <connection_string var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]"/>
  <vds_name operation="[operation.value]">[vds_name.value]</vds_name>
</vds_object>    
```
###### State

```
<vds_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
  comment="[RECOMMENDATION TITLE]"
  id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" version="1">
  <vlan_mtu_health_check_enabled datatype="[datatype.value]" operation="[operation.value]"
    >[vlan_mtu_health_check_enabled.value]</vlan_mtu_health_check_enabled>
</vds_state>   
```

###### Variable

```
<external_variable
  comment="This value is used in [RECOMMENDATION TITLE]"
  datatype="[datatype.value]" id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" version="1"/>                   
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
          name: vds_name
          type: string
          value: [vds_name.value]
      - parameter: 
        name: check_existence
        type: string
        value: [check_existence.value]   
      - parameter: 
        name: ds_name_operation
        type: string
        value: [vds_name_operation.value]  
    test:
      type: [TESTTYPE NAME]
      parameters:
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
          name: vlan_mtu_health_check_enabled
          type: string
          value: [vlan_mtu_health_check_enabled.value]      
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
          "name": "vds_name",
          "type": "string",
          "value": [vds_name.value]
        }
      },
      {
        "parameter": {
          "name": "check_existence",
          "type": "string",
          "value": [check_existence.value]
        }
      },
      {
        "parameter": {
          "name": "vds_name_operation",
          "type": "string",
          "value": [vds_name_operation.value]
        }
      }
    ]
  },
  "test": {
    "type": [TESTTYPE NAME],
    "parameters": [
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
          "name": "vlan_mtu_health_check_enabled",
          "type": "string",
          "value": [vlan_mtu_health_check_enabled.value]
        }
      }
    ]
  }
}
``` 