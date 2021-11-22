Linux: Software Package
=======================

Description
-----------

The linux.software_package_v1 test is used to check the RPM header
information for a given RPM package.

The rpminfo_object element is used to define the object to be
evaluated. An rpm info object consists of a single name entity that
identifies the package being checked.

The rpminfo_state element defines the different information
that can be used to evaluate the specified rpm. This includes the
architecture, epoch number, and version numbers. Most of this
information can be obtained through the rpm function.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

linux.software_package_v1
^^^^^^^^^^^^^^^^^^^^^^^^^

+-----------+--------+-----------------------------------------------+
| Name      | Type   | Description                                   |
+===========+========+===============================================+
| existence | string | Existence requirement.                        |
+-----------+--------+-----------------------------------------------+
| check     | string | Defines how many collected items must match   |
|           |        | the expected state.                           |
+-----------+--------+-----------------------------------------------+
| operation | string | Comparison operation.                         |
+-----------+--------+-----------------------------------------------+
| package   | string | The name of the package being checked.        |
+-----------+--------+-----------------------------------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Null Test
  - Existence Test

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

null_test_v1
^^^^^^^^^^^^

==== ==== ===========
Name Type Description
==== ==== ===========
N/A       
==== ==== ===========

existence_test
^^^^^^^^^^^^^^

===== ====== =======================
Name  Type   Description
===== ====== =======================
value string The value to be tested.
===== ====== =======================

NOTE: The ``value`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_satisfy
  - none_exist
  - only_one_exists

Generated Content
~~~~~~~~~~~~~~~~~

null_test_v1
^^^^^^^^^^^^

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
             <ae:parameter dt="string" name="existence">[existence.value]</ae:parameter>
             <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
             <ae:parameter dt="string" name="package">[package.value]</ae:parameter>
             <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
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
 </xccdf:complex-check>

SCAP
^^^^

XCCDF
'''''

For ``linux.software_package_v1`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

::

 <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
   <check-content-ref 
     href="[BENCHMARK-TITLE]"
     name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
 </check>

OVAL
''''

Test

::

 <rpminfo_test 
   xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
   id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
   check_existence="[check_existence.value]" 
   check="[check.value]"
   comment="[RECOMMENDATION-TITLE]"
   version="1">
   <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
 </rpminfo_test>

Object

::

 <rpminfo_object 
   xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
   id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
   comment="[RECOMMENDATION-TITLE]"
   version="1">
   <name 
     operation="[operation.value]">
     [name.value]
   </name>
 </rpminfo_object>

State

::

  N/A

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
           name: "existence"
           dt: "string"
           value: "[existence.value]"
       - parameter: 
           name: "package"
           dt: "string"
           value: "[package.value]"
       - parameter: 
           name: "operation"
           dt: "string"
           value: "[operation.value]"
   test:
     type: "[TEST-TYPE-NAME]"
     parameters: []

JSON
^^^^

::

 {
   "artifact-expression": {
     "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
     "artifact-title": "[RECOMMENDATION-TITLE]",
     "artifact": {
       "type": "linux.software_package_v1",
       "parameters": [
         {
           "parameter": {
             "name": "existence",
             "type": "string",
             "value": "[existence.value]"
           }
         },
         {
           "parameter": {
             "name": "package",
             "type": "string",
             "value": "[package.value]"
           }
         },
         {
           "parameter": {
             "name": "operation",
             "type": "string",
             "value": "[operation.value]"
           }
         }
       ]
     },
     "test": {
       "type": "[TEST-TYPE-NAME]",
       "parameters": [
       ]
     }
   }
 }

Generated Content
~~~~~~~~~~~~~~~~~

existence_test
^^^^^^^^^^^^^^

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
              <ae:parameter dt="string" name="existence">[existence.value]</ae:parameter>
              <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
              <ae:parameter dt="string" name="package">[package.value]</ae:parameter>
              <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
            <ae:parameters/>
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

For ``linux.software_package_v1`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-content-ref 
      href="[BENCHMARK-TITLE]"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <rpminfo_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]" 
    check="[check.value]"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </rpminfo_test>

Object

::

  <rpminfo_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <name 
      operation="[operation.value]">
      [name.value]
    </name>
  </rpminfo_object>

State

::

  N/A

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
            name: "existence"
            dt: "string"
            value: "[existence.value]"
        - parameter: 
            name: "package"
            dt: "string"
            value: "[package.value]"
        - parameter: 
            name: "operation"
            dt: "string"
            value: "[operation.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
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
        "type": "linux.software_package_v1",
        "parameters": [
          {
            "parameter": {
              "name": "existence",
              "type": "string",
              "value": "[existence.value]"
            }
          },
          {
            "parameter": {
              "name": "package",
              "type": "string",
              "value": "[package.value]"
            }
          },
          {
            "parameter": {
              "name": "operation",
              "type": "string",
              "value": "[operation.value]"
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
          }
        ]
      }
    }
  }
