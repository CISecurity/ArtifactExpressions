Linux: Auditd Rule
==================

Description
-----------

The Linux: Auditd Rule test is used to check the contents of audit
configuration and audit log files by looking at individual blocks of
text.

The required textfilecontent54_object element is used to define the
specific block(s) of text of a file(s) to be evaluated. The
textfilecontent54_object will only collect regular files on UNIX
systems.

The set of files to be evaluated may be identified with either a
complete filepath or a path and filename. Only one of these options may
be selected.

The optional textfilecontent54_state element contains entities that are
used to check the file path and name, as well as the text block in
question and the value of the subexpressions.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

Human ID:
   -  linux.auditd_rule_v1

+-----------------+--------+-----------------------------------------+
| Name            | Type   | Description                             |
+=================+========+=========================================+
| check_existence | string | Defines how many items should be        |
|                 |        | collected. Typically set to 'at least   |
|                 |        | one'.                                   |
+-----------------+--------+-----------------------------------------+

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values:
   -  all_exist
   -  any_exist
   -  at_least_one_exists
   -  none_satisfy
   -  none_exist
   -  only_one_exists

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

-  Set Includes

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

Human ID:
   -  set.includes_v1

========= ====== =============================================
Name      Type   Description
========= ====== =============================================
value     string The value included within the set of results.
data_type string The data type of the value.
========= ====== =============================================

NOTE: The ``data_type`` parameter is governed by a constraint allowing only the following values:
   -  boolean
   -  float
   -  int
   -  string
   -  version
   -  set

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
               <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
             </ae:parameters>
           </ae:artifact>
           <ae:test type="[TEST-TYPE-NAME]">
             <ae:parameters>
               <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
               <ae:parameter dt="string" name="data_type">[data_type.value]</ae:parameter>
             </ae:parameters>
           </ae:test>
           <ae:profiles>
             <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_2"/>
           </ae:profiles>
         </ae:artifact_expression>
       </xccdf:check-content>
     </xccdf:check>
   </xccdf:complex-check>

SCAP
^^^^

XCCDF
'''''

For ``linux.auditd_rule_v1`` artifacts, the xccdf:check looks like this.
There is no Value element in the XCCDF for this Artifact.

::

   <xccdf:complex-check operator="AND">
     <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
       <check-content-ref 
         href="[BENCHMARK-TITLE]" 
         name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
     </check>
   </xccdf:complex-check>

OVAL
''''

Test

::

   <textfilecontent54_test 
     xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"     
     check_existence="at_least_one_exists"
     check="all"
     comment="[RECOMMENDATION-TITLE]"
     version="1">
     <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
   </textfilecontent54_test>

Object

::

   <textfilecontent54_object 
     xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
     comment="[RECOMMENDATION-TITLE]" 
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"     
     version="1">
     <path>
       /etc/audit
     </path>
     <filename>
       auditd.rules
     </filename>
     <pattern
       datatype="[datatype.value]"
       operation="pattern match">
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
             name: "check_existence"
             dt: "string"
             value: "[check_existence.value]"
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
               "name": "check_existence",
               "type": "string",
               "value": "[check_existence.value]"
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
