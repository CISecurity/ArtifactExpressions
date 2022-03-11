macos:inetlisteningserver510
============================

Description
-----------
The macos:inetlisteningserver510 test is generally used to check if an application is listening on the network, either for a new connection or as part of an ongoing connection. This is limited to applications that are listening for connections that use the TCP or UDP protocols and have addresses represented as IPv4 or IPv6 addresses (AF_INET or AF_INET6). It is generally speaking the parsed output of running the command netstat -tuwlnpe with root privilege.

The inetlisteningservers_object element is used by an inetlisteningserver test to define the inet listening server to be evaluated.

The inetlisteningservers_state element defines the different information that can be used to evaluate the specified inet listening server. This includes the local address, foreign address, port information, and process id.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**macos.inetlisteningserver510**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| check_existence             | string  | Defines how many items should be   |
|                             |         | collected. Typically set to 'at    |
|                             |         | least one'.                        |
+-----------------------------+---------+------------------------------------+
| protocol                    | string  | Defines a certain transport-layer  |
|                             |         | protocol, in lowercase: tcp or     |
|                             |         | udp. Cannot be blank.              |
+-----------------------------+---------+------------------------------------+
| local_address               | string  | This is the IP address of the      |
|                             |         | network interface on which an      |
|                             |         | application listens. Note that the |
|                             |         | IP address can be IPv4 or IPv6.    |
|                             |         | Cannot be blank.                   |
+-----------------------------+---------+------------------------------------+
| local_port                  | integer | This is the TCP or UDP port on     |
|                             |         | which an application would listen. |
|                             |         | Note that this is not a list -- if |
|                             |         | a program listens on multiple      |
|                             |         | ports, or on a combination of TCP  |
|                             |         | and UDP, each will be represented  |
|                             |         | by its own object. Cannot be       |
|                             |         | blank.                             |
+-----------------------------+---------+------------------------------------+
:strong:`NOTE: The` ``protocol``, ``local_address``, :strong:`and` ``local_port`` :strong:`parameters are governed by a constraint allowing only values conforming to the following regex pattern:` ``^.+$``

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values: 
  - all_exist 
  - any_exist 
  - at_least_one_exists 
  - none_exist 
  - only_one_exists

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - macos:inetlisteningserver510

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**macos.inetlisteningserver510**

