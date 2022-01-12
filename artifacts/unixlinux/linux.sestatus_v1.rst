linux:sestatus
==============

Description
-----------
The linux.sestatus test is used to check the sestatus config file for implementation details. 

The sestatus_object element is used by an sestatus_test to define the sestatus config file to be evaluated.

The sestatus_state element defines the implementation details to be checked in the sestatus config file.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**linux.sestatus_v1_parameters**

=================================  ========  =================================
Name                               Type      Description  
=================================  ========  =================================
N/A
=================================  ========  =================================


Supported Test Types
~~~~~~~~~~~~~~~~~~~~

- linux:sestatus_current_mode
- linux:sestatus_loaded_policy_name
- linux:sestatus_mode_from_config
- linux:sestatus_selinux_status

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**linux.sestatus_current_mode_v1_parameters**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| check_existence             | string  | Defines how many items should be   |
|                             |         | collected. Typically set to 'at    |
|                             |         | least one'.                        |
+-----------------------------+---------+------------------------------------+
| check                       | string  | Defines how many collected items   |
|                             |         | must match the expected state.     |
+-----------------------------+---------+------------------------------------+
| operation                   | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+
| datatype                    | string  | The data type of the value.        |
+-----------------------------+---------+------------------------------------+
| current_mode                | string  | Indicates if SELinux is currently  |
|                             |         | enforcing or not utilizing the     |
|                             |         | following values: enforcing,       |
|                             |         | permissive, disabled.              |
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

**linux.sestatus_loaded_policy_name_v1**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| check_existence             | string  | Defines how many items should be   |
|                             |         | collected. Typically set to 'at    |
|                             |         | least one'.                        |
+-----------------------------+---------+------------------------------------+
| check                       | string  | Defines how many collected items   |
|                             |         | must match the expected state.     |
+-----------------------------+---------+------------------------------------+
| operation                   | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+
| datatype                    | string  | The data type of the value.        |
+-----------------------------+---------+------------------------------------+
| loaded_policy_name          | string  | Displays what type of SELinux      |
|                             |         | policy is currently loaded         |
|                             |         | ('targeted', 'mimimum', or 'mls'). |
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

**linux.sestatus_mode_from_config_v1**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| check_existence             | string  | Defines how many items should be   |
|                             |         | collected. Typically set to 'at    |
|                             |         | least one'.                        |
+-----------------------------+---------+------------------------------------+
| check                       | string  | Defines how many collected items   |
|                             |         | must match the expected state.     |
+-----------------------------+---------+------------------------------------+
| operation                   | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+
| datatype                    | string  | The data type of the value.        |
+-----------------------------+---------+------------------------------------+
| mode_from_config            | string  | Displays the mode from the config  |
|                             |         | file ('targeted', 'mimimum', or    |
|                             |         | 'mls').                            |
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

**linux.sestatus_selinux_status_v1**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| check_existence             | string  | Defines how many items should be   |
|                             |         | collected. Typically set to 'at    |
|                             |         | least one'.                        |
+-----------------------------+---------+------------------------------------+
| check                       | string  | Defines how many collected items   |
|                             |         | must match the expected state.     |
+-----------------------------+---------+------------------------------------+
| operation                   | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+
| datatype                    | string  | The data type of the value.        |
+-----------------------------+---------+------------------------------------+
| selinux_status              | string  | Indicates whether SELinux module   |
|                             |         | is enabled or disabled.            |
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

**linux.sestatus_current_mode_v1**

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
          <ae:parameters />
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
            <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
            <ae:parameter dt="string" name="current_mode">[current_mode.value]</ae:parameter>
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

For ``linux.sestatus_v1 linux.sestatus_current_mode_v1`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

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

  <sestatus_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check="[check.value]"
    check_existence="[check_existence.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </sestatus_test>

Object     

::

  <sestatus_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[ARTIFACT-TITLE]" 
    version="1" />
 
State  

::

  <sestatus_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
    comment="[ARTIFACT-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    version="1">
    <current_mode 
      datatype="[datatype.value]"
      operation="[operation.value]">
        [current_mode.value]
    </current_mode>
  </sestatus_state>

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact-title: "[ARTIFACT-TITLE]"
      artifact:
        type: "[ARTIFACT-TYPE-NAME]"
        parameters: []
      test:
        type: "[TEST-TYPE-NAME]"
        parameters:
          - parameter:
              name: "check_existence"
              dt: "string"
              value: "[check_existence.value]"
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
              name: "current_mode"
              dt: "string"
              value: "[current_mode.value]"

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact-title": "[ARTIFACT-TITLE]",
      "artifact": {
        "type": "[ARTIFACT-TYPE-NAME]",
        "parameters": []
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
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
              "name": "current_mode",
              "dt": "string",
              "value": "[current_mode.value]"
            }
          }
        ]
      }
    }
  }


Generated Content
~~~~~~~~~~~~~~~~~

**linux.sestatus_loaded_policy_name_v1**

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
          <ae:parameters />
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
            <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
            <ae:parameter dt="string" name="loaded_policy_name">[loaded_policy_name.value]</ae:parameter>
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

For ``linux.sestatus_v1 linux.sestatus_loaded_policy_name_v1`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

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

  <sestatus_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check="[check.value]"
    check_existence="[check_existence.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </sestatus_test>

