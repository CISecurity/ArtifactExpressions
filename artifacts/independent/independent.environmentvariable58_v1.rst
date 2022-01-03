independent:environmentvariable58_v1
======================================

Description
-----------

This item stores information about an environment variable, the process ID of 
the process from which it was retrieved, and its corresponding value.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

+-------------------+---------+----------------------------------------+
| Name              | Type    | Description                            |
+===================+=========+========================================+
| name              | string  | This element describes the name of an  |
|                   |         | environment variable. Cannot be blank. |
+-------------------+---------+----------------------------------------+
| check_existence   | string  | Defines how many items should be       |
|                   |         | collected.                             |
+-------------------+---------+----------------------------------------+

check_existence NOTE: This parameter is governed by a constraint
allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_satisfy
  - none_exist
  - only_one_exists

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - independent:environmentvariable58_v1

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

independent:environmentvariable58_v1
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+-------------------+---------+----------------------------------------+
| Name              | Type    | Description                            |
+===================+=========+========================================+
| check             | string  | Defines how many collected items must  |
|                   |         | match the expected state.              |
+-------------------+---------+----------------------------------------+
| operation         | string  | comparison operation.                  |
+-------------------+---------+----------------------------------------+
| datatype          | string  | datatype.                              |
+-------------------+---------+----------------------------------------+
| value             | string  | The actual value of the specified      |
|                   |         | environment variable. Cannot be blank  |
+-------------------+---------+----------------------------------------+

check NOTE: This parameter is governed by a constraint allowing only the 
following values: 
  - all
  - at least one
  - none satisfy
  - only one

operation NOTE: This parameter is governed by a constraint allowing only the 
following values: 
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

datatype NOTE: This parameter is governed by a constraint allowing only the 
following values: 
  - boolean
  - float
  - int
  - string
  - version
  - set

Generated Content
~~~~~~~~~~~~~~~~~

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION_NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[RECOMMENDATION TITLE]</ae:title>
        <ae:artifact type="[ARTIFACTTYPE NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="name">[name.value]</ae:parameter>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TESTTYPE NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
            <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
            <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
          </ae:parameters>
        </ae:test>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>  

SCAP
^^^^

XCCDF
'''''

For ``independent.mysql_text_file_content_v1`` artifacts, the xccdf:check looks like this.

::

  <check system='http://oval.mitre.org/XMLSchema/oval-definitions-5'>
    <check-export 
      export-name='oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]' 
      value-id='xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var' />
    <check-export 
      export-name='oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]' 
      value-id='xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var' />
    <check-content-ref 
      href='[BENCHMARK NAME]'
      name='oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]' />
  </check>

OVAL
''''

Test

::

  <environmentvariable58_test 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]' 
    check_existence='[check_existence.value]' 
    check='[check.value]' 
    comment='[RECOMMENDATION TITLE]' 
    version='[version.value]'>
    <object object_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]' />
    <state state_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]' />
  </environmentvariable58_test>

Object

::

  <environmentvariable58_object 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
    comment='[RECOMMENDATION TITLE]' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]' 
    version='[version.value]'>
    <name>[name.value]</name>
  </environmentvariable58_object>

State

::

  <environmentvariable58_state 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]' 
    comment='[RECOMMENDATION TITLE]' 
    version='[version.value]'>
    <value 
      datatype='[datatype.value]' 
      operation='[operation.value]'>
      [value.value]
    </value>
  </environmentvariable58_state>

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact-title: "[RECOMMENDATION TITLE]"
    artifact:
      type: "[ARTIFACTTYPE NAME]"
      parameters:
        - parameter: 
            name: "name"
            type: "string"
            value: "[name.value]"
        - parameter: 
            name: "check_existence"
            type: "string"
            value: "[check_existence.value]"
    test:
      type: "[TESTTYPE NAME]"
      parameters:   
        - parameter: 
            name: "check"
            type: "string"
            value: "[check.value]"
        - parameter: 
            name: "operation"
            type: "string"
            value: "operation.value]"
        - parameter: 
            name: "datatype"
            type: "string"
            value: "[datatype.value]"
        - parameter: 
            name: "value"
            type: "string"
            value: "value.value]"

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact-title": "[RECOMMENDATION TITLE]",
      "artifact": {
        "type": "[ARTIFACTTYPE NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "name",
              "type": "string",
              "value": "[name.value]"
            }
          },
          {
            "parameter": {
              "name": "check_existence",
              "type": "string",
              "value": "[check_existence.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TESTTYPE NAME]",
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
              "name": "value",
              "dt": "string",
              "value": "[value.value]"
            }
          }
        ]
      }
    }
  }