+--------------------------------+---------+-------------------------------------+
| Name                           | Type    | Description                         |
+================================+=========+=====================================+
| check                          | string  | Defines how many collected items    |
|                                |         | must match the expected state.      |
+--------------------------------+---------+-------------------------------------+
| protocol                       | string  | This is the transport-layer         |
|                                |         | protocol, in lowercase: tcp or udp. |
+--------------------------------+---------+-------------------------------------+
| protocol_operation             | string  | Comparison operation.               |
+--------------------------------+---------+-------------------------------------+
| protocol_datatype              | string  | Datatype.                           |
+--------------------------------+---------+-------------------------------------+
| local_address                  | binary  | This is the IP address of the       |
|                                |         | network interface on which the      |
|                                |         | program listens. Note that the IP   |
|                                |         | address can be IPv4 or IPv6.        |
+--------------------------------+---------+-------------------------------------+
| local_address_operation        | string  | Comparison operation.               |
+--------------------------------+---------+-------------------------------------+
| local_address_datatype         | string  | Datatype.                           |
+--------------------------------+---------+-------------------------------------+
| local_port                     | integer | This is the TCP or UDP port on      |
|                                |         | which the program listens. Note     |
|                                |         | that this is not a list -- if a     |
|                                |         | program listens on multiple ports,  |
|                                |         | or on a combination of TCP and      |
|                                |         | UDP, each will have its own entry   |
|                                |         | in the table data stored by this    |
|                                |         | test.                               |
+--------------------------------+---------+-------------------------------------+
| local_port_operation           | string  | Comparison operation.               |
+--------------------------------+---------+-------------------------------------+
| local_port_datatype            | string  | Datatype                            |
+--------------------------------+---------+-------------------------------------+
| local_full_address             | string  | This is the IP address and network  |
|                                |         | port on which the program listens,  |
|                                |         | equivalent to                       |
|                                |         | local_address:local_port. Note      |
|                                |         | that the IP address can be IPv4 or  |
|                                |         | IPv6.                               |
+--------------------------------+---------+-------------------------------------+
| local_full_address_operation   | string  | Comparison operation.               |
+--------------------------------+---------+-------------------------------------+
| local_full_address_datatype    | string  | Datatype.                           |
+--------------------------------+---------+-------------------------------------+
| program_name                   | string  | This is the name of the             |
|                                |         | communicating program.              |
+--------------------------------+---------+-------------------------------------+
| program_name_operation         | string  | Comparison operation.               |
+--------------------------------+---------+-------------------------------------+
| program_name_datatype          | string  | Datatype.                           |
+--------------------------------+---------+-------------------------------------+
| foreign_address                | string  | This is the IP address with which   |
|                                |         | the program is communicating, or    |
|                                |         | with which it will communicate, in  |
|                                |         | the case of a listening server.     |
|                                |         | Note that the IP address can be     |
|                                |         | IPv4 or IPv6.                       |
+--------------------------------+---------+-------------------------------------+
| foreign_address_operation      | string  | Comparison operation.               |
+--------------------------------+---------+-------------------------------------+
| foreign_address_datatype       | string  | Datatype.                           |
+--------------------------------+---------+-------------------------------------+
| foreign_port                   | integer | This is the TCP or UDP port to      |
|                                |         | which the program communicates. In  |
|                                |         | the case of a listening program     |
|                                |         | accepting new connections, this is  |
|                                |         | usually '0'.                        |
+--------------------------------+---------+-------------------------------------+
| foreign_port_operation         | string  | Comparison operation.               |
+--------------------------------+---------+-------------------------------------+
| foreign_port_datatype          | string  | Datatype.                           |
+--------------------------------+---------+-------------------------------------+
| foreign_full_address           | binary  | This is the IP address and network  |
|                                |         | port to which the program is        |
|                                |         | communicating or will accept        |
|                                |         | communications from, equivalent to  |
|                                |         | foreign_address:foreign_port. Note  |
|                                |         | that the IP address can be IPv4 or  |
|                                |         | IPv6.                               |
+--------------------------------+---------+-------------------------------------+
| foreign_full_address_operation | string  | Comparison operation.               |
+--------------------------------+---------+-------------------------------------+
| foreign_full_address_datatype  | string  | Datatype.                           |
+--------------------------------+---------+-------------------------------------+
| pid                            | integer | This is the process ID of the       |
|                                |         | process. The process in question    |
|                                |         | is that of the program              |
|                                |         | communicating on the network.       |
+--------------------------------+---------+-------------------------------------+
| pid_operation                  | string  | Comparison operation.               |
+--------------------------------+---------+-------------------------------------+
| pid_datatype                   | string  | Datatype.                           |
+--------------------------------+---------+-------------------------------------+
| user_id                        | integer | The numeric user id, or uid, is     |
|                                |         | the third column of each user's     |
|                                |         | entry in /etc/passwd. It            |
|                                |         | represents the owner, and thus      |
|                                |         | privilege level, of the specified   |
|                                |         | program.                            |
+--------------------------------+---------+-------------------------------------+
| user_id_operation              | string  | Comparison operation.               |
+--------------------------------+---------+-------------------------------------+
| user_id_datatype               | string  | Datatype.                           |
+--------------------------------+---------+-------------------------------------+

