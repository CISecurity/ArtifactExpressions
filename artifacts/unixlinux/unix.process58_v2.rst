unix:process58
==============

Description
-----------

The unix:process58 test is used to check information found in the UNIX
processes. It is equivalent to parsing the output of the ps command.

The required process58_object element is used to define the specific
process(es) to be evaluated. A process58_object defines the command line
used to start the process(es) and pid.

The optional process58_state element defines the different metadata
associate with the UNIX processes.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

Human ID:
  - unix.process58_v2

+------------------------+--------+-----------------------------+
| Name                   | Type   | Description                 |
+========================+========+=============================+
| command_line           | string | The string used to start    |
|                        |        | the process. This includes  |
|                        |        | any parameters that are     |
|                        |        | part of the command line.   |
|                        |        | Cannot be blank.            |
+------------------------+--------+-----------------------------+
| pid                    | int    | The process ID of the       |
|                        |        | process.                    |
+------------------------+--------+-----------------------------+
| command_line_operation | string | Specifies what operation is |
|                        |        | to be performed using the   |
|                        |        | Command value.              |
+------------------------+--------+-----------------------------+
| pid_operation          | string | Specifies what operation is |
|                        |        | to be performed using the   |
|                        |        | Process ID value.           |
+------------------------+--------+-----------------------------+

NOTE: The ``command_line_operation`` parameter is governed by a constraint allowing only the following values:
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
  - subset of
  - superset of

NOTE: The ``pid_operation`` parameter is governed by a constraint allowing only the following values:
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

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - unix:process58_command_line

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

Human ID:
  - unix.process58_command_line_v1

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
| datatype        | string | The data type of the value.             |
+-----------------+--------+-----------------------------------------+
| command_line    | string | The string used to start the process.   |
|                 |        | This includes any parameters that are   |
|                 |        | part of the command line.               |
+-----------------+--------+-----------------------------------------+

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_satisfy
  - none_exist
  - only_one_exists

NOTE: The ``check`` parameter is governed by a constraint allowing only the following values:
  - all
  - at least one
  - none satisfy
  - only one

NOTE: The ``operation`` parameter is governed by a constraint allowing
only the following values:

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

NOTE: The ``datatype`` parameter is governed by a constraint allowing only the following values:
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
               <ae:parameter dt="string" name="command_line">[command_line.value]</ae:parameter>
               <ae:parameter dt="string" name="command_line_operation">command_line_operation.value]</ae:parameter>
               <ae:parameter dt="integer" name="pid">[pid.value]</ae:parameter>
               <ae:parameter dt="string" name="pid_operation">[pid_operation.value]</ae:parameter>
             </ae:parameters>
           </ae:artifact>
           <ae:test type="[TEST-TYPE-NAME]">
             <ae:parameters>
               <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
               <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
               <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
               <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
               <ae:parameter dt="string" name="command_line">[command_line.value]</ae:parameter>
             </ae:parameters>
           </ae:test>
         </ae:artifact_expression>
       </xccdf:check-content>
     </xccdf:check>
   </xccdf:complex-check>

SCAP
^^^^

XCCDF
'''''

For ``unix.process58_v2`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

::

   <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
     <check-content-ref 
       href="{BENCHMARK_NAME]"
       name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
   </check>

OVAL
''''

Test

::

   <process58_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
     check_existence="all_exist"
     check="all"
     comment="[RECOMMENDATION-TITLE]"
     version="1">
     <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
     <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
   </process58_test>

Object

::

   <process58_object 
     xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
     comment="[RECOMMENDATION-TITLE]"
     version="1">
     <command_line 
       operation="[operation.value]">
       [command_line.value]
     </command_line>
     <pid 
       datatype="int" 
       operation="[operation.value]">
       [pid.value]
     </pid>
   </process58_object>

State

::

   <process58_state 
     xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
     comment="[RECOMMENDATION-TITLE]"
     version="1">
     <command_line 
       operation="[operation.value]" 
       datatype="int">
       [command_line.value]
     </command_line>
   </process58_state>

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
             name: "command_line"
             dt: "string"
             value: "[command_line.value]"
         - parameter: 
             name: "pid"
             dt: "string"
             value: "[pid.value]"
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
         - parameter: 
             name: "data_type"
             dt: "string"
             value: "[data_type.value]"
         - parameter: 
             name: "command_line"
             dt: "string"
             value: "[command_line.value]"    

JSON
^^^^

::

   {
     "artifact-expression": {
       "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
       "artifact-title": "[RECOMMENDATION-TITLE]",
       "artifact": {
         "type": "unix.process58_v2",
         "parameters": [
           {
             "parameter": {
               "name": "command_line",
               "type": "string",
               "value": "[command_line.value]"
             }
           },
           {
             "parameter": {
               "name": "pid",
               "type": "string",
               "value": "[pid.value]"
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
               "name": "command_line",
               "type": "string",
               "value": "[command_line.value]"
             }
           }
         ]
       }
     }
   }
