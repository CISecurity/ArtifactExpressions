macos.plist511_v1
=================

Description
-----------

The plist511_test is used to check the value(s) associated with property
list preference keys. It can be used to represent any plist file in XML
form (whether its native format is ASCII text, binary, or XML),
permitting the use of the XPATH query language to explore its contents.
It extends the standard TestType as defined in the
oval-definitions-schema and one should refer to the TestType description
for more information. The object element references a
plist511_object and The plist511_state element specifies the
data to check.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| filepath                            | String      | The absolute     |
|                                     |             | path to a plist  |
|                                     |             | file             |
|                                     |             | (e.g             |
|                                     |             | . ~/Library/Pref |
|                                     |             | erences/com.appl |
|                                     |             | e.Safari.plist). |
|                                     |             | A directory      |
|                                     |             | cannot be        |
|                                     |             | specified as a   |
|                                     |             | filepath.        |
+-------------------------------------+-------------+------------------+
| xpath                               | String      | The preference   |
|                                     |             | key to check. If |
|                                     |             | the xsi:nil      |
|                                     |             | attribute is set |
|                                     |             | to ‘true’, the   |
|                                     |             | plist does not   |
|                                     |             | have any keys    |
|                                     |             | associated with  |
|                                     |             | it (i.e. it is   |
|                                     |             | not a            |
|                                     |             | CFDictionary)    |
|                                     |             | and the default  |
|                                     |             | value of the     |
|                                     |             | plist will be    |
|                                     |             | collected.       |
+-------------------------------------+-------------+------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - macos.plist511_v1

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| check_existence                     | String      | Define how many  |
|                                     |             | items should be  |
|                                     |             | collected        |
+-------------------------------------+-------------+------------------+
| check                               | String      | Defines how many |
|                                     |             | collected items  |
|                                     |             | must match the   |
|                                     |             | expected state   |
+-------------------------------------+-------------+------------------+
| operation                           | String      | comparison       |
|                                     |             | operation        |
+-------------------------------------+-------------+------------------+
| datatype                            | String      | datatype         |
+-------------------------------------+-------------+------------------+
| value_of                            | String      | The value of the |
|                                     |             | preference key.  |
+-------------------------------------+-------------+------------------+

check_existence NOTE: This parameter is governed by a constraint
allowing only the following values:

  - all_exist
  - any_exist
  - at_least_one_exists
  - none_satisfy
  - none_exist
  - only_one_exists

check NOTE: This parameter is governed by a constraint allowing only the
following values:

  - all
  - at least one
  - none satisfy
  - only one

operation NOTE: This parameter is governed by a constraint allowing only
the following values:

  - equals
  - not equal
  - case insensitive equals 
  - case insensitive not equal 
  - greater than
  - less than
  - greater than or equal 
  - less than or equal 
  - bitwise and 
  - bitwise or 
  - pattern match
  - subset of 
  - superset of

datatype NOTE: This parameter is governed by a constraint allowing only
the following values:
 
  - boolean 
  - float 
  - int 
  - string 
  - version 
  - set

Generated Content
~~~~~~~~~~~~~~~~~

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

   <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
     <xccdf:check-content>
       <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION_NUMBER]">
         <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
         <ae:title>[RECOMMENDATION TITLE]</ae:title>
         <ae:artifact type="[ARTIFACTTYPE NAME]">
           <ae:parameters>
             <ae:parameter dt="string" name="filepath"
               >[filepath.value]</ae:parameter>
             <ae:parameter dt="string" name="xpath"
               >[xpath.value]</ae:parameter>
           </ae:parameters>
         </ae:artifact>
         <ae:test type="[TESTTYPE NAME]">
           <ae:parameters>
             <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
             <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
             <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
             <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
             <ae:parameter dt="string" name="value_of">[value_of.value]</ae:parameter>
           </ae:parameters>
         </ae:test>
         <ae:profiles>
           <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1"
           />
         </ae:profiles>
       </ae:artifact_expression>
     </xccdf:check-content>
   </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``macos.plist511_v1`` artifacts, the xccdf:check looks like this. There is no Value in the xccdf for this Artifact.

::

   <xccdf:check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
      <xccdf:check-content-ref xmlns:ae="http://benchmarks.cisecurity.org/ae/0.5"
         xmlns:cpe="http://cpe.mitre.org/language/2.0"
         xmlns:ecl="http://cisecurity.org/check"
         href="[BENCHMARK NAME]"
         name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]"/>
   </xccdf:check>

OVAL
''''

Test

::

   <macos:plist511_test check="[check.value]" check_existence="[check_existence.value]"
     comment="[RECOMMENDATION TITLE]"
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" version="[version.value]">
     <macos:object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"/>
     <macos:state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"/>
   </macos:plist511_test>

Object

::

   <macos:plist511_object
     comment="[RECOMMENDATION TITLE]"
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" version="[version.value]">
     <macos:filepath>[filepath.value]</macos:filepath>
     <macos:xpath>[xpath.value]</macos:xpath>
   </macos:plist511_object>

State

::

   <macos:plist511_state
     comment="[RECOMMENDATION TITLE]"
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" version="[version.value]">
     <macos:value_of datatype="[datatype.value]" operation="[operation.value]">[value_of.value]</macos:value_of>
   </macos:plist511_state>    

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
             name: filepath
             type: string
             value: [filepath.value]
         - parameter: 
           name: xpath
           type: string
           value: [xpath.value]    
       test:
         type: [TESTTYPE NAME]
         parameters:
         - parameter:
             name: check_existence
             type: string
             value: [check_existence.value]
         - parameter: 
             name: check
             type: string
             value: [check.value]
         - parameter:
             name: operation
             type: string
             value: [operation.value]
         - parameter: 
             name: datatype
             type: string
             value: [datatype.value]  
         - parameter: 
             name: value_of
             type: string
             value: [value_of.value]      

JSON
^^^^

::

   "artifact-expression": {
     "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
     "artifact-title": "[RECOMMENDATION TITLE]",
     "artifact": {
       "type": "[ARTIFACTTYPE NAME]",
       "parameters": [
         {
           "parameter": {
             "name": "filepath",
             "type": "string",
             "value": "[filepath.value]"
           }
         },
         {
           "parameter": {
             "name": "xpath",
             "type": "string",
             "value": "[xpath.value]"
           }
         }
       ]
     },
     "test": {
       "type": "[TESTTYPE NAME]",
       "parameters": [
         {
           "parameter": {
             "name": "check_existence",
             "type": "string",
             "value": "[check_existence.value]"
           }
         },
         {
           "parameter": {
             "name": "check",
             "type": "string",
             "value": "[check.value]"
           }
         },
         {
           "parameter": {
             "name": "operation",
             "type": "string",
             "value": "[operation.value]"
           }
         },
         {
           "parameter": {
             "name": "datetype",
             "type": "string",
             "value": "[datatype.value]"
           }
         },
         {
           "parameter": {
             "name": "value_of",
             "type": "string",
             "value": "[value_of.value]"
           }
         }
       ]
     }
   }
