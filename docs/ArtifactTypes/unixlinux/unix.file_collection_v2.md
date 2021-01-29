# unix.file_collection_v2

## Description
The textfilecontent54_test element is used to check the contents of a text file (aka a configuration file) by looking at individual blocks of text. It extends the standard TestType as defined in the oval-definitions-schema and one should refer to the TestType description for more information. The required object element references a textfilecontent54_object and the optional state element specifies the metadata to check. The evaluation of the test is guided by the check attribute that is inherited from the TestType.


## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| existence | String | existence requirement |
| path | String | path to the file  |
| file_name | String | The name of the file |
| recurse | String | should subdirectories be recursed through |
| check | string | check |
| file_system | String | file system limitation for recursion. All fileSystems, restrict to local only, or restrict to filesystem defined by Path |

existence NOTE: This parameter is governed by a constraint allowing only the following values:
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

### Supported Test Types
- pattern match
- unix_file_attributes_v1
- pattern not match

### Test Type Parameters
####pattern match, pattern not match
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| data_type | String | datatype |
| value | String | Regular expression to be matched  |

#### unix_file_attributes_v1
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| uread | String | Can the owner read the file |
| uwrite | String | Can the owner write the file |
| uexec | String | Can the owner execute the file |
| gread | String | Can the group read the file |
| gwrite | String | Can the group write the file |
| gexec | String | Can the group execute the file |
| oread | String | Can the world read the file |
| owrite | String | Can the world write the file |
| oexec | String | Can the world execute the file |
| suid | String | Can the file execute as the owner |
| sgid | String | Can the file execute as the group|
| sticky | String | Is the sticky bit set |
| uid | int | Owner UID (empty to ignore) |
| gid | int | owner GID (empty to ignore) | 


data_type
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
<xccdf:complex-check operator="AND">
system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
        <ae:artifact_expression
        id="xccdf_org.cisecurity.benchmarks_ae_1.3.2.5">
        <ae:artifact_oval_id>[ARTIFACT_OVAL_ID]</ae:artifact_oval_id>
        <ae:title>[RECOMMENDATION_TITLE]</ae:title>
        <ae:artifact type="[ARTIFACTTYPE]">
        <ae:parameters>
        <ae:parameter dt="string" name="existence"
        >[existence.value]</ae:parameter>
        <ae:parameter dt="string" name="check"
        >[check.value]</ae:parameter>
        <ae:parameter dt="string" name="path"
        >[path.value]</ae:parameter>
        <ae:parameter dt="string" name="file_name"
        >[file_name.value]</ae:parameter>
        <ae:parameter dt="string" name="recurse"
        >[recurse.value]</ae:parameter>
        <ae:parameter dt="string" name="file_system"
        >[file_system.value]</ae:parameter>
        </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST_TYPE]">
        <ae:parameters>
        <ae:parameter dt="string" name="value"
        >[value.value]</ae:parameter>
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
For `unix.file_collection_v2` artifacts, an XCCDF check element looks like this ; no value element is generated.

```
<check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
			<check-content-ref href="[BENCHMARK_NAME]"
				name="oval:org.cisecurity.benchmarks.centos_centos_7:def:[ARTIFACT_OVAL_ID]"/>
		</check>
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
		</textfilecontent54_test>
```

###### Object

```
<textfilecontent54_object
			xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
			id="oval:org.cisecurity.benchmarks.centos_centos_7:obj:[ARTIFACT_OVAL_ID]"
			comment="[RECOMMENDATION_TITLE]"
			version="1">
			<path>/etc/yum.repos.d</path>
			<filename operation="pattern match">.*</filename>
			<pattern operation="pattern match" datatype="string"
				>^\s*gpgcheck\s*=\s*[^1]\s*(\s+#.*)?$</pattern>
			<instance datatype="int" operation="equals">1</instance>
		</textfilecontent54_object>
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
      type: unix.file_collection_v2
      parameters:
      - parameter: 
          name: existence
          type: string
          value: [existence.value]
      - parameter: 
          name: path
          type: string
          value: [path.value]
      - parameter: 
          name: file_name
          type: string
          value: [file_name.value]
      - parameter: 
          name: recurse
          type: string
          value: [recurse.value]
      - parameter: 
          name: check
          type: string
          value: [filesystem.value]
      - parameter: 
          name: file_system
          type: string
          value: [file_system.value]
    test:
      type: unix_file_attributes_v1
      parameters:
      - parameter: 
          name: uread
          type: string
          value: [uread.value]
      - parameter: 
          name: uwrite
          type: string
          value: [uwrite.value]                   
      - parameter: 
          name: uexec
          type: string
          value: [uexec.value]
      - parameter: 
          name: gread
          type: string
          value: [gread.value]                   
      - parameter: 
          name: gwrite
          type: string
          value: [gwrite.value]
      - parameter: 
          name: gexec
          type: string
          value: [gexec.value]                   
      - parameter: 
          name: oread
          type: string
          value: [oread.value]
      - parameter: 
          name: owrite
          type: string
          value: [owrite.value]                   
      - parameter: 
          name: oexec
          type: string
          value: [oexec.value]
      - parameter: 
          name: suid
          type: string
          value: [suid.value]                   
      - parameter: 
          name: sgid
          type: string
          value: [sgid.value]
      - parameter: 
          name: sticky
          type: string
          value: [sticky.value]                   
  	  - parameter: 
          name: uid
          type: string
          value: [uid.value]
      - parameter: 
          name: gid
          type: string
          value: [gid.value]                   
               
                        
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
      "type": "unix.file_collection_v2",
      "parameters": [
        {
          "parameter": {
            "name": "existence",
            "type": "string",
            "value": [
              "existence.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "path",
            "type": "string",
            "value": [
              "path.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "file_name",
            "type": "string",
            "value": [
              "file_name.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "recurse",
            "type": "string",
            "value": [
              "recurse.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "check",
            "type": "string",
            "value": [
              "filesystem.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "file_system",
            "type": "string",
            "value": [
              "file_system.value"
            ]
          }
        }
      ]
    },
    "test": {
      "type": "unix_file_attributes_v1",
      "parameters": [
        {
          "parameter": {
            "name": "uread",
            "type": "string",
            "value": [
              "uread.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "uwrite",
            "type": "string",
            "value": [
              "uwrite.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "uexec",
            "type": "string",
            "value": [
              "uexec.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "gread",
            "type": "string",
            "value": [
              "gread.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "gwrite",
            "type": "string",
            "value": [
              "gwrite.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "gexec",
            "type": "string",
            "value": [
              "gexec.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "oread",
            "type": "string",
            "value": [
              "oread.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "owrite",
            "type": "string",
            "value": [
              "owrite.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "oexec",
            "type": "string",
            "value": [
              "oexec.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "suid",
            "type": "string",
            "value": [
              "suid.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "sgid",
            "type": "string",
            "value": [
              "sgid.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "sticky",
            "type": "string",
            "value": [
              "sticky.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "uid",
            "type": "string",
            "value": [
              "uid.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "gid",
            "type": "string",
            "value": [
              "gid.value"
            ]
          }
        }
      ]
    }
  }
}
```