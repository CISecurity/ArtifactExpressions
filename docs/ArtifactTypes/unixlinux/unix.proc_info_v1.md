# unix.proc_info_v1

## Description
The process58_test is used to check information found in the UNIX processes. It is equivalent to parsing the output of the ps command. It extends the standard TestType as defined in the oval-definitions-schema and one should refer to the TestType description for more information. The required object element references a process58_object and the optional state element references a process58_state that specifies the process information to check.
   


## Intent
TBD

## Technical Details
### Artifact Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| command_line | String | The command entity is the string used to start the process. This includes any parameters that are part of the command line.	 |
| pid | String |The pid entity is the process ID of the process.	 |
| command_line_operation | String |  Specifies what operation is to be performed using the Command value.	|
| pid_operation | String | Specifies what operation is to be performed using the Process ID value.	|

### Supported Test Types
- unix.proc_info_v1

### Test Type Parameters

| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| command_line | String |This is the string used to start the process. This includes any parameters that are part of the command line.	 |
| cmd_operation | String |Specifies what operation is to be performed using the Command value.	 |
| exec_time | String |  This is the cumulative CPU time, formatted in [DD-]HH:MM:SS where DD is the number of days when execution time is 24 hours or more.		|
| exec_time_operation | String | 	Specifies what operation is to be performed using the execution time value.	|
| pid | String | This is the process ID of the process.		 |
| pid_operation | String | Specifies what operation is to be performed using the process ID value.	|
| ppid | String |  This is the process ID of the process's parent process.		|
| ppid_operation | String | Specifies what operation is to be performed using the parent process ID value.		|
| priority | int |  This is the scheduling priority with which the process runs. This can be adjusted with the nice command or nice() system call.	|
| priority_operation | Specifies what operation is to be performed using the process priority value.		 |
| ruid | String | This is the real user id which represents the user who has created the process.	 	|
| ruid_operation | String |Specifies what operation is to be performed using the parent real user ID value.		|
| scheduling_class | String | 	A platform specific characteristic maintained by the scheduler: RT (real-time), TS (timeshare), FF (fifo), SYS (system), etc.	 |
| scheduling_class_operation | String |Specifies what operation is to be performed using the scheduling class value.	 |
| start_time | String |  This is the time of day the process started formatted in HH:MM:SS if the same day the process started or formatted as MMM_DD (Ex.: Feb_5) if process started the previous day or further in the past.		|
| start_time_operation | String |Specifies what operation is to be performed using the process start time value.		|
| tty | String | This is the TTY on which the process was started, if applicable.		 |
| tty_operation | String |Specifies what operation is to be performed using the process TTY value.	 |
| user_id | String | This is the effective user id which represents the actual privileges of the process.	 	|
| user_id_operation | String | Specifies what operation is to be performed using the user ID value.		|
| exec_shield | boolean | A boolean that when true would indicates that ExecShield is enabled for the process.	 |
| exec_shield_operation | String |	Specifies what operation is to be performed using the ExecShield Status value.	 |
| loginuid | String | The loginuid shows which account a user gained access to the system with. The /proc/XXXX/loginuid shows this value.	 	|
| loginuid_operation | String | Specifies what operation is to be performed using the process' account value.		|
| posix_capability_operation | String | Specifies what operation is to be performed using the POSIX capability value.	 |
| selinux_domain_label | String |	An selinux domain label associated with the process.	 |
| selinux_domain_label_operation | String |Specifies what operation is to be performed using the SELinux domain label value.	  |
| session_id |  String |The session ID of the process.		|
| session_id_operation | String |  Specifies what operation is to be performed using the process' session ID value.		|
| posix_capability |  String | An effective capability associated with the process. See linux/include/linux/capability.h for more information.		|


### Generated Content
#### XCCDF+AE
This is what the AE check looks like, inside a Rule, in the XCCDF

```
TODO
```

