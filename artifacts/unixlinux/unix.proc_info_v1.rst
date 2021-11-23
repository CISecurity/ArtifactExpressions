Unix: Process Information
==========================

Description
-----------

The Unix: Process Information test is used to check information found in the UNIX processes. It is equivalent to parsing the output of the ps command. 

The process58_object element is used to define the specific process(es) to be evaluated. A process58_object defines the command line used to start the process(es) and pid.

The process58_state element defines the different metadata associate with the UNIX processes.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**unix.proc_info_v1**

+---------------------------------+---------+--------------------------------+
| Name                            | Type    | Description                    |
+=================================+=========+================================+
| command_line                    | string  | The command entity is the      |
|                                 |         | string used to start the       |
|                                 |         | process. This includes any     |
|                                 |         | parameters that are part of    |
|                                 |         | the command line.              |
+---------------------------------+---------+--------------------------------+
| pid                             | string  | The pid entity is the process  |
|                                 |         | ID of the process.             |
+---------------------------------+---------+--------------------------------+
| command_line_operation          | string  | Specifies what operation is to |
|                                 |         | be performed using the Command |
|                                 |         | value.                         |
+---------------------------------+---------+--------------------------------+
| pid_operation                   | string  | Specifies what operation is to |
|                                 |         | be performed using the Process |
|                                 |         | ID value.                      |
+---------------------------------+---------+--------------------------------+

NOTE: ``command_line_operation`` and ``pid_operation`` parameters are governed by a constraint allowing only the following values:
  - bitwise and
  - bitwise or
  - case insensitive equals 
  - case insensitive not equal
  - equals
  - greater than
  - greater than or equal
  - less than
  - less than or equal
  - not equal
  - pattern match 
  - subset of
  - superset of 

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Unix: Process Information

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**unix.proc_info_v1**

