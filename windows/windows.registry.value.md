# windows.registry.value

## Description
The registry test is used to check metadata associated with Windows registry key. It extends the standard TestType as defined in the oval-definitions-schema and one should refer to the TestType description for more information. The required object element references a registry_object and the optional state element specifies the registry data to check.

## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| hive | String | The hive of the target registry key	|
| key_operator | String |  The operator used to qualify the target key. This is typically 'case_insensitive_equals'.	|
| key | String |  The key to collect, using the above operator	|
| name | String |  The name of the registry key to collect	|
| check_existence | String | Typically set to 'at least one'. Set to 'any exist' to pass even if the key does not exist.	|
| windows_view | String |  Typically left to 'default'. Set to 32_bit to force collecting 32bit registry on a 64bit OS.	|
| registry_data_type | String |The type of registry value to collect|

hive 
NOTE: This parameter is governed by a constraint allowing only the following values:
- HKEY_LOCAL_MACHINE
- HKEY_USER
- HKEY_CURRENT_USER
- HKEY_CLASSES_ROOT
- HKEY_CURRENT_CONFIG

windows_view 
NOTE: This parameter is governed by a constraint allowing only the following values:
- default
- 32_bit
- 64_bit

registry_data_type 
NOTE: This parameter is governed by a constraint allowing only the following values:
- reg_dword
- reg_sz
- reg_dword_little_endian
- reg_dword_big_endian
- reg_expand_sz
- reg_multi_sz
- reg_binary
- reg_link
- reg_none
- reg_qword_little_endian

### Supported Test Types
- windows.registry.value
- existence_test
- equal
- equals

### Test Type Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| operator | String | The operation to perform on the collected registry values|
| value_data_type | String | The data type of the collected value |
| value | String | The value to compare against the collected registry value |
| check | String | Determines how many of the collected registry values must satisfy the operator/value test. Typically set to 'at least one'	 |
| data_type | String | datatype |

data_type/value_data_type
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
<xccdf:complex-check operator="AND">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
        <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_5.1.2">
            <ae:artifact_oval_id>[ARTIFACT_OVAL_ID]</ae:artifact_oval_id>
            <ae:title>[RECOMMENDATION_TITLE]</ae:title>
            <ae:artifact type="[ARTIFACT_TYPE.name]">
                <ae:parameters>
                    <ae:parameter dt="string" name="hive"
                        >[hive.value]</ae:parameter>
                    <ae:parameter dt="string" name="key_operator"
                        >[key_operator.value]</ae:parameter>
                    <ae:parameter dt="string" name="key>[key.value]</ae:parameter>
                    <ae:parameter dt="string" name="name>[name.value]</ae:parameter>
                    <ae:parameter dt="string" name="check_existence"
                        >[check_existence.value]</ae:parameter>
                    <ae:parameter dt="string" name="windows_view"
                        >[windows_view.value]</ae:parameter>
                    <ae:parameter dt="string" name="registry_data_type"
                        >[registry_data_type.value]</ae:parameter>
                    <ae:parameter dt="string" name="name_operation"
                        >[name_operation.value]</ae:parameter>
                </ae:parameters>
            </ae:artifact>
            <ae:test type="[TESTTYPE_NAME]">
                <ae:parameters>
                    <ae:parameter dt="string" name="value">all_exist</ae:parameter>
                </ae:parameters>
            </ae:test>
        </ae:artifact_expression>
    </xccdf:check-content>
    </xccdf:check>
</xccdf:complex-check>
```

#### SCAP
##### XCCDF
For `windows.registry.value` artifacts, an XCCDF Value element is generated:

```
<Values>
			<Value id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT_OVAL_ID]_var1" type="string"
				operator="equals">
				<title>[RECOMMENDATION_TITLE]</title>
				<description>This value is used in Rule: [RECOMMENDATION_TITLE]</description>
				<value>[TestType.value.value]</value>
			</Value>
			<Value id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT_OVAL_ID]_var2" type="string"
				operator="equals">
				<title>[RECOMMENDATION_TITLE]</title>
				<description>This value is used in Rule: [RECOMMENDATION_TITLE]</description>
				<value>[TestType.value.value]</value>
			</Value>
		</Values>
```

##### OVAL
###### Test

```
<registry_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
			id="oval:org.cisecurity.benchmarks.windows_8.1:tst:[ARTIFACT_OVAL_ID]"
			check_existence="at_least_one_exists" check="all"
			comment="[RECOMMENDATION_TITLE]"
			version="1">
			<object object_ref="oval:org.cisecurity.benchmarks.windows_8.1:obj:[ARTIFACT_OVAL_ID]"/>
			<state state_ref="oval:org.cisecurity.benchmarks.windows_8.1:ste:[ARTIFACT_OVAL_ID]"/>
		</registry_test>
