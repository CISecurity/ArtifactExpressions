Unix: Shadow Parameter
======================

Description
-----------

The Unix: Shadow Parameter test is used to check information from the /etc/shadow file for a specific user. This file contains a user’s password, but also their password aging and lockout information.

The required shadow_object element is used to define the shadow file to be evaluated. A shadow object consists of a single user entity that identifies the username associted with the shadow file.

The optional shadows_state element defines the different information associated with the system shadow file.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

Human ID: 
  - unix.shadow_parameter_v1

.. table:: unix.shadow_parameter_v1_parameters
   :widths: 33, 8, 33
=================================  ========  =================================
Name                               Type      Description  
=================================  ========  =================================
operation                          string    Comparison operation.
username                           string    Username to match. Cannot be blank.
parameter                          string    Shadow parameter to check.
=================================  ========  =================================

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
	- not equal
	- pattern match
	- set is empty
	- set white list


NOTE: The ``parameter`` parameter is governed by a constraint allowing only the following values: 
	- username
	- password
	- chg_lst
	- chg_allow 
	- chg_req
	- exp_warn
	- exp_inact
	- exp_date
	- flag
	- encrypt_method


Supported Test Types
~~~~~~~~~~~~~~~~~~~~

- Equals
- Equal
- Not Equal
- Less Than
- Less Than Or Equal
- Greater Than
- Greater Than Or Equal
- Pattern Match
- Pattern Not Match

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

Human IDs:
  - equals
  - not equal
  - less than
  - less than or equal
  - greater than
  - greater than or equal
  - pattern match
  - pattern not match

.. table:: equals_parameters
   :widths: 33, 8, 33  
=================================  ========  =================================
Name                               Type      Description
=================================  ========  =================================
value                              string    The value to be tested.
data_type                          string    The data type of the value.
=================================  ========  =================================

NOTE: The ``data_type`` parameter is governed by a constraint allowing only the following values:
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
            <ae:parameters>
              <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
              <ae:parameter dt="string" name="username">[username.value]</ae:parameter>
              <ae:parameter dt="string" name="parameter">[parameter.value[</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
              <ae:parameter dt="string" name="data_type">[data_type.value]</ae:parameter>
            </ae:parameters>
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

For ``unix.shadow_parameter_v1`` artifacts, an XCCDF Value element is generated.

::

  <Values>
    <Value 
      id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" 
      type="string"
      operator="[operatpr.value]">
      <title>[RECOMMENDATION-TITLE]</title>
      <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
      <value>[value.value]</value>
    </Value>
  </Values>

For ``unix.shadow_parameter_v1`` artifacts, the xccdf:check looks like this.

::

  <xccdf:complex-check operator="AND">
    <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
      <check-export 
        export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
        value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
      <check-content-ref 
        href="CIS_AlmaLinux_OS_8_Benchmark_v1.0.0-oval.xml" 
        name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
    </check>
  </xccdf:complex-check>


OVAL
''''

Test    

::

  <shadow_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="all"
    check="[check.value]"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </shadow_test>

Object      

::

  <shadow_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <username 
      operation="[operation.value]">
      [username.value]
    </username>
  </shadow_object>

State     

::

  <shadow_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <[parameterName.value] 
      datatype="[datatype.value]" 
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </shadow_state>

Variable        

::

  <external_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    datatype="[datatype.value]" 
    version="1"
    comment="This value is used in [RECOMMENDATION-TITLE]" />


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
            name: "username"
            dt: "string"
            value: "[username.value]"
        - parameter: 
            name: "parameter"
            dt: "string"
            value: "[parameter.value]"
        - parameter: 
            name: "command_line_operation"
            dt: "string"
            value: "[command_line_operation.value]"
        - parameter: 
            name: "pid_operation"
            dt: "string"
            value: "[pid_operation.value]"
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
        "type": "[ARTIFACT-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "username",
              "type": "string",
              "value": "[username.value]"
            }
          },
          {
            "parameter": {
              "name": "parameter",
              "type": "string",
              "value": "[parameter.value]"
            }
          },
          {
            "parameter": {
              "name": "command_line_operation",
              "type": "string",
              "value": "[command_line_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "pid_operation",
              "type": "string",
              "value": "[pid_operation.value]"
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