#### SCAP
##### XCCDF
For `unix.proc_info_v1` artifacts, an XCCDF Check element is generated:

```
    <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    			<check-content-ref
    				href="[BENCHMARK_NAME]"
    				name="oval:org.cisecurity.benchmarks.oracle_mysql_8:def:[ARTIFACT_OVAL_ID]"/>
    		</check>
```

##### OVAL
###### Test

```
<process58_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
			id="oval:org.cisecurity.benchmarks.oracle_mysql_8:tst:[ARTIFACT_OVAL_ID]"
			check_existence="all_exist" check="all"
			comment="[RECOMMENDATION_TITLE]" version="1">
			<object object_ref="oval:org.cisecurity.benchmarks.oracle_mysql_8:obj:[ARTIFACT_OVAL_ID]"/>
			<state state_ref="oval:org.cisecurity.benchmarks.oracle_mysql_8:ste:[ARTIFACT_OVAL_ID]"/>
		</process58_test>
```

###### Object

```
<process58_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
			id="oval:org.cisecurity.benchmarks.oracle_mysql_8:obj:[ARTIFACT_OVAL_ID]"
			comment="[RECOMMENDATION_TITLE]" version="1">
			<command_line operation="pattern match">/usr/sbin/mysqld .*</command_line>
			<pid datatype="int" operation="equals">0</pid>
		</process58_object>
```
###### State

```
	<process58_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
			id="oval:org.cisecurity.benchmarks.oracle_mysql_8:ste:[ARTIFACT_OVAL_ID]"
			comment="[RECOMMENDATION_TITLE]" version="1">
			<user_id datatype="int" operation="equals"
				var_ref="oval:org.cisecurity.benchmarks:var:1000002"/>
		</process58_state>
```

#### YAML

```
artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: unix.proc_info_v1
      parameters:
      - parameter: 
          name: command_line
          type: string
          value: [command_line.value]
      - parameter: 
          name: pid
          type: string
          value: [pid.value]
      - parameter: 
          name: command_line_operation
          type: string
          value: [command_line_operation.value]
      - parameter: 
          name: pid_operation
          type: string
          value: [pid_operation.value]
    test:
      type: [testType name]
      parameters:
      - parameter: 
          name: command_line
          type: string
          value: [command_line.value]
      - parameter: 
          name: cmd_operation
          type: string
          value: [cmd_operation.value]
      - parameter: 
          name: exec_time
          type: string
          value: [exec_time.value]
      - parameter: 
          name: exec_time_operation
          type: string
          value: [exec_time_operation.value]
      - parameter: 
          name: pid
          type: string
          value: [pid.value]
      - parameter: 
          name: pid_operation
          type: string
          value: [pid_operation.value]
      - parameter: 
          name: ppid
          type: string
          value: [ppid.value]
      - parameter: 
          name: ppid_operation
          type: string
          value: [ppid_operation.value]
      - parameter: 
          name: priority
          type: string
          value: [priority.value]
      - parameter: 
          name: priority_operation
          type: string
          value: [priority_operation.value]     
      - parameter: 
          name: ruid_operation
          type: string
          value: [ruid_operation.value]
      - parameter: 
          name: ruid
          type: string
          value: [ruid.value]
      - parameter: 
          name: scheduling_class
          type: string
          value: [scheduling_class.value]
      - parameter: 
          name: scheduling_class_operation
          type: string
          value: [scheduling_class_operation.value]
      - parameter: 
          name: start_time
          type: string
          value: [start_time.value]
      - parameter: 
          name: start_time_operation
          type: string
          value: [start_time_operation.value]
      - parameter: 
          name: tty_operation
          type: string
          value: [tty_operation.value]
      - parameter: 
          name: user_id
          type: string
          value: [user_id.value]     
      - parameter: 
          name: tty
          type: string
          value: [tty.value]
      - parameter: 
          name: user_id_operation
          type: string
          value: [user_id_operation.value]
      - parameter: 
          name: exec_shield
          type: string
          value: [exec_shield.value]
      - parameter: 
          name: exec_shield_operation
          type: string
          value: [exec_shield_operation.value]
      - parameter: 
          name: loginuid
          type: string
          value: [loginuid.value]
      - parameter: 
          name: loginuid_operation
          type: string
          value: [loginuid_operation.value]     
      - parameter: 
          name: posix_capability_operation
          type: string
          value: [posix_capability_operation.value]
      - parameter: 
          name: selinux_domain_label
          type: string
          value: [selinux_domain_label.value]
      - parameter: 
          name: selinux_domain_label_operation
          type: string
          value: [selinux_domain_label_operation.value]
      - parameter: 
          name: session_id
          type: string
          value: [session_id.value]
      - parameter: 
          name: session_id_operation
          type: string
          value: [session_id_operation.value]     
      - parameter: 
          name: posix_capability
          type: string
          value: [posix_capability.value]
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
      "type": "unix.proc_info_v1",
      "parameters": [
        {
          "parameter": {
            "name": "command_line",
            "type": "string",
            "value": [
              "command_line.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "pid",
            "type": "string",
            "value": [
              "pid.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "command_line_operation",
            "type": "string",
            "value": [
              "command_line_operation.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "pid_operation",
            "type": "string",
            "value": [
              "pid_operation.value"
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
            "name": "command_line",
            "type": "string",
            "value": [
              "command_line.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "cmd_operation",
            "type": "string",
            "value": [
              "cmd_operation.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "exec_time",
            "type": "string",
            "value": [
              "exec_time.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "exec_time_operation",
            "type": "string",
            "value": [
              "exec_time_operation.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "pid",
            "type": "string",
            "value": [
              "pid.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "pid_operation",
            "type": "string",
            "value": [
              "pid_operation.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "ppid",
            "type": "string",
            "value": [
              "ppid.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "ppid_operation",
            "type": "string",
            "value": [
              "ppid_operation.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "priority",
            "type": "string",
            "value": [
              "priority.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "priority_operation",
            "type": "string",
            "value": [
              "priority_operation.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "ruid_operation",
            "type": "string",
            "value": [
              "ruid_operation.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "ruid",
            "type": "string",
            "value": [
              "ruid.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "scheduling_class",
            "type": "string",
            "value": [
              "scheduling_class.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "scheduling_class_operation",
            "type": "string",
            "value": [
              "scheduling_class_operation.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "start_time",
            "type": "string",
            "value": [
              "start_time.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "start_time_operation",
            "type": "string",
            "value": [
              "start_time_operation.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "tty_operation",
            "type": "string",
            "value": [
              "tty_operation.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "user_id",
            "type": "string",
            "value": [
              "user_id.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "tty",
            "type": "string",
            "value": [
              "tty.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "user_id_operation",
            "type": "string",
            "value": [
              "user_id_operation.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "exec_shield",
            "type": "string",
            "value": [
              "exec_shield.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "exec_shield_operation",
            "type": "string",
            "value": [
              "exec_shield_operation.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "loginuid",
            "type": "string",
            "value": [
              "loginuid.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "loginuid_operation",
            "type": "string",
            "value": [
              "loginuid_operation.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "posix_capability_operation",
            "type": "string",
            "value": [
              "posix_capability_operation.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "selinux_domain_label",
            "type": "string",
            "value": [
              "selinux_domain_label.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "selinux_domain_label_operation",
            "type": "string",
            "value": [
              "selinux_domain_label_operation.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "session_id",
            "type": "string",
            "value": [
              "session_id.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "session_id_operation",
            "type": "string",
            "value": [
              "session_id_operation.value"
            ]
          }
        },
        {
          "parameter": {
            "name": "posix_capability",
            "type": "string",
            "value": [
              "posix_capability.value"
            ]
          }
        }
      ]
    }
  }
}
```