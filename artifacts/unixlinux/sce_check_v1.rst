Script Check Engine Check
=========================

Description
-----------

The Script Check Engine Check test defines a check system by executing scripts in various scripting languages, then evaluating XCCDF rules compliance based on the results. 

There are no OVAL tests, objects or states generated.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

sce_check_v1
^^^^^^^^^^^^

====================== ======== ========================================
Name                   Type     Description  
====================== ======== ========================================
script                 string   The SCE script to run. Cannot be blank.
export_variable_value  string   The value of the export variable.
export_variable_type   string   The datatype of the export variable.
export_variable_name   string   The name of the export variable.
====================== ======== ========================================

NOTE: The ``export_variable_type`` parameter is governed by a constraint allowing only the following values:
  - boolean
  - float
  - int
  - string
  - version
  - set

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Null Test

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

null_test_v1
^^^^^^^^^^^^

====================== ======== ========================================
Name                   Type     Description  
====================== ======== ========================================
N/A
====================== ======== ========================================

Generated Content
~~~~~~~~~~~~~~~~~

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:complex-check operator="AND">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
        <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
          <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
          <ae:title>[RECOMMENDATION-TITLE]</ae:title>
          <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="script">[script.value]</ae:parameter>
              <ae:parameter dt="string" name="export_variable_value">[export_variable_value.value]</ae:parameter>
              <ae:parameter dt="string" name="export_variable_type">[export_variable_type.value]</ae:parameter>
              <ae:parameter dt="string" name="export_variable_name">[export_variable_name.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters />
          </ae:test>
          <ae:profiles>
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1 "/>
          </ae:profiles>          
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  </xccdf:complex-check>

SCAP
^^^^

XCCDF
'''''

For ``linux.sce_check_v1`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" 
    type="string"
    operator="equals">
    <title override>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``linux.sce_check_v1`` artifacts, the xccdf:check looks like this.

::

  <check system="http://open-SCAP.org/page/SCE">
    <check-import import-name="stdout" />
    <check-export 
      export-name="[export-name.value]" 
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
    <check-content-ref href="[SCRIPT-PATH]" />
  </check>

OVAL
''''

There are no OVAL tests, objects or states generated for ``linux.sce_check_v1``.

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact-title: "[RECOMMENDATION-TITLE]"
    artifact:
      type: "[ARTIFACT-TYPE-NAME]"
      parameters:
        - parameter: 
            name: "script"
            dt: "string"
            value: "[script.value]"
        - parameter: 
            name: "export_variable_value"
            dt: "string"
            value: "[export_variable_value.value]"
        - parameter: 
            name: "export_variable_type"
            dt: "string"
            value: "[export_variable_type.value]"  
        - parameter: 
            name: "export_variable_name"
            dt: "string"
            value: "[export_variable_name.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters: []

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
              "name": "script",
              "type": "string",
              "value": "[script.value]"
            }
          },
          {
            "parameter": {
              "name": "export_variable_value",
              "type": "string",
              "value": "[export_variable_value.value]"
            }
          },
          {
            "parameter": {
              "name": "export_variable_type",
              "type": "string",
              "value": "[export_variable_type.value]"
            }
          },
          {
            "parameter": {
              "name": "export_variable_name",
              "type": "string",
              "value": "[export_variable_name.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
      }
    }
  }