```

###### Object

```
<registry_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
			id="oval:org.cisecurity.benchmarks.windows_8.1:obj:[ARTIFACT_OVAL_ID]"
			comment="[RECOMMENDATION_TITLE]"
			version="1">
			<hive>[hive.value]</hive>
			<key operation="[testType.name]">[key.value]</key>
			<name>[name.value]</name>
		</registry_object>
```

###### State

```
<registry_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
			id="oval:org.cisecurity.benchmarks.windows_8.1:ste:[ARTIFACT_OVAL_ID]"
			comment="[RECOMMENDATION_TITLE]"
			version="1">
			<type>[testType.value.value]</type>
			<value datatype="string" operation="[testType.name]">O:BAG:BAD:(A;;RC;;;BA)</value>
		</registry_state>
```

###### Variable

```
<external_variable id="oval:org.cisecurity.benchmarks.windows_8.1:var:[ARTIFACT_OVAL_ID]1"
			datatype="string" version="1"
			comment="This value is used in Rule: [RECOMMENDATION_TITLE]/>
<external_variable id="oval:org.cisecurity.benchmarks.windows_8.1:var:[ARTIFACT_OVAL_ID]2"
    datatype="string" version="1"
    comment="This value is used in Rule:[RECOMMENDATION_TITLE]"
/>
```


#### YAML

```
- artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: windows.registry.value
      parameters:
      - parameter: 
          name: hive
          type: string
          value: [ARTIFACT TYPE PARAMETER VALUE]
      - parameter: 
            name: key_operator
            type: string
            value: [ARTIFACT TYPE PARAMETER VALUE]
        - parameter: 
             name: key
             type: string
             value: [ARTIFACT TYPE PARAMETER VALUE]
        - parameter: 
               name: name
               type: string
               value: [ARTIFACT TYPE PARAMETER VALUE]
        - parameter: 
             name: check_existence
             type: string
             value: [ARTIFACT TYPE PARAMETER VALUE]
         - parameter: 
               name: windows_view
               type: string
               value: [ARTIFACT TYPE PARAMETER VALUE]
         - parameter: 
                name: registry_data_type
                type: string
                value: [ARTIFACT TYPE PARAMETER VALUE]
        - parameter: 
              name: name_operation
              type: string
              value: [ARTIFACT TYPE PARAMETER VALUE]
               
test:
      type: [TestType Name]
      parameters:
      - parameter:
          name: value
          type: string
          value: [TestType.value.value]
```

#### JSON

```
"artifact-expression": {
  "artifact-unique-id": [ARTIFACT-OVAL-ID],
  "artifact-title": [RECOMMENDATION TITLE],
  "artifact": {
    "type": "windows.registry.value",
    "parameters": [
      {
        "parameter": {
          "name": "hive",
          "type": "string",
          "value": [ARTIFACT TYPE PARAMETER VALUE]
        }
      }, 
       {
          "parameter": {
            "name": "key_operator",
            "type": "string",
            "value": [ARTIFACT TYPE PARAMETER VALUE]
          }
        },
        {
            "parameter": {
              "name": "key",
              "type": "string",
              "value": [ARTIFACT TYPE PARAMETER VALUE]
            }
        }, 
        {
          "parameter": {
            "name": "name",
            "type": "string",
            "value": [ARTIFACT TYPE PARAMETER VALUE]
          }
        },
        {
            "parameter": {
              "name": "check_existence",
              "type": "string",
              "value": [ARTIFACT TYPE PARAMETER VALUE]
            }
          }, 
        {
          "parameter": {
            "name": "windows_view",
            "type": "string",
            "value": [ARTIFACT TYPE PARAMETER VALUE]
          }
         }, 
          {
           "parameter": {
             "name": "registry_data_type",
             "type": "string",
             "value": [ARTIFACT TYPE PARAMETER VALUE]
           }
          }, 
           {
            "parameter": {
              "name": "operation",
              "type": "string",
              "value": [ARTIFACT TYPE PARAMETER VALUE]
            }
           }, 
    ]
  },
  "test": {
    "type": [TestType Name],
    "parameters": [
      {
        "parameter": {
          "name": "value",
          "type": "string",
          "value": [TestType.value.value]
        }
      }
    ]
  }
}
``` 