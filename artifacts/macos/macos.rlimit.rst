macos:rlimit
=================

Description
-----------

The macos:rlimit test is used to check system resource limits for launchd. 

The rlimit_object element is a singleton used to access resource limit information.

The rlimit_state element specifies the system setup elements to check.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**macos.rlimit**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| check_existence             | string  | Defines how many items should be   |
|                             |         | collected.                         |
+-----------------------------+---------+------------------------------------+

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_satisfy
  - none_exist
  - only_one_exists

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - macos:rlimit

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**macos.rlimit**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| check                       | string  | Defines how many collected items   |
|                             |         | must match the expected state.     |
+-----------------------------+---------+------------------------------------+
| datatype                    | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| operation                   | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+
| cpu_current                 | integer | The maximum amount of cpu time (in | 
|                             |         | seconds) to be used by each        |
|                             |         | process. Cannot be blank.          |
+-----------------------------+---------+------------------------------------+
| cpu_max                     | integer | CPU hard limit. Cannot be blank.   |
+-----------------------------+---------+------------------------------------+
| filesize_current            | integer | The largest size (in bytes) file   |
|                             |         | that may be created. Cannot be     |
|                             |         | blank.                             |
+-----------------------------+---------+------------------------------------+
| filesize_max                | integer | Filesize hard limit. Cannot be     |
|                             |         | blank.                             |
+-----------------------------+---------+------------------------------------+
| data_current                | integer | The maximum size (in bytes) of the |
|                             |         | data segment for a process; this   |
|                             |         | defines how far a program may      |
|                             |         | extend its break with the sbrk(2)  |
|                             |         | system call. Cannot be blank.      |
+-----------------------------+---------+------------------------------------+
| data_max                    | integer | Data hard limit. Cannot be blank.  |
+-----------------------------+---------+------------------------------------+
| stack_current               | integer | The maximum size (in bytes) of the |
|                             |         | stack segment for a process; this  |
|                             |         | defines how far a program's stack  |
|                             |         | segment may be extended. Stack     |
|                             |         | extension is performed             |
|                             |         | automatically by the system.       |
|                             |         | Cannot be blank.                   |
+-----------------------------+---------+------------------------------------+
| stack_max                   | integer | Stack hard limit. Cannot be blank. |
+-----------------------------+---------+------------------------------------+
| core_current                | integer | The largest size (in bytes) core   |
|                             |         | file that may be created. Cannot   |
|                             |         | be blank.                          |
+-----------------------------+---------+------------------------------------+
| core_max                    | integer | Core hard limit. Cannot be blank.  |
+-----------------------------+---------+------------------------------------+
| rss_current                 | integer | The maximum size (in bytes) to     |
|                             |         | which a process's resident set     |
|                             |         | size may grow. This imposes a      |
|                             |         | limit on the amount of physical    |
|                             |         | memory to be given to a process;   |
|                             |         | if memory is tight, the system     |
|                             |         | will prefer to take memory from    |
|                             |         | processes that are exceeding their |
|                             |         | declared resident set size.        |
|                             |         | Cannot be blank.                   |
+-----------------------------+---------+------------------------------------+
| rss_max                     | integer | RSS hard limit. Cannot be blank.   |
+-----------------------------+---------+------------------------------------+
| memlock_current             | integer | The maximum size (in bytes) which  |
|                             |         | a process may lock into memory     |
|                             |         | using the mlock(2) function.       |
|                             |         | Cannot be blank.                   |
+-----------------------------+---------+------------------------------------+
| memlock_max                 | integer | Memlock hard limit. Cannot be      |
|                             |         | blank.                             |
+-----------------------------+---------+------------------------------------+
| maxproc_current             | string  | The maximum number of simultaneous |
|                             |         | processes for this user id.        |
|                             |         | Cannot be blank.                   |
+-----------------------------+---------+------------------------------------+
| maxproc_max                 | integer | Maxproc hard limit. Cannot be      |
|                             |         | blank.                             |
+-----------------------------+---------+------------------------------------+
| maxfiles_current            | integer | The maximum number of open files   |
|                             |         | for this process. Cannot be blank. | 
+-----------------------------+---------+------------------------------------+
| maxfiles_max                | integer | Maxfiles hard limit. Cannot be     |
|                             |         | blank.                             |
+-----------------------------+---------+------------------------------------+

NOTE: The ``check`` parameter is governed by a constraint allowing only the following values:
  - all
  - at least one
  - none satisfy
  - only one

NOTE: The ``operation`` parameter is governed by a constraint allowing only the following values:
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

NOTE: The ``datatype`` parameter is governed by a constraint allowing only the following values:
  - boolean
  - float
  - int
  - string
  - version
  - set

Generated Content
~~~~~~~~~~~~~~~~~

