macos.accountinfo_v1
====================

Description
-----------
The accountinfo_test is used to check the properties of user account information (username, uid, gid, etc.).

The accountinfo_object consists of a single username that identifies the account from which to gather information.

The accountinfo_state element defines the different information that can be used to evaluate the specified accounts.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| username                            | String      | Specifies the    |
|                                     |             | username of the  |
|                                     |             | account to       |
|                                     |             | gather           |
|                                     |             | information      |
|                                     |             | from.            |
|                                     |             |                  |
+-------------------------------------+-------------+------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - macos.accountinfo_v1

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~


+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| existence_check                     | String      | Define how many  |
|                                     |             | items should be  |
|                                     |             | collected        |
+-------------------------------------+-------------+------------------+
| check                               | String      | Defines how many |
|                                     |             | collected items  |
|                                     |             | must match the   |
|                                     |             | expected state   |
+-------------------------------------+-------------+------------------+
| operation                           | String      | Comparison       |
|                                     |             | operation        |
+-------------------------------------+-------------+------------------+
| datatype                            | String      | Datatype         |
+-------------------------------------+-------------+------------------+
| username                            | Integer     | Specifies the    |
|                                     |             | user of the      |
|                                     |             | account to       |
|                                     |             | gather           |
|                                     |             | information      |
|                                     |             | from.            |
+-------------------------------------+-------------+------------------+
| password                            | String      | Obfuscated       |
|                                     |             | (*****) or       |
|                                     |             | encrypted        |
|                                     |             | password for     |
|                                     |             | this user        |
+-------------------------------------+-------------+------------------+
| uid                                 | Integer     | The numeric user |
|                                     |             | id, or uid, is   |
|                                     |             | the third column |
|                                     |             | of each user's   |
|                                     |             | entry in         |
|                                     |             | /etc/passwd.     |
|                                     |             | This element     |
|                                     |             | represents the   |
|                                     |             | owner of the     |
|                                     |             | file.            |
+-------------------------------------+-------------+------------------+
| gid                                 | Integer     | Group ID of this |
|                                     |             | account          |
+-------------------------------------+-------------+------------------+
| realname                            | String      | User's real      |
|                                     |             | name, aka gecos  |
|                                     |             | field of         |
|                                     |             | /etc/passwd.     |
+-------------------------------------+-------------+------------------+
| home_dir                            | String      | The home         |
|                                     |             | directory for    |
|                                     |             | this user        |
|                                     |             | account.         |
+-------------------------------------+-------------+------------------+
| login_shell                         | String      | The login shell  |
|                                     |             | for this user    |
|                                     |             | account.         |
+-------------------------------------+-------------+------------------+


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

NOTE: The ``operation`` parameter is governed by a constraint allowing
only the following values:
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

macos.accountinfo_v1
^^^^^^^^^^^^^^^^^^^^

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

   <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
     <xccdf:check-content>
       <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION_NUMBER]">
         <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
         <ae:title>[RECOMMENDATION TITLE]</ae:title>
         <ae:artifact type="[ARTIFACTTYPE NAME]">
           <ae:parameters>
             <ae:parameter dt="string" name="username">[username.value]</ae:parameter>
           </ae:parameters>
         </ae:artifact>
         <ae:test type="[TESTTYPE NAME]">
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
           <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_[level.value]"/>
         </ae:profiles>
       </ae:artifact_expression>
     </xccdf:check-content>
   </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``macos.accountinfo_v1`` artifacts, the xccdf:check looks like this. There is no Value in the xccdf for this Artifact.

::

   <xccdf rule-id="[RULE_ID]"
        artifact-expression-id="[AE_ID]" artifact-oval-id="[ARTIFACT-OVAL-ID]">
        <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
            <check-content-ref
                href="[BENCHMARK_NAME]"
                name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]"/>
        </check>
    </xccdf>

