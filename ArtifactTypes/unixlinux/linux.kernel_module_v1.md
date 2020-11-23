# linux.kernel_module_v1

## Description

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| module | String | Add in  |


### Supported Test Types
- linux.kernel_module.loadable_v1 
- linux.kernel_module.loaded_v1

### Test Type Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| loadable | String | Is the module loadable |
| loaded | String | Is the module currently loaded |


### Generated Content
#### XCCDF+AE
This is what the AE check looks like, inside a Rule, in the XCCDF

```
<xccdf:complex-check operator="AND">
   <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
        <xccdf:check-content>
            <ae:artifact_expression
                id="xccdf_org.cisecurity.benchmarks_ae_1.1.1.1.1">
                <ae:artifact_oval_id>[ARTIFACT_OVAL_ID]</ae:artifact_oval_id>
                <ae:title>[RECOMMENDATION_TITLE]</ae:title>
                <ae:artifact type="[ARTIFACTTYPE]">
                    <ae:parameters>
                        <ae:parameter dt="string" name="module"
                            >[module.value]</ae:parameter>
                    </ae:parameters>
                </ae:artifact>
                <ae:test type="[TESTTYPE]">
                    <ae:parameters>
                        <ae:parameter dt="string" name="loadable"
                            >[loadable.value]</ae:parameter>
                    </ae:parameters>
                </ae:test>
            </ae:artifact_expression>
        </xccdf:check-content>
    </xccdf:check>
</xccdf:complex-check>
```

#### SCAP
##### XCCDF
For `linux.kernel_module_v1` artifacts, the xccdf:check looks like this.  There is no Value in the xccdf for this Artifact.

```
<check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-content-ref href="[BENCHMARK_TITLE]"
        name="oval:org.cisecurity.benchmarks.centos_centos_7:def:[ARTIFACT_OVAL_ID]"/>
</check>
```

##### OVAL
###### Test

```
  <shellcommand_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#cmd"
            id="oval:org.cisecurity.benchmarks.centos_centos_7:tst:[ARTIFACT_OVAL_ID]"
            check_existence="at_least_one_exists" check="at least one"
            comment="[RECOMMENDATION_TITLE]" version="1">
            <object object_ref="oval:org.cisecurity.benchmarks.centos_centos_7:obj:[ARTIFACT_OVAL_ID]"/>
            <state state_ref="oval:org.cisecurity.benchmarks.centos_centos_7:ste:[ARTIFACT_OVAL_ID]"/>
        </shellcommand_test>
```

###### Object

```
<shellcommand_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#cmd"
            id="oval:org.cisecurity.benchmarks.centos_centos_7:obj:[ARTIFACT_OVAL_ID]"
            comment="[RECOMMENDATION_TITLE]" version="1">
            <command>modprobe -n -v dccp</command>
            <line_selection operation="pattern match">.+</line_selection>
        </shellcommand_object>
```
###### State

```
<shellcommand_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#cmd"
            id="oval:org.cisecurity.benchmarks.centos_centos_7:ste:[ARTIFACT_OVAL_ID]"
            comment="[RECOMMENDATION_TITLE]" version="1">
            <stdout_line entity_check="at least one" operation="[testtype.name]"
                >[testType.name.value]</stdout_line>
</shellcommand_state>
```

#### YAML


```
artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: linux.kernel_module_v1
      parameters:
      - parameter: 
          name: module
          type: string
          value: [module.value]
    test:
      type: [TestType Name]
      parameters:
      - parameter:
          name: loadable
          type: string
          value: [loadable.value]
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
      "type": "linux.kernel_module_v1",
      "parameters": [
        {
          "parameter": {
            "name": "module",
            "type": "string",
            "value": [
              "module.value"
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
            "name": "loadable",
            "type": "string",
            "value": [
              "loadable.value"
            ]
          }
        }
      ]
    }
  }
}
``` 