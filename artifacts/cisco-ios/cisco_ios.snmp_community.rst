cisco_ios.snmp_community
========================

Description
-----------

The cisco_ios.snmp_community is used to check the properties of specific
output lines from an SNMP configuration.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

============================= ====== ========================
Name                          Type   Description
============================= ====== ========================
cisco_ios.snmp_community_name String The SNMP community name.
============================= ====== ========================

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - existence_test
  - cisco_ios.snmp_community_mode
  - cisco_ios.snmp_community_ipv4_acl
  - cisco_ios.snmp_community_ipv6_acl

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

existence_test
^^^^^^^^^^^^^^

===== ====== ===========
Name  Type   Description
===== ====== ===========
value String Value.
===== ====== ===========

cisco_ios.snmp_community_mode
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

========= ====== ===========================================
Name      Type   Description
========= ====== ===========================================
operation String Comparison Operator.
mode      String The read-write privileges of the community.
========= ====== ===========================================

operation NOTE: This parameter is governed by a constraint allowing only
the following values: - equals - not equal - case insensitive equals -
case insensitive not equal - greater than - less than - greater than or
equal - less than or equal - bitwise and - bitwise or - pattern match -
subset of - superset of

cisco_ios.snmp_community_ipv4_acl
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

======== ====== ===========================================
Name     Type   Description
======== ====== ===========================================
operator String Comparison Operator.
ipv4_acl String The IPv4 ACL name applied to the community.
======== ====== ===========================================

cisco_ios.snmp_community_ipv6_acl
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

======== ====== ===========================================
Name     Type   Description
======== ====== ===========================================
operator String Comparison Operator.
ipv6_acl String The IPv6 ACL name applied to the community.
======== ====== ===========================================

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
                       <ae:parameter dt="string" name="cisco_ios.snmp_community_name">[cisco_ios.snmp_community_name.value]</ae:parameter>
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

For ``cisco_ios.snmp_community`` artifacts, the xccdf:check looks like
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

   snmpcommunity_test 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]'
       check_existence='[check_existence.value]' 
       check='[check.value]' 
       comment='[RECOMMENDATION TITLE]'
       version='[version.value]'>
       <object object_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
       <state state_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]'/>
   </snmpcommunity_test>

Object

::

   <snmpcommunity_object 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
       comment='[RECOMMENDATION TITLE]'
       version='[version.value]'>
       <name>[name.value]</name>
   </snmpcommunity_object>

State

::

   <snmpcommunity_state 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
       comment='[RECOMMENDATION TITLE]'
       version='[version.value]'>
       <mode operation='[operation.value]' 
           var_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
   </snmpcommunity_state>

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
             name: cisco_ios.snmp_community_name
             type: string
             value: [cisco_ios.snmp_community_name.value]
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
                 "name": "cisco_ios.snmp_community_name",
                 "type": "string",
                 "value": [
                   "cisco_ios.snmp_community_name.value"
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
