MS-SQL: Multi-DB-Query SCE
==========================

Description
-----------

The MS-SQL: Multi-DB-Query SCE test is used by a sql test to define the specific database and query to be evaluated. Connection information is supplied allowing the tool to connect to the desired database and a query is supplied to call out the desired setting.

There are no OVAL tests, objects or states generated.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**ms-sql.multi-db-query_sce_v1**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| sql                         | string  | The sql entity defines a query     |
|                             |         | used to identify the object(s) to  |
|                             |         | test against.                      |
+-----------------------------+---------+------------------------------------+
| sysdbs                      | string  | This determines whether the system |
|                             |         | databases will be assessed for     |
|                             |         | compliance. (Yes/No)               |
+-----------------------------+---------+------------------------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Null Test

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**null_test_v1**

==== ==== ===========
Name Type Description
==== ==== ===========
N/A
==== ==== ===========

Generated Content
~~~~~~~~~~~~~~~~~

**null_test**

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
            <ae:parameter dt="string" name="sql">[sql.value]</ae:parameter>
            <ae:parameter dt="string" name="sysdbs">[sysdbs.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters />
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

For ``ms-sql.multi-db-query_sce_v1`` ``null_test_v1`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]1_var"
    type="string"
    operator="equals">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID21_var"
    type="string"
    operator="equals">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>  

For ``ms-sql.multi-db-query_sce_v1`` ``null_test_v1`` artifacts, the XCCDF check looks like this.

::

  <check system="http://open-scap.org/page/SCE">
    <check-import import-name="stdout">
    <check-export 
      export-name="XCCDF_VALUE_CONNSTRING"
      value-id="xccdf_org.cisecurity_value_jdbc.url" />
    <check-export 
      export-name="XCCDF_VALUE_QUERY"
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]1_var" />
    <check-export 
      export-name="XCCDF_VALUE_INCLUDESYSDBS"
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]2_var" />
    <check-content-ref 
      href="sce/multi-db-query.ps1"
  </check>

OVAL
''''

Test

::

  N/A

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
            name: "sql"
            dt: "string"
            value: "[sql.value]"
        - parameter: 
            name: "sysdbs"
            dt: "string"
            value: "[sysdbs.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters: []   

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
              "name": "sql",
              "type": "string",
              "value": "[sql.value]"
            }
          },
          {
            "parameter": {
              "name": "sysdbs",
              "type": "string",
              "value": "[sysdbs.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": []
      }
    }
  }
