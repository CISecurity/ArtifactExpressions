Cisco ASA: Line Object With Untrusted Interfaces
================================================

Description
-----------

The Cisco ASA: Line Object With Untrusted Interfaces test is used to check the properties of specific output lines from a SHOW command, such as SHOW RUNNING-CONFIG.

The line_object element is used by a line_test to define the name of a SHOW sub-command to be tested.

The line_state element defines the different information that can be used to evaluate the result of a specific SHOW sub-command. This includes the name of ths sub-command and the corresponding config line. 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**cisco_asa.line_object_with_untrusted_interfaces**

================ ====== ==========================
Name             Type   Description
================ ====== ==========================
show_run_command string Show Run command fragment.
================ ====== ==========================

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Cisco ASA: Line Config Line
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

**cisco_asa.untrusted_interfaces_state**

============ ====== ==========================
Name         Type   Description
============ ====== ==========================
regex_prefix string Regular expression prefix.
regex_suffix string Regular expression suffix.
check        string Check enumeration value.
============ ====== ==========================

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
              <ae:parameter dt="string" name="show_run_command">[show_run_command.value]</ae:parameter>
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

For ``cisco_asa.line_object_with_untrusted_interfaces`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    type="string"
    operator="pattern match">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``cisco_asa.line_object_with_untrusted_interfaces`` artifacts, the xccdf:check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
    <check-content-ref 
      href="[BENCHMARK-TITLE]" 
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
    check="all" 
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
    <show_subcommand
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2" />
  </line_object>

State

::

  <line_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#asa" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[ARTIFACT-TITLE]" 
    version="1">
    <config_line 
      operation="pattern match" 
      var_check="[var_check.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </line_state>

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
    version="1" />
    <concat>
      <literal_component>[literal_component.value]</literal_component>
      <variable_component
        var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
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
            name: "show_run_command"
            dt: "string"
            value: "[show_run_command.value]"
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
              "name": "show_run_command",
              "type": "string",
              "value": "[show_run_command.value]"
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

**cisco_asa.untrusted_interfaces_state**

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
              <ae:parameter dt="string" name="show_run_command">[show_run_command.value]</ae:parameter>
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

For ``cisco_asa.line_object_with_untrusted_interfaces cisco_asa.untrusted_interfaces_state`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    type="string"
    operator="pattern match">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``cisco_asa.line_object_with_untrusted_interfaces cisco_asa.untrusted_interfaces_state`` artifacts, the xccdf:check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
    <check-content-ref 
      href="[BENCHMARK-TITLE]" 
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
    check="all" 
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
    <show_subcommand
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2" />
  </line_object>

State

::

  <line_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#asa" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[ARTIFACT-TITLE]" 
    version="1">
    <config_line 
      operation="pattern match" 
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]3" />
  </line_state>

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
    version="1" />
    <concat>
      <literal_component>[literal_component.value]</literal_component>
      <variable_component
        var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    </concat>
  </local_variable>  

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]3"
    datatype="string"
    comment="This value is used in Rule: [RECOMMENDATION-TITLE]"
    version="1" />
    <concat>
      <literal_component>[literal_component.value]</literal_component>
      <variable_component
        var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
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
            name: "show_run_command"
            dt: "string"
            value: "[show_run_command.value]"
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
              "name": "show_run_command",
              "type": "string",
              "value": "[show_run_command.value]"
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
              "value": "[check_line.value]"
            }
          }
        ]
      }
    }
  }  