cisco_ios.global
================

Description
-----------

The cisco_ios.global is used to check for the existence of a particular
line in the IOS-XE config file under the global context. It extends the
standard TestType as defined in the oval-definitions-schema and one
should refer to the TestType description for more information. The
required object element references a global_object and the optional
state element specifies the data to check.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| cisco_ios.global_command            | String      | The global       |
|                                     |             | command          |
|                                     |             | identifies a     |
|                                     |             | specific line in |
|                                     |             | the IOS config   |
|                                     |             | file under the   |
|                                     |             | global context.  |
+-------------------------------------+-------------+------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

-  cisco_ios.global_command

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| operator                            | String      | The comparison   |
|                                     |             | operator.        |
+-------------------------------------+-------------+------------------+
| global_command                      | String      | The              |
|                                     |             | global_command   |
|                                     |             | entity           |
|                                     |             | identifies a     |
|                                     |             | specific line in |
|                                     |             | the ios config   |
|                                     |             | file under the   |
|                                     |             | global context.  |
+-------------------------------------+-------------+------------------+
| existence_check                     | String      | Number of global |
|                                     |             | config lines     |
|                                     |             | required in the  |
|                                     |             | result.          |
+-------------------------------------+-------------+------------------+

existence_check NOTE: This parameter is governed by a constraint
allowing only the following values: - all_exist - any_exist -
at_least_one_exists - none_satisfy - none_exist - only_one_exists

Generated Content
~~~~~~~~~~~~~~~~~

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

   <xccdf:complex-check operator="AND">
           <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
               <xccdf:check-content>
                   <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION_NUMBER]">
                       <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
                       <ae:title>[RECOMMENDATION TITLE]</ae:title>
                       <ae:artifact type="[ARTIFACTTYPE NAME]">
                           <ae:parameters>
                               <ae:parameter dt="string" name="cisco_ios.global_command">[cisco_ios.global_command.value]</ae:parameter>
                           </ae:parameters>
                       </ae:artifact>
                       <ae:test type="[TESTTYPE NAME]">
                           <ae:parameters>
                               <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
                               <ae:parameter dt="string" name="global_command">[global_command.value]</ae:parameter>
                               <ae:parameter dt="string" name="existence_check">[existence_check.value]</ae:parameter>
                           </ae:parameters>
                       </ae:test>
                       <ae:profiles>
                           <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1"/>
                       </ae:profiles>
                   </ae:artifact_expression>
               </xccdf:check-content>
           </xccdf:check>
   </xccdf:complex-check>

SCAP
^^^^

XCCDF
'''''

For ``cisco_ios.global`` artifacts, the xccdf:check looks like this.

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

   <global_test 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]'
       check_existence='[check_existence.value]' 
       check='[check.value]' 
       comment='[RECOMMENDATION TITLE]' 
       version='[version.value]'>
       <object object_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
       <state state_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]'/>
   </global_test>

Object

::

   <global_object 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
       comment='[RECOMMENDATION TITLE]' 
       version='[version.value]'>
       <global_command operation='[operation.value]'>[global_command.value]</global_command>
   </global_object>

State

::

   <global_state 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
       comment='[RECOMMENDATION TITLE]'
       version='[version.value]'>
       <global_command operation='[operation.value]' 
           var_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
   </global_state>

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
             name: cisco_ios.global_command
             type: string
             value: [operator.value]
       test:
         type: [TESTTYPE NAME]
         parameters:   
         - parameter: 
             name: operator
             type: string
             value: [operator.value]
         - parameter: 
             name: global_command
             type: string
             value: [global_command.value]
         - parameter: 
             name: existence_check
             type: string
             value: [existence_check.value]

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
                 "name": "cisco_ios.global_command",
                 "type": "string",
                 "value": [
                   "operator.value"
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
                 "name": "operator",
                 "type": "string",
                 "value": [
                   "operator.value"
                 ]
               }
             },
             {
               "parameter": {
                 "name": "global_command",
                 "type": "string",
                 "value": [
                   "global_command.value"
                 ]
               }
             },
             {
               "parameter": {
                 "name": "existence_check",
                 "type": "string",
                 "value": [
                   "existence_check.value"
                 ]
               }
             }
           ]
         }
       }
     }
