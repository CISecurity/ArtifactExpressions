Unix: Uname Parameter
=====================

Description
-----------

The Unix: Uname Parameter test The uname test reveals information about
the hardware the machine is running on. This information is the parsed
equivalent of uname -a. For example: "Linux quark 2.6.5-7.108-default #1
Wed Aug 25 13:34:40 UTC 2004 i686 i686 i386 GNU/Linux".

The uname_object element is used to define those objects to be
evaluated based on a specified state. There is actually only one object
relating to uname and this is the system as a whole. Therefore, there
are no child entities defined. Any test written to check uname will
reference the same uname_object which is basically an empty object
element.

The uname_state element defines the information about the
hardware the machine is running one.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**unix.uname_parameter_v1**

========= ====== =================================
Name      Type   Description
========= ====== =================================
parameter string The uname parameter to be tested.
========= ====== =================================

NOTE: The ``parameter`` parameter is governed by a constraint allowing only the following values: 
  - machine_class 
  - node_name 
  - os_name 
  - os_release 
  - os_version 
  - processor_type

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Equals
  - Not Equal
  - Less Than
  - Less Than Or Equal
  - Greater Than
  - Greater Than Or Equal
  - Pattern Match
  - Pattern Not Match

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

| **equals**
| **not equal**
| **less than**
| **less than or equal**
| **greater than**
| **greater than or equal**
| **pattern match**
| **pattern not match**
========= ====== ===========================
Name      Type   Description
========= ====== ===========================
value     string The value to be tested.
data_type string The data type of the value.
========= ====== ===========================

NOTE: The ``data_type`` parameter is governed by a constraint allowing only the following values:
  - boolean
  - float
  - int
  - string
  - version
  - set

Generated Content
~~~~~~~~~~~~~~~~~

| **equals**
| **not equal**
| **less than**
| **less than or equal**
| **greater than**
| **greater than or equal**
| **pattern match**
| **pattern not match**
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
          <ae:parameters>
            <ae:parameter dt="string" name="parameter">[parameter.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
            <ae:parameter dt="string" name="data_type">[data_type.value]</ae:parameter>
          </ae:parameters>
        </ae:test>
        <ae:profiles>
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_2" />
        </ae:profiles>          
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``unix.uname_parameter_v1`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    type="string"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``unix.uname_parameter_v1`` artifacts, the xccdf:check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
    <check-content-ref 
      href="[BENCHMARK-TITLE]"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <uname_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="all"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </uname_test>

Object

::

  <uname_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[RECOMMENDATION-TITLE]"
    version="1" />

State

::

  <uname_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <parameter 
      datatype="[datatype.value]"
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </uname_state>

Variable

::

  <external_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="[datatype.value]"
    comment="This value is used in [RECOMMENDATION-TITLE]"
    version="1" />

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
            name: "parameter"
            dt: "string"
            value: "[parameter.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter: 
            name: "value"
            dt: "string"
            value: "[value.value]"
        - parameter: 
            name: "data_type"
            dt: "string"
            value: "[data_type.value]"        

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact-title": "[RECOMMENDATION-TITLE]",
      "artifact": {
        "type": "unix.uname_parameter_v1",
        "parameters": [
          {
            "parameter": {
              "name": "parameter",
              "type": "string",
              "value": "[parameter.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "value",
              "type": "string",
              "value": "[value.value]"
            }
          },
          {
            "parameter": {
              "name": "data_type",
              "type": "string",
              "value": "[data_type.value]"
            }
          }
        ]
      }
    }
  }
