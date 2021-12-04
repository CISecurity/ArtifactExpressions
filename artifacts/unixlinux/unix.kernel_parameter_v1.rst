Unix: Kernel Parameter
======================

Description
-----------

The Unix: Kernel Parameter test is used to check the values associated
with the kernel parameters that are used by the local system. Test
elements evaluate the sysctl configuration file and files within the
sysctl.d directory, by looking at individual blocks of text.

The sysctl_object is used to define which kernel parameters on
the local system should be collected.

The textfilecontent54_object elements are used to define the
specific block(s) of text of a file(s) to be evaluated. The
textfilecontent54_object will only collect regular files on UNIX
systems.

The set of files to be evaluated may be identified with either a
complete filepath or a path and filename. Only one of these options may
be selected.

The sysctl_state contains two entities that are used to check
the kernel parameter name and value(s).

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**unix.kernel_parameter_v1**

========= ====== ===============================================
Name      Type   Description
========= ====== ===============================================
parameter string Kernel parameter to be checked.Cannot be blank.
========= ====== ===============================================

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

  <xccdf:complex-check operator="AND">
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
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1" />
          </ae:profiles>          
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  </xccdf:complex-check>

SCAP
^^^^

XCCDF
'''''

For ``unix.kernel_parameter_v1`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    type="string"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``unix.kernel_parameter_v1`` artifacts, the xccdf:check looks like this.

::

  <xccdf:complex-check operator="AND">
    <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
      <check-export 
        export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
        value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
      <check-content-ref 
        href="[BENCHMARK-TITLE]"
        name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
    </check>
  </xccdf:complex-check>

OVAL
''''

Test

::

  <sysctl_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]1"
    check_existence="at_least_one_exists"
    check="all"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]1" />
  </sysctl_test>

  <textfilecontent54_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]2"
    check_existence="at_least_one_exists"
    check="all"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
  </textfilecontent54_test>

  <textfilecontent54_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]3"
    check_existence="at_least_one_exists"
    check="all"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]3" />
  </textfilecontent54_test>

Object

::

  <sysctl_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <name>[name.value]</name>
  </sysctl_object>

  <textfilecontent54_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <filepath>/etc/sysctl.conf</filepath>
    <pattern 
      operation="pattern match"
      datatype="string">
        [pattern.value]
    </pattern>
    <instance 
      datatype="int"
      operation="equals">
        1
    </instance>
  </textfilecontent54_object>

  <textfilecontent54_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]3"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <path>/etc/sysctl.d</path>
    <filename 
      operation="pattern match"
      datatype="string">
        .*
    </filename>
    <pattern 
      operation="pattern match"
      datatype="string">
        [pattern.value]
    </pattern>
    <instance 
      datatype="int"
      operation="equals">
        1
    </instance>
  </textfilecontent54_object>

State

::

  <sysctl_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]1"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <name 
      datatype="string"
      operation="equals">
        [name.value]
    </name>
    <value 
      datatype="[datatype.value]" 
      operation="[operation.value]" 
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </sysctl_state>

Variable

::

  <external_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="[datatype.value]"
    version="1"
    comment="This value is used in Rule: [RECOMMENDATION-TITLE]" />  

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
      "artifact-title": "[RECOMMENDATION-TITLE]",
      "artifact": {
        "type": "[ARTIFACT-TYPE-NAME]",
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
              "name": "data_type",
              "type": "string",
              "value": "[enabled.value]"
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
