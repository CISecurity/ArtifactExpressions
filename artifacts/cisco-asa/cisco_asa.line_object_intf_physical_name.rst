cisco_asa.line_object_intf_physical_name
========================================

Description
-----------

The cisco_asa.line_object_intf_physical_name is used to check the
properties of specific output lines.

Technical Details

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

======================= ====== ========================
Name                    Type   Description
======================= ====== ========================
show_run_command_prefix String Show Run command prefix.
show_run_command_suffix String Show Run Command Suffix.
======================= ====== ========================

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - cisco_asa.line_config_line

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

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
                       <ae:parameter dt="string" name="show_run_command_prefix">[show_run_command_prefix.value]</ae:parameter>
                       <ae:parameter dt="string" name="show_run_command_suffix">[show_run_command_suffix.value]</ae:parameter>
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

For ``cisco_asa.line_object_intf_physical_name`` artifacts, the
xccdf:check looks like this.

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
           var_check='[var_check.value]'
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
             name: show_run_command_prefix
             type: string
             value: [show_run_command_prefix.value]
         - parameter: 
             name: show_run_command_suffix
             type: string
             value: [show_run_command_suffix.value]
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
                 "name": "show_run_command_prefix",
                 "type": "string",
                 "value": [
                   "show_run_command_prefix.value"
                 ]
               }
             },
             {
               "parameter": {
                 "name": "show_run_command_suffix",
                 "type": "string",
                 "value": [
                   "show_run_command_suffix.value"
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
