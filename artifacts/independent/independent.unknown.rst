Independent: Unknown
====================

Description
-----------

An Independent: Unknown test acts as a placeholder for tests whose implementation is unknown. This test always evaluates to a result of 'unknown'. Any information that is known about the test should be held in the notes child element that is available through the extension of the abstract test element.

Note that for an unknown_test, the required check attribute that is part of the extended TestType should be ignored during evaluation and hence can be set to any valid value.

The unknown_test has no object or state elements.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**independent.unknown**

======= ====== ===========
Name    Type   Description
======= ====== ===========
unknown string 
======= ====== ===========

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Independent: Unknown

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**independent.unknown**

=======  ======  ===========
Name     Type    Description
=======  ======  ===========
unknown  string  Enter NA
=======  ======  ===========

Generated Content
~~~~~~~~~~~~~~~~~

**independent.unknown**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[ARTIFACT-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACT-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="unknown">[unknown.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="unknown">[unknown.value]</ae:parameter>
          </ae:parameters>
        </ae:test>
        <ae:profiles>
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1" />
        </ae:profiles>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``independent.unknown`` ``independent.unknown`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-content-ref
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <unknown_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1" />

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
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact-title: "[ARTIFACT-TITLE]"
    artifact:
      type: "[ARTIFACT-TYPE-NAME]"
      parameters:
        - parameter: 
            name: "unknown"
            dt: "string"
            value: "[unknown.value]"
    test:
      type: "[TEST-TYPE-NAME]"
        - parameter:
            name: "unknown"
            dt: "string"
            value: "[unknown.value]"

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
              "name": "unknown",
              "type": "string",
              "value": "[unknown.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "unknown",
              "type": "string",
              "value": "[unknown.value]"
            }
          }
        ]
      }
    }
  }
