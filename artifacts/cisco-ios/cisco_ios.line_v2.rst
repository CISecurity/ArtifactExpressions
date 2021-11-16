cisco_ios.line_v2
=================

Description
-----------

The cisco_ios.line_v2 is used to check the properties of specific output
lines from an SNMP configuration.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| cisco_ios.show_subcommand           | String      | The name of a    |
|                                     |             | SHOW             |
|                                     |             | sub-command.     |
|                                     |             | This value can   |
|                                     |             | either start     |
|                                     |             | with the word.   |
+-------------------------------------+-------------+------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - cisco_ios.line_config_line_v2

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

============= ====== =================================
Name          Type   Description
============= ====== =================================
operation     String Comparison Operator.
config_line   String The collected configuration line.
filter        String Filter.
filter_action String Filter action.
============= ====== =================================

operation NOTE: This parameter is governed by a constraint allowing only
the following values: - equals - not equal - case insensitive equals -
case insensitive not equal - greater than - less than - greater than or
equal - less than or equal - bitwise and - bitwise or - pattern match -
subset of - superset of

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
                       <ae:parameter dt="string" name="cisco_ios.show_subcommand">[cisco_ios.show_subcommand.value]</ae:parameter>
                   </ae:parameters>
               </ae:artifact>
               <ae:test type="[TESTTYPE NAME]">
                   <ae:parameters>
                       <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
                       <ae:parameter dt="string" name="config_line">[config_line.value]</ae:parameter>
                       <ae:parameter dt="string" name="filter">[filter.value]</ae:parameter>
                       <ae:parameter dt="string" name="filter_action">[filter_action.value]</ae:parameter>
                   </ae:parameters>
               </ae:test>
           </ae:artifact_expression>
       </xccdf:check-content>
   </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``cisco_ios.line_v2`` artifacts, the xccdf:check looks like this.

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
       <show_subcommand operation='[operation.value]'>[show_subcommand.value]</show_subcommand>
       <filter 
           xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5'
           action='[action.value]'>oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]</filter>
   </line_object>

State

::

   <line_state 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
       comment='[RECOMMENDATION TITLE]' 
       version='[version.value]'>
       <config_line operation='[config_line.value]' 
           var_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]''/>
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
             name: cisco_ios.show_subcommand
             type: string
             value: [cisco_ios.show_subcommand.value]
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
              name: filter
              type: string
              value: [filter.value]
         - parameter: 
              name: filter_action
              type: string
              value: [filter_action.value]

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
                 "name": "cisco_ios.show_subcommand",
                 "type": "string",
                 "value": [
                   "cisco_ios.show_subcommand.value"
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
                 "name": "filter",
                 "type": "string",
                 "value": [
                   "filter.value"
                 ]
               }
             },
             {
               "parameter": {
                 "name": "filter_action",
                 "type": "string",
                 "value": [
                   "filter_action.value"
                 ]
               }
             }
           ]
         }
       }
     }
