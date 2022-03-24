macos:rlimit
============

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
| cpu_current                 | integer | The maximum amount of cpu time (in | 
|                             |         | seconds) to be used by each        |
|                             |         | process. Cannot be blank.          |
+-----------------------------+---------+------------------------------------+
| cpu_current_datatype        | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| cpu_current_operation       | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+
| cpu_max                     | integer | CPU hard limit. Cannot be blank.   |
+-----------------------------+---------+------------------------------------+
| cpu_max_datatype            | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| cpu_max_operation           | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+
| filesize_current            | integer | The largest size (in bytes) file   |
|                             |         | that may be created. Cannot be     |
|                             |         | blank.                             |
+-----------------------------+---------+------------------------------------+
| filesize_current_datatype   | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| filesize_current_operation  | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+
| filesize_max                | integer | Filesize hard limit. Cannot be     |
|                             |         | blank.                             |
+-----------------------------+---------+------------------------------------+
| filesize_max_datatype       | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| filesize_max_operation      | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+
| data_current                | integer | The maximum size (in bytes) of the |
|                             |         | data segment for a process; this   |
|                             |         | defines how far a program may      |
|                             |         | extend its break with the sbrk(2)  |
|                             |         | system call. Cannot be blank.      |
+-----------------------------+---------+------------------------------------+
| data_current_datatype       | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| data_current_operation      | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+
| data_max                    | integer | Data hard limit. Cannot be blank.  |
+-----------------------------+---------+------------------------------------+
| data_max_datatype           | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| data_max_operation          | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+
| stack_current               | integer | The maximum size (in bytes) of the |
|                             |         | stack segment for a process; this  |
|                             |         | defines how far a program's stack  |
|                             |         | segment may be extended. Stack     |
|                             |         | extension is performed             |
|                             |         | automatically by the system.       |
|                             |         | Cannot be blank.                   |
+-----------------------------+---------+------------------------------------+
| stack_current_datatype      | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| stack_current_operation     | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+
| stack_max                   | integer | Stack hard limit. Cannot be blank. |
+-----------------------------+---------+------------------------------------+
| stack_max_datatype          | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| stack_max_operation         | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+
| core_current                | integer | The largest size (in bytes) core   |
|                             |         | file that may be created. Cannot   |
|                             |         | be blank.                          |
+-----------------------------+---------+------------------------------------+
| core_current_datatype       | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| core_current_operation      | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+
| core_max                    | integer | Core hard limit. Cannot be blank.  |
+-----------------------------+---------+------------------------------------+
| core_max_datatype           | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| core_max_operation          | string  | Comparison operation.              |
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
| rss_current_datatype        | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| rss_current_operation       | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+
| rss_max                     | integer | RSS hard limit. Cannot be blank.   |
+-----------------------------+---------+------------------------------------+
| rss_max_datatype            | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| rss_max_operation           | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+
| memlock_current             | integer | The maximum size (in bytes) which  |
|                             |         | a process may lock into memory     |
|                             |         | using the mlock(2) function.       |
|                             |         | Cannot be blank.                   |
+-----------------------------+---------+------------------------------------+
| memlock_current_datatype    | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| memlock_current_operation   | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+
| memlock_max                 | integer | Memlock hard limit. Cannot be      |
|                             |         | blank.                             |
+-----------------------------+---------+------------------------------------+
| memlock_max_datatype        | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| memlock_max_operation       | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+
| maxproc_current             | string  | The maximum number of simultaneous |
|                             |         | processes for this user id.        |
|                             |         | Cannot be blank.                   |
+-----------------------------+---------+------------------------------------+
| maxproc_current_datatype    | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| maxproc_current_operation   | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+
| maxproc_max                 | integer | Maxproc hard limit. Cannot be      |
|                             |         | blank.                             |
+-----------------------------+---------+------------------------------------+
| maxproc_max_datatype        | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| maxproc_max_operation       | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+
| maxfiles_current            | integer | The maximum number of open files   |
|                             |         | for this process. Cannot be blank. | 
+-----------------------------+---------+------------------------------------+
| maxfiles_current_datatype   | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| maxfiles_current_operation  | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+
| maxfiles_max                | integer | Maxfiles hard limit. Cannot be     |
|                             |         | blank.                             |
+-----------------------------+---------+------------------------------------+
| maxfiles_max_datatype       | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| maxfiles_max_operation      | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+

