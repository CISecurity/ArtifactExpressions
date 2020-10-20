# macos.systemsetup_v1

## Description
The systemsetup_test is used to check systemsetup properties. It is a singleton object. It extends the standard TestType as defined in the oval-definitions-schema and one should refer to the TestType description for more information. The state element specifies the system setup elements to check

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| filepath | String | macos.systemsetup_v1 is a singleton and is effectively unused and not needed.  Artifact Types required a parameter in Workbench in the past|


### Supported Test Types
- macos.systemsetup_remoteappleevents_v1
- macos.systemsetup_remotelogin_v1
- macos.systemsetup_usingnetworktime_v1
- macos.systemsetup_wakeonnetworkaccess_v1

### Test Type Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| check_existence | String | Define how many items should be collected|
| check | String | Defines how many collected items must match the expected state |
| operation | String | comparison operation |
| datatype | String | datatype |
| remoteappleevents | Boolean | Specifies whether remote Apple events are enabled..|

| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| check_existence | String | Define how many items should be collected|
| check | String | Defines how many collected items must match the expected state |
| operation | String | comparison operation |
| datatype | String | datatype |
| remotelogin | Boolean |   Specifies whether remote Apple events are enabled. |

| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| check_existence | String | Define how many items should be collected|
| check | String | Defines how many collected items must match the expected state |
| operation | String | comparison operation |
| datatype | String | datatype |
| usingnetworktime | Boolean | Specifies weather the machine is using network time. |

| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| check_existence | String | Define how many items should be collected|
| check | String | Defines how many collected items must match the expected state |
| operation | String | comparison operation |
| datatype | String | datatype |
| wakeonnetworkaccess | Boolean | Specifies weather the machine is using network time.|




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
          <ae:parameter dt="string" name="systemsetup"
            >[systemsetup.value]</ae:parameter>
        </ae:parameters>
      </ae:artifact>
      <ae:test type="[TESTTYPE NAME]">
        <ae:parameters>
          <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
          <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
          <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
          <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
          <ae:parameter dt="boolean" name="remoteappleevents">[remoteappleevents.value]</ae:parameter>
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
      name="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:def:[ARTIFACT-OVAL-ID]"/>
</xccdf:check>
```

##### OVAL
###### Test

```
<macos:systemsetup_test check="[check.value]" check_existence="[check_existence.value]"
  comment="[RECOMMENDATION TITLE]"
  id="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:tst:[ARTIFACT-OVAL-ID]" version="1">
  <macos:object object_ref="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:obj:[ARTIFACT-OVAL-ID]"/>
  <macos:state state_ref="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:ste:[ARTIFACT-OVAL-ID]"/>
</macos:systemsetup_test>
```

###### Object

```
<macos:systemsetup_object
  comment="[RECOMMENDATION TITLE]"
  id="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:obj:[ARTIFACT-OVAL-ID]" version="1">
</macos:systemsetup_object>

```
###### State

``` 
<macos:systemsetup_state
  comment="[RECOMMENDATION TITLE]"
  id="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:ste:[ARTIFACT-OVAL-ID]" version="1">
  <macos:remoteappleevents datatype="[datatype.value]" operation="[operation.value]">[remoteappleevents.value]</macos:remoteappleevents>
</macos:systemsetup_state>    
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
          name: systemsetup
          type: string
          value: [systemsetup.value]   
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
          name: remoteappleevents
          type: string
          value: [remoteappleevents.value]      
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
          "name": "systemsetup",
          "type": "string",
          "value": [systemsetup.value]
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
          "name": "remoteappleevents",
          "type": "string",
          "value": [remoteappleevents.value]
        }
      }
    ]
  }
}
```



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
          <ae:parameter dt="string" name="systemsetup"
            >[systemsetup.value]</ae:parameter>
        </ae:parameters>
      </ae:artifact>
      <ae:test type="[TESTTYPE NAME]">
        <ae:parameters>
          <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
          <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
          <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
          <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
          <ae:parameter dt="boolean" name="remotelogin">[remotelogin.value]</ae:parameter>
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
      name="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:def:[ARTIFACT-OVAL-ID]"/>
</xccdf:check>
```

##### OVAL
###### Test

```
<macos:systemsetup_test check="[check.value]" check_existence="[check_existence.value]"
  comment="[RECOMMENDATION TITLE]"
  id="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:tst:[ARTIFACT-OVAL-ID]" version="1">
  <macos:object object_ref="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:obj:[ARTIFACT-OVAL-ID]"/>
  <macos:state state_ref="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:ste:[ARTIFACT-OVAL-ID]"/>
</macos:systemsetup_test>
```

###### Object

```
<macos:systemsetup_object
  comment="[RECOMMENDATION TITLE]"
  id="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:obj:[ARTIFACT-OVAL-ID]" version="1">
</macos:systemsetup_object>

```
###### State

