cisco_ios.interface
===================

Description
-----------

The cisco_ios.interface test enumerate various attributes about the
interfaces on a system. It extends the standard TestType as defined in
the oval-definitions-schema and one should refer to the TestType
description for more information. The object element references
an interface_object and the state element specifies the
interface information to check.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| cisco_ios.interface_name            | String      | The name of the  |
|                                     |             | IOS interface to |
|                                     |             | be tested.       |
+-------------------------------------+-------------+------------------+
| operation                           | String      | The operator     |
|                                     |             | defining how to  |
|                                     |             | collect the IOS  |
|                                     |             | interface(s).    |
+-------------------------------------+-------------+------------------+

operation NOTE: This parameter is governed by a constraint allowing only
the following values: - equals - not equal - case insensitive equals -
case insensitive not equal - greater than - less than - greater than or
equal - less than or equal - bitwise and - bitwise or - pattern match -
subset of - superset of

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - cisco_ios.interface_existence_test
  - cisco_ios.interface_proxy_arp
  - cisco_ios.interface_urpf

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

cisco_ios.interface_existence_test
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

=============== ====== ==============================================
Name            Type   Description
=============== ====== ==============================================
existence_check String Number of interfaces expected to be collected.
operator        String Interface Name comparison operator.
interface_name  String The interface name.
=============== ====== ==============================================

existence_check NOTE: This parameter is governed by a constraint
allowing only the following values: - all_exist - any_exist -
at_least_one_exists - none_satisfy - none_exist - only_one_exists

cisco_ios.interface_proxy_arp
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| operation                           | String      | Comparison       |
|                                     |             | Operator.        |
+-------------------------------------+-------------+------------------+
| proxy_arp_enabled                   | String      | True if the      |
|                                     |             | proxy_arp        |
|                                     |             | command is       |
|                                     |             | enabled on the   |
|                                     |             | interface. The  |
|                                     |             | default is true. |
+-------------------------------------+-------------+------------------+

operation NOTE: This parameter is governed by a constraint allowing only
the following values: - equals - not equal - case insensitive equals -
case insensitive not equal - greater than - less than - greater than or
equal - less than or equal - bitwise and - bitwise or - pattern match -
subset of - superset of

cisco_ios.interface_urpf
^^^^^^^^^^^^^^^^^^^^^^^^

============ ====== ===================================
Name         Type   Description
============ ====== ===================================
operator     String Interface Name comparison operator.
urpf_command String The uRPF commands expected value.
============ ====== ===================================

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
                               <ae:parameter dt="string" name="cisco_ios.interface_name">[cisco_ios.interface_name.value]</ae:parameter>
                               <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
                           </ae:parameters>
                       </ae:artifact>
                       <ae:test type="[TESTTYPE NAME]">
                           <ae:parameters>
                               <ae:parameter dt="string" name="existence_check">[existence_check.value]</ae:parameter>
                               <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
                               <ae:parameter dt="string" name="interface_name">[interface_name.value]</ae:parameter>
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

For ``cisco_ios.interface`` artifacts, the xccdf:check looks like this.

::

   <check system='http://oval.mitre.org/XMLSchema/oval-definitions-5'>
       <check-content-ref 
           href='[BENCHMARK NAME]' 
           name='oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]'/>
   </check>

OVAL
''''

Test

::

   <interface_test 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]'
       check_existence='[check_existence.value]' 
       check='[check.value]' 
       comment='[RECOMMENDATION TITLE]'
       version='[version.value]'>
       <object object_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
   </interface_test>

Object

::

   <interface_object 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
       comment='[RECOMMENDATION TITLE]'
       version='[version.value]'>
       <name operation='[operation.value]'>[name.value]</name>
   </interface_object>

State

::

   <interface_state 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
       comment='[RECOMMENDATION TITLE]'
       version='[version.value]'>
       <proxy_arp_command operation='[operation.value]' 
           var_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
   </interface_state>

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
             name: cisco_ios.interface_name
             type: string
             value: [cisco_ios.interface_name.value]
         - parameter: 
             name: operation
             type: string
             value: [operation.value]
       test:
         type: [TESTTYPE NAME]
         parameters:   
         - parameter: 
             name: existence_check
             type: string
             value: [existence_check.value]
         - parameter: 
             name: operator
             type: string
             value: [operator.value]
         - parameter: 
             name: interface_name
             type: string
             value: [interface_name.value]

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
                 "name": "cisco_ios.interface_name",
                 "type": "string",
                 "value": [
                   "cisco_ios.interface_name.value"
                 ]
               }
             },
             {
               "parameter": {
                 "name": "operation",
                 "type": "string",
                 "value": [
                   "operation.value"
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
                 "name": "existence_check",
                 "type": "string",
                 "value": [
                   "existence_check.value"
                 ]
               }
             },
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
                 "name": "interface_name",
                 "type": "string",
                 "value": [
                   "interface_name.value"
                 ]
               }
             }
           ]
         }
       }
     }