Object     

::

  <sestatus_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[ARTIFACT-TITLE]" 
    version="1" />
 
State  

::

  <sestatus_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
    comment="[ARTIFACT-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    version="1">
    <loaded_policy_name 
      datatype="[datatype.value]"
      operation="[operation.value]">
        [loaded_policy_name.value]
    </loaded_policy_name>
  </sestatus_state>

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact-title: "[ARTIFACT-TITLE]"
      artifact:
        type: "[ARTIFACT-TYPE-NAME]"
        parameters: []
      test:
        type: "[TEST-TYPE-NAME]"
        parameters:
          - parameter:
              name: "check_existence"
              dt: "string"
              value: "[check_existence.value]"
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
              name: "loaded_policy_name"
              dt: "string"
              value: "[loaded_policy_name.value]"

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact-title": "[ARTIFACT-TITLE]",
      "artifact": {
        "type": "[ARTIFACT-TYPE-NAME]",
        "parameters": []
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
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
              "name": "loaded_policy_name",
              "dt": "string",
              "value": "[loaded_policy_name.value]"
            }
          }
        ]
      }
    }
  }

Generated Content
~~~~~~~~~~~~~~~~~

**linux.sestatus_mode_from_config_v1**

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
          <ae:parameters />
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
            <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
            <ae:parameter dt="string" name="mode_from_config">[mode_from_config.value]</ae:parameter>
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

For ``linux.sestatus_v1 linux.sestatus_mode_from_config_v1`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

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

  <sestatus_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check="[check.value]"
    check_existence="[check_existence.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </sestatus_test>

Object     

::

  <sestatus_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[ARTIFACT-TITLE]" 
    version="1" />
 
State  

::

  <sestatus_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
    comment="[ARTIFACT-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    version="1">
    <mode_from_config 
      datatype="[datatype.value]"
      operation="[operation.value]">
        [mode_from_config.value]
    </mode_from_config>
  </sestatus_state>

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact-title: "[ARTIFACT-TITLE]"
      artifact:
        type: "[ARTIFACT-TYPE-NAME]"
        parameters: []
      test:
        type: "[TEST-TYPE-NAME]"
        parameters:
          - parameter:
              name: "check_existence"
              dt: "string"
              value: "[check_existence.value]"
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
              name: "mode_from_config"
              dt: "string"
              value: "[mode_from_config.value]"

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact-title": "[ARTIFACT-TITLE]",
      "artifact": {
        "type": "[ARTIFACT-TYPE-NAME]",
        "parameters": []
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
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
              "name": "mode_from_config",
              "dt": "string",
              "value": "[mode_from_config.value]"
            }
          }
        ]
      }
    }
  }

Generated Content
~~~~~~~~~~~~~~~~~

**linux.sestatus_selinux_status_v1**

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
          <ae:parameters />
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
            <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
            <ae:parameter dt="string" name="selinux_status">[selinux_status.value]</ae:parameter>
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

For ``linux.sestatus_v1 linux.sestatus_selinux_status_v1`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

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

  <sestatus_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check="[check.value]"
    check_existence="[check_existence.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </sestatus_test>

Object     

::

  <sestatus_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[ARTIFACT-TITLE]" 
    version="1" />
 
State  

::

  <sestatus_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
    comment="[ARTIFACT-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    version="1">
    <selinux_status 
      datatype="[datatype.value]"
      operation="[operation.value]">
        [selinux_status.value]
    </selinux_status>
  </sestatus_state>

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact-title: "[ARTIFACT-TITLE]"
      artifact:
        type: "[ARTIFACT-TYPE-NAME]"
        parameters: []
      test:
        type: "[TEST-TYPE-NAME]"
        parameters:
          - parameter:
              name: "check_existence"
              dt: "string"
              value: "[check_existence.value]"
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
              name: "selinux_status"
              dt: "string"
              value: "[selinux_status.value]"

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact-title": "[ARTIFACT-TITLE]",
      "artifact": {
        "type": "[ARTIFACT-TYPE-NAME]",
        "parameters": []
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
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
              "name": "selinux_status",
              "dt": "string",
              "value": "[selinux_status.value]"
            }
          }
        ]
      }
    }
  }