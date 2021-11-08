Unix: Symlink
=============

Description
-----------

The Unix: Symlink test is used to obtain canonical path information for
symbolic links.

The required symlink_object element is used to define the object to be
evaluated. A symlink_object consists of a filepath entity that contains
the path to a symbolic link file. The resulting item identifies the
canonical path of the link target (followed to its final destination, if
there are intermediate links), an error if the link target does not
exist or is a circular link (e.g., a link to itself). If the file
located at filepath is not a symlink, or if there is no file located at
the filepath, then any resulting item would itself have a status of does
not exist.

The optional symlink_state element defines a value used to evaluate the
result of a specific symlink_object item.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

Human ID:
   -  unix.symlink_v1

+--------------------+--------+--------------------------------------+
| Name               | Type   | Description                          |
+====================+========+======================================+
| filepath           | string | Specifies the filepath for the       |
|                    |        | symbolic link.                       |
+--------------------+--------+--------------------------------------+
| filepath_operation | string | Specifies what operation is to be    |
|                    |        | performed using the filepath value.  |
+--------------------+--------+--------------------------------------+

NOTE: The ``filepath_operation`` parameter is governed by a constraint allowing only the following values:
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

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

-  Unix: Symlink
-  Unix: Symlink Password Object v1

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

Human ID:
   -  unix.symlink_v1

+--------------------------+--------+-----------------------------+
| Name                     | Type   | Description                 |
+==========================+========+=============================+
| filepath                 | string | Specifies the filepath for  |
|                          |        | the symbolic link.          |
+--------------------------+--------+-----------------------------+
| filepath_operation       | string | Specifies what operation is |
|                          |        | to be performed using the   |
|                          |        | filepath value.             |
+--------------------------+--------+-----------------------------+
| canonical_path           | string | Specifies the canonical     |
|                          |        | path for the target of a    |
|                          |        | symbolic link file          |
|                          |        | specified by the filepath.  |
+--------------------------+--------+-----------------------------+
| canonical_path_operation | string | Specifies what operation is |
|                          |        | to be performed using the   |
|                          |        | canonical path value.       |
+--------------------------+--------+-----------------------------+

NOTE: The ``file_path_operation`` parameter is governed by a constraint allowing only the following values:
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

NOTE: The ``canonical_path_operation`` parameter is governed by a constraint allowing only the following values:
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

Human ID:
   -  unix.symlink_password_object_v1

+--------------------------+--------+-----------------------------+
| Name                     | Type   | Description                 |
+==========================+========+=============================+
| filepath                 | string | Specifies the filepath used |
|                          |        | to create the object.       |
+--------------------------+--------+-----------------------------+
| filepath_operation       | string | Specifies what operation is |
|                          |        | to be performed using the   |
|                          |        | filepath value.             |
+--------------------------+--------+-----------------------------+
| canonical_path           | string | Specifies the canonical     |
|                          |        | path for the target of a    |
|                          |        | symbolic link file          |
|                          |        | specified by the filepath.  |
+--------------------------+--------+-----------------------------+
| canonical_path_operation | string | Specifies what operation is |
|                          |        | to be performed using the   |
|                          |        | canonical path value.       |
+--------------------------+--------+-----------------------------+

NOTE: The ``file_path_operation`` parameter is governed by a constraint allowing only the following values:
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

NOTE: The ``canonical_path_operation`` parameter is governed by a constraint allowing only the following values:
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

Generated Content
~~~~~~~~~~~~~~~~~

unix.symlink_v1

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
             <ae:parameter dt="string" name="filepath">[filepath.value]</ae:parameter>
             <ae:parameter dt="string" name="filepath_operation">[filepath_operation.value]</ae:parameter>
           </ae:parameters>
         </ae:artifact>
         <ae:test type="[TEST-TYPE-NAME]">
           <ae:parameters>
             <ae:parameter dt="string" name="filepath">[filepath.value]</ae:parameter>
             <ae:parameter dt="string" name="file_path_operation">[file_path_operation.value]</ae:parameter>
             <ae:parameter dt="string" name="canonical_path">[canonical_path.value]</ae:parameter>
             <ae:parameter dt="string" name="canonical_path_operation">[canonical_path_operation.value]</ae:parameter>
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

For ``unix.symlink_v1`` artifacts, an XCCDF Value element is generated.

