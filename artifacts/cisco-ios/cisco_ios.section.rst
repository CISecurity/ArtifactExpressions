Cisco IOS: Section Config
=========================

Description
-----------

The Cisco IOS: Section Config test is used to check the properties of specific output lines from a configuration section.


The section_object element is used by a section test to define the name of a section command to be tested.

The section_state element defines the different information that can be used to evaluate the result of a specific section command. This includes the name of ths section_command and the corresponding config lines. 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**cisco_ios.section**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| cisco_ios.section_name      | string  | The name of the section for which  |
|                             |         | to collect configuration           |
|                             |         | information. Cannot be blank.      |
+-----------------------------+---------+------------------------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Cisco IOS: Section Existence Test
  - Cisco IOS: Section Config Line

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**cisco_ios.section_existence_test**

=============== ====== ============================================
Name            Type   Description
=============== ====== ============================================
existence_check string Number of sections expected to be collected.
=============== ====== ============================================

NOTE: The ``existence_check`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_satisfy
  - none_exist
  - only_one_exists

**cisco_ios.section_config_line**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| section_config_line         | string  | One config line of the collected   |
|                             |         | configuration section.             |
+-----------------------------+---------+------------------------------------+
| operation                   | string  | Comparison Operator.               |
+-----------------------------+---------+------------------------------------+
| entity_check                | string  | The number of section              |
|                             |         | configuration lines which must     |
|                             |         | match the expected state.          |
+-----------------------------+---------+------------------------------------+

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

NOTE: The ``entity_check`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_exist
  - only_one_exists

Generated Content
~~~~~~~~~~~~~~~~~

**cisco_ios.section_existence_test**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:complex-check operator="OR">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
        <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
          <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
          <ae:title>[ARTIFACT-TITLE]</ae:title>
          <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="cisco_ios.section_name">[cisco_ios.section_name.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="existence_check">[existence_check.value]</ae:parameter>
            </ae:parameters>
          </ae:test>
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  </xccdf:complex-check>   

SCAP
^^^^

XCCDF
'''''

For ``cisco_ios.section cisco_ios.section_existence_test`` artifacts, the xccdf:check looks like this. There is no Value element in the xccdf for this Artifact. 

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
    <check-content-ref 
      href="[BENCHMARK NAME]"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
""

Test

::

  <section_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#ios"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </section_test>

Object

::

  <section_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#ios"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <section_command>[section_command.value]</section_command>
  </section_object>

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
            name: "cisco_ios.section_name"
            dt: "string"
            value: "[cisco_ios.section_name.value]"
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
      "artifact-title": "[RECOMMENDATION-TITLE]",
      "artifact": {
        "type": "[ARTIFACT-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "cisco_ios.section_name",
              "type": "string",
              "value": "[cisco_ios.section_name.value]"
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

**cisco_ios.section_config_line**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:complex-check operator="OR">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
        <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
          <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
          <ae:title>[ARTIFACT-TITLE]</ae:title>
          <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="cisco_ios.section_name">[cisco_ios.section_name.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="section_config_line">[section_config_line.value]</ae:parameter>
              <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
              <ae:parameter dt="string" name="entity_check">[entity_check.value]</ae:parameter>
            </ae:parameters>
          </ae:test>
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  </xccdf:complex-check>   

SCAP
^^^^

XCCDF
'''''

For ``cisco_ios.section cisco_ios.section_config_line`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    type="string"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``cisco_ios.section cisco_ios.section_config_line`` artifacts, the xccdf:check looks like this.

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
""

Test

::

  <section_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#ios"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </section_test>

Object

::

  <section_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#ios"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <section_command>[section_command.value]</section_command>
  </section_object>

State

::

  <section_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#ios"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <config_line 
      entity_check="[entity_check.value]"
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </section_state>  

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
            name: "cisco_ios.section_name"
            dt: "string"
            value: "[cisco_ios.section_name.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:   
        - parameter: 
            name: "operation"
            dt: "string"
            value: "[operation.value]"
        - parameter: 
            name: "entity_check"
            dt: "string"
            value: "[entity_check.value]"              

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact-title": "[RECOMMENDATION-TITLE]",
      "artifact": {
        "type": "[ARTIFACT-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "cisco_ios.section_name",
              "type": "string",
              "value": "[cisco_ios.section_name.value]"
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
              "name": "entity_check",
              "type": "string",
              "value": "[entity_check.value]"
            }
          }          
        ]
      }
    }
  }

