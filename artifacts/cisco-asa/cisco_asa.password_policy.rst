Cisco ASA: Password Policy
==========================

Description
-----------

The Cisco ASA: Password Policy test is used to check the properties of the password policy.

The variable_object element is used by a variable_test to define the variable to be evaluated.

The variable_state element contains two entities that are used to check the var_ref of the specified varible and the value associated with it.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**cisco_asa.password_policy**

====================== ====== =====================================
Name                   Type   Description
====================== ====== =====================================
password_policy_option string Password Policy configuration option.
====================== ====== =====================================

NOTE: The ``password_policy_option`` parameter is governed by a constraint allowing only the following values:
  - lifetime
  - minimum-changes
  - minimum-uppercase
  - minimum-lowercase
  - minimum-numeric
  - minimum-special
  - minimum-length

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Cisco ASA: Expected Value Via Regex Capture

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**cisco_asa.expected_value_regex_capture**

+------------------------+---------+-----------------------------------------+
| Name                   | Type    | Description                             |
+========================+=========+=========================================+
| operator               | string  | Comparison operator.                    |
+------------------------+---------+-----------------------------------------+
| expected_value         | string  | Expected value of the password policy   |
|                        |         | option.                                 |
+------------------------+---------+-----------------------------------------+
| regex_capture          | string  | The regex_capture to use to isolate the |
|                        |         | expected value.                         |
+------------------------+---------+-----------------------------------------+
| expected_value_type    | string  | Data type of expected value.            |
+------------------------+---------+-----------------------------------------+

NOTE: The ``operator`` parameter is governed by a constraint allowing only the following values:
  - bitwise and
  - bitwise or
  - case insensitive equals
  - case insensitive not equal
  - equals
  - greater than
  - greater than or equal
  - less than
  - less than or equal
  - pattern match
  - not equal
  - set white list
  - set is empty

NOTE: The ``expected_value_type`` parameter is governed by a constraint allowing only the following values:
  - boolean
  - float
  - int
  - string
  - version
  - set  

Generated Content
~~~~~~~~~~~~~~~~~

**cisco_asa.expected_value_regex_capture**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:complex-check operator="AND">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
        <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
          <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
          <ae:title>[ARTIFACT-TITLE]</ae:title>
          <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="password_policy_option">[password_policy_option.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
              <ae:parameter dt="string" name="expected_value">[expected_value.value]</ae:parameter>
              <ae:parameter dt="string" name="regex_capture">[regex_capture.value]</ae:parameter>
              <ae:parameter dt="string" name="expected_value_type">[expected_value_type.value]</ae:parameter>
            </ae:parameters>
          </ae:test>
          <ae:profiles>
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_2" />
          </ae:profiles>
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  </xccdf:complex-check>  

SCAP
^^^^

XCCDF
'''''

For ``cisco_asa.password_policy`` ``cisco_asa.expected_value_regex_capture`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    type="string"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``cisco_asa.password_policy`` ``cisco_asa.expected_value_regex_capture`` artifacts, the XCCDF check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
    <check-content-ref 
      href="[BENCHMARK-TITLE]-oval.xml" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <variable_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
    check_existence="at_least_one_exists" 
    check="all" 
    comment="[ARTIFACT-TITLE]" 
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </variable_test>

Object

::

  <variable_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[ARTIFACT-TITLE]" 
    version="1">
    <var_ref>
      oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2
    </var_ref>
  </variable_object>

  <line_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#asa" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" 
    comment="[ARTIFACT-TITLE]" 
    version="1">
    <show_subcommand>[show_subcommand.value]</show_subcommand>
  </line_object>

State

::

  <variable_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[ARTIFACT-TITLE]" 
    version="1">
    <value 
      operation="[operation.value]" 
      datatype="[datatype.value]" 
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </variable_state>

Variable

::

  <external_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="string"
    comment="This value is used in Rule: [RECOMMENDATION-TITLE]"
    version="1" />

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2"
    datatype="string"
    comment="This value is used in Rule: [RECOMMENDATION-TITLE]"
    version="1">
    <regex_capture pattern:"[pattern.value]">
      <object_component
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2"
        item_field="config_line" />
    </regex_capture>
  </constant_variable>

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
            name: "password_policy_option"
            dt: "string"
            value: "[password_policy_option.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "operator"
            dt: "string"
            value: "[operator.value]"
        - parameter:
            name: "expected_value"
            dt: "string"
            value: "[expected_value.value]"
        - parameter:
            name: "regex_capture"
            dt: "string"
            value: "[regex_capture.value]"
        - parameter:
            name: "expected_value_type"
            dt: "string"
            value: "[expected_value_type.value]"

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
              "name": "password_policy_option",
              "type": "string",
              "value": "[password_policy_option.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "operator",
              "type": "string",
              "value": "[operator.value]"
            }
          },
          {
            "parameter": {
              "name": "expected_value",
              "type": "string",
              "value": "[expected_value.value]"
            }
          },
          {
            "parameter": {
              "name": "regex_capture",
              "type": "string",
              "value": "[regex_capture.value]"
            }
          },
          {
            "parameter": {
              "name": "expected_value_type",
              "type": "string",
              "value": "[expected_value_type.value]"
            }
          }
        ]
      }
    }
  }