::

   <Value 
     id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" 
     type="string"
     operator="pattern match">
     <title>[RECOMMENDATION-TITLE]</title>
     <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
     <value>[value.value]</value>
   </Value>

For ``unix.symlink_v1`` artifacts, the xccdf:check looks like this.

::

   <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
     <check-export 
       export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
       value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
     <check-content-ref 
       href="[BENCHMARK-NAME]" 
       name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
   </check>

OVAL
''''

Test

::

   <symlink_test 
     xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
     check_existence="all_exist"
     check="all" 
     comment="[RECOMMENDATION-TITLE]" 
     version="1"> 
     <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
     <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
   </symlink_test>

Object

::

   <symlink_object 
     xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
     comment="[RECOMMENDATION-TITLE]" 
     version="1"> 
     <filepath 
       datatype="string" 
       operation="[operation.value]">
       [filepath.value]
     </filepath>
   </symlink_object>

State

::

   <symlink_state 
     xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
     comment="[RECOMMENDATION-TITLE]" 
     version="1"> 
     <canonical_path 
       datatype="string" 
       operation="[operation.value]" 
       var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
   </symlink_state>

Variable

::

   <external_variable
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
     datatype="string" 
     version="1" 
     comment="This value is used in Rule: [RECOMMENDATION-TITLE]" />

YAML
^^^^

::

   - artifact-expression:
     artifact-unique-id: "[ARTIFACT-OVAL-ID]"
     artifact-title: "[RECOMMENDATION-TITLE]"
     artifact:
       type: "[ARTIFACT-TYPE-NAME]"
       parameters:
         - parameter: 
             name: "filepath"
             dt: "string"
             value: "[filepath.value]"
         - parameter: 
             name: "filepath_operation"
             dt: "string"
             value: "[filepath_operation.value]"
     test:
       type: "[TESTTYPE-NAME]"
       parameters:   
         - parameter:
             name: "filepath"
             dt: "string"
             value: "[filepath.value]"
         - parameter:
             name: "file_path_operation"
             dt: "string"
             value: "[file_path_operation.value]"
         - parameter:
             name: "canonical_path"
             dt: "string"
             value: "[canonical_path.value]"
         - parameter:
             name: "canonical_path_operation"
             dt: "string"
             value: "[canonical_path_operation.value]"

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
               "name": "filepath",
               "type": "string",
               "value": "[filepath.value]"
             }
           },
           {
             "parameter": {
               "name": "filepath_operation",
               "type": "string",
               "value": "[filepath_operation.value]"
             }
           }
         ]
       }
     },
     "test": {
       "type": "[TESTTYPE-NAME]",
       "parameters": [
         {
           "parameter": {
             "name": "filepath",
             "dt": "string",
             "value": "[filepath.value]"
           }
         },
         {
           "parameter": {
             "name": "file_path_operation",
             "dt": "string",
             "value": "[file_path_operation.value]"
           }
         },
         {
           "parameter": {
             "name": "canonical_path",
             "dt": "string",
             "value": "[canonical_path.value]"
           }
         },
         {
           "parameter": {
             "name": "canonical_path_operation",
             "dt": "string",
             "value": "[canonical_path_operation.value]"
           }
         }
       ]
     }
   }

.. _generated-content-1:

Generated Content
~~~~~~~~~~~~~~~~~

unix.symlink_password_object_v1

.. _xccdfae-1:

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
             <ae:parameter dt="string" name="filepath">[filepath.value]</ae:parameter>
             <ae:parameter dt="string" name="filepath_operation">[filepath_operation.value]</ae:parameter>
           </ae:parameters>
         </ae:artifact>
         <ae:test type="[TEST-TYPE-NAME]">
           <ae:parameters>
             <ae:parameter dt="string" name="filepath">[filepath.value]</ae:parameter>
             <ae:parameter dt="string" name="file_path_operation">[file_path_operation.value]</ae:parameter>
             <ae:parameter dt="string" name="canonical_path">[canonical_path.value]</ae:parameter>
             <ae:parameter dt="string" name="canonical_path_operation">[canonical_path_operation.value]</ae:parameter>
           </ae:parameters>
         </ae:test>
         <ae:profiles>
           <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_2" />
         </ae:profiles>
       </ae:artifact_expression>
     </xccdf:check-content>
   </xccdf:check>

.. _scap-1:

SCAP
^^^^

.. _xccdf-1:

XCCDF
'''''

