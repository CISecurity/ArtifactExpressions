cisco_ios.snmp
==============

Description
-----------

The cisco_ios.snmp is used to check the properties of specific output
lines from an SNMP configuration.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

==== ==== ===========
Name Type Description
==== ==== ===========
==== ==== ===========

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - existence_test
  - cisco_ios.snmp

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

existence_test
^^^^^^^^^^^^^^

===== ====== ===========
Name  Type   Description
===== ====== ===========
value String Value.
===== ====== ===========

cisco_ios.snmp
^^^^^^^^^^^^^^

=========== ====== =============================
Name        Type   Description
=========== ====== =============================
operator    String Comparison Operator.
access_list String The defined SNMP Access List.
=========== ====== =============================

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
                   <ae:parameters/>
               </ae:artifact>
               <ae:test type="[TESTTYPE NAME]">
                   <ae:parameters>
                       <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
                       <ae:parameter dt="string" name="access_list">[access_list.value]</ae:parameter>
                   </ae:parameters>
               </ae:test>
           </ae:artifact_expression>
       </xccdf:check-content>
   </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``cisco_ios.snmp`` artifacts, the xccdf:check looks like this.

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

   <snmp_test 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]'
       check_existence='[check_existence.value]' 
       check='[check.value]' 
       comment='[RECOMMENDATION TITLE]'
       version='[version.value]'>
       <object object_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
       <state state_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]'/>
   </snmp_test>

Object

::

   <snmp_object 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
       comment='[RECOMMENDATION TITLE]'
       version='[version.value]'/>
   </snmp_object>

State

::

   <snmp_state 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
       comment='[RECOMMENDATION TITLE]'
       version='[version.value]'>
       <access_list operation='[operation.value]' 
           var_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
   </snmp_state>

YAML
^^^^

::

  - artifact-expression:
       artifact-unique-id: [ARTIFACT-OVAL-ID]
       artifact-title: [RECOMMENDATION TITLE]
       artifact:
         type: [ARTIFACTTYPE NAME]
         parameters:
       test:
         type: [TESTTYPE NAME]
         parameters:  
         - parameter: 
             name: operator
             type: string
             value: [operator.value]
         - parameter: 
             name: access_list
             type: string
             value: [access_list.value] 

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
           "parameters": null
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
                 "name": "access_list",
                 "type": "string",
                 "value": [
                   "access_list.value"
                 ]
               }
             }
           ]
         }
       }
     }