``` 
<macos:systemsetup_state
  comment="[RECOMMENDATION TITLE]"
  id="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:ste:[ARTIFACT-OVAL-ID]" version="1">
  <macos:remotelogin datatype="[datatype.value]" operation="[operation.value]">[remotelogin.value]</macos:remotelogin>
</macos:systemsetup_state>    
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
          name: systemsetup
          type: string
          value: [systemsetup.value]   
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
          name: remotelogin
          type: string
          value: [remotelogin.value]      
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
          "name": "systemsetup",
          "type": "string",
          "value": [systemsetup.value]
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
          "name": "remotelogin",
          "type": "string",
          "value": [remotelogin.value]
        }
      }
    ]
  }
}
```



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
          <ae:parameter dt="string" name="systemsetup"
            >[systemsetup.value]</ae:parameter>
        </ae:parameters>
      </ae:artifact>
      <ae:test type="[TESTTYPE NAME]">
        <ae:parameters>
          <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
          <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
          <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
          <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
          <ae:parameter dt="boolean" name="usingnetworktime">[usingnetworktime.value]</ae:parameter>
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
      name="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:def:[ARTIFACT-OVAL-ID]"/>
</xccdf:check>
```

##### OVAL
###### Test

```
<macos:systemsetup_test check="[check.value]" check_existence="[check_existence.value]"
  comment="[RECOMMENDATION TITLE]"
  id="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:tst:[ARTIFACT-OVAL-ID]" version="1">
  <macos:object object_ref="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:obj:[ARTIFACT-OVAL-ID]"/>
  <macos:state state_ref="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:ste:[ARTIFACT-OVAL-ID]"/>
</macos:systemsetup_test>
```

###### Object

```
<macos:systemsetup_object
  comment="[RECOMMENDATION TITLE]"
  id="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:obj:[ARTIFACT-OVAL-ID]" version="1">
</macos:systemsetup_object>

```
###### State

``` 
<macos:systemsetup_state
  comment="[RECOMMENDATION TITLE]"
  id="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:ste:[ARTIFACT-OVAL-ID]" version="1">
  <macos:usingnetworktime datatype="[datatype.value]" operation="[operation.value]">[usingnetworktime.value]</macos:usingnetworktime>
</macos:systemsetup_state>    
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
          name: systemsetup
          type: string
          value: [systemsetup.value]   
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
          name: usingnetworktime
          type: string
          value: [usingnetworktime.value]      
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
          "name": "systemsetup",
          "type": "string",
          "value": [systemsetup.value]
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
          "name": "usingnetworktime",
          "type": "string",
          "value": [usingnetworktime.value]
        }
      }
    ]
  }
}
```



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
          <ae:parameter dt="string" name="systemsetup"
            >[systemsetup.value]</ae:parameter>
        </ae:parameters>
      </ae:artifact>
      <ae:test type="[TESTTYPE NAME]">
        <ae:parameters>
          <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
          <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
          <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
          <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
          <ae:parameter dt="boolean" name="wakeonnetworkaccess">[wakeonnetworkaccess.value]</ae:parameter>
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
      name="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:def:[ARTIFACT-OVAL-ID]"/>
</xccdf:check>
```

##### OVAL
###### Test

```
<macos:systemsetup_test check="[check.value]" check_existence="[check_existence.value]"
  comment="[RECOMMENDATION TITLE]"
  id="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:tst:[ARTIFACT-OVAL-ID]" version="1">
  <macos:object object_ref="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:obj:[ARTIFACT-OVAL-ID]"/>
  <macos:state state_ref="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:ste:[ARTIFACT-OVAL-ID]"/>
</macos:systemsetup_test>
```

###### Object

```
<macos:systemsetup_object
  comment="[RECOMMENDATION TITLE]"
  id="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:obj:[ARTIFACT-OVAL-ID]" version="1">
</macos:systemsetup_object>

```
###### State

``` 
<macos:systemsetup_state
  comment="[RECOMMENDATION TITLE]"
  id="oval:org.cisecurity.benchmarks.o_apple_mac_os_x:ste:[ARTIFACT-OVAL-ID]" version="1">
  <macos:wakeonnetworkaccess datatype="[datatype.value]" operation="[operation.value]">[wakeonnetworkaccess.value]</macos:wakeonnetworkaccess>
</macos:systemsetup_state>    
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
          name: systemsetup
          type: string
          value: [systemsetup.value]   
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
          name: wakeonnetworkaccess
          type: string
          value: [wakeonnetworkaccess.value]      
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
          "name": "systemsetup",
          "type": "string",
          "value": [systemsetup.value]
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
          "name": "wakeonnetworkaccess",
          "type": "string",
          "value": [wakeonnetworkaccess.value]
        }
      }
    ]
  }
}
```