OVAL
''''

Test

::

    accountinfo_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
      id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
      check_existence="[check_existence.value] check="[check.value]"
      comment="[comment.value]"
      version="[version.value]">
      <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"/>
      <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"/>
    </accountinfo_test>

Object

::

    <accountinfo_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
      id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" version="[version.value]"
      comment="[comment.value]"
      version="[version.value]">
      <username>[username.value]</username>
    </accountinfo_object>

State

::

   <accountinfo_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
      id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" version="[version.value]"
      comment="[comment.value]"
      version="[version.value]">
      <username datatype="[DATATYPE.value]" operation="[OPERATION.value]">[VALUE]</username>
      <password datatype="[DATATYPE.value]" operation="[OPERATION.value]">[VALUE]</password>
      <uid datatype="[DATATYPE.value]">[VALUE]</uid>
      <gid datatype="[DATATYPE.value]">[VALUE]</gid>
      <realname datatype="[DATATYPE.value]" operation="[OPERATION.value]">[VALUE]</realname>
      <home_dir datatype="[DATATYPE.value]" operation="[OPERATION.value]">[VALUE]</home_dir>
      <login_shell datatype="[DATATYPE.value]" operation="[OPERATION.value]">[VALUE]</login_shell>
    </accountinfo_state>


YAML
^^^^

::

  - artifact-expression:
       artifact-unique-id: [ARTIFACT-OVAL-ID]
       artifact-title: [RECOMMENDATION TITLE]
       artifact:
         type: [ARTIFACTTYPE NAME]
         parameters:
         - parameter: 
             name: username
             type: string
             value: [username.value]
       test:
         type: [TESTTYPE NAME]
         parameters:
         - parameter:
             name: existence_check
             type: string
             value: [existence_check.value]
         - parameter: 
             name: check
             type: string
             value: [check.value]
         - parameter:
             name: operation
             type: string
             value: [operation.value]
         - parameter: 
             name: datatype
             type: string
             value: [datatype.value]  
         - parameter: 
             name: username
             type: string
             value: [username.value]
         - parameter:
             name: password
             type: string
             value: [password.value]
         - parameter:
             name: uid
             type: integer
             value: [uid.value]
         - parameter:
             name: gid
             type: integer
             value: [gid.value]
         - parameter:
             name: realname
             type: string
             value: [realname.value]
         - parameter:
             name: home_dir
             type: string
             value: [home_dir.value]
         - parameter:
             name: login_shell
             type: string
             value: [login_shell.value]

JSON
^^^^

::

   [
    {
        "artifact-expression": {
            "artifact-unique-id": [
                "ARTIFACT-OVAL-ID"
            ],
            "artifact-title": [
                "RECOMMENDATION TITLE"
            ],
            "artifact": {
                "type": [
                    "ARTIFACTTYPE NAME"
                ],
                "parameters": [
                    {
                        "parameter": {
                            "name": "username",
                            "type": "string",
                            "value": [
                                "username.value"
                            ]
                        }
                    }
                ]
            },
            "test": {
                "type": [
                    "TESTTYPE NAME"
                ],
                "parameters": [
                    {
                        "parameter": {
                            "name": "existence_check",
                            "type": "string",
                            "value": [
                                "existence_check.value"
                            ]
                        }
                    },
                    {
                        "parameter": {
                            "name": "check",
                            "type": "string",
                            "value": [
                                "check.value"
                            ]
                        }
                    },
                    {
                        "parameter": {
                            "name": "operation",
                            "type": "string",
                            "value": [
                                "operation.value"
                            ]
                        }
                    },
                    {
                        "parameter": {
                            "name": "datatype",
                            "type": "string",
                            "value": [
                                "datatype.value"
                            ]
                        }
                    },
                    {
                        "parameter": {
                            "name": "username",
                            "type": "string",
                            "value": [
                                "username.value"
                            ]
                        }
                    },
                    {
                        "parameter": {
                            "name": "password",
                            "type": "string",
                            "value": [
                                "password.value"
                            ]
                        }
                    },
                    {
                        "parameter": {
                            "name": "uid",
                            "type": "integer",
                            "value": [
                                "uid.value"
                            ]
                        }
                    },
                    {
                        "parameter": {
                            "name": "gid",
                            "type": "integer",
                            "value": [
                                "gid.value"
                            ]
                        }
                    },
                    {
                        "parameter": {
                            "name": "realname",
                            "type": "string",
                            "value": [
                                "realname.value"
                            ]
                        }
                    },
                    {
                        "parameter": {
                            "name": "home_dir",
                            "type": "string",
                            "value": [
                                "home_dir.value"
                            ]
                        }
                    },
                    {
                        "parameter": {
                            "name": "login_shell",
                            "type": "string",
                            "value": [
                                "login_shell.value"
                            ]
                        }
                    }
                ]
            }
        }
    }
]
