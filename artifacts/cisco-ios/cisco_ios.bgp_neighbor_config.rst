Cisco IOS: BGP Neighbor Config
==============================

Description
-----------

The Cisco IOS: BGP Neighbor Config test is used to check the bgp neighbor properties of bgp instances in IOS.

The bgpneighbor_object element is used by a bgpneighbor test to define a neighbor entity.

The bgpneighbor_state element defines the different information that can be used to evaluate the result of a bgp neighbor configuration. This includes the neighbor and the password option, if configured. 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**cisco_ios.bgp_neighbor_config**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| operator                    | string  | Comparison operator used for       |
|                             |         | collecting BGP Neighbor items.     |
+-----------------------------+---------+------------------------------------+
| neighbor                    | string  | The BGP Neighbor(s) to collect.    |
+-----------------------------+---------+------------------------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Cisco IOS: All BGP Neighbors Have A Password

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**cisco_ios:all_bgp_neighbor_password**

==== ==== ===========
Name Type Description
==== ==== ===========
N/A
==== ==== ===========

Generated Content
~~~~~~~~~~~~~~~~~

**cisco_ios:all_bgp_neighbor_password**

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
              <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
              <ae:parameter dt="string" name="neighbor">[neighbor.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters />
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

For ``cisco_ios.bgp_neighbor_config`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    type="string"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``cisco_ios.bgp_neighbor_config`` artifacts, the xccdf:check looks like this.

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

  <bgpneighbor_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iso"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="any_exist"
    check="all"
    comment="[ARTIFACT-TITLE]">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </bgpneighbor_test>

Object

::

  <bgpneighbor_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iso"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]">
    <neighbor operation="[operation.value]">[neighbor.value]</neighbor>
  </bgpneighbor_object>

State

::

  <bgpneighbor_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iso"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]">
    <password 
      operation="pattern match"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </bgpneighbor_state>

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
            name: "operator"
            dt: "string"
            value: "[operator.value]"
        - parameter: 
            name: "neighbor"
            dt: "string"
            value: "[neighbor.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:

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
              "name": "operator",
              "type": "string",
              "value": "[operator.value]"
            }
          },
          {
            "parameter": {
              "name": "neighbor",
              "type": "string",
              "value": "[neighbor.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": null
      }
    }
  }