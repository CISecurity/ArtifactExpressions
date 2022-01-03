VMware: VM Host: Account
========================

Description
-----------

The VMware: VM Host: Account test is used to verify one or more local ESXi user accounts have been created for the specified ESXi host, and that the specified user account has been granted shell access.

The vmhost_account_object element is used by the vmhost_account_test to define the name and connection string of the vmhost, and the user account to be evaluated.

The vmhost_account_state elemement holds information regarding the role and shell access settings of the specified user account.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**vmware.vmhost.account**

+-------------------------------------+---------+----------------------------+
| Name                                | Type    | Description                |
+=====================================+=========+============================+
| vmhost_name                         | string  | The name of the ESXi host  |
|                                     |         | to limit collection to.    |
|                                     |         | Set to NA if not           |
|                                     |         | applicable.                |
+-------------------------------------+---------+----------------------------+
| account_name                        | string  | Set to NA if not           |
|                                     |         | applicable.                |
+-------------------------------------+---------+----------------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - VMware: VM Host: Account

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**vmware.vmhost.account**

+-------------------------------------+---------+----------------------------+
| Name                                | Type    | Description                |
+=====================================+=========+============================+
| shell_access_enabled_operator       | boolean | The test to perform on the |
|                                     |         | Shell Access Enabled       |
|                                     |         | field. Enter NA if not     |
|                                     |         | applicable.                |
+-------------------------------------+---------+----------------------------+
| shell_access_enabled                | boolean | Enter NA if not            |
|                                     |         | applicable.                |
+-------------------------------------+---------+----------------------------+
| role_operator                       | string  | The test to perform on the |
|                                     |         | Role field. Enter NA if    |
|                                     |         | not applicable.            |
+-------------------------------------+---------+----------------------------+
| role                                | string  | Enter NA if not            |
|                                     |         | applicable.                |
+-------------------------------------+---------+----------------------------+

NOTE: The ``shell_access_enabled_operator`` parameter is governed by a constraint allowing only the following values:
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

NOTE: The ``role_operator`` parameter is governed by a constraint allowing only the following values:- equals
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

Generated Content
~~~~~~~~~~~~~~~~~

**vmware.vmhost.account**

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
            <ae:parameter dt="string" name="vmhost_name">[vmhost_name.value]</ae:parameter>
            <ae:parameter dt="string" name="account_name">[account_name.value]</ae:parameter>        
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="shell_access_enabled_operator">[shell_access_enabled_operator.value]</ae:parameter>
            <ae:parameter dt="boolean" name="shell_access_enabled">[shell_access_enabled.value]</ae:parameter>
            <ae:parameter dt="string" name="role_operator">[role_operator.value]</ae:parameter>
            <ae:parameter dt="string" name="role">[role.value]</ae:parameter>
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

For ``vmware.vmhost.account`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:100000"
      value-id="xccdf_org.cisecurity.benchmarks_value_esxi.connection" />
    <check-content-ref 
      href="[BENCHMARK-NAME]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <vmhost_account_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi" 
    id="oval:org.cisecurity.benchmarks[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="at least one"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </vmhost_account_test>

Object

::

  <vmhost_account_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <connection_string var_ref="oval:org.cisecurity.benchmarks[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <vmhost_name operation="pattern match">
      .*
    </vmhost_name>
    <account_name operation="pattern match">
      .*
    </account_name>
  </vmhost_account_object> 

State

::

  <vmhost_account_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <shell_access_enabled 
      datatype="boolean"
      operation="[operation.value]">
        [shell_access_enabled.value]
    </shell_access_enabled>
    <role 
      datatype="string"
      operation="[operation.value]">
        [role.value]
    </role>
  </vmhost_account_state>

Variable

::

  <external_variable 
    id="oval:org.cisecurity.benchmarks[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="boolean"
    version="1"
    comment="This value is used in Rule: [RECOMMENDATION-TITLE]" />

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
            name: "vmhost_name"
            dt: "string"
            value: "[vmhost_name.value]"
        - parameter: 
            name: "account_name"
            dt: "string"
            value: "[account_name.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter: 
            name: "shell_access_enabled_operator"
            dt: "string"
            value: "[shell_access_enabled_operator.value]"
        - parameter:
            name: "shell_access_enabled"
            dt: "boolean"
            value: "[shell_access_enabled.value]"
        - parameter: 
            name: "role_operator"
            dt: "string"
            value: "[role_operator.value]"
        - parameter: 
            name: "role"
            dt: "string"
            value: "[role.value]"

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
              "name": "vmhost_name",
              "dt": "string",
              "value": "[vmhost_name.value]"
            }
          },
          {
            "parameter": {
              "name": "account_name",
              "dt": "string",
              "value": "[account_name.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "shell_access_enabled_operator",
              "dt": "string",
              "value": "[shell_access_enabled_operator.value]"
            }
          },
          {
            "parameter": {
              "name": "shell_access_enabled",
              "dt": "boolean",
              "value": "[shell_access_enabled.value]"
            }
          },
          {
            "parameter": {
              "name": "role_operator",
              "dt": "string",
              "value": "[role_operator.value]"
            }
          },
          {
            "parameter": {
              "name": "role",
              "dt": "string",
              "value": "[role.value]"
            }
          }
        ]
      }
    }
  }
