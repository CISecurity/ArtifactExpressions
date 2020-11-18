# iis.webserverconfig

## Description
The webconfig_test is used to check the status of Gatekeeper and any unsigned applications that have been granted execute permission.

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| site_name | String | Name of the site to collect. Can be a regex. |
| application_name | String | Name of the application to collect. Can be a regex. |
| virtual_directory_name | String |   The name of a virtual directory to collect. Can be a regex. |


### Supported Test Types
- iis.webserverconfig

### Test Type Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| operator | String | comparison operation |
| configuration_setting | String |  The web.config setting to test |
| data_type | String | The data type of the web.config setting |
| value | String | The value to compare to the collected web.config setting |

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
          <ae:parameter dt="string" name="site_name"
            >[site_name.value]</ae:parameter>
          <ae:parameter dt="string" name="application_name"
            >[application_name.value]</ae:parameter>  
          <ae:parameter dt="string" name="virtual_directory_name"
            >[virtual_directory_name.value]</ae:parameter>  
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
<iis:webconfig_test check="all" check_existence="at_least_one_exists"
   comment="[RECOMMENDATION TITLE]"
   id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" version="1">
   <iis:object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:"/>
   <iis:state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"/>
</iis:webconfig_test>

```

###### Object

```
<iis:webconfig_object id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
   version="1">
   <iis:site_name operation="pattern match">[site_name.value]</iis:site_name>
   <iis:application_name operation="pattern match">[application_name.value]</iis:application_name>
   <iis:virtual_directory_name operation="pattern match">[virtual_directory_name.value]</iis:virtual_directory_name>
   <filter action="include">oval:org.cisecurity.benchmarks.iis:ste:20000</filter>
</iis:webconfig_object> 
  
```

###### State

```
<iis:webconfig_state
   id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" version="1">
   <directory_browse_enabled xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iis"
      datatype="[data_type.value]" operation="[operator.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"/>
</iis:webconfig_state> 

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
          name: site_name
          type: string
          value: [site_name.value]
      - parameter: 
          name: application_name
          type: string
          value: [application_name.value]
      - parameter: 
          name: virtual_directory_name
          type: string
          value: [virtual_directory_name.value]        
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
          "name": "site_name",
          "type": "string",
          "value": [site_name.value]
        }
      },
      {
        "parameter": {
          "name": "application_name",
          "type": "string",
          "value": [application_name.value]
        }
      },
      {
        "parameter": {
          "name": "virtual_directory_name",
          "type": "string",
          "value": [virtual_directory_name.value]
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