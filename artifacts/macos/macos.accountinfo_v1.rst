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
| operation                   | string  | Comparison Operation.              |
+-----------------------------+---------+------------------------------------+
| datatype                    | string  | Data type.                         |
+-----------------------------+---------+------------------------------------+
| username                    | integer | Specifies the user of the account  |
|                             |         | to gather information from.        |
+-----------------------------+---------+------------------------------------+
| password                    | string  | Obfuscated (*****) or encrypted    |
|                             |         | password for this user.            |
+-----------------------------+---------+------------------------------------+
| uid                         | integer | The numeric user id, or uid, is    |
|                             |         | the third column of each user's    |
|                             |         | entry in /etc/passwd. This element |
|                             |         | represents the owner of the file.  |
+-----------------------------+---------+------------------------------------+
| gid                         | integer | Group ID of this account.          |
+-----------------------------+---------+------------------------------------+
| realname                    | string  | User's real name, aka gecos field  |
|                             |         | of /etc/passwd.                    |
+-----------------------------+---------+------------------------------------+
| home_dir                    | string  | The home directory for this user   |
|                             |         | account.                           |
+-----------------------------+---------+------------------------------------+
| login_shell                 | string  | The login shell for this user      |
|                             |         | account.                           |
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
            <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
            <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
            <ae:parameter dt="string" name="username">[username.value]</ae:parameter>
            <ae:parameter dt="string" name="password">[password.value]</ae:parameter>
            <ae:parameter dt="integer" name="uid">[uid.value]</ae:parameter>
            <ae:parameter dt="integer" name="gid">[gid.value]</ae:parameter>
            <ae:parameter dt="string" name="home_dir">[home_dir.value]</ae:parameter>
            <ae:parameter dt="string" name="login_shell">[login_shell.value]</ae:parameter>
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
      datatype="[datatype.value]"
      operation="[operation.value]">
        [username.value]
    </username>
    <password 
      datatype="[datatype.value]"
      operation="[operation.value]">
        [password.value]
    </password>
    <uid 
      datatype="int"
      operation="equals">
        [uid.value]
    </uid>
    <gid
      datatype="int"
      operation="equals">
        [gid.value]
    </gid>
    <realname 
      datatype="[datatype.value]"
      operation="[operation.value]">
        [realname.value]
    </realname>
    <home_dir
      datatype="[datatype.value]"
      operation="[operation.value]">
        [home_dir.value]
    </home_dir>
    <login_shell 
      datatype="[datatype.value]"
      operation="[operation.value]">
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
            name: "operation"
            dt: "string"
            value: "[operation.value]"
        - parameter: 
            name: "datatype"
            dt: "string"
            value: "[datatype.value]"  
        - parameter: 
            name: "username"
            dt: "string"
            value: "[username.value]"
        - parameter: 
            name: "password"
            dt: "string"
            value: "[password.value]"
        - parameter: 
            name: "uid"
            dt: "integer"
            value: "[uid.value]"
        - parameter: 
            name: "gid"
            dt: "integer"
            value: "[gid.value]"
        - parameter: 
            name: "realname"
            dt: "string"
            value: "[realname.value]"
        - parameter: 
            name: "home_dir"
            dt: "string"
            value: "[home_dir.value]"
        - parameter: 
            name: "login_shell"
            dt: "string"
            value: "[login_shell.value]"

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
              "name": "username",
              "dt": "string",
              "value": "[username.value]"
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
              "name": "uid",
              "dt": "integer",
              "value": "[uid.value]"
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
              "name": "realname",
              "dt": "string",
              "value": "[realname.value]"
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
              "name": "login_shell",
              "dt": "string",
              "value": "[login_shell.value]"
            }
          }
        ]
      }
    }
  }