`NOTE: The ``check`` parameter is governed by a constraint allowing only the following values:
  - all
  - at least one
  - none satisfy
  - only one

:strong:`NOTE: The following parameters:`
  +--------------------------------------------+--------------------------------------------+
  | ``local_address_operation``                | ``protocol_operation``                     |
  +--------------------------------------------+--------------------------------------------+
  | ``local_port_operation``                   | ``local_full_address_operation``           |
  +--------------------------------------------+--------------------------------------------+
  | ``program_name_operation``                 | ``foreign_address_operation``              |
  +--------------------------------------------+--------------------------------------------+
  | ``foreign_port_operation``                 | ``foreign_full_address_operation``         |
  +--------------------------------------------+--------------------------------------------+
  | ``pid_operation``                          | ``user_id_operation``                      |
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
  | ``protocol_datatype``                     | ``local_address_datatype``                |
  +-------------------------------------------+-------------------------------------------+
  | ``local_port_datatype``                   | ``local_full_address_datatype``           |
  +-------------------------------------------+-------------------------------------------+
  | ``program_name_datatype``                 | ``foreign_address_datatype``              |
  +-------------------------------------------+-------------------------------------------+
  | ``foreign_port_datatype``                 | ``foreign_full_address_datatype``         |
  +-------------------------------------------+-------------------------------------------+
  | ``pid_datatype``                          | ``user_id_datatype``                      |
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

**macos.inetlisteningserver510**

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
            <ae:parameter dt="string" name="protocol">[protocol.value]</ae:parameter>
            <ae:parameter dt="string" name="local_address">[local_address.value]</ae:parameter>
            <ae:parameter dt="integer" name="local_port">[local_port.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="protocol">[protocol.value]</ae:parameter>
            <ae:parameter dt="string" name="protocol_operation">equals</ae:parameter>
            <ae:parameter dt="string" name="protocol_datatype">string</ae:parameter>
            <ae:parameter dt="binary" name="local_address">[local_address.value]</ae:parameter>
            <ae:parameter dt="string" name="local_address_operation">[local_address_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="local_address_datatype">[local_address_datatype.value]</ae:parameter>
            <ae:parameter dt="integer" name="local_port">[local_port.value]</ae:parameter>
            <ae:parameter dt="string" name="local_port_operation">[local_port_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="local_port_datatype">[local_port_datatype.value]</ae:parameter>
            <ae:parameter dt="string" name="local_full_address">[local_full_address.value]</ae:parameter>
            <ae:parameter dt="string" name="local_full_address_operation">[local_full_address_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="local_full_address_datatype">[local_full_address_datatype.value]</ae:parameter>
            <ae:parameter dt="string" name="program_name">[program_name.value]</ae:parameter>
            <ae:parameter dt="string" name="program_name_operation">[program_name_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="program_name_datatype">[program_name_datatype.value]</ae:parameter>
            <ae:parameter dt="string" name="foreign_address">[foreign_address.value]</ae:parameter>
            <ae:parameter dt="string" name="foreign_address_operation">[foreign_address_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="foreign_address_datatype">[foreign_address_datatype.value]</ae:parameter>
            <ae:parameter dt="integer" name="foreign_port">[foreign_port.value]</ae:parameter>
            <ae:parameter dt="string" name="foreign_port_operation">[foreign_port_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="foreign_port_datatype">[foreign_port_datatype.value]</ae:parameter>
            <ae:parameter dt="binary" name="foreign_full_address">[foreign_full_address.value]</ae:parameter>
            <ae:parameter dt="string" name="foreign_full_address_operation">[foreign_full_address_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="foreign_full_address_datatype">[foreign_full_address_datatype.value]</ae:parameter>
            <ae:parameter dt="integer" name="pid">[pid.value]</ae:parameter>
            <ae:parameter dt="string" name="pid_operation">[pid_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="pid_datatype">[pid_datatype.value]</ae:parameter>
            <ae:parameter dt="integer" name="user_id">[user_id.value]</ae:parameter>
            <ae:parameter dt="string" name="user_id_operation">[user_id_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="user_id_datatype">[user_id_datatype.value]</ae:parameter>
          </ae:parameters>
        </ae:test>
        <ae:profiles>
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_2" />
        </ae:profiles>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``macos.inetlisteningserver510`` ``macos.inetlisteningserver510`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-content-ref
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <inetlisteningserver510_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[ARTIFACT-TTILE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </inetlisteningserver510_test>

Object

::

  <inetlisteningserver510_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TTILE]"
    version="1">
    <protocol>[protocol.value]</protocol>
    <local_address>[local_address.value]</local_address>
    <local_port>[local_port.value]</local_port>
  </inetlisteningserver510_object>

State

::

  <inetlisteningserver510_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TTILE]"
    version="1">
    <protocol 
      datatype="[protocol_datatype.value]"
      operation="[protocol_operation.value]">
        [protocol.value]
    </protocol>
    <local_address 
      datatype="[local_address_datatype.value]"
      operation="[local_address_operation.value]">
        [local_address.value]
    </local_address>
    <local_port 
      datatype="[local_port_datatype.value]"
      operation="[local_port_operation.value]">
        [local_port.value]
    </local_port>
    <local_full_address 
      datatype="[local_full_address_datatype.value]"
      operation="[local_full_address_operation.value]">
        [local_full_address.value]
    </local_full_address>
    <program_name 
      datatype="[program_name_datatype.value]"
      operation="[program_name_operation.value]">
        [program_name.value]
    </program_name>
    <foreign_address 
      datatype="[foreign_address_datatype.value]"
      operation="[foreign_address_operation.value]">
        [foreign_address.value]
    </foreign_address>
    <foreign_port 
      datatype="[foreign_port_datatype.value]"
      operation="[foreign_port_datatype_operation.value]">
        [foreign_port.value]
    </foreign_port>
    <foreign_full_address 
      datatype="[foreign_full_address_datatype.value]"
      operation="[foreign_full_address_operation.value]">
        [foreign_full_address.value]
    </foreign_full_address>
    <pid 
      datatype="[pid_datatype.value]"
      operation="[pid_operation.value]">
        [pid.value]
    </pid>
    <user_id 
      datatype="[user_id_datatype.value]"
      operation="[user_id_operation.value]">
        [user_id.value]
    </user_id>
  </inetlisteningserver510_state>

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
        - parameter:
            name: "protocol"
            dt: "string"
            value: "[protocol.value]"
        - parameter:
            name: "local_address"
            dt: "string"
            value: "[local_address.value]"
        - parameter:
            name: "local_port"
            dt: "integer"
            value: "[local_port.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "check"
            dt: "string"
            value: "[check.value]"
        - parameter:
            name: "datatype"
            dt: "string"
            value: "[datatype.value]"
        - parameter:
            name: "protocol"
            dt: "string"
            value: "[protocol.value]"
        - parameter:
            name: "protocol_operation"
            dt: "string"
            value: "[protocol_operation]"
        - parameter:
            name: "protocol_datatype"
            dt: "string"
            value: "[protocol_datatype]"
        - parameter:
            name: "local_address"
            dt: "binary"
            value: "[local_address.value]"
        - parameter:
            name: "local_address_operation"
            dt: "string"
            value: "[local_address_operation]"
        - parameter:
            name: "local_address_datatype"
            dt: "string"
            value: "[local_address_datatype]"
        - parameter:
            name: "local_port"
            dt: "integer"
            value: "[local_port.value]"
        - parameter:
            name: "local_port_operation"
            dt: "string"
            value: "[local_port_operation]"
        - parameter:
            name: "local_port_datatype"
            dt: "string"
            value: "[local_port_datatype]"
        - parameter:
            name: "local_full_address"
            dt: "string"
            value: "[local_full_address.value]"
        - parameter:
            name: "local_full_address_operation"
            dt: "string"
            value: "[local_full_address_operation]"
        - parameter:
            name: "local_full_address_datatype"
            dt: "string"
            value: "[local_full_address_datatype]"
        - parameter:
            name: "program_name"
            dt: "string"
            value: "[program_name.value]"
        - parameter:
            name: "program_name_operation"
            dt: "string"
            value: "[program_name_operation]"
        - parameter:
            name: "program_name_datatype"
            dt: "string"
            value: "[program_name_datatype]"
        - parameter:
            name: "foreign_address"
            dt: "string"
            value: "[foreign_address.value]"
        - parameter:
            name: "foreign_address_operation"
            dt: "string"
            value: "[foreign_address_operation]"
        - parameter:
            name: "foreign_address_datatype"
            dt: "string"
            value: "[foreign_address_datatype]"
        - parameter:
            name: "foreign_port"
            dt: "integer"
            value: "[foreign_port.value]"
        - parameter:
            name: "foreign_port_operation"
            dt: "string"
            value: "[foreign_port_operation]"
        - parameter:
            name: "foreign_port_datatype"
            dt: "string"
            value: "[foreign_port_datatype]"
        - parameter:
            name: "foreign_full_address"
            dt: "binary"
            value: "[foreign_full_address.value]"
        - parameter:
            name: "foreign_full_address_operation"
            dt: "string"
            value: "[foreign_full_address_operation]"
        - parameter:
            name: "foreign_full_address_datatype"
            dt: "string"
            value: "[foreign_full_address_datatype]"
        - parameter:
            name: "pid"
            dt: "integer"
            value: "[pid.value]"
        - parameter:
            name: "pid_operation"
            dt: "string"
            value: "[pid_operation]"
        - parameter:
            name: "pid_datatype"
            dt: "string"
            value: "[pid_datatype]"
        - parameter:
            name: "user_id"
            dt: "integer"
            value: "[user_id.value]"
        - parameter:
            name: "user_id_operation"
            dt: "string"
            value: "[user_id_operation]"
        - parameter:
            name: "user_id_datatype"
            dt: "string"
            value: "[user_id_datatype]"

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
              "name": "check_existence",
              "dt": "string",
              "value": "[check_existence.value]"
            }
          },
          {
            "parameter": {
              "name": "protocol",
              "dt": "string",
              "value": "[protocol.value]"
            }
          },
          {
            "parameter": {
              "name": "local_address",
              "dt": "string",
              "value": "[local_address.value]"
            }
          },
          {
            "parameter": {
              "name": "local_port",
              "dt": "integer",
              "value": "[local_port.value]"
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
              "name": "datatype",
              "dt": "string",
              "value": "[datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "protocol",
              "dt": "string",
              "value": "[protocol.value]"
            }
          },
          {
            "parameter": {
              "name": "protocol_operation",
              "dt": "string",
              "value": "[protocol_operation]"
            }
          },
          {
            "parameter": {
              "name": "protocol_datatype",
              "dt": "string",
              "value": "[protocol_datatype]"
            }
          },
          {
            "parameter": {
              "name": "local_address",
              "dt": "binary",
              "value": "[local_address.value]"
            }
          },
          {
            "parameter": {
              "name": "local_address_operation",
              "dt": "string",
              "value": "[local_address_operation]"
            }
          },
          {
            "parameter": {
              "name": "local_address_datatype",
              "dt": "string",
              "value": "[local_address_datatype]"
            }
          },
          {
            "parameter": {
              "name": "local_port",
              "dt": "integer",
              "value": "[local_port.value]"
            }
          },
          {
            "parameter": {
              "name": "local_port_operation",
              "dt": "string",
              "value": "[local_port_operation]"
            }
          },
          {
            "parameter": {
              "name": "local_port_datatype",
              "dt": "string",
              "value": "[local_port_datatype]"
            }
          },
          {
            "parameter": {
              "name": "local_full_address",
              "dt": "string",
              "value": "[local_full_address.value]"
            }
          },
          {
            "parameter": {
              "name": "local_full_address_operation",
              "dt": "string",
              "value": "[local_full_address_operation]"
            }
          },
          {
            "parameter": {
              "name": "local_full_address_datatype",
              "dt": "string",
              "value": "[local_full_address_datatype]"
            }
          },
          {
            "parameter": {
              "name": "program_name",
              "dt": "string",
              "value": "[program_name.value]"
            }
          },
          {
            "parameter": {
              "name": "program_name_operation",
              "dt": "string",
              "value": "[program_name_operation]"
            }
          },
          {
            "parameter": {
              "name": "program_name_datatype",
              "dt": "string",
              "value": "[program_name_datatype]"
            }
          },
          {
            "parameter": {
              "name": "foreign_address",
              "dt": "string",
              "value": "[foreign_address.value]"
            }
          },
          {
            "parameter": {
              "name": "foreign_address_operation",
              "dt": "string",
              "value": "[foreign_address_operation]"
            }
          },
          {
            "parameter": {
              "name": "foreign_address_datatype",
              "dt": "string",
              "value": "[foreign_address_datatype]"
            }
          },
          {
            "parameter": {
              "name": "foreign_port",
              "dt": "integer",
              "value": "[foreign_port.value]"
            }
          },
          {
            "parameter": {
              "name": "foreign_port_operation",
              "dt": "string",
              "value": "[foreign_port_operation]"
            }
          },
          {
            "parameter": {
              "name": "foreign_port_datatype",
              "dt": "string",
              "value": "[foreign_port_datatype]"
            }
          },
          {
            "parameter": {
              "name": "foreign_full_address",
              "dt": "binary",
              "value": "[foreign_full_address.value]"
            }
          },
          {
            "parameter": {
              "name": "foreign_full_address_operation",
              "dt": "string",
              "value": "[foreign_full_address_operation]"
            }
          },
          {
            "parameter": {
              "name": "foreign_full_address_datatype",
              "dt": "string",
              "value": "[foreign_full_address_datatype]"
            }
          },
          {
            "parameter": {
              "name": "pid",
              "dt": "integer",
              "value": "[pid.value]"
            }
          },
          {
            "parameter": {
              "name": "pid_operation",
              "dt": "string",
              "value": "[pid_operation]"
            }
          },
          {
            "parameter": {
              "name": "pid_datatype",
              "dt": "string",
              "value": "[pid_datatype]"
            }
          },
          {
            "parameter": {
              "name": "user_id",
              "dt": "integer",
              "value": "[user_id.value]"
            }
          },
          {
            "parameter": {
              "name": "user_id_operation",
              "dt": "string",
              "value": "[user_id_operation]"
            }
          },
          {
            "parameter": {
              "name": "user_id_datatype",
              "dt": "string",
              "value": "[user_id_datatype]"
            }
          }
        ]
      }
    }
  }