NOTE: The ``check`` parameter is governed by a constraint allowing only the following values:
  - all
  - at least one
  - none satisfy
  - only one

:strong:`NOTE: The following parameters:`
  +--------------------------------------------+--------------------------------------------+
  | ``cpu_current_operation``                  | ``cpu_max_operation``                      |
  +--------------------------------------------+--------------------------------------------+
  | ``filesize_current_operation``             | ``filesize_max_operation``                 |
  +--------------------------------------------+--------------------------------------------+
  | ``data_current_operation``                 | ``data_max_operation``                     |
  +--------------------------------------------+--------------------------------------------+
  | ``stack_current_operation``                | ``stack_max_operation``                    |
  +--------------------------------------------+--------------------------------------------+
  | ``core_current_operation``                 | ``core_max_operation``                     |
  +--------------------------------------------+--------------------------------------------+
  | ``rss_current_operation``                  | ``rss_max_operation``                      |
  +--------------------------------------------+--------------------------------------------+
  | ``memlock_current_operation``              | ``memlock_max_operation``                  |
  +--------------------------------------------+--------------------------------------------+
  | ``maxproc_current_operation``              | ``maxproc_max_operation``                  |
  +--------------------------------------------+--------------------------------------------+
  | ``maxfiles_current_operation``             | ``maxfiles_max_operation``                 |
  +--------------------------------------------+--------------------------------------------+
  are governed by a constraint allowing only the following values:
    -  equals
    -  not equal
    -  case insensitive equals
    -  case insensitive not equal
    -  greater than
    -  less than
    -  greater than or equal
    -  less than or equal
    -  bitwise and
    -  bitwise or
    -  pattern match
    -  subset of
    -  superset of

