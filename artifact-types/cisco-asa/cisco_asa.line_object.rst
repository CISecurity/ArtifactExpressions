cisco_asa.line_object
=====================

Description
-----------

The cisco_asa.line_object is used to check the properties of specific
output lines from a SHOW command, such as SHOW RUNNING-CONFIG. It
extends the standard TestType as defined in the oval-definitions-schema
and one should refer to the TestType description for more information.
The required object element references a line_object and the optional
state element specifies the data to check.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

=============== ====== ===============================
Name            Type   Description
=============== ====== ===============================
show_subcommand String The name of a SHOW sub-command.
=============== ====== ===============================

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

-  cisco_asa.line_config_line
-  cisco_asa.existence_check
-  cisco_asa.expected_value_regex_capture
-  cisco_asa.untrusted_interfaces_state

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

cisco_asa.line_config_line
^^^^^^^^^^^^^^^^^^^^^^^^^^

=========== ====== =================================
Name        Type   Description
=========== ====== =================================
operation   String Comparison Operator.
config_line String The collected configuration line.
check       String Check enumeration value.
=========== ====== =================================

operation NOTE: This parameter is governed by a constraint allowing only
the following values: - equals - not equal - case insensitive equals -
case insensitive not equal - greater than - less than - greater than or
equal - less than or equal - bitwise and - bitwise or - pattern match -
subset of - superset of

check NOTE: This parameter is governed by a constraint allowing only the
following values: - all - at least one - none satisfy - only one

cisco_asa.existence_check
^^^^^^^^^^^^^^^^^^^^^^^^^

=============== ====== =========================================
Name            Type   Description
=============== ====== =========================================
existence_check String Number of lines expected to be collected.
=============== ====== =========================================

existence_check NOTE: This parameter is governed by a constraint
allowing only the following values: - all_exist - any_exist -
at_least_one_exists - none_satisfy - none_exist - only_one_exists

cisco_asa.expected_value_regex_capture
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| operator                            | String      | Comparison       |
|                                     |             | Operator.        |
+-------------------------------------+-------------+------------------+
| expected_value                      | String      | Expected value   |
|                                     |             | of the password  |
|                                     |             | policy option.   |
+-------------------------------------+-------------+------------------+
| regex_capture                       | String      | The              |
|                                     |             | regex_capture to |
|                                     |             | use to isolate   |
|                                     |             | the expected     |
|                                     |             | value.           |
+-------------------------------------+-------------+------------------+
| expected_value_type                 | String      | Datatype of      |
|                                     |             | Expected Value.  |
+-------------------------------------+-------------+------------------+

cisco_asa.untrusted_interfaces_state
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

============ ====== ===========================
Name         Type   Description
============ ====== ===========================
regex_prefix String Regular Expression Prefix.
regex_suffix String Regular Expression Suffix.
check        String The test's check attribute.
============ ====== ===========================

check NOTE: This parameter is governed by a constraint allowing only the
following values: - all - at least one - none satisfy - only one

Generated Content
~~~~~~~~~~~~~~~~~

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

   <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
       <xccdf:check-content>
           <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION_NUMBER]">
               <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
               <ae:title>[RECOMMENDATION TITLE]</ae:title>
               <ae:artifact type="[ARTIFACTTYPE NAME]">
                   <ae:parameters>
                       <ae:parameter dt="string" name="show_subcommand">[show_subcommand.value]</ae:parameter>
                   </ae:parameters>
               </ae:artifact>
               <ae:test type="[TESTTYPE NAME]">
                   <ae:parameters>
                       <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
                       <ae:parameter dt="string" name="config_line">[config_line.value]</ae:parameter>
                       <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
                   </ae:parameters>
               </ae:test>
           </ae:artifact_expression>
       </xccdf:check-content>
   </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``cisco_asa.line_object`` artifacts, the xccdf:check looks like
this.

::

   <check system='http://oval.mitre.org/XMLSchema/oval-definitions-5'>
       <check-export 
            export-name='oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]' 
            value-id='xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var'/>
       <check-content-ref 
           href='[BENCHMARK NAME]' 
           name='oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]'/>
   </check>

OVAL
''''

Test
    

::

   <line_test 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]'
       check_existence='[check_existence.value]' 
       check='[check.value]' 
       comment='[RECOMMENDATION TITLE]'
       version='[version.value]'>
       <object object_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
       <state state_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]'/>
   </line_test>

Object
      

::

   <line_object 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
       comment='[RECOMMENDATION TITLE]'
       version='[version.value]'>
       <show_subcommand>[show_subcommand.value]</show_subcommand>
   </line_object>

State
     

::

   <line_state 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
       comment='[RECOMMENDATION TITLE]'
       version='[version.value]'>
       <config_line operation='[operation.value]' 
           var_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
   </line_state>

YAML
^^^^

::

   - artifact-expression:
       artifact-unique-id: [ARTIFACT-OVAL-ID]
       artifact-title: [RECOMMENDATION TITLE]
       artifact:
         type: [ARTIFACTTYPE NAME]
         parameters:
         - parameter: 
             name: show_subcommand
             type: string
             value: [show_subcommand.value]
       test:
         type: [TESTTYPE NAME]
         parameters:   
         - parameter: 
              name: operation
              type: string
              value: [operation.value]
         - parameter: 
              name: config_line
              type: string
              value: [config_line.value]
         - parameter: 
              name: check
              type: string
              value: check_line.value]

JSON
^^^^

::

   {
       "artifact-expression": {
         "artifact-unique-id": [
           "ARTIFACT-OVAL-ID"
         ],
         "artifact-title": [
           "RECOMMENDATION TITLE"
         ],
         "artifact": {
           "type": [
             "ARTIFACTTYPE NAME"
           ],
           "parameters": [
             {
               "parameter": {
                 "name": "show_subcommand",
                 "type": "string",
                 "value": [
                   "show_subcommand.value"
                 ]
               }
             }
           ]
         },
         "test": {
           "type": [
             "TESTTYPE NAME"
           ],
           "parameters": [
             {
               "parameter": {
                 "name": "operation",
                 "type": "string",
                 "value": [
                   "operation.value"
                 ]
               }
             },
             {
               "parameter": {
                 "name": "config_line",
                 "type": "string",
                 "value": [
                   "config_line.value"
                 ]
               }
             },
             {
               "parameter": {
                 "name": "check",
                 "type": "string",
                 "value": "check_line.value]"
               }
             }
           ]
         }
       }
     }
