macos:accountinfo
=================

Description
-----------
The macos:accountinfo test is used to check the properties of user account information (username, uid, gid, etc.).

The accountinfo_object element is used by an accountinfo_test to identify the account from which to gather information.

The accountinfo_state element defines the different information that can be used to evaluate the specified account.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**macos.accountinfo_v1**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| username                    | string  | Specifies the username of the      |
|                             |         | account to gather information from.|
+-----------------------------+---------+------------------------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - macos:accountinfo

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**macos.accountinfo_v1**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| existence_check             | string  | Defines how many items should be   |
|                             |         | collected.                         |
+-----------------------------+---------+------------------------------------+
| check                       | string  | Defines how many collected items   |
|                             |         | must match the expected state.     |
+-----------------------------+---------+------------------------------------+
| username                    | integer | Specifies the user of the account  |
|                             |         | to gather information from.        |
+-----------------------------+---------+------------------------------------+
| username_operation          | string  | Comparison Operation.              |
+-----------------------------+---------+------------------------------------+
| username_datatype           | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| password                    | string  | Obfuscated (*****) or encrypted    |
|                             |         | password for this user.            |
+-----------------------------+---------+------------------------------------+
| password_operation          | string  | Comparison Operation.              |
+-----------------------------+---------+------------------------------------+
| password_datatype           | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| uid                         | integer | The numeric user id, or uid, is    |
|                             |         | the third column of each user's    |
|                             |         | entry in /etc/passwd. This element |
|                             |         | represents the owner of the file.  |
+-----------------------------+---------+------------------------------------+
| uid_operation               | string  | Comparison Operation.              |
+-----------------------------+---------+------------------------------------+
| uid_datatype                | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| gid                         | integer | Group ID of this account.          |
+-----------------------------+---------+------------------------------------+
| gid_operation               | string  | Comparison Operation.              |
+-----------------------------+---------+------------------------------------+
| gid_datatype                | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| realname                    | string  | User's real name, aka gecos field  |
|                             |         | of /etc/passwd.                    |
+-----------------------------+---------+------------------------------------+
| realname_operation          | string  | Comparison Operation.              |
+-----------------------------+---------+------------------------------------+
| realname_datatype           | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| home_dir                    | string  | The home directory for this user   |
|                             |         | account.                           |
+-----------------------------+---------+------------------------------------+
| home_dir_operation          | string  | Comparison Operation.              |
+-----------------------------+---------+------------------------------------+
| home_dir_datatype           | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| login_shell                 | string  | The login shell for this user      |
|                             |         | account.                           |
+-----------------------------+---------+------------------------------------+
| login_shell_operation       | string  | Comparison Operation.              |
+-----------------------------+---------+------------------------------------+
| login_shell_datatype        | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_satisfy
  - none_exist
  - only_one_exists

NOTE: The ``check`` parameter is governed by a constraint allowing only the following values:
  - all
  - at least one
  - none satisfy
  - only one

NOTE: All ``operation`` parameters are governed by a constraint allowing only the following values:
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

NOTE: All ``datatype`` parameters are governed by a constraint allowing only the following values:
  - boolean
  - float
  - int
  - string
  - version
  - set

Generated Content
~~~~~~~~~~~~~~~~~