+---------------------------------+---------+--------------------------------+
| Name                            | Type    | Description                    |
+=================================+=========+================================+
| command_line                    | string  | This is the string used to     |
|                                 |         | start the process. This        |
|                                 |         | includes any parameters that   |
|                                 |         | are part of thecommand line.   |
+---------------------------------+---------+--------------------------------+
| cmd_operation                   | string  | Specifies what operation is to |
|                                 |         | be performed using the Command |
|                                 |         | value.                         |
+---------------------------------+---------+--------------------------------+
| exec_time                       | string  | This is the cumulative CPU     |
|                                 |         | time, formatted in             |
|                                 |         | [DD-]HH:MM:SS where DD is the  |
|                                 |         | number of days when execution  |
|                                 |         | time is 24 hours or more.      |
+---------------------------------+---------+--------------------------------+
| exec_time_operation             | string  | Specifies what operation is to |
|                                 |         | be performed using the         |
|                                 |         | execution time value.          |
+---------------------------------+---------+--------------------------------+
| pid                             | string  | This is the process ID of the  |
|                                 |         | process.                       |
+---------------------------------+---------+--------------------------------+
| pid_operation                   | string  | Specifies what operation is to |
|                                 |         | be performed using the process |
|                                 |         | ID value.                      |
+---------------------------------+---------+--------------------------------+
| ppid                            | string  | This is the process ID of the  |
|                                 |         | process’s parent process.      |
+---------------------------------+---------+--------------------------------+
| ppid_operation                  | string  | Specifies what operation is to |
|                                 |         | be performed using the parent  |
|                                 |         | process ID value.              |
+---------------------------------+---------+--------------------------------+
| priority                        | int     | This is the scheduling         |
|                                 |         | priority with which the        |
|                                 |         | process runs. This can be      |
|                                 |         | adjusted with the nice         |
|                                 |         | commandor nice() system call.  |
+---------------------------------+---------+--------------------------------+
| priority_operation              | string  | Specifies what operation is to |
|                                 |         | be performed using the process |
|                                 |         | priority value.                |
+---------------------------------+---------+--------------------------------+
| ruid                            | string  | This is the real user id which |
|                                 |         | represents the user who has    |
|                                 |         | created the process.           |
+---------------------------------+---------+--------------------------------+
| ruid_operation                  | string  | Specifies what operation is to |
|                                 |         | be performed using the parent  |
|                                 |         | real user ID value.            |
+---------------------------------+---------+--------------------------------+
| scheduling_class                | string  | A platform specific            |
|                                 |         | characteristic maintained by   |
|                                 |         | the scheduler:                 |
|                                 |         | RT (real-time),                |
|                                 |         | TS (timeshare),                |
|                                 |         | FF (fifo),                     |
|                                 |         | SYS (system), etc.             |
+---------------------------------+---------+--------------------------------+
| scheduling_class_operation      | string  | Specifies what operation is to |
|                                 |         | be performed using the         |
|                                 |         | scheduling class value.        |
+---------------------------------+---------+--------------------------------+
| start_time                      | string  | This is the time of day the    |
|                                 |         | process started formatted in   |
|                                 |         | HH:MM:SS if the same day the   |
|                                 |         | process started or formatted   |
|                                 |         | as MMM_DD (Ex.: Feb_5) if      |
|                                 |         | process started the previous   |
|                                 |         | day or further in the past.    |
+---------------------------------+---------+--------------------------------+
| start_time_operation            | string  | Specifies what operation is to |
|                                 |         | be performed using the process |
|                                 |         | start time value.              |
+---------------------------------+---------+--------------------------------+
| tty                             | string  | This is the TTY on which the   |
|                                 |         | process was started, if        |
|                                 |         | applicable.                    |
+---------------------------------+---------+--------------------------------+
| tty_operation                   | string  | Specifies what operation is to |
|                                 |         | be performed using the process |
|                                 |         | TTY value.                     |
+---------------------------------+---------+--------------------------------+
| user_id                         | string  | This is the effective user id  |
|                                 |         | which represents the actual    |
|                                 |         | privileges of the process.     |
+---------------------------------+---------+--------------------------------+
| user_id_operation               | string  | Specifies what operation is to |
|                                 |         | be performed using the user ID |
|                                 |         | value.                         |
+---------------------------------+---------+--------------------------------+
| exec_shield                     | boolean | A boolean that when true would |
|                                 |         | indicates that ExecShield is   |
|                                 |         | enabled for the process.       |
+---------------------------------+---------+--------------------------------+
| exec_shield_operation           | string  | Specifies what operation is to |
|                                 |         | be performed using the         |
|                                 |         | ExecShield Status value.       |
+---------------------------------+---------+--------------------------------+
| loginuid                        | string  | The loginuid shows which       |
|                                 |         | account a user gained access   |
|                                 |         | to the system with.            |
|                                 |         | The /proc/XXXX/loginuid shows  |
|                                 |         | this value.                    |
+---------------------------------+---------+--------------------------------+
| loginuid_operation              | string  | Specifies what operation is to |
|                                 |         | be performed using the         |
|                                 |         | process’ account value.        |
+---------------------------------+---------+--------------------------------+
| posix_capability_operation      | string  | Specifies what operation is to |
|                                 |         | be performed using the POSIX   |
|                                 |         | capability value.              |
+---------------------------------+---------+--------------------------------+
| selinux_domain_label            | string  | An selinux domain label        |
|                                 |         | associated with the process.   |
+---------------------------------+---------+--------------------------------+
| selinux_domain_label_operation  | string  | Specifies what operation is to |
|                                 |         | be performed using the SELinux |
|                                 |         | domain label value.            |
+---------------------------------+---------+--------------------------------+
| session_id                      | string  | The session ID of the process. |
+---------------------------------+---------+--------------------------------+
| session_id_operation            | string  | Specifies what operation is to |
|                                 |         | be performed using the         |
|                                 |         | process’ session ID value.     |
+---------------------------------+---------+--------------------------------+
| posix_capability                | string  | An effective capability        |
|                                 |         | associated with the process.   |
|                                 |         | See linux/include/linux        |
|                                 |         | /capability.h for more         |
|                                 |         | information.                   |
+---------------------------------+---------+--------------------------------+