:strong:`NOTE: The following parameters:`
  +-------------------------------------------+-------------------------------------------+
  | ``cpu_current_datatype``                  | ``cpu_max_datatype``                      |
  +-------------------------------------------+-------------------------------------------+
  | ``filesize_current_datatype``             | ``filesize_max_datatype``                 |
  +-------------------------------------------+-------------------------------------------+
  | ``data_current_datatype``                 | ``data_max_datatype``                     |
  +-------------------------------------------+-------------------------------------------+
  | ``stack_current_datatype``                | ``stack_max_datatype``                    |
  +-------------------------------------------+-------------------------------------------+
  | ``core_current_datatype``                 | ``core_max_datatype``                     |
  +-------------------------------------------+-------------------------------------------+
  | ``rss_current_datatype``                  | ``rss_max_datatype``                      |
  +-------------------------------------------+-------------------------------------------+
  | ``memlock_current_datatype``              | ``memlock_max_datatype``                  |
  +-------------------------------------------+-------------------------------------------+
  | ``maxproc_current_datatype``              | ``maxproc_max_datatype``                  |
  +-------------------------------------------+-------------------------------------------+
  | ``maxfiles_current_datatype``             | ``maxfiles_max_datatype``                 |
  +-------------------------------------------+-------------------------------------------+
  are governed by a constraint allowing only the following values:
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
            <ae:parameter dt="integer" name="cpu_current">[cpu_current.value]</ae:parameter>
            <ae:parameter dt="string"  name="cpu_current_operation">[cpu_current_operation.value]</ae:parameter>
            <ae:parameter dt="string"  name="cpu_current_datatype">[cpu_current_datatype.value]</ae:parameter>
            <ae:parameter dt="integer" name="cpu_max">[cpu_max.value]</ae:parameter>
            <ae:parameter dt="string"  name="cpu_max_operation">[cpu_max_operation.value]</ae:parameter>
            <ae:parameter dt="string"  name="cpu_max_datatype">[cpu_max_datatype.value]</ae:parameter>
            <ae:parameter dt="integer" name="filesize_current">[filesize_current.value]</ae:parameter>
            <ae:parameter dt="string"  name="filesize_current_operation">[filesize_current_operation.value]</ae:parameter>
            <ae:parameter dt="string"  name="filesize_current_datatype">[filesize_current_datatype.value]</ae:parameter>
            <ae:parameter dt="integer" name="filesize_max">[filesize_max.value]</ae:parameter>
            <ae:parameter dt="string"  name="filesize_max_operation">[filesize_max_operation.value]</ae:parameter>
            <ae:parameter dt="string"  name="filesize_max_datatype">[filesize_max_datatype.value]</ae:parameter>
            <ae:parameter dt="integer" name="data_current">[data_current.value]</ae:parameter>
            <ae:parameter dt="string"  name="data_current_operation">[data_current_operation.value]</ae:parameter>
            <ae:parameter dt="string"  name="data_current_datatype">[data_current_datatype.value]</ae:parameter>
            <ae:parameter dt="integer" name="data_max">[data_max.value]</ae:parameter>
            <ae:parameter dt="string"  name="data_max_operation">[data_max_operation.value]</ae:parameter>
            <ae:parameter dt="string"  name="data_max_datatype">[data_max_datatype.value]</ae:parameter>
            <ae:parameter dt="integer" name="stack_current">[stack_current.value]</ae:parameter>
            <ae:parameter dt="string"  name="stack_current_operation">[stack_current_operation.value]</ae:parameter>
            <ae:parameter dt="string"  name="stack_current_datatype">[stack_current_datatype.value]</ae:parameter>
            <ae:parameter dt="integer" name="stack_max">[stack_max.value]</ae:parameter>
            <ae:parameter dt="string"  name="stack_max_operation">[stack_max_operation.value]</ae:parameter>
            <ae:parameter dt="string"  name="stack_max_datatype">[stack_max_datatype.value]</ae:parameter>
            <ae:parameter dt="integer" name="core_current">[core_current.value]</ae:parameter>
            <ae:parameter dt="string"  name="core_current_operation">[core_current_operation.value]</ae:parameter>
            <ae:parameter dt="string"  name="core_current_datatype">[core_current_datatype.value]</ae:parameter>
            <ae:parameter dt="integer" name="core_max">[core_max.value]</ae:parameter>
            <ae:parameter dt="string"  name="core_max_operation">[core_max_operation.value]</ae:parameter>
            <ae:parameter dt="string"  name="core_max_datatype">[core_max_datatype.value]</ae:parameter>
            <ae:parameter dt="integer" name="rss_current">[rss_current.value]</ae:parameter>
            <ae:parameter dt="string"  name="rss_current_operation">[rss_current_operation.value]</ae:parameter>
            <ae:parameter dt="string"  name="rss_current_datatype">[rss_current_datatype.value]</ae:parameter>
            <ae:parameter dt="integer" name="rss_max">[rss_max.value]</ae:parameter>
            <ae:parameter dt="string"  name="rss_max_operation">[rss_max_operation.value]</ae:parameter>
            <ae:parameter dt="string"  name="rss_max_datatype">[rss_max_datatype.value]</ae:parameter>
            <ae:parameter dt="integer" name="memlock_current">[memlock_current.value]</ae:parameter>
            <ae:parameter dt="string"  name="memlock_current_operation">[memlock_current_operation.value]</ae:parameter>
            <ae:parameter dt="string"  name="memlock_current_datatype">[memlock_current_datatype.value]</ae:parameter>
            <ae:parameter dt="integer" name="memlock_max">[memlock_max.value]</ae:parameter>
            <ae:parameter dt="string"  name="memlock_max_operation">[memlock_max_operation.value]</ae:parameter>
            <ae:parameter dt="string"  name="memlock_max_datatype">[memlock_max_datatype.value]</ae:parameter>
            <ae:parameter dt="integer" name="maxproc_current">[maxproc_current.value]</ae:parameter>
            <ae:parameter dt="string"  name="maxproc_current_operation">[maxproc_current_operation.value]</ae:parameter>
            <ae:parameter dt="string"  name="maxproc_current_datatype">[maxproc_current_datatype.value]</ae:parameter>
            <ae:parameter dt="integer" name="maxproc_max">[maxproc_max.value]</ae:parameter>
            <ae:parameter dt="string"  name="maxproc_max_operation">[maxproc_max_operation.value]</ae:parameter>
            <ae:parameter dt="string"  name="maxproc_max_datatype">[maxproc_max_datatype.value]</ae:parameter>
            <ae:parameter dt="integer" name="maxfiles_current">[maxfiles_current.value]</ae:parameter>
            <ae:parameter dt="string"  name="maxfiles_current_operation">[maxfiles_current_operation.value]</ae:parameter>
            <ae:parameter dt="string"  name="maxfiles_current_datatype">[maxfiles_current_datatype.value]</ae:parameter>
            <ae:parameter dt="integer" name="maxfiles_max">[maxfiles_max.value]</ae:parameter>
            <ae:parameter dt="string"  name="maxfiles_max_operation">[maxfiles_max_operation.value]</ae:parameter>
            <ae:parameter dt="string"  name="maxfiles_max_datatype">[maxfiles_max_datatype.value]</ae:parameter>
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

