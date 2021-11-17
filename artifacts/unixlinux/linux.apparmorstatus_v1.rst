linux:apparmorstatus
====================

Description
-----------

The linux:apparmorstatus test is used to check properties representing
the counts of profiles and processes as per the results of the
"apparmor_status" or "aa-status" command.

The required apparmorstatus_object element is used to define the
different information about the current AppArmor policy. There is
actually only one object relating to AppArmor Status and this is the
system as a whole. Therefore, there are no child entities defined. Any
test written to check AppArmor status will reference the same
apparmorstatus_object which is basically an empty object element.

The optional apparmorstatus_state element displays various information
about the current AppArmor policy. This item maps the counts of profiles
and processes as per the results of the "apparmor_status" or "aa-status"
command.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

linux.apparmorstatus_v1
^^^^^^^^^^^^^^^^^^^^^^^

==== ==== ===========
Name Type Description
==== ==== ===========
N/A       
==== ==== ===========

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

- linux:apparmorstatus_enforce_mode_profiles_count

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

linux.apparmorstatus_enforce_mode_profiles_count_v1
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+-----------------------------+--------+-----------------------------+
| Name                        | Type   | Description                 |
+=============================+========+=============================+
| check_existence             | string | Defines how many items      |
|                             |        | should be collected.        |
|                             |        | Typically set to 'at least  |
|                             |        | one'.                       |
+-----------------------------+--------+-----------------------------+
| check                       | string | Defines how many collected  |
|                             |        | items must match the        |
|                             |        | expected state.             |
+-----------------------------+--------+-----------------------------+
| operation                   | string | Comparison operation        |
+-----------------------------+--------+-----------------------------+
| datatype                    | string | The data type of the value  |
+-----------------------------+--------+-----------------------------+
| enforce_mode_profiles_count | int    | Displays the number of      |
|                             |        | profiles in enforce mode.   |
|                             |        | Cannot be blank.            |
+-----------------------------+--------+-----------------------------+

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
            <ae:parameters/>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
              <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
              <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
              <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
              <ae:parameter dt="string" name="enforce_mode_profiles_count">[enforce_mode_profiles_count.value]</ae:parameter>
            </ae:parameters>
          </ae:test>
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_2" />
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  </xccdf:complex-check>

SCAP
^^^^

XCCDF
'''''

For ``linux.apparmorstatus_v1`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

::

  <xccdf:complex-check operator="AND">
    <xccdf:check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
      <xccdf:check-content-ref
        href="[BENCHMARK-NAME]"
        name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
    </xccdf:check>
  </xccdf:complex-check>

OVAL
''''

Test

::

  <apparmorstatus_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#Linux"
    check="[check.value]"    
    check_existence="[check_existence.value]"
    comment="[RECOMMENDATION-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </apparmorstatus_test>

Object

::

  <apparmorstatus_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#Linux"
    comment="[RECOMMENDATION-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"    
    version="1" />

State

::

  <apparmorstatus_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#Linux"
    comment="[RECOMMENDATION-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"    
    version="1">
    <enforce_mode_profiles_count 
      datatype="[datatype.value]" 
      operation="[operation.value]">
      [enforce_mode_profiles_count.value]
    </enforce_mode_profiles_count>
  </apparmorstatus_state>

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
            name: "right_name"
            dt: "string"
            value: "[right_name.value]"
        - parameter: 
            name: xpath
            dt: "string"
            value: "[xpath.value]" 
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
            name: "enforce_mode_profiles_count"
            dt: "integer"
            value: "[enforce_mode_profiles_count.value]"

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

        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "check_existence",
              "type": "string",
              "value": "[check_existence.value]"
            }
          },
          {
            "parameter": {
              "name": "check",
              "type": "string",
              "value": "[check.value]"
            }
          },
          {
            "parameter": {
              "name": "operation",
              "type": "string",
              "value": "[operation.value]"
            }
          },
          {
            "parameter": {
              "name": "datatype",
              "type": "string",
              "value": "[datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "enforce_mode_profiles_count",
              "type": "integer",
              "value": "[enforce_mode_profiles_count.value]"
            }
          }
        ]
      }
    }
  }
