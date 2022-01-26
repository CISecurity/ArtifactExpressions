IIS: Application Pool
=====================

Description
-----------

An Application Pool Test contains configuration settings for all application pools running on your Internet Information Services (IIS) 7 or later server. An application pool defines a group of one or more worker processes, configured with common settings that serve requests to one or more applications that are assigned to that application pool. Because application pools allow a set of Web applications to share one or more similarly configured worker processes, they provide a convenient way to isolate a set of Web applications from other Web applications on the server computer. Process boundaries separate each worker process; therefore, application problems in one application pool do not affect Web sites or applications in other application pools. Application pools significantly increase both the reliability and manageability of your Web infrastructure.

The applicationpool_object element is used by an applicationpool_test to define the
name of the Application Pool to be evaluated.

The applicationpool_state element defines various information about the Application Pool configuration settings under evaluation.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**iis.applicationpool**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| applicationpool_name        | string  | The name of the application pool   |
|                             |         | to collect. Can be a regex.        |
+-----------------------------+---------+------------------------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - IIS: Application Pool

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**iis.applicationpool**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| operator                    | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+
| value                       | string  |                                    |
+-----------------------------+---------+------------------------------------+
| configuration_setting       | string  | The name of application pool       |
|                             |         | property to test.                  |
+-----------------------------+---------+------------------------------------+
| data_type                   | string  | The data type of the application   |
|                             |         | pool property to test.             |
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

NOTE: The ``configuration_setting`` parameter is governed by a constraint allowing only the following values:
  - application_count
  - identity_type

NOTE: The ``data_type`` parameter is governed by a constraint allowing only the following values:
	- boolean
	- float
	- int
	- string
	- version
	- set

Generated Content
~~~~~~~~~~~~~~~~~

**iis.applicationpool**

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
            <ae:parameter dt="string" name="applicationpool_name">[applicationpool_name.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
            <ae:parameter dt="string" name="configuration_setting">[configuration_setting.value]</ae:parameter>
            <ae:parameter dt="string" name="data_type">[data_type.value]</ae:parameter>
            <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
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

For ``iis.applicationpool`` ``iis.applicationpool`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    type="string"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``iis.applicationpool`` ``iis.applicationpool`` artifacts, the XCCDF check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
    <check-content-ref 
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <applicationpool_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iis"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </applicationpool_test>

Object

::

  <applicationpool_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iis"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <applicationpool_name operation="pattern match">[applicationpool_name.value]</applicationpool_name>
  </applicationpool_object>   

State

::

  <applicationhostconfig_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iis"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <[configuration_setting.value] 
      datatype="[data_type.value]"
      operation="[operator.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </applicationhostconfig_state>   

Variable     

::

  <external_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="boolean"
    comment="This value is used in [RECOMMENDATION-TITLE]"
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
            name: "applicationpool_name"
            dt: "string"
            value: "[applicationpool_name.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "operator"
            dt: "string"
            value: "[operator.value]"
        - parameter: 
            name: "configuration_setting"
            dt: "string"
            value: "[configuration_setting.value]"
        - parameter:
            name: "data_type"
            dt: "string"
            value: "[data_type.value]"
        - parameter: 
            name: "value"
            dt: "string"
            value: "[value.value]"

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
              "name": "applicationpool_name",
              "type": "string",
              "value": "[applicationpool_name.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
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
              "name": "configuration_setting",
              "type": "string",
              "value": "[configuration_setting.value]"
            }
          },
          {
            "parameter": {
              "name": "data_type",
              "type": "string",
              "value": "[data_type.value]"
            }
          },
          {
            "parameter": {
              "name": "value",
              "type": "string",
              "value": "[value.value]"
            }
          }
        ]
      }
    }
  }