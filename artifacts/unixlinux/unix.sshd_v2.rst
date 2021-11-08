unix.sshd_v2
============

Description
-----------

The unix:sshd_v2 test is used to check the contents of an sshd
configuration file, by looking at individual blocks of text.

The required sshd_object element is used to define the specific block(s)
of text of a file(s) to be evaluated. The sshd_object will only collect
regular files on UNIX systems.

The set of files to be evaluated may be identified with either a
complete filepath or a path and filename. Only one of these options may
be selected.

The optional sshd_state element contains entities that are used to check
the file path and name, as well as the text block in question and the
value of the subexpressions. Technical Details -----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

Human ID:
   -  unix.sshd_v2

+------+--------+----------------------------------------------------+
| Name | Type   | Description                                        |
+======+========+====================================================+
| name | string | The name element specifies the name(s) of the sshd |
|      |        | parameter(s) that should be collected from the     |
|      |        | local system. Cannot be blank.                     |
+------+--------+----------------------------------------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

-  unix:sshd

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

Human ID:
   -  unix.sshd_v2

+-----------------+--------+-----------------------------------------+
| Name            | Type   | Description                             |
+=================+========+=========================================+
| check_existence | string | Defines how many items should be        |
|                 |        | collected. Typically set to 'at least   |
|                 |        | one'.                                   |
+-----------------+--------+-----------------------------------------+
| check           | string | Defines how many collected items must   |
|                 |        | match the expected state.               |
+-----------------+--------+-----------------------------------------+
| operation       | string | Comparison operation.                   |
+-----------------+--------+-----------------------------------------+
| value           | string | The value(s) associated with the        |
|                 |        | specified sshd parameter.               |
+-----------------+--------+-----------------------------------------+
| datatype        | string | The data type of the value.             |
+-----------------+--------+-----------------------------------------+

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values:
   -  all_exist
   -  any_exist
   -  at_least_one_exists
   -  none_satisfy
   -  none_exist
   -  only_one_exists

NOTE: The ``check`` parameter is governed by a constraint allowing only the following values:
   -  all
   -  at least one
   -  none satisfy
   -  only one

NOTE: The ``operation`` parameter is governed by a constraint allowing only the following values:
   -  equals

      -  not equal
      -  case insensitive equals
      -  case insensitive not equal
      -  greater than
      -  less than
      -  greater than or equal
      -  less than or equal
      -  bitwise and
      -  bitwise or
      -  pattern match
      -  subset of
      -  superset of

NOTE: The ``datatype`` parameter is governed by a constraint allowing only the following values:
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
           <ae:title>[RECOMMENDATION-TITLE</ae:title>
           <ae:artifact type="[ARTIFACT-TYPE-NAME]">
             <ae:parameters>
               <ae:parameter dt="string" name="name">[name.value]</ae:parameter>
             </ae:parameters>
           </ae:artifact>
           <ae:test type="[TEST-TYPE-NAME]">
             <ae:parameters>
               <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
               <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
               <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
               <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
               <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
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

For ``unix.sshd_v2`` artifacts, the xccdf:check looks like this. There
is no Value element in the XCCDF for this Artifact.

::

   check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
     <check-content-ref 
       href="[BENCHMARK-TITLE]"
       name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
   </check>

OVAL
''''

Test

::

   <sshd_test 
     xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
     check_existence="[check_existence.value]"
     check="[check.value]"
     comment="[RECOMMENDATION-TITLE]"
     version="1">
     <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
     <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
   </sshd_test>

Object

::

   <sshd_object 
     xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
     comment="[RECOMMENDATION-TITLE]"
     version="1">
     <name>
       [name.value]
     </name>
   </sshd_object>

State

::

   <sshd_state 
     xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
     comment="[RECOMMENDATION-TITLE]"
     version="1">
     <value 
       datatype="[datatype.value]" 
       operation="[operation.value]">
       [value.value]
     </value>
   </sshd_state>

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
             name: "name"
             dt: "string"
             value: "[name.value]"
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
         - parameter: 
             name: "check_existence"
             dt: "string"
             value: "[check_existence.value]"
         - parameter: 
             name: "check"
             dt: "string"
             value: "[check.value]"
         - parameter: 
             name: "operation"
             dt: "string"
             value: "[operation.value]"

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
               "name": "name",
               "type": "string",
               "value": "[name.value]"
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
           },
           {
             "parameter": {
               "name": "check_existence",
               "type": "string",
               "value": "[check_existence.value]"
             }
           },
           {
             "parameter": {
               "name": "check",
               "type": "string",
               "value": "[check.value]"
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
       }
     }
   }
