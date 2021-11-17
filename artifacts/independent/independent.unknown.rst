independent.unknown
===================

Description
  -----------

The independent.unknown test acts as a placeholder for tests whose
implementation is unknown. This test always evaluates to a result of
‘unknown’. Any information that is known about the test should be held
in the notes child element that is available through the extension of
the abstract test element. It extends the standard TestType as defined
in the oval-definitions-schema and one should refer to the TestType
description for more information. Note that for an unknown_test, the
required check attribute that is part of the extended TestType should be
ignored during evaluation and hence can be set to any valid value.

Technical Details
  -----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

======= ====== ===========
Name    Type   Description
======= ====== ===========
unknown String 
======= ====== ===========

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - independent.unknown

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

There are no Test Type Parameters.

Generated Content
~~~~~~~~~~~~~~~~~

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION_NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[RECOMMENDATION TITLE]</ae:title>
        <ae:artifact type="[ARTIFACTTYPE NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="unknown">[unknown.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TESTTYPE NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="unknown">[unknown.value]</ae:parameter>
          </ae:parameters>
        </ae:test>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``independent.unknown`` artifacts, the xccdf:check looks like this.

::

  <check system='http://oval.mitre.org/XMLSchema/oval-definitions-5'>
    <check-content-ref 
      href='[BENCHMARK NAME]' 
      name='oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]'/>
  </check>

OVAL
''''

Test

::

  <unknown_test
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]'
    check_existence='[check_existence.value]' 
    check='[check.value]' 
    comment='[RECOMMENDATION TITLE]'
    version='[version.value]'/>

Object

::

   N/A

State

::

   N/A

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: [ARTIFACTTYPE NAME]
      parameters:
      - parameter: 
          name: unknown
          type: string
          value: [unknown.value]
    test:
      type: [TESTTYPE NAME]
      parameters:   
      - parameter: 
          name: unknown
          type: string
          value: [unknown.value]

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": [
        "ARTIFACT-OVAL-ID"
      ],
      "artifact-title": [
        "RECOMMENDATION TITLE"
      ],
      "artifact": {
        "type": [
          "ARTIFACTTYPE NAME"
        ],
        "parameters": [
          {
            "parameter": {
              "name": "unknown",
              "type": "string",
              "value": [
                "unknown.value"
              ]
            }
          }
        ]
      },
      "test": {
        "type": [
          "TESTTYPE NAME"
        ],
        "parameters": [
          {
            "parameter": {
              "name": "unknown",
              "type": "string",
              "value": [
                "unknown.value"
              ]
            }
          }
        ]
      }
    }
  }
