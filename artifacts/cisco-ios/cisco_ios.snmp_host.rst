cisco_ios.snmp_host
===================

Description
-----------

The cisco_ios.snmp_host is used to check the properties of specific
output lines from an SNMP configuration.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

======================== ====== ==================================
Name                     Type   Description
======================== ====== ==================================
cisco_ios.snmp_host_name String The SNMP host address or hostname.
cisco_ios.snmp_host_op   String SNMP Host Collection Operator.
======================== ====== ==================================

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - existence_test
  - cisco_ios.snmp_host_traps

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

existence_test
^^^^^^^^^^^^^^

===== ====== ===========
Name  Type   Description
===== ====== ===========
value String Value.
===== ====== ===========

cisco_ios.snmp_host_traps
^^^^^^^^^^^^^^^^^^^^^^^^^

======== ====== ==========================
Name     Type   Description
======== ====== ==========================
operator String Comparison Operator.
traps    String The SNMP Traps configured.
======== ====== ==========================

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
                       <ae:parameter dt="string" name="cisco_ios.snmp_host_name">[cisco_ios.snmp_host_name.value]</ae:parameter>
                       <ae:parameter dt="string" name="cisco_ios.snmp_host_op">[cisco_ios.snmp_host_op.value]</ae:parameter>
                   </ae:parameters>
               </ae:artifact>
               <ae:test type="[TESTTYPE NAME]">
                   <ae:parameters>
                       <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
                   </ae:parameters>
               </ae:test>
           </ae:artifact_expression>
       </xccdf:check-content>
   </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``cisco_ios.snmp_host`` artifacts, the xccdf:check looks like this.

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

   snmphost_test 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]'
       check_existence='[check_existence.value]' 
       check='[check.value]' 
       comment='[RECOMMENDATION TITLE]'
       version='[version.value]'>
       <object object_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
       <state state_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]'/>
   </snmphost_test>

Object

::

   <snmphost_object 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
       comment='[RECOMMENDATION TITLE]'
       version='[version.value]'>
       <host operation='[operation.value]'>[host.value]</host>
   </snmphost_object>

State

::

   N/A

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
             name: cisco_ios.snmp_host_name
             type: string
             value: [cisco_ios.snmp_host_name.value]
         - parameter: 
             name: cisco_ios.snmp_host_op
             type: string
             value: [cisco_ios.snmp_host_op.value]
       test:
         type: [TESTTYPE NAME]
         parameters:   
         - parameter: 
             name: value
             type: string
             value: [value.value]

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
                 "name": "cisco_ios.snmp_host_name",
                 "type": "string",
                 "value": [
                   "cisco_ios.snmp_host_name.value"
                 ]
               }
             },
             {
               "parameter": {
                 "name": "cisco_ios.snmp_host_op",
                 "type": "string",
                 "value": [
                   "cisco_ios.snmp_host_op.value"
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
                 "name": "value",
                 "type": "string",
                 "value": [
                   "value.value"
                 ]
               }
             }
           ]
         }
       }
     }