For ``macos.rlimit`` ``macos.rlimit`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <xccdf:check-content-ref
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

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
      datatype="[cpu_current_datatype.value]"
      operation="[cpu_current_operation.value]">
        [cpu_current.value]
    </cpu_current>
    <cpu_max 
      datatype="[cpu_max_datatype.value]"
      operation="[cpu_max_operation.value]">
        [cpu_max.value]
    </cpu_max>
    <filesize_current 
      datatype="[filesize_current_datatype.value]"
      operation="[filesize_current_operation.value]">
        [filesize_current.value]
    </filesize_current>
    <filesize_max
      datatype="[filesize_max_datatype.value]"
      operation="[filesize_max_operation.value]">
        [filesize_max.value]
    </filesize_max>
    <data_current 
      datatype="[data_current_datatype.value]"
      operation="[data_current_operation.value]">
        [data_current.value]
    </data_current>
    <data_max
      datatype="[data_max_datatype.value]"
      operation="[data_max_operation.value]">
        [data_max.value]
    </data_max>
    <stack_current 
      datatype="[stack_current_datatype.value]"
      operation="[stack_current_operation.value]">
        [stack_current.value]
    </stack_current>
    <stack_max 
      datatype="[stack_max_datatype.value]"
      operation="[stack_max_operation.value]">
        [stack_max.value]
    </stack_max>
    <core_current 
      datatype="[core_current_datatype.value]"
      operation="[core_current_operation.value]">
        [core_current.value]
    </core_current>
    <core_max 
      datatype="[core_max_datatype.value]"
      operation="[core_max_operation.value]">
        [core_max.value]
    </core_max>
    <rss_current
      datatype="[rss_current_datatype.value]"
      operation="[rss_current_operation.value]">
        [rss_current.value]
    </rss_current>
    <rss_max 
      datatype="[rss_max_datatype.value]"
      operation="[rss_max_operation.value]">
        [rss_max.value]
    </rss_max>
    <memlock_current
      datatype="[memlock_current_datatype.value]"
      operation="[memlock_current_operation.value]">
        [memlock_current.value]
    </memlock_current>
    <memlock_max 
      datatype="[memlock_max_datatype.value]"
      operation="[memlock_max_operation.value]">
        [memlock_max.value]
    </memlock_max>
    <maxproc_current 
      datatype="[maxproc_current_datatype.value]"
      operation="[maxproc_current_operation.value]">
        [maxproc_current.value]
    </maxproc_current>
    <maxproc_max 
      datatype="[maxproc_max_datatype.value]"
      operation="[maxproc_max_operation.value]">
        [maxproc_max.value]
    </maxproc_max>
    <maxfiles_current 
      datatype="[maxfiles_current_datatype.value]"
      operation="[maxfiles_current_operation.value]">
        [maxfiles_current.value]
    </maxfiles_current>
    <maxfiles_max
      datatype="[maxfiles_max_datatype.value]"
      operation="[maxfiles_max_operation.value]">
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
            name="cpu_current"
            dt: "integer"
            value: "[cpu_current.value]"
        - parameter:
            name="cpu_current_datatype"
            dt: "string"
            value: "[cpu_current_datatype.value]"
        - parameter:
            name="cpu_current_operation"
            dt: "string"
            value: "[cpu_current_operation.value]"
        - parameter:
            name="cpu_max"
            dt: "integer"
            value: "[cpu_max.value]"
        - parameter:
            name="cpu_max_datatype"
            dt: "string"
            value: "[cpu_max_datatype.value]"
        - parameter:
            name="cpu_max_operation"
            dt: "string"
            value: "[cpu_max_operation.value]"
        - parameter:
            name="filesize_current"
            dt: "integer"
            value: "[filesize_current.value]"
        - parameter:
            name="filesize_current_datatype"
            dt: "string"
            value: "[filesize_current_datatype.value]"
        - parameter:
            name="filesize_current_operation"
            dt: "string"
            value: "[filesize_current_operation.value]"
        - parameter:
            name="filesize_max"
            dt: "integer"
            value: "[filesize_max.value]"
        - parameter:
            name="filesize_max_datatype"
            dt: "string"
            value: "[filesize_max_datatype.value]"
        - parameter:
            name="filesize_max_operation"
            dt: "string"
            value: "[filesize_max_operation.value]"
        - parameter:
            name="data_current"
            dt: "integer"
            value: "[data_current.value]"
        - parameter:
            name="data_current_operation"
            dt: "string"
            value: "[data_current_operation.value]"
        - parameter:
            name="data_current_datatype"
            dt: "string"
            value: "[data_current_datatype.value]"
        - parameter:
            name="data_max"
            dt: "integer"
            value: "[data_max.value]"
        - parameter:
            name="data_max_datatype"
            dt: "string"
            value: "[data_max_datatype.value]"
        - parameter:
            name="data_max_operation"
            dt: "string"
            value: "[data_max_operation.value]"
        - parameter:
            name="stack_current"
            dt: "integer"
            value: "[stack_current.value]"
        - parameter:
            name="stack_current_datatype"
            dt: "string"
            value: "[stack_current_datatype.value]"
        - parameter:
            name="stack_current_operation"
            dt: "string"
            value: "[stack_current_operation.value]"
        - parameter:
            name="stack_max"
            dt: "integer"
            value: "[stack_max.value]"
        - parameter:
            name="stack_max_datatype"
            dt: "string"
            value: "[stack_max_datatype.value]"
        - parameter:
            name="stack_max_operation"
            dt: "string"
            value: "[stack_max_operation.value]"
        - parameter:
            name="core_current"
            dt: "integer"
            value: "[core_current.value]"
        - parameter:
            name="core_current_datatype"
            dt: "string"
            value: "[core_current_datatype.value]"
        - parameter:
            name="core_current_operation"
            dt: "string"
            value: "[core_current_operation.value]"
        - parameter:
            name="core_max"
            dt: "integer"
            value: "[core_max.value]"
        - parameter:
            name="core_max_datatype"
            dt: "string"
            value: "[core_max_datatype.value]"
        - parameter:
            name="core_max_operation"
            dt: "string"
            value: "[core_max_operation.value]"
        - parameter:
            name="rss_current"
            dt: "integer"
            value: "[rss_current.value]"
        - parameter:
            name="rss_current_datatype"
            dt: "string"
            value: "[rss_current_datatype.value]"
        - parameter:
            name="rss_current_operation"
            dt: "string"
            value: "[rss_current_operation.value]"
        - parameter:
            name="rss_max"
            dt: "integer"
            value: "[rss_max.value]"
        - parameter:
            name="rss_max_datatype"
            dt: "string"
            value: "[rss_max_datatype.value]"
        - parameter:
            name="rss_max_operation"
            dt: "string"
            value: "[rss_max_operation.value]"
        - parameter:
            name="memlock_current"
            dt: "integer"
            value: "[memlock_current.value]"
        - parameter:
            name="memlock_current_datatype"
            dt: "string"
            value: "[memlock_current_datatype.value]"
        - parameter:
            name="memlock_current_operation"
            dt: "string"
            value: "[memlock_current_operation.value]"
        - parameter:
            name="memlock_max"
            dt: "integer"
            value: "[memlock_max.value]"
        - parameter:
            name="memlock_max_datatype"
            dt: "string"
            value: "[memlock_max_datatype.value]"
        - parameter:
            name="memlock_max_operation"
            dt: "string"
            value: "[memlock_max_operation.value]"
        - parameter:
            name="maxproc_current"
            dt: "integer"
            value: "[maxproc_current.value]"
        - parameter:
            name="maxproc_current_datatype"
            dt: "string"
            value: "[maxproc_current_datatype.value]"
        - parameter:
            name="maxproc_current_operation"
            dt: "string"
            value: "[maxproc_current_operation.value]"
        - parameter:
            name="maxproc_max"
            dt: "integer"
            value: "[maxproc_max.value]"
        - parameter:
            name="maxproc_max_datatype"
            dt: "string"
            value: "[maxproc_max_datatype.value]"
        - parameter:
            name="maxproc_max_operation"
            dt: "string"
            value: "[maxproc_max_operation.value]"
        - parameter:
            name="maxfiles_current"
            dt: "integer"
            value: "[maxfiles_current.value]"
        - parameter:
            name="maxfiles_current_datatype"
            dt: "string"
            value: "[maxfiles_current_datatype.value]"
        - parameter:
            name="maxfiles_max_operation"
            dt: "string"
            value: "[maxfiles_max_operation.value]"

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact_title": "[ARTIFACT-TITLE]",
      "artifact": {
        "type": "[ARTIFACT-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "check_existence",
              "dt": "string",
              "value": "[check_existence.value]"
            }
          }
        ]
      },
        "test": {
          "type": "[TEST-TYPE-NAME]",
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
                  "name": "cpu_current",
                  "dt": "integer",
                  "value": "[cpu_current.value]"
                }
              },
              {
                "parameter": {
                  "name": "cpu_current_datatype",
                  "dt": "string",
                  "value": "[cpu_current_datatype.value]"
                }
              },
              {
                "parameter": {
                  "name": "cpu_current_operation",
                  "dt": "string",
                  "value": "[cpu_current_operation.value]"
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
                  "name": "cpu_max_datatype",
                  "dt": "string",
                  "value": "[cpu_max_datatype.value]"
                }
              },
              {
                "parameter": {
                  "name": "cpu_max_operation",
                  "dt": "string",
                  "value": "[cpu_max_operation.value]"
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
                  "name": "filesize_current_datatype",
                  "dt": "string",
                  "value": "[filesize_current_datatype.value]"
                }
              },
              {
                "parameter": {
                  "name": "filesize_current_operation",
                  "dt": "string",
                  "value": "[filesize_current_operation.value]"
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
                  "name": "filesize_max_datatype",
                  "dt": "string",
                  "value": "[filesize_max_datatype.value]"
                }
              },
              {
                "parameter": {
                  "name": "filesize_max_operation",
                  "dt": "string",
                  "value": "[filesize_max_operation.value]"
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
                  "name": "data_current_datatype",
                  "dt": "string",
                  "value": "[data_current_datatype.value]"
                }
              },
              {
                "parameter": {
                  "name": "data_current_operation",
                  "dt": "string",
                  "value": "[data_current_operation.value]"
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
                  "name": "data_max_datatype",
                  "dt": "string",
                  "value": "[data_max_datatype.value]"
                }
              },
              {
                "parameter": {
                  "name": "data_max_operation",
                  "dt": "string",
                  "value": "[data_max_operation.value]"
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
                  "name": "stack_current_datatype",
                  "dt": "string",
                  "value": "[stack_current_datatype.value]"
                }
              },
              {
                "parameter": {
                  "name": "stack_current_operation",
                  "dt": "string",
                  "value": "[stack_current_operation.value]"
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
                  "name": "stack_max_datatype",
                  "dt": "string",
                  "value": "[stack_max_datatype.value]"
                }
              },
              {
                "parameter": {
                  "name": "stack_max_operation",
                  "dt": "string",
                  "value": "[stack_max_operation.value]"
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
                  "name": "core_current_datatype",
                  "dt": "string",
                  "value": "[core_current_datatype.value]"
                }
              },
              {
                "parameter": {
                  "name": "core_current_operation",
                  "dt": "string",
                  "value": "[core_current_operation.value]"
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
                  "name": "core_max_datatype",
                  "dt": "string",
                  "value": "[core_max_datatype.value]"
                }
              },
              {
                "parameter": {
                  "name": "core_max_operation",
                  "dt": "string",
                  "value": "[core_max_operation.value]"
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
                  "name": "rss_current_datatype",
                  "dt": "string",
                  "value": "[rss_current_datatype.value]"
                }
              },
              {
                "parameter": {
                  "name": "rss_current_operation",
                  "dt": "string",
                  "value": "[rss_current_operation.value]"
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
                  "name": "rss_max_datatype",
                  "dt": "string",
                  "value": "[rss_max_datatype.value]"
                }
              },
              {
                "parameter": {
                  "name": "rss_max_operation",
                  "dt": "string",
                  "value": "[rss_max_operation.value]"
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
                  "name": "memlock_current_datatype",
                  "dt": "string",
                  "value": "[memlock_current_datatype.value]"
                }
              },
              {
                "parameter": {
                  "name": "memlock_current_operation",
                  "dt": "string",
                  "value": "[memlock_current_operation.value]"
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
                  "name": "memlock_max_datatype",
                  "dt": "string",
                  "value": "[memlock_max_datatype.value]"
                }
              },
              {
                "parameter": {
                  "name": "memlock_max_operation",
                  "dt": "string",
                  "value": "[memlock_max_operation.value]"
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
                  "name": "maxproc_current_datatype",
                  "dt": "string",
                  "value": "[maxproc_current_datatype.value]"
                }
              },
              {
                "parameter": {
                  "name": "maxproc_current_operation",
                  "dt": "string",
                  "value": "[maxproc_current_operation.value]"
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
                  "name": "maxproc_max_datatype",
                  "dt": "string",
                  "value": "[maxproc_max_datatype.value]"
                }
              },
              {
                "parameter": {
                  "name": "maxproc_max_operation",
                  "dt": "string",
                  "value": "[maxproc_max_operation.value]"
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
                  "name": "maxfiles_current_datatype",
                  "dt": "string",
                  "value": "[maxfiles_current_datatype.value]"
                }
              },
              {
                "parameter": {
                  "name": "maxfiles_current_operation",
                  "dt": "string",
                  "value": "[maxfiles_current_operation.value]"
                }
              },
              {
                "parameter": {
                  "name": "maxfiles_max",
                  "dt": "integer",
                  "value": "[maxfiles_max.value]"
                }
              },
              {
                "parameter": {
                  "name": "maxfiles_max_datatype",
                  "dt": "string",
                  "value": "[maxfiles_max_datatype.value]"
                }
              },
              {
                "parameter": {
                  "name": "maxfiles_max_operation",
                  "dt": "string",
                  "value": "[maxfiles_max_operation.value]"
                }
              }
          ]
        }
    }
  }