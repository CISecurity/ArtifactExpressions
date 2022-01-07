Cisco ASA: Line Object
======================

Description
-----------

The Cisco ASA: Line Object test is used to check the properties of specific output lines from a SHOW command, such as SHOW RUNNING-CONFIG.

The line_object element is used by a line_test to define the name of a SHOW sub-command to be tested.

The line_state element defines the different information that can be used to evaluate the result of a specific SHOW sub-command. This includes the name of ths sub-command and the corresponding config line. 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**cisco_asa.line_object**

=============== ====== =======================================================
Name            Type   Description
=============== ====== =======================================================
show_subcommand string The name of a SHOW sub-command. Cannot be blank.
=============== ====== =======================================================

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Cisco ASA: Line Config Line
  - Cisco ASA: Existence Check
  - Cisco ASA: Expected Value Via Regex Capture
  - Cisco ASA: Line State With Untrusted Interfaces

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**cisco_asa.line_config_line**

=========== ====== =================================
Name        Type   Description
=========== ====== =================================
operation   string Comparison operator.
config_line string The collected configuration line.
check       string Check enumeration value.
=========== ====== =================================

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

NOTE: The ``check`` parameter is governed by a constraint allowing only the following values:
  - all
  - at least one
  - none satisfy
  - only one

**cisco_asa.existence_check**

=============== ====== =========================================
Name            Type   Description
=============== ====== =========================================
existence_check string Number of lines expected to be collected.
=============== ====== =========================================

NOTE: The ``existence_check`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_satisfy
  - none_exist
  - only_one_exists

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
| expected_value_type    | string  | Datatype of expected value.             |
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

**cisco_asa.untrusted_interfaces_state**

============ ====== ===========================
Name         Type   Description
============ ====== ===========================
regex_prefix string Regular Expression Prefix.
regex_suffix string Regular Expression Suffix.
check        string The test's check attribute.
============ ====== ===========================

NOTE: The ``check`` parameter is governed by a constraint allowing only the following values:
  - all
  - at least one
  - none satisfy
  - only one

Generated Content
~~~~~~~~~~~~~~~~~

**cisco_asa.line_config_line**

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
              <ae:parameter dt="string" name="show_subcommand">[show_subcommand.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
              <ae:parameter dt="string" name="config_line">[config_line.value]</ae:parameter>
              <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            </ae:parameters>
          </ae:test>
          <ae:profiles>
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1" />
          </ae:profiles>          
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  </xccdf:complex-check>  

SCAP
^^^^

XCCDF
'''''

For ``cisco_asa.line_object cisco_asa.line_config_line`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    type="string"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``cisco_asa.line_object cisco_asa.line_config_line`` artifacts, the xccdf:check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
    <check-content-ref 
      href="[BENCHMARK-NAME]" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <line_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#asa"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="[check.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </line_test>

Object

::

  <line_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#asa"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <show_subcommand>[show_subcommand.value]</show_subcommand>
  </line_object>

State

::

  <line_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#asa"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <config_line 
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </line_state>

Variable

::

  <external_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="string" 
    comment="This value is used in Rule: [RECOMMENDATION-TITLE]"
    version="1" />  

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
            name: "show_subcommand"
            dt: "string"
            value: "[show_subcommand.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "operation"
            dt: "string"
            value: "[operation.value]"
        - parameter:
            name: "config_line"
            dt: "string"
            value: "[config_line.value]"
        - parameter:
            name: "check"
            dt: "string"
            value: "[check_line.value]"

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
              "name": "show_subcommand",
              "type": "string",
              "value": "[show_subcommand.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "operation",
              "type": "string",
              "value": "[operation.value]"
            }
          },
          {
            "parameter": {
              "name": "config_line",
              "type": "string",
              "value": "[config_line.value]"
            }
          },
          {
            "parameter": {
              "name": "check",
              "type": "string",
              "value": "[check_line.value]"
            }
          }
        ]
      }
    }
  }

Generated Content
~~~~~~~~~~~~~~~~~

