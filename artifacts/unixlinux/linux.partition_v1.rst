Linux: Partition
================

Description
-----------

The Linux: Partition test is used to check the information associated
with partitions on the local system.

The required partition_object is used to define which partitions on the
local system should be collected.

The optional partition_state element defines the different information
associated with a partition. This includes the name, filesystem type,
mount options, total space, space used, and space left.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

Human ID:
   -  linux.partition_v1

+-------------+--------+---------------------------------------------+
| Name        | Type   | Description                                 |
+=============+========+=============================================+
| mount_point | string | Filesystem mount point being tested. Cannot |
|             |        | be blank.                                   |
+-------------+--------+---------------------------------------------+
| existence   | string | Specifies how many items in the set must    |
|             |        | exist for the test to evaluate to true.     |
+-------------+--------+---------------------------------------------+
| check       | string | Defines how many collected items must match |
|             |        | the expected state.                         |
+-------------+--------+---------------------------------------------+

NOTE: The ``existence`` parameter is governed by a constraint allowing only the following values:
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

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

-  Null Test
-  Linux: Partition Option

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

Human ID:
   -  null_test_v1

==== ==== ===========
Name Type Description
==== ==== ===========
N/A       
==== ==== ===========

Human ID:
   -  linux.partition_option_v1

+-----------+--------+-----------------------------------------------+
| Name      | Type   | Description                                   |
+===========+========+===============================================+
| value     | string | The value to be tested.                       |
+-----------+--------+-----------------------------------------------+
| check     | string | Defines how many collected items must match   |
|           |        | the expected state.                           |
+-----------+--------+-----------------------------------------------+
| operation | string | Comparison operation.                         |
+-----------+--------+-----------------------------------------------+
| data_type | string | The data type of the value.                   |
+-----------+--------+-----------------------------------------------+

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

NOTE: The ``data_type`` parameter is governed by a constraint allowing only the following values:
   -  boolean
   -  float
   -  int
   -  string
   -  version
   -  set

Generated Content
~~~~~~~~~~~~~~~~~

null_test_v1

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
               <ae:parameter dt="string" name="existence">[existence_value]</ae:parameter>
               <ae:parameter dt="set" name="check">[check.value]</ae:parameter>
               <ae:parameter dt="string" name="mount_point">[mount_point.value]</ae:parameter>
             </ae:parameters>
           </ae:artifact>
           <ae:test type="[TEST-TYPE-NAME]">
             <ae:parameters />
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

For ``linux.partition_v1`` artifacts, the xccdf:check looks like this.
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

   <partition_test 
     xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
     check_existence="[check_existence.value]"
     check="[check.value]"
     comment="[RECOMMENDATION-TITLE]"
     version="1">
     <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
     <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
   </partition_test>

Object

::

   <partition_object
     xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
     comment="[RECOMMENDATION-TITLE]"
     version="1">
     <mount_point>
       [mount_point.value]
     </mount_point>
   </partition_object>

State

:

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
             name: "check"
             type: "set"
             value: "[check.value]"
         - parameter: 
             name: "mount_point"
             dt: "string"
             value: "[mount_point.value]"
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
         "type": "[ARTIFACT-TYPE-NAME]",
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
               "name": "check",
               "type": "set",
               "value": "[check.value]"
             }
           },
           {
             "parameter": {
               "name": "mount_point",
               "type": "string",
               "value": "[mount_point.value]"
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

.. _generated-content-1:

Generated Content
~~~~~~~~~~~~~~~~~

linux.partition_option_v1

.. _xccdfae-1:

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
               <ae:parameter dt="string" name="existence">[existence_value]</ae:parameter>
               <ae:parameter dt="set" name="check">[check.value]</ae:parameter>
               <ae:parameter dt="string" name="mount_point">[mount_point.value]</ae:parameter>
             </ae:parameters>
           </ae:artifact>
           <ae:test type="[TEST-TYPE-NAME]">
             <ae:parameters>
               <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
               <ae:parameter dt="set" name="operation">[operation.value]</ae:parameter>
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

.. _scap-1:

SCAP
^^^^

.. _xccdf-1:

XCCDF
'''''

For ``linux.partition_v1`` artifacts, the xccdf:check looks like this.
There is no Value element in the XCCDF for this Artifact.

::

   <xccdf:complex-check operator="AND">
     <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
       <check-content-ref 
         href="[BENCHMARK-TITLE]"
         name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
     </check>
   </xccdf:complex-check>

.. _oval-1:

OVAL
''''

Test

::

   <partition_test 
     xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
     check_existence="[check_existence.value]"
     check="[check.value]"
     comment="[RECOMMENDATION-TITLE]"
     version="1">
     <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
     <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
   </partition_test>

Object

::

   <partition_object
     xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
     comment="[RECOMMENDATION-TITLE]"
     version="1">
     <mount_point>
       [mount_point.value]
     </mount_point>
   </partition_object>

State

::

   <partition_state
     xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
     comment="[RECOMMENDATION-TITLE]"
     version="1">
     <mount_options> 
       entity_check="[entity_check.value]" 
       operation="[operation.value]"
       datatype="[datatype.value]">
       [mount_point.value]
     </mount_options>
   </partition_state>  

.. _yaml-1:

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
             name: "check"
             type: "set"
             value: "[check.value]"
         - parameter: 
             name: "mount_point"
             dt: "string"
             value: "[mount_point.value]"
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
             name: "operation"
             type: "set"
             value: "[operation.value]"
         - parameter:
             name: "check"
             dt: "string"
             value: "[check.value]"

.. _json-1:

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
               "name": "existence",
               "type": "string",
               "value": "[existence.value]"
             }
           },
           {
             "parameter": {
               "name": "check",
               "type": "set",
               "value": "[check.value]"
             }
           },
           {
             "parameter": {
               "name": "mount_point",
               "type": "string",
               "value": "[mount_point.value]"
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
               "name": "operation",
               "type": "set",
               "value": "[operation.value]"
             }
           },
           {
             "parameter": {
               "name": "check",
               "type": "string",
               "value": "[check.value]"
             }
           }
         ]
       }
     }
   }
