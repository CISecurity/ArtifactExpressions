# unix.file_collection_v1

## Description
The file test is used to check metadata associated with UNIX files, of the sort returned by either an ls command, stat command or stat() system call. It extends the standard TestType as defined in the oval-definitions-schema and one should refer to the TestType description for more information. The required object element references a file_object and the optional state element specifies the metadata to check.

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
| max_depth | int |  max depth for recursion. -1 for unlimited recursion|
| file_system | String | file system limitation for recursion. All fileSystems, restrict to local only, or restrict to filesystem defined by Path |

### Supported Test Types
- unix.file_permissions_v1
- unix_file_ownership_v1
- null_test_v1

### Test Type Parameters
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


### Generated Content
#### XCCDF+AE
This is what the AE check looks like, inside a Rule, in the XCCDF

```
<xccdf:complex-check operator="AND">
system="https://benchmarks.cisecurity.org/ae/0.5">
  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
  					<xccdf:check-content>
  						<ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_20.2.1">
  							<ae:artifact_oval_id>[ARTIFACT_OVAL_ID]</ae:artifact_oval_id>
  							<ae:title>[RECOMMENDATION_TITLE]</ae:title>
  							<ae:artifact type="[ARTIFACT_TYPE]">
  								<ae:parameters>
  									<ae:parameter dt="string" name="existence"
  										>[existence.value]</ae:parameter>
  									<ae:parameter dt="string" name="path">[path.value]</ae:parameter>
  									<ae:parameter dt="string" name="file_name"
  										>[file_name.value]</ae:parameter>
  									<ae:parameter dt="string" name="recurse">[recurse.value]</ae:parameter>
  									<ae:parameter dt="int" name="max_depth"> [max_depth.value] </ae:parameter>
  									<ae:parameter dt="string" name="file_system">[file_system.value]</ae:parameter>
  								</ae:parameters>
  							</ae:artifact>
  							<ae:test type="[TEST_TYPE]">
  								<ae:parameters>
  									<ae:parameter dt="string" name="uread">[uread.value]</ae:parameter>
  									<ae:parameter dt="string" name="uwrite">[uwrite.value]</ae:parameter>
  									<ae:parameter dt="string" name="uexec">[uexec.value]</ae:parameter>
  									<ae:parameter dt="string" name="gread">[gread.value]</ae:parameter>
  									<ae:parameter dt="string" name="gwrite">[gwrite.value]</ae:parameter>
  									<ae:parameter dt="string" name="gexec">[gexec.value]</ae:parameter>
  									<ae:parameter dt="string" name="oread">[oread.value]</ae:parameter>
  									<ae:parameter dt="string" name="owrite">[owrite.value]</ae:parameter>
  									<ae:parameter dt="string" name="oexec">[oexec.value]</ae:parameter>
  									<ae:parameter dt="string" name="suid">[suid.value]</ae:parameter>
  									<ae:parameter dt="string" name="sgid">[sgid.value]</ae:parameter>
  									<ae:parameter dt="string" name="sticky">[sticky.value]</ae:parameter>
  								</ae:parameters>
  							</ae:test>
  						</ae:artifact_expression>
  					</xccdf:check-content>
  				</xccdf:check>
</xccdf:complex-check>
```

#### SCAP
##### XCCDF
For `unix.file_collection_v1` artifacts, an XCCDF check looks like this. an XCCDF Value element is not  generated:

```
     <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
     			<check-content-ref
     				href="[BENCHMARK_NAME]"
     				name="oval:org.cisecurity.benchmarks.redhat_redhat_enterprise_linux_5:def:[ARTIFACT_OVAL_ID]"/>
     		</check>
```

##### OVAL
###### Test

```
<file_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
			id="oval:org.cisecurity.benchmarks.redhat_redhat_enterprise_linux_5:tst:[ARTIFACT_OVAL_ID]"
			check_existence="at_least_one_exists" check="all"
			comment="[RECOMMENDATION_TITLE]"
			version="1">
			<object
				object_ref="oval:org.cisecurity.benchmarks.redhat_redhat_enterprise_linux_5:obj:[ARTIFACT_OVAL_ID]"/>
			<state
				state_ref="oval:org.cisecurity.benchmarks.redhat_redhat_enterprise_linux_5:ste:[ARTIFACT_OVAL_ID]"
			/>
		</file_test>
```

###### Object

```
<file_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
			id="oval:org.cisecurity.benchmarks.redhat_redhat_enterprise_linux_5:obj:[ARTIFACT_OVAL_ID]"
			comment="[RECOMMENDATION_TITLE]"
			version="1">
			<path>/etc</path>
			<filename>grub.conf</filename>
		</file_object>
```
###### State

```
<file_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
			id="oval:org.cisecurity.benchmarks.redhat_redhat_enterprise_linux_5:ste:[ARTIFACT_OVAL_ID]"
			comment="[RECOMMENDATION_TITLE]"
			version="1">
			<group_id datatype="int">0</group_id>
			<user_id datatype="int">0</user_id>
		</file_state>
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
- artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: unix.file_collection_v1
      parameters:
      - parameter: 
          name: command
          type: string
          value: [ARTIFACT TYPE PARAMETER VALUE]
    test:
      type: [TestType Name]
      parameters:
      - parameter:
          name: value
          type: string
          value: [TestType.value.value]
      - parameter: 
          name: data_type
          type: string
          value: [TestType.data_type.value]
```

#### JSON

```
"artifact-expression": {
  "artifact-unique-id": [ARTIFACT-OVAL-ID],
  "artifact-title": [RECOMMENDATION TITLE],
  "artifact": {
    "type": "unix_command_output_v1",
    "parameters": [
      {
        "parameter": {
          "name": "command",
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
          "name": "value",
          "type": "string",
          "value": [TestType.value.value]
        }
      },
      {
        "parameter": {
          "name": "data_type",
          "type": "string",
          "value": [TestType.data_type.value]
        }
      }
    ]
  }
}
```