**macos.accountinfo_v1**

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
            <ae:parameter dt="string" name="username">[username.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="existence_check">[existence_check.value]</ae:parameter>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="username">[username.value]</ae:parameter>
            <ae:parameter dt="string" name="username_operation">[username_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="username_datatype">[username_datatype.value]</ae:parameter>
            <ae:parameter dt="string" name="password">[password.value]</ae:parameter>
            <ae:parameter dt="string" name="password_operation">[password_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="password_datatype">[password_datatype.value]</ae:parameter>
            <ae:parameter dt="integer" name="uid">[uid.value]</ae:parameter>
            <ae:parameter dt="string" name="uid_operation">[uid_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="uid_datatype">[uid_datatype.value]</ae:parameter>
            <ae:parameter dt="integer" name="gid">[gid.value]</ae:parameter>
            <ae:parameter dt="string" name="gid_operation">[gid_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="gid_datatype">[gid_datatype.value]</ae:parameter>
            <ae:parameter dt="string" name="home_dir">[home_dir.value]</ae:parameter>
            <ae:parameter dt="string" name="home_dir_operation">[home_dir_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="home_dir_datatype">[home_dir_datatype.value]</ae:parameter>
            <ae:parameter dt="string" name="login_shell">[login_shell.value]</ae:parameter>
            <ae:parameter dt="string" name="login_shell_operation">[login_shell_operation.value]</ae:parameter>
            <ae:parameter dt="string" name="login_shell_datatype">[login_shell_datatype.value]</ae:parameter>
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

For ``macos.accountinfo_v1`` ``macos.accountinfo_v1`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this artifact.

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

  <accountinfo_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[ARTIFACT-TTILE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </accountinfo_test>

Object

::

  <accountinfo_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TTILE]"
    version="1">
    <username>[username.value]</username>
  </accountinfo_object>

State

::

  <accountinfo_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TTILE]"
    version="1">
    <username 
      datatype="[username_datatype.value]"
      operation="[username_operation.value]">
        [username.value]
    </username>
    <password 
      datatype="[password_datatype.value]"
      operation="[password_operation.value]">
        [password.value]
    </password>
    <uid 
      datatype="[uid_datatype.value]"
      operation="[uid_operation.value]">
        [uid.value]
    </uid>
    <gid
      datatype="[gid_datatype.value]"
      operation="[gid_operation.value]">
        [gid.value]
    </gid>
    <realname 
      datatype="[realname_datatype.value]"
      operation="[realname_operation.value]">
        [realname.value]
    </realname>
    <home_dir
      datatype="[home_dir_datatype.value]"
      operation="[home_dir_operation.value]">
        [home_dir.value]
    </home_dir>
    <login_shell 
      datatype="[login_shell_datatype.value]"
      operation="[login_shell_operation.value]">
        [login_shell.value]
    </login_shell>
  </accountinfo_state>

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
            name: "username"
            dt: "string"
            value: "[username.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "existence_check"
            dt: "string"
            value: "[existence_check.value]"
        - parameter: 
            name: "check"
            dt: "string"
            value: "[check.value]" 
        - parameter: 
            name: "username"
            dt: "string"
            value: "[username.value]"
        - parameter:
            name: "username_operation"
            dt: "string"
            value: "[username_operation.value]"
        - parameter: 
            name: "username_datatype"
            dt: "string"
            value: "[username_datatype.value]" 
        - parameter: 
            name: "password"
            dt: "string"
            value: "[password.value]"
        - parameter:
            name: "password_operation"
            dt: "string"
            value: "[password_operation.value]"
        - parameter: 
            name: "password_datatype"
            dt: "string"
            value: "[password_datatype.value]" 
        - parameter: 
            name: "uid"
            dt: "integer"
            value: "[uid.value]"
        - parameter:
            name: "uid_operation"
            dt: "string"
            value: "[uid_operation.value]"
        - parameter: 
            name: "uid_datatype"
            dt: "string"
            value: "[uid_datatype.value]" 
        - parameter: 
            name: "gid"
            dt: "integer"
            value: "[gid.value]"
        - parameter:
            name: "gid_operation"
            dt: "string"
            value: "[gid_operation.value]"
        - parameter: 
            name: "gid_datatype"
            dt: "string"
            value: "[gid_datatype.value]" 
        - parameter: 
            name: "realname"
            dt: "string"
            value: "[realname.value]"
        - parameter:
            name: "realname_operation"
            dt: "string"
            value: "[realname_operation.value]"
        - parameter: 
            name: "realname_datatype"
            dt: "string"
            value: "[realname_datatype.value]" 
        - parameter: 
            name: "home_dir"
            dt: "string"
            value: "[home_dir.value]"
        - parameter:
            name: "home_dir_operation"
            dt: "string"
            value: "[home_dir_operation.value]"
        - parameter: 
            name: "home_dir_datatype"
            dt: "string"
            value: "[home_dir_datatype.value]" 
        - parameter: 
            name: "login_shell"
            dt: "string"
            value: "[login_shell.value]"
        - parameter:
            name: "login_shell_operation"
            dt: "string"
            value: "[login_shell_operation.value]"
        - parameter: 
            name: "login_shell_datatype"
            dt: "string"
            value: "[login_shell_datatype.value]" 

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
              "name": "username",
              "dt": "string",
              "value": "[username.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "existence_check",
              "dt": "string",
              "value": "[existence_check.value]"
            }
          },
          {
            "parameter": {
              "name": "check",
              "dt": "string",
              "value": "[check.value]"
            }
          },
          {
            "parameter": {
              "name": "username",
              "dt": "string",
              "value": "[username.value]"
            }
          },
          {
            "parameter": {
              "name": "username_operation",
              "dt": "string",
              "value": "[username_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "username_datatype",
              "dt": "string",
              "value": "[username_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "password",
              "dt": "string",
              "value": "[password.value]"
            }
          },
          {
            "parameter": {
              "name": "password_operation",
              "dt": "string",
              "value": "[password_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "password_datatype",
              "dt": "string",
              "value": "[password_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "uid",
              "dt": "integer",
              "value": "[uid.value]"
            }
          },
          {
            "parameter": {
              "name": "uid_operation",
              "dt": "string",
              "value": "[uid_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "uid_datatype",
              "dt": "string",
              "value": "[uid_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "gid",
              "dt": "integer",
              "value": "[gid.value]"
            }
          },
          {
            "parameter": {
              "name": "gid_operation",
              "dt": "string",
              "value": "[gid_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "gid_datatype",
              "dt": "string",
              "value": "[gid_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "realname",
              "dt": "string",
              "value": "[realname.value]"
          },
          {
            "parameter": {
              "name": "realname_operation",
              "dt": "string",
              "value": "[realname_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "realname_datatype",
              "dt": "string",
              "value": "[realname_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "home_dir",
              "dt": "string",
              "value": "[home_dir.value]"
            }
          },
          {
            "parameter": {
              "name": "home_dir_operation",
              "dt": "string",
              "value": "[home_dir_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "home_dir_datatype",
              "dt": "string",
              "value": "[home_dir_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "login_shell",
              "dt": "string",
              "value": "[login_shell.value]"
            }
          },
          {
            "parameter": {
              "name": "login_shell_operation",
              "dt": "string",
              "value": "[login_shell_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "login_shell_datatype",
              "dt": "string",
              "value": "[login_shell_datatype.value]"
            }
          }
        ]
      }
    }
  }