**macos.rlimit**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[ARTIFACT-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACT-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
            <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
            <ae:parameter dt="integer" name="cpu_current">[cpu_current.value]</ae:parameter>
            <ae:parameter dt="integer" name="cpu_max">[cpu_max.value]</ae:parameter>
            <ae:parameter dt="integer" name="filesize_current">[filesize_current.value]</ae:parameter>
            <ae:parameter dt="integer" name="filesize_max">[filesize_max.value]</ae:parameter>
            <ae:parameter dt="integer" name="data_current">[data_current.value]</ae:parameter>
            <ae:parameter dt="integer" name="data_max">[data_max.value]</ae:parameter>
            <ae:parameter dt="integer" name="stack_current">[stack_current.value]</ae:parameter>
            <ae:parameter dt="integer" name="stack_max">[stack_max.value]</ae:parameter>
            <ae:parameter dt="integer" name="core_current">[core_current.value]</ae:parameter>
            <ae:parameter dt="integer" name="core_max">[core_max.value]</ae:parameter>
            <ae:parameter dt="integer" name="rss_current">[rss_current.value]</ae:parameter>
            <ae:parameter dt="integer" name="rss_max">[rss_max.value]</ae:parameter>
            <ae:parameter dt="integer" name="memlock_current">[memlock_current.value]</ae:parameter>
            <ae:parameter dt="integer" name="memlock_max">[memlock_max.value]</ae:parameter>
            <ae:parameter dt="integer" name="maxproc_current">[maxproc_current.value]</ae:parameter>
            <ae:parameter dt="integer" name="maxproc_max">[maxproc_max.value]</ae:parameter>
            <ae:parameter dt="integer" name="maxfiles_current">[maxfiles_current.value]</ae:parameter>
            <ae:parameter dt="integer" name="maxfiles_max">[maxfiles_max.value]</ae:parameter>
          </ae:parameters>
        </ae:test>
        <ae:profiles>
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_1" />
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_2" />
        </ae:profiles>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``macos.accountinfo_v1`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

::

  <xccdf:check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <xccdf:check-content-ref
      href="[BENCHMARK-TITLE]"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </xccdf:check>

OVAL
''''

Test

::

  <rlimit_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[ARTIFACT-TTILE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </rlimit_test>

Object

::

  <rlimit_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TTILE]"
    version="1" />

State

::

  <rlimit_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TTILE]"
    version="1">
    <cpu_current 
      datatype="int"
      operation="[operation.value]">
        [cpu_current.value]
    </cpu_current>
    <cpu_max 
      datatype="int"
      operation="[operation.value]">
        [cpu_max.value]
    </cpu_max>
    <filesize_current 
      datatype="int"
      operation="equals">
      [filesize_current.value]
    </filesize_current>
    <filesize_max
      datatype="int"
      operation="equals">
      [filesize_max.value]
    </filesize_max>
    <data_current 
      datatype="int"
      operation="[operation.value]">
      [data_current.value]
    </data_current>
    <data_max
      datatype="int"
      operation="[operation.value]">
        [data_max.value]
    </data_max>
    <stack_current 
      datatype="int"
      operation="[operation.value]">
        [stack_current.value]
    </stack_current>
    <stack_max 
      datatype="int"
      operation="[operation.value]">
        [stack_max.value]
    </stack_max>
    <core_current 
      datatype="int"
      operation="[operation.value]">
        [core_current.value]
    </core_current>
    <core_max 
      datatype="int"
      operation="equals">
      [core_max.value]
    </core_max>
    <rss_current
      datatype="int"
      operation="equals">
      [rss_current.value]
    </rss_current>
    <rss_max 
      datatype="int"
      operation="[operation.value]">
      [rss_max.value]
    </rss_max>
    <memlock_current
      datatype="int"
      operation="[operation.value]">
        [memlock_current.value]
    </memlock_current>
    <memlock_max 
      datatype="int"
      operation="[operation.value]">
        [memlock_max.value]
    </memlock_max>
    <maxproc_current 
      datatype="int"
      operation="[operation.value]">
        [maxproc_current.value]
    </maxproc_current>
    <maxproc_max 
      datatype="int"
      operation="[operation.value]">
        [maxproc_max.value]
    </maxproc_max>
    <maxfiles_current 
      datatype="int"
      operation="equals">
      [maxfiles_current.value]
    </maxfiles_current>
    <maxfiles_max
      datatype="int"
      operation="equals">
      [maxfiles_max.value]
    </maxfiles_max>
 
YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact-title: "[ARTIFACT-TITLE]"
    artifact:
      type: "[ARTIFACT-TYPE-NAME]"
        parameters:
          - parameter:
              name: "check_existence"
              dt: "string"
              value: "[check_existence.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name="check"
            dt: "string"
            value: "[check.value]"
        - parameter:
            name="operation"
            dt: "string"
            value: "[operation.value]"
        - parameter:
            name="datatype"
            dt: "string"
            value: "[datatype.value]"
        - parameter:
            name="cpu_current"
            dt: "integer"
            value: "[cpu_current.value]"
        - parameter:
            name="cpu_max"
            dt: "integer"
            value: "[cpu_max.value]"
        - parameter:
            name="filesize_current"
            dt: "integer"
            value: "[filesize_current.value]"
        - parameter:
            name="filesize_max"
            dt: "integer"
            value: "[filesize_max.value]"
        - parameter:
            name="data_current"
            dt: "integer"
            value: "[data_current.value]"
        - parameter:
            name="data_max"
            dt: "integer"
            value: "[data_max.value]"
        - parameter:
            name="stack_current"
            dt: "integer"
            value: "[stack_current.value]"
        - parameter:
            name="stack_max"
            dt: "integer"
            value: "[stack_max.value]"
        - parameter:
            name="core_current"
            dt: "integer"
            value: "[core_current.value]"
        - parameter:
            name="core_max"
            dt: "integer"
            value: "[core_max.value]"
        - parameter:
            name="rss_current"
            dt: "integer"
            value: "[rss_current.value]"
        - parameter:
            name="rss_max"
            dt: "integer"
            value: "[rss_max.value]"
        - parameter:
            name="memlock_current"
            dt: "integer"
            value: "[memlock_current.value]"
        - parameter:
            name="memlock_max"
            dt: "integer"
            value: "[memlock_max.value]"
        - parameter:
            name="maxproc_current"
            dt: "integer"
            value: "[maxproc_current.value]"
        - parameter:
            name="maxproc_max"
            dt: "integer"
            value: "[maxproc_max.value]"
        - parameter:
            name="maxfiles_current"
            dt: "integer"
            value: "[maxfiles_current.value]"
        - parameter:
            name="maxfiles_max"
            dt: "integer"
            value: "[maxfiles_max.value]"

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact-title": "[ARTIFACT-TITLE]",
      "artifact": {
        "type": "[ARTIFACT-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "check",
              "dt": "string",
              "value": "[check.value]"
            }
          },
          {
            "parameter": {
              "name": "operation",
              "dt": "string",
              "value": "[operation.value]"
            }
          },
          {
            "parameter": {
              "name": "datatype",
              "dt": "string",
              "value": "[datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "cpu_current",
              "dt": "integer",
              "value": "[cpu_current.value]"
            }
          },
          {
            "parameter": {
              "name": "cpu_max",
              "dt": "integer",
              "value": "[cpu_max.value]"
            }
          },
          {
            "parameter": {
              "name": "filesize_current",
              "dt": "integer",
              "value": "[filesize_current.value]"
            }
          },
          {
            "parameter": {
              "name": "filesize_max",
              "dt": "integer",
              "value": "[filesize_max.value]"
            }
          },
          {
            "parameter": {
              "name": "data_current",
              "dt": "integer",
              "value": "[data_current.value]"
            }
          },
          {
            "parameter": {
              "name": "data_max",
              "dt": "integer",
              "value": "[data_max.value]"
            }
          },
          {
            "parameter": {
              "name": "stack_current",
              "dt": "integer",
              "value": "[stack_current.value]"
            }
          },
          {
            "parameter": {
              "name": "stack_max",
              "dt": "integer",
              "value": "[stack_max.value]"
            }
          },
          {
            "parameter": {
              "name": "core_current",
              "dt": "integer",
              "value": "[core_current.value]"
            }
          },
          {
            "parameter": {
              "name": "core_max",
              "dt": "integer",
              "value": "[core_max.value]"
            }
          },
          {
            "parameter": {
              "name": "rss_current",
              "dt": "integer",
              "value": "[rss_current.value]"
            }
          },
          {
            "parameter": {
              "name": "rss_max",
              "dt": "integer",
              "value": "[rss_max.value]"
            }
          },
          {
            "parameter": {
              "name": "memlock_current",
              "dt": "integer",
              "value": "[memlock_current.value]"
            }
          },
          {
            "parameter": {
              "name": "memlock_max",
              "dt": "integer",
              "value": "[memlock_max.value]"
            }
          },
          {
            "parameter": {
              "name": "maxproc_current",
              "dt": "integer",
              "value": "[maxproc_current.value]"
            }
          },
          {
            "parameter": {
              "name": "maxproc_max",
              "dt": "integer",
              "value": "[maxproc_max.value]"
            }
          },
          {
            "parameter": {
              "name": "maxfiles_current",
              "dt": "integer",
              "value": "[maxfiles_current.value]"
            }
          },
          {
            "parameter": {
              "name": "maxfiles_max",
              "dt": "integer",
              "value": "[maxfiles_max.value]"
            }
          }
        ]
      }
    }
  }