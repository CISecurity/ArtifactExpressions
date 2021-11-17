cisco_asa.snmp_user_object
==========================

Description
  -----------

The cisco_asa.snmp_user_object is used to check the properties of
specific output lines from an SNMP user configuration.

Technical Details
  -----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

======== ====== ====================
Name     Type   Description
======== ====== ====================
name     String The SNMP user name.
operator String Comparison Operator.
======== ====== ====================

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - cisco_asa.snmp_user_auth_priv

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

============= ====== =======================================
Name          Type   Description
============= ====== =======================================
auth_operator String Comparison operator for the auth value.
auth          String Authentication.
priv_operator String Comparison operator for the priv value.
priv          String Priv.
============= ====== =======================================

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
                       <ae:parameter dt="string" name="name">[name.value]</ae:parameter>
                       <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
                   </ae:parameters>
               </ae:artifact>
               <ae:test type="[TESTTYPE NAME]">
                   <ae:parameters>
                       <ae:parameter dt="string" name="auth_operator">[auth_operator.value]</ae:parameter>
                       <ae:parameter dt="string" name="auth">[auth.value]</ae:parameter>
                       <ae:parameter dt="string" name="priv_operator">[priv_operator.value]</ae:parameter>
                       <ae:parameter dt="string" name="priv">[priv.value]</ae:parameter>
                   </ae:parameters>
               </ae:test>
           </ae:artifact_expression>
       </xccdf:check-content>
   </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``cisco_asa.snmp_user_object`` artifacts, the xccdf:check looks like
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

   <snmp_user_test 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]'
       check_existence='[check_existence.value]' 
       check='[check.value]' 
       comment='[RECOMMENDATION TITLE]'
       version='[version.value]'>
       <object object_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
       <state state_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]'/>
   </snmp_user_test>

Object

::

   <snmp_user_object 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
       comment='[RECOMMENDATION TITLE]'
       version='[version.value]'>
       <name operation='[operation.value]'>[name.value</name>
   </snmp_user_object>

State

::

   <snmp_user_state 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
       comment='[RECOMMENDATION TITLE]'
       version='[version.value]'>
       <priv operation='[operation.value]' 
           var_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
       <auth operation='[operation.value]' 
           var_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
   </snmp_user_state>

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
             name: name
             type: string
             value: [name.value]
         - parameter: 
             name: operator
             type: string
             value: [operator.value]
       test:
         type: [TESTTYPE NAME]
         parameters:   
         - parameter: 
              name: auth_operator
              type: string
              value: [auth_operator.value]
         - parameter: 
              name: auth
              type: string
              value: [auth.value]
         - parameter: 
              name: priv_operator
              type: string
              value: [priv_operator.value]
         - parameter: 
              name: priv
              type: string
              value: [priv.value]

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
                 "name": "name",
                 "type": "string",
                 "value": [
                   "name.value"
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
                 "name": "auth_operator",
                 "type": "string",
                 "value": [
                   "auth_operator.value"
                 ]
               }
             },
             {
               "parameter": {
                 "name": "auth",
                 "type": "string",
                 "value": [
                   "auth.value"
                 ]
               }
             },
             {
               "parameter": {
                 "name": "priv_operator",
                 "type": "string",
                 "value": [
                   "priv_operator.value"
                 ]
               }
             },
             {
               "parameter": {
                 "name": "priv",
                 "type": "string",
                 "value": [
                   "priv.value"
                 ]
               }
             }
           ]
         }
       }
     }