For ``unix.symlink_v1`` artifacts, an XCCDF Value element is generated.

::

   <Value 
     id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" 
     type="string"
     operator="pattern match">
     <title>[RECOMMENDATION-TITLE]</title>
     <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
     <value>[value.value]</value>
   </Value>

For ``unix.symlink_v1`` artifacts, the xccdf:check looks like this.

::

   <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
     <check-export 
       export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
       value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
     <check-content-ref 
       href="[BENCHMARK-NAME]" 
       name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
   </check>

.. _oval-1:

OVAL
''''

Test

::

   <symlink_test 
     xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
     check_existence="all_exist"
     check="all" 
     comment="[RECOMMENDATION-TITLE]" 
     version="1"> 
     <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
     <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
   </symlink_test>

Object

::

   <symlink_object 
     xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
     comment="[RECOMMENDATION-TITLE]" 
     version="1"> 
     <filepath 
       datatype="string" 
       operation="[operation.value]"
       var_ref= "oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1" />
   </symlink_object>

   <password_object
     xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1"
     comment="[RECOMMENDATION-TITLE]" 
     version="1"> 
     <username
       datatype="string"
       operation="[operation.value]">
       "^.+\$"
     </username>
     <filter
       xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5" 
       action="exclude">
       oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]1
     </filter>
   </password_object>

State

::

   <symlink_state 
     xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
     comment="[RECOMMENDATION-TITLE]" 
     version="1"> 
     <canonical_path 
       datatype="string" 
       operation="[operation.value]" 
       var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
   </symlink_state>

   <password_state 
     xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]1" 
     comment="[RECOMMENDATION-TITLE]" 
     version="1"> 
     <login_shell 
       datatype="string" 
       operation="[operation.value]">
       [login_shell.value]
     </login_shell
   </password_state>  

Variable

::

   <external_variable
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
     datatype="string" 
     version="1" 
     comment="This value is used in Rule: [RECOMMENDATION-TITLE]" />

   <local_variable
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1"
     datatype="string" 
     comment="This value is used in Rule: [RECOMMENDATION-TITLE]"
     version="1">
     <concat>
       <end
         character="/">
         <object_component
           object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1" 
           item_field="home_dir" />
       </end>
       <literal_component>
         .mysql_history
       </.mysql_history>
     </concat>
   </local_variable>

.. _yaml-1:

YAML
^^^^

::

   - artifact-expression:
     artifact-unique-id: "[ARTIFACT-OVAL-ID]"
     artifact-title: "[RECOMMENDATION-TITLE]"
     artifact:
       type: "[ARTIFACT-TYPE-NAME]"
       parameters:
         - parameter: 
             name: "filepath"
             dt: "string"
             value: "[filepath.value]"
         - parameter: 
             name: "filepath_operation"
             dt: "string"
             value: "[filepath_operation.value]"
     test:
       type: "[TESTTYPE-NAME]"
       parameters:   
         - parameter:
             name: "filepath"
             dt: "string"
             value: "[filepath.value]"
         - parameter:
             name: "file_path_operation"
             dt: "string"
             value: "[file_path_operation.value]"
         - parameter:
             name: "canonical_path"
             dt: "string"
             value: "[canonical_path.value]"
         - parameter:
             name: "canonical_path_operation"
             dt: "string"
             value: "[canonical_path_operation.value]"

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
               "name": "filepath",
               "type": "string",
               "value": "[filepath.value]"
             }
           },
           {
             "parameter": {
               "name": "filepath_operation",
               "type": "string",
               "value": "[filepath_operation.value]"
             }
           }
         ]
       }
     },
     "test": {
       "type": "[TESTTYPE-NAME]",
       "parameters": [
         {
           "parameter": {
             "name": "filepath",
             "dt": "string",
             "value": "[filepath.value]"
           }
         },
         {
           "parameter": {
             "name": "file_path_operation",
             "dt": "string",
             "value": "[file_path_operation.value]"
           }
         },
         {
           "parameter": {
             "name": "canonical_path",
             "dt": "string",
             "value": "[canonical_path.value]"
           }
         },
         {
           "parameter": {
             "name": "canonical_path_operation",
             "dt": "string",
             "value": "[canonical_path_operation.value]"
           }
         }
       ]
     }
   }  
