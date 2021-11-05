cisco_ios.snmp_group
====================

Description
-----------

The cisco_ios.snmp_group is used to check the properties of specific
output lines from an SNMP group configuration.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

========================= ======= ============================
Name                      Type    Description
========================= ======= ============================
cisco_ios.snmp_group_name String  The SNMP group name.
cisco_ios.snmp_group_op   String  The SNMP group op.
cisco_ios.snmpv3_filter   boolean Collect only SNMP v3 Groups?
========================= ======= ============================

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

-  cisco_ios.snmp_groups_priv

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

================ ====== =============================================
Name             Type   Description
================ ====== =============================================
operator         String Comparison Operator.
snmpv3_sec_level String The SNMPv3 security configured for the group.
================ ====== =============================================

snmpv3_sec_level NOTE: This parameter is governed by a constraint
allowing only the following values: - PRIV - AUTH - NO_AUTH

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
                       <ae:parameter dt="string" name="cisco_ios.snmp_group_name">[cisco_ios.snmp_group_name.value]</ae:parameter>
                       <ae:parameter dt="string" name="cisco_ios.snmp_group_op">[cisco_ios.snmp_group_op.value]</ae:parameter>
                       <ae:parameter dt="boolean" name="cisco_ios.snmpv3_filter">[cisco_ios.snmpv3_filter.value]</ae:parameter>
                   </ae:parameters>
               </ae:artifact>
               <ae:test type="[TESTTYPE NAME]">
                   <ae:parameters>
                       <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
                       <ae:parameter dt="string" name="snmpv3_sec_level">[snmpv3_sec_level.value]</ae:parameter>
                   </ae:parameters>
               </ae:test>
           </ae:artifact_expression>
       </xccdf:check-content>
   </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``cisco_ios.snmp_group`` artifacts, the xccdf:check looks like this.

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

   <snmpgroup_test 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]'
       check_existence='[check_existence.value]' 
       check='[check.value]' 
       comment='[RECOMMENDATION TITLE]'
       version='[version.value]'>
       <object object_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
       <state state_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]'/>
   </snmpgroup_test>

Object
      

::

   <snmpgroup_object 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
       comment='[RECOMMENDATION TITLE]' 
       version='[version.value]'>
       <filter 
           xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5'
           action='.+'>oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]</filter>
   </snmpgroup_object>

State
     

::

   <snmpgroup_state 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
       comment='[RECOMMENDATION TITLE]'
       version='[version.value]'>
       <snmpv3_sec_level operation='pattern match' 
           var_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
   </snmpgroup_state>

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
             name: cisco_ios.snmp_group_name
             type: string
             value: [cisco_ios.snmp_group_name.value]
         - parameter: 
             name: cisco_ios.snmp_group_op
             type: string
             value: [cisco_ios.snmp_group_op.value]
         - parameter: 
             name: cisco_ios.snmpv3_filter
             type: boolean
             value: [cisco_ios.snmpv3_filter.value]
       test:
         type: [TESTTYPE NAME]
         parameters:   
         - parameter: 
             name: operator
             type: string
             value: [operator.value]
         - parameter: 
             name: snmpv3_sec_level
             type: string
             value: [snmpv3_sec_level.value]

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
                 "name": "cisco_ios.snmp_group_name",
                 "type": "string",
                 "value": [
                   "cisco_ios.snmp_group_name.value"
                 ]
               }
             },
             {
               "parameter": {
                 "name": "cisco_ios.snmp_group_op",
                 "type": "string",
                 "value": [
                   "cisco_ios.snmp_group_op.value"
                 ]
               }
             },
             {
               "parameter": {
                 "name": "cisco_ios.snmpv3_filter",
                 "type": "boolean",
                 "value": [
                   "cisco_ios.snmpv3_filter.value"
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
                 "name": "snmpv3_sec_level",
                 "type": "string",
                 "value": [
                   "snmpv3_sec_level.value"
                 ]
               }
             }
           ]
         }
       }
     }
