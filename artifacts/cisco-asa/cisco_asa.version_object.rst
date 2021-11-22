Cisco ASA: Version Object
=========================

Description
-----------

The Cisco ASA: Version Object test is used to check the version of the PIX
operating system. It is based off of the SHOW VERSION command. It
extends the standard TestType as defined in the oval-definitions-schema
and one should refer to the TestType description for more information.
The required object element references a version_object and the optional
state element specifies the data to check.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**cisco_asa.version_object**

==== ==== ===========
Name Type Description
==== ==== ===========
N/A
==== ==== ===========

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Cisco ASA: Major Version
  - Cisco ASA: Major/Minor Version

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**cisco_asa.major_version**

============= ====== ====================
Name          Type   Description
============= ====== ====================
operation     string Comparison operator.
major_version string Major version.
============= ====== ====================

NOTE: The ``operation`` parameter is governed by a constraint allowing only the following values:
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

**cisco_asa.major_minor_version**

+-------------------------+---------+----------------------------------------+
| Name                    | Type    | Description                            |
+=========================+=========+========================================+
| asa_major_release       | string  | The asa_major_releaseis the dotted     |
|                         |         | version that starts a version string.  |
+-------------------------+---------+----------------------------------------+
| major_release_operation | string  | Comparison operator.                   |
+-------------------------+---------+----------------------------------------+
| minor_release_operation | string  | Minor Release Comparison operator.     |
+-------------------------+---------+----------------------------------------+
| asa_minor_release       | string  | The asa_minor_release is the dotted    |
|                         |         | version that starts a version string.  |
+-------------------------+---------+----------------------------------------+

NOTE: The ``major_release_operation`` and ``minor_release_operation`` parameters are governed by a constraint allowing only the following values:
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

Generated Content
~~~~~~~~~~~~~~~~~

**cisco_asa.major_version**

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
          <ae:parameters/>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
            <ae:parameter dt="string" name="major_version">[major_version.value]</ae:parameter>
          </ae:parameters>
        </ae:test>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``cisco_asa.version_object`` artifacts, the xccdf:check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"/>
    <check-content-ref 
      href="[BENCHMARK NAME]" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]"/>
  </check>

OVAL
''''

Test

::

  <version_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[RECOMMENDATION-TITLE]"
    version="[version.value]">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"/>
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"/>
  </version_test>

Object

::

  <version_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[RECOMMENDATION-TITLE]"
    version="[version.value]">
  </version_object >

State

::

  <version_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[RECOMMENDATION TITLE]"
    version="[version.value]">
    <asa_major_release 
      datatype="[datatype.value]" 
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"/>
    <asa_minor_release 
      datatype="[datatype.value]" 
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"/>
  </version_state>

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact-title: "[RECOMMENDATION-TITLE]"
    artifact:
      type: "[ARTIFACT-TYPE-NAME]"
      parameters:
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "operation"
            dt: "string"
            value: "[operation.value]"
        - parameter:
            name: "major_version"
            dt: "string"
            value: "[major_version.value]"

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact-title": "[RECOMMENDATION-TITLE]",
      "artifact": {
        "type": "[ARTIFACT-TYPE-NAME]",
        "parameters": null
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
              "name": "major_version",
              "type": "string",
              "value": "[major_version.value]"
            }
          }
        ]
      }
    }
  }
