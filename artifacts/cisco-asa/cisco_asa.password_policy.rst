cisco_asa.password_policy
=========================

Description
  -----------

The cisco_asa.password_policy is used to check the properties of the
password policy.

Technical Details
  -----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

====================== ====== =====================================
Name                   Type   Description
====================== ====== =====================================
password_policy_option String Password Policy configuration option.
====================== ====== =====================================

password_policy_option NOTE: This parameter is governed by a constraint
allowing only the following values: - lifetime - minimum-changes -
minimum-uppercase - minimum-lowercase - minimum-numeric -
minimum-special - minimum-length

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - cisco_asa.expected_value_regex_capture

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

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
                       <ae:parameter dt="string" name="password_policy_option">[password_policy_option.value]</ae:parameter>
                   </ae:parameters>
               </ae:artifact>
               <ae:test type="[TESTTYPE NAME]">
                   <ae:parameters>
                       <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
                       <ae:parameter dt="string" name="expected_value">[expected_value.value]</ae:parameter>
                       <ae:parameter dt="string" name="regex_capture">[regex_capture.value]</ae:parameter>
                       <ae:parameter dt="string" name="expected_value_type">[expected_value_type.value]</ae:parameter>
                   </ae:parameters>
               </ae:test>
           </ae:artifact_expression>
       </xccdf:check-content>
   </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``cisco_asa.password_policy`` artifacts, the xccdf:check looks like
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

   <variable_test 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]'
       check_existence='[check_existence.value]' 
       check='[check.value]' 
       comment='[RECOMMENDATION TITLE]'
       version='[version.value]'>
       <object object_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
       <state state_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]'/>
   </variable_test>

Object

::

   <variable_object 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
       comment='[RECOMMENDATION TITLE]'
       version='[version.value]'>
       <var_ref>oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]</var_ref>
   </variable_object>

State

::

   <variable_state 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
       comment='[RECOMMENDATION TITLE]'
       version='[version.value]'>
       <value operation='[operation.value]' 
           datatype='[datatype.value]' 
           var_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
   </variable_state>

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
             name: password_policy_option
             type: string
             value: [password_policy_option.value]
       test:
         type: [TESTTYPE NAME]
         parameters:   
         - parameter: 
              name: operator
              type: string
              value: [operator.value]
         - parameter: 
              name: expected_value
              type: string
              value: [expected_value.value]
         - parameter: 
              name: regex_capture
              type: string
              value: [regex_capture.value]
         - parameter: 
              name: expected_value_type
              type: string
              value: [expected_value_type.value]

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
                 "name": "password_policy_option",
                 "type": "string",
                 "value": [
                   "password_policy_option.value"
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
                 "name": "expected_value",
                 "type": "string",
                 "value": [
                   "expected_value.value"
                 ]
               }
             },
             {
               "parameter": {
                 "name": "regex_capture",
                 "type": "string",
                 "value": [
                   "regex_capture.value"
                 ]
               }
             },
             {
               "parameter": {
                 "name": "expected_value_type",
                 "type": "string",
                 "value": [
                   "expected_value_type.value"
                 ]
               }
             }
           ]
         }
       }
     }