:emphasis:`NOTE: The following _operation parameters:`
  +-------------------------------------+------------------------------------+
  | ``cmd_operation``                   | ``exec_time_operation``            |
  +-------------------------------------+------------------------------------+
  | ``pid_operation``                   | ``priority_operation``             |
  +-------------------------------------+------------------------------------+       
  | ``ruid_operation``                  | ``scheduling_class_operation``     |
  +-------------------------------------+------------------------------------+
  | ``start_time_operation``            | ``tty_operation``                  |
  +-------------------------------------+------------------------------------+
  | ``user_id_operation``               | ``exec_shield_operation``          |
  +-------------------------------------+------------------------------------+
  | ``loginuid_operation``              | ``posix_capability_operation``     |
  +-------------------------------------+------------------------------------+
  | ``selinux_domain_label_operation``  | ``session_id_operation``           |
  +-------------------------------------+------------------------------------+
  
  are governed by a constraint allowing only the following values: 
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

:emphasis:`NOTE: The` ``exec_time`` `and` ``start_time`` `parameters are governed by a constraint allowing only values conforming to the following regex pattern:` 
  ``^(([0-9]{0,2}-)?(([0-1][0-9])|([2][0-3])):([0-5][0-9]):([0-5][0-9])){0,1}$``

:emphasis:`NOTE: The following ID parameters:`
  +-------------+--------------+----------------+
  | ``pid``     | ``ppid``     | ``ruid``       |
  +-------------+--------------+----------------+
  | ``user_id`` | ``loginuid`` | ``session_id`` |
  +-------------+--------------+----------------+

  :emphasis:`are governed by a constraint allowing only empty, positive integer, or OVAL Variable ID values conforming to the following regex pattern:` 
    ``^()|([0-9]+|oval:org.cisecurity[A-Za-z0-9_\-\.]+:var:[1-9][0-9]*)$``

NOTE: The ``posix_capability`` parameter is governed by a constraint allowing only the following values:
  - CAP_CHOWN
  - CAP_DAC_OVERRIDE
  - CAP_DAC_READ_SEARCH
  - CAP_FOWNER
  - CAP_FSETID
  - CAP_KILL
  - CAP_SETGID
  - CAP_SETUID
  - CAP_SETPCAP
  - CAP_LINUX_IMMUTABLE
  - CAP_NET_BIND_SERVICE
  - CAP_NET_BROADCAST
  - CAP_NET_ADMIN
  - CAP_NET_RAW
  - CAP_IPC_LOCK
  - CAP_IPC_OWNER
  - CAP_SYS_MODULE
  - CAP_SYS_RAWIO
  - CAP_SYS_CHROOT
  - CAP_SYS_PTRACE
  - CAP_SYS_ADMIN
  - CAP_SYS_BOOT
  - CAP_SYS_NICE
  - CAP_SYS_RESOURCE
  - CAP_SYS_TIME
  - CAP_SYS_TTY_CONFIG
  - CAP_MKNOD
  - CAP_LEASE
  - CAP_AUDIT_WRITE
  - CAP_AUDIT_CONTROL
  - CAP_SETFCAP
  - CAP_MAC_OVERRIDE
  - CAP_MAC_ADMIN
  - CAP_SYS_PACCT
  - CAP_SYSLOG
  - CAP_WAKE_ALARM
  - CAP_BLOCK_SUSPEND
  - CAP_AUDIT_READ

Generated Content
~~~~~~~~~~~~~~~~~