**cisco_asa.existence_check**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:complex-check operator="AND">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
        <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
          <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
          <ae:title>[ARTIFACT-TITLE]</ae:title>
          <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="show_subcommand">[show_subcommand.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="existence_check">[existence_check.value]</ae:parameter>
            </ae:parameters>
          </ae:test>
          <ae:profiles>
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1" />
          </ae:profiles>          
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  </xccdf:complex-check>  

SCAP
^^^^

XCCDF
'''''

For ``cisco_asa.line_object cisco_asa.existence_check`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

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

  <line_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#asa"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </line_test>

Object

::

  <line_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#asa"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <show_subcommand>[show_subcommand.value]</show_subcommand>
  </line_object>

State

::

  N/A

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
            name: "show_subcommand"
            dt: "string"
            value: "[show_subcommand.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "existence_check"
            dt: "string"
            value: "[existence_check.value]"

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
              "name": "show_subcommand",
              "type": "string",
              "value": "[show_subcommand.value]"
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
              "type": "string",
              "value": "[existence_check.value]"
            }
          }
        ]
      }
    }
  }  

Generated Content
~~~~~~~~~~~~~~~~~

**cisco_asa.expected_value_regex_capture**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:complex-check operator="AND">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
        <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
          <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
          <ae:title>[ARTIFACT-TITLE]</ae:title>
          <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="show_subcommand">[show_subcommand.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
              <ae:parameter dt="string" name="expected_value">[expected_value.value]</ae:parameter>
              <ae:parameter dt="string" name="regex_capture">[regex_capture.value]</ae:parameter>
              <ae:parameter dt="string" name="expected_value_type">[expected_value_type.value]</ae:parameter>
            </ae:parameters>
          </ae:test>
          <ae:profiles>
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1" />
          </ae:profiles>          
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  </xccdf:complex-check>  

SCAP
^^^^

XCCDF
'''''

For ``cisco_asa.line_object cisco_asa.expected_value_regex_capture`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    type="string"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``cisco_asa.line_object cisco_asa.expected_value_regex_capture`` artifacts, the xccdf:check looks like this.

::

  <xccdf:complex-check operator="AND">
    <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
      <check-export 
        export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
        value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
      <check-content-ref 
        href="[BENCHMARK-NAME]" 
        name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
    </check>
  </xccdf:complex-check>

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
    <var_ref>oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2</var_ref>
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
      datatype="[datatype.value]"
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
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
    <regex_capture pattern="[pattern.value]"> 
      <object_component
        object_ref="[oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2]"
        item_field="config_line" />
    </regex_capture>
  </local_variable>

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
            name: "show_subcommand"
            dt: "string"
            value: "[show_subcommand.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "operation"
            dt: "string"
            value: "[operation.value]"
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
              "name": "show_subcommand",
              "type": "string",
              "value": "[show_subcommand.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "operation",
              "type": "string",
              "value": "[operation.value]"
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

Generated Content
~~~~~~~~~~~~~~~~~

**cisco_asa.untrusted_interfaces_state**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:complex-check operator="AND">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
        <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
          <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
          <ae:title>[ARTIFACT-TITLE]</ae:title>
          <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="show_subcommand">[show_subcommand.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="regex_prefix">[regex_prefix.value]</ae:parameter>
              <ae:parameter dt="string" name="regex_suffix">[regex_suffix.value]</ae:parameter>
              <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
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

For ``cisco_asa.line_object cisco_asa.untrusted_interfaces_state`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    type="string"
    operator="pattern match">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``cisco_asa.line_object cisco_asa.expected_value_regex_capture`` artifacts, the xccdf:check looks like this.

::

  <xccdf:complex-check operator="AND">
    <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
      <check-export 
        export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
        value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
      <check-content-ref 
        href="[BENCHMARK-NAME]" 
        name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
    </check>
  </xccdf:complex-check>  

OVAL
''''

Test

::

  <line_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#asa"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="[check.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </line_test>

Object

::

  <line_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#asa"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <show_subcommand>[show_subcommand.value]</show_subcommand>
  </line_object>

State

::

  <line_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#asa"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <config_line
      operation="pattern match
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" /> 
  </line_state>

Variable

::

  <local_variable
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#asa"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    comment="This value is used in Rule: [RECOMMENDATION-TITLE]"
    datatype="string"
    version="1">
    <concat>
      <literal_component>[literal_component.value]</literal_component>
      <variable_component var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
      <literal_component>[literal_component.value]</literal_component>
    </concat>
  </local_variable>    

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
            name: "show_subcommand"
            dt: "string"
            value: "[show_subcommand.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "regex_prefix"
            dt: "string"
            value: "[regex_prefix.value]"
        - parameter:
            name: "regex_suffix"
            dt: "string"
            value: "[regex_suffix.value]"
        - parameter:
            name: "check"
            dt: "string"
            value: "[check.value]"

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
              "name": "show_subcommand",
              "type": "string",
              "value": "[show_subcommand.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "regex_prefix",
              "type": "string",
              "value": "[regex_prefix.value]"
            }
          },
          {
            "parameter": {
              "name": "regex_suffix",
              "type": "string",
              "value": "[regex_suffix.value]"
            }
          },
          {
            "parameter": {
              "name": "check",
              "type": "string",
              "value": "[check.value]"
            }
          }                    
        ]
      }
    }
  }    