**unix.proc_info_v1**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[RECOMMENDATION-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACT-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="command_line">[command_line.value]</ae:parameter>
            <ae:parameter dt="int" name="pid">[pid.value]</ae:parameter>
            <ae:parameter dt="string" name="command_line_operation">[command_line_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="pid_operation">[pid_operation.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="command_line">[command_line.value]</ae:parameter>
            <ae:parameter dt="string" name="cmd_operation">[cmd_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="exec_time">[exec_time.value]</ae:parameter>
            <ae:parameter dt="string" name="exec_time_operation">[exec_time_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="pid">[pid.value]</ae:parameter>
            <ae:parameter dt="string" name="pid_operation">[pid_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="ppid">[ppid.value]</ae:parameter>
            <ae:parameter dt="string" name="ppid_operation">[ppid_operation.value]</ae:parameter>
            <ae:parameter dt="int" name="priority">[priority.value]</ae:parameter>
            <ae:parameter dt="string" name="priority_operation">[priority_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="ruid">[ruid.value]</ae:parameter>
            <ae:parameter dt="string" name="ruid_operation">[ruid_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="scheduling_class">[scheduling_class.value]</ae:parameter>
            <ae:parameter dt="string" name="scheduling_class_operation">[scheduling_class_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="start_time">[start_time.value]</ae:parameter>
            <ae:parameter dt="string" name="start_time_operation">[start_time_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="tty">[tty.value]</ae:parameter>
            <ae:parameter dt="string" name="tty_operation">[tty_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="user_id">[user_id.value]</ae:parameter>
            <ae:parameter dt="string" name="user_id_operation">[user_id_operation.value]</ae:parameter>
            <ae:parameter dt="boolean" name="exec_shield">[exec_shield.value]</ae:parameter>
            <ae:parameter dt="string" name="exec_shield_operation">[exec_shield_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="loginuid">[loginuid.value]</ae:parameter>
            <ae:parameter dt="string" name="loginuid_operation">[loginuid_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="posix_capability_operation">[posix_capability_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="selinux_domain_label">[selinux_domain_label.value]</ae:parameter>
            <ae:parameter dt="string" name="selinux_domain_label_operation">[selinux_domain_label_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="session_id">[session_id.value]</ae:parameter>
            <ae:parameter dt="string" name="session_id_operation">[session_id_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="posix_capability">[posix_capability.value]</ae:parameter>
          </ae:parameters>
        </ae:test>
        <ae:profiles>
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1" />
        </ae:profiles>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``unix.proc_info_v1`` artifacts, the xccdf:check looks like this. 
There is no Value element in the XCCDF for this Artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-content-ref
      href="[BENCHMARK-TITLE]"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test    

::

  <process58_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="all_exist"
    check="all"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </process58_test>

Object      

::

  <process58_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <command_line operation="[operation.value]">
      [command_line.value]
    </command_line>
    <pid 
      datatype="int" 
      operation="[operation.value]">
      [pid.value]
    </pid>
  </process58_object>

State     

::

  <process58_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <command_line 
      datatype="string"
      operation="[operation.value]">
      [command_line.value]
    </command_line>
    <exec_time 
      datatype="string"
      operation="[operation.value]">
      [exec_time.value]
    </exec_time>
    <pid 
      datatype="int"
      operation="[operation.value]">
      [pid.value]
    </pid>
    <ppid 
      datatype="int"
      operation="[operation.value]">
      [ppid.value]
    </ppid>
    <priority 
      datatype="int"
      operation="[operation.value]">
      [priority.value]
    </priority>
    <ruid 
      datatype="int"
      operation="[operation.value]">
      [ruid.value]
    </ruid>
    <scheduling_class 
      datatype="string"
      operation="[operation.value]">
      [scheduling_class.value]
    </scheduling_class>
    <start_time 
      datatype="string"
      operation="[operation.value]">
      [start_time.value]
    </start_time>
    <tty 
      datatype="string"
      operation="[operation.value]">
      [tty.value]
    </tty>
    <user_id 
      datatype="int"
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]">
      [user_id.value]
    </user_id>
    <exec_shield 
      datatype="boolean"
      operation="[operation.value]">
      [exec_shield.value]
    </exec_shield>
    <loginuid 
      datatype="int"
      operation="[operation.value]">
      [loginuid.value]
    </loginuid>
    <posix_capability 
      datatype="string"
      operation="[operation.value]">
      [posix_capability.value]
    </posix_capability>
    <selinux_domain_label 
      datatype="string"
      operation="[operation.value]">
      [selinux_domain_label.value]
    </selinux_domain_label>
    <session_id 
      datatype="int"
      operation="[operation.value]">
      [session_id.value]
    </session_id>    
  </process58_state>

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact-title: "[RECOMMENDATION-TITLE]"
    artifact:
      type: "[ARTIFACT-TYPE-NAME]"
      parameters:
        - parameter: 
            name: "command_line"
            dt: "string"
            value: "[command_line.value]"
        - parameter: 
            name: "pid"
            dt: "int"
            value: "[pid.value]"
        - parameter: 
            name: "command_line_operation"
            dt: "string"
            value: "[command_line_operation.value]"
        - parameter: 
            name: "pid_operation"
            dt: "string"
            value: "[pid_operation.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter: 
            name: "command_line"
            dt: "string"
            value: "[command_line.value]"
        - parameter: 
            name: "cmd_operation"
            dt: "string"
            value: "[cmd_operation.value]"
        - parameter: 
            name: "exec_time"
            dt: "string"
            value: "[exec_time.value]"
        - parameter: 
            name: "exec_time_operation"
            dt: "string"
            value: "[exec_time_operation.value]"
        - parameter: 
            name: "pid"
            dt: "string"
            value: "[pid.value]"
        - parameter: 
            name: "pid_operation"
            dt: "string"
            value: ["pid_operation.value]"
        - parameter: 
            name: "ppid"
            dt: "string"
            value: "[ppid.value]"
        - parameter: 
            name: "ppid_operation"
            dt: "string"
            value: "[ppid_operation.value]"
        - parameter: 
            name: "priority"
            dt: "int"
            value: "[priority.value]"
        - parameter: 
            name: "priority_operation"
            dt: "string"
            value: "[priority_operation.value]"
        - parameter: 
            name: "ruid_operation"
            dt: "string"
            value: "[ruid_operation.value]"
        - parameter: 
            name: "ruid"
            dt: "string"
            value: "[ruid.value]"
        - parameter: 
            name: "scheduling_class"
            dt: "string"
            value: "[scheduling_class.value]"
        - parameter: 
            name: "scheduling_class_operation"
            dt: "string"
            value: "[scheduling_class_operation.value]"
        - parameter: 
            name: "start_time"
            dt: "string"
            value: "[start_time.value]"
        - parameter: 
            name: "start_time_operation"
            dt: "string"
            value: "[start_time_operation.value]"
        - parameter: 
            name: "tty_operation"
            dt: "string"
            value: "[tty_operation.value]"
        - parameter: 
            name: "user_id"
            dt: "string"
            value: "[user_id.value]"  
        - parameter: 
            name: "tty"
            dt: "string"
            value: "[tty.value]"
        - parameter: 
            name: "user_id_operation"
            dt: "string"
            value: "[user_id_operation.value]"
        - parameter: 
            name: "exec_shield"
            dt: "boolean"
            value: "[exec_shield.value]"
        - parameter: 
            name: "exec_shield_operation"
            dt: "string"
            value: "[exec_shield_operation.value]"
        - parameter: 
            name: "loginuid"
            dt: "string"
            value: "[loginuid.value]"
        - parameter: 
            name: "loginuid_operation"
            dt: "string"
            value: "[loginuid_operation.value]"    
        - parameter: 
            name: "posix_capability_operation"
            dt: "string"
            value: "[posix_capability_operation.value]"
        - parameter: 
            name: "selinux_domain_label"
            dt: "string"
            value: "[selinux_domain_label.value]"
        - parameter: 
            name: "selinux_domain_label_operation"
            dt: "string"
            value: "[selinux_domain_label_operation.value]"
        - parameter: 
            name: "session_id"
            dt: "string"
            value: "[session_id.value]"
        - parameter: 
            name: "session_id_operation"
            dt: "string"
            value: "[session_id_operation.value]"     
        - parameter: 
            name: "posix_capability"
            dt: "string"
            value: "[posix_capability.value]"

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact-title": "[RECOMMENDATION-TITLE]",
      "artifact": {
        "type": "[ARTIFACT-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "command_line",
              "type": "string",
              "value": "[command_line.value]"
            }
          },
          {
            "parameter": {
              "name": "pid",
              "type": "int",
              "value": "[pid.value]"
            }
          },
          {
            "parameter": {
              "name": "command_line_operation",
              "type": "string",
              "value": "[command_line_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "pid_operation",
              "type": "string",
              "value": "[pid_operation.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "command_line",
              "type": "string",
              "value": "[command_line.value]"
            }
          },
          {
            "parameter": {
              "name": "cmd_operation",
              "type": "string",
              "value": "[cmd_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "exec_time",
              "type": "string",
              "value": "[exec_time.value]"
            }
          },
          {
            "parameter": {
              "name": "exec_time_operation",
              "type": "string",
              "value": "[exec_time_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "pid",
              "type": "string",
              "value": "[pid.value]"
            }
          },
          {
            "parameter": {
              "name": "pid_operation",
              "type": "string",
              "value": "[pid_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "ppid",
              "type": "string",
              "value": "[ppid.value]"
            }
          },
          {
            "parameter": {
              "name": "ppid_operation",
              "type": "string",
              "value": "[ppid_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "priority",
              "type": "int",
              "value": "[priority.value]"
            }
          },
          {
            "parameter": {
              "name": "priority_operation",
              "type": "string",
              "value": "[priority_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "ruid_operation",
              "type": "string",
              "value": "[ruid_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "ruid",
              "type": "string",
              "value": "[ruid.value]"
            }
          },
          {
            "parameter": {
              "name": "scheduling_class",
              "type": "string",
              "value": "[scheduling_class.value]"
            }
          },
          {
            "parameter": {
              "name": "scheduling_class_operation",
              "type": "string",
              "value": "[scheduling_class_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "start_time",
              "type": "string",
              "value": "[start_time.value]"
            }
          },
          {
            "parameter": {
              "name": "start_time_operation",
              "type": "string",
              "value": "[start_time_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "tty_operation",
              "type": "string",
              "value": "[tty_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "user_id",
              "type": "string",
              "value": "[user_id.value]"
            }
          },
          {
            "parameter": {
              "name": "tty",
              "type": "string",
              "value": "[tty.value]"
            }
          },
          {
            "parameter": {
              "name": "user_id_operation",
              "type": "string",
              "value": "[user_id_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "exec_shield",
              "type": "boolean",
              "value": "[exec_shield.value]"
            }
          },
          {
            "parameter": {
              "name": "exec_shield_operation",
              "type": "string",
              "value": "[exec_shield_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "loginuid",
              "type": "string",
              "value": "[loginuid.value]"
            }
          },
          {
            "parameter": {
              "name": "loginuid_operation",
              "type": "string",
              "value": "[loginuid_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "posix_capability_operation",
              "type": "string",
              "value": "[posix_capability_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "selinux_domain_label",
              "type": "string",
              "value": "[selinux_domain_label.value]"
            }
          },
          {
            "parameter": {
              "name": "selinux_domain_label_operation",
              "type": "string",
              "value": "[selinux_domain_label_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "session_id",
              "type": "string",
              "value": "[session_id.value]"
            }
          },
          {
            "parameter": {
              "name": "session_id_operation",
              "type": "string",
              "value": "[session_id_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "posix_capability",
              "type": "string",
              "value": "[posix_capability.value]"
            }
          }
        ]
      }
    }
  }