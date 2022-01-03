windows.user_registry_value_v1
==============================

Description
-----------

The registry test is used to check metadata associated with Windows
registry key. It extends the standard TestType as defined in the
oval-definitions-schema and one should refer to the TestType description
for more information. The object element references a
registry_object and the state element specifies the registry
data to check.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

============= ====== =========================================
Name          Type   Description
============= ====== =========================================
key           String The registry sub-key under HKEY_USERS/SID
name          String The name of the registry key to collect
registry_view String The windows view parameter for collection
============= ====== =========================================

registry_view NOTE: This parameter is governed by a constraint allowing
only the following values: - default - 32_bit - 64_bit

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - windows.user_registry_value_v1

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| existence_check                     | String      | The existence    |
|                                     |             | check determines |
|                                     |             | a required       |
|                                     |             | number of items  |
|                                     |             | to be collected  |
|                                     |             | from the target  |
|                                     |             | endpoint         |
+-------------------------------------+-------------+------------------+
| check                               | String      | The check        |
|                                     |             | element          |
|                                     |             | describes how    |
|                                     |             | many collected   |
|                                     |             | items must match |
|                                     |             | the expected     |
|                                     |             | state            |
+-------------------------------------+-------------+------------------+
| registry_type                       | String      | The datatype of  |
|                                     |             | the collected    |
|                                     |             | registry value   |
+-------------------------------------+-------------+------------------+
| registry_type_operator              | String      | The registry     |
|                                     |             | type operator    |
|                                     |             | describes the    |
|                                     |             | comparison       |
|                                     |             | operation for    |
|                                     |             | the registry     |
|                                     |             | type field       |
+-------------------------------------+-------------+------------------+
| registry_value                      | String      | The registry     |
|                                     |             | value            |
+-------------------------------------+-------------+------------------+
| registry_value_datatype             | String      | datatype         |
+-------------------------------------+-------------+------------------+
| registry_value_operator             | String      | The registry     |
|                                     |             | value comparison |
|                                     |             | operation        |
+-------------------------------------+-------------+------------------+

registry_type NOTE: This parameter is governed by a constraint allowing
only the following values: - reg_dword - reg_sz -
reg_dword_little_endian - reg_dword_big_endian - reg_expand_sz -
reg_multi_sz - reg_binary - reg_link - reg_none -
reg_qword_little_endian

check NOTE: This parameter is governed by a constraint allowing only the
following values: - all - at least one - none satisfy - only one

check_existence NOTE: This parameter is governed by a constraint
allowing only the following values: - all_exist - any_exist -
at_least_one_exists - none_satisfy - none_exist - only_one_exists

registry_value_datatype NOTE: This parameter is governed by a constraint
allowing only the following values: - boolean - float - int - string -
version - set

registry_value_operator NOTE: This parameter is governed by a constraint
allowing only the following values: - equals - not equal - case
insensitive equals - case insensitive not equal - greater than - less
than - greater than or equal - less than or equal - bitwise and -
bitwise or - pattern match - subset of - superset of

Generated Content
~~~~~~~~~~~~~~~~~

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

   <xccdf:complex-check operator="AND">
       <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
       <xccdf:check-content>
           <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_5.1.2">
               <ae:artifact_oval_id>[ARTIFACT_OVAL_ID]</ae:artifact_oval_id>
               <ae:title>[RECOMMENDATION_TITLE]</ae:title>
               <ae:artifact type="[ARTIFACT_TYPE.name]">
                   <ae:parameters>
                       <ae:parameter dt="string" name="key>[key.value]</ae:parameter>
                       <ae:parameter dt="string" name="name>[name.value]</ae:parameter>
                       <ae:parameter dt="string" name="registry_view"
                           >[registry_view.value]</ae:parameter>
                   </ae:parameters>
               </ae:artifact>
               <ae:test type="[TESTTYPE_NAME]">
                   <ae:parameters>
           <ae:parameters>
               <ae:parameter dt="string" name="existence_check"
                   >[existence_check.value]</ae:parameter>
               <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
               <ae:parameter dt="string" name="registry_type"
                   >[registry_type.value]</ae:parameter>
               <ae:parameter dt="string" name="registry_type_operator"
                   >[registry_type_operator.value]</ae:parameter>
               <ae:parameter dt="string" name="registry_value"
                   >[registry_value.value]</ae:parameter>
               <ae:parameter dt="string" name="registry_value_datatype"
                   >[registry_value_datatype.value]</ae:parameter>
               <ae:parameter dt="string" name="registry_value_operator"
                   >[registry_value_operator.value]</ae:parameter>
           </ae:parameters>               
               </ae:test>
           </ae:artifact_expression>
       </xccdf:check-content>
       </xccdf:check>
   </xccdf:complex-check>

SCAP
^^^^

XCCDF
'''''

For ``windows.user_registry_value_v1`` artifacts, an XCCDF Value element
is generated:

::

   <Values>
               <Value id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT_OVAL_ID]_var1" type="string"
                   operator="equals">
                   <title>[RECOMMENDATION_TITLE]</title>
                   <description>This value is used in Rule: [RECOMMENDATION_TITLE]</description>
                   <value>[TestType.value.value]</value>
               </Value>
               <Value id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT_OVAL_ID]_var2" type="string"
                   operator="equals">
                   <title>[RECOMMENDATION_TITLE]</title>
                   <description>This value is used in Rule: [RECOMMENDATION_TITLE]</description>
                   <value>[TestType.value.value]</value>
               </Value>
           </Values>

OVAL
''''

Test

::

   <registry_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
               id="oval:org.cisecurity.benchmarks.windows_8.1:tst:[ARTIFACT_OVAL_ID]"
               check_existence="at_least_one_exists" check="all"
               comment="[RECOMMENDATION_TITLE]"
               version="[version.value]">
               <object object_ref="oval:org.cisecurity.benchmarks.windows_8.1:obj:[ARTIFACT_OVAL_ID]"/>
               <state state_ref="oval:org.cisecurity.benchmarks.windows_8.1:ste:[ARTIFACT_OVAL_ID]"/>
           </registry_test>

Object

::

   <registry_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
               id="oval:org.cisecurity.benchmarks.windows_8.1:obj:[ARTIFACT_OVAL_ID]"
               comment="[RECOMMENDATION_TITLE]"
               version="[version.value]">
               <hive>[hive.value]</hive>
               <key operation="[testType.name]">[key.value]</key>
               <name>[name.value]</name>
           </registry_object>

State

::

   <registry_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
               id="oval:org.cisecurity.benchmarks.windows_8.1:ste:[ARTIFACT_OVAL_ID]"
               comment="[RECOMMENDATION_TITLE]"
               version="[version.value]">
               <type>[testType.value.value]</type>
               <value datatype="string" operation="[testType.name]">O:BAG:BAD:(A;;RC;;;BA)</value>
           </registry_state>

Variable
        

::

   <external_variable id="oval:org.cisecurity.benchmarks.windows_8.1:var:[ARTIFACT_OVAL_ID]1"
               datatype="string" version="[version.value]"
               comment="This value is used in Rule: [RECOMMENDATION_TITLE]/>
   <external_variable id="oval:org.cisecurity.benchmarks.windows_8.1:var:[ARTIFACT_OVAL_ID]2"
       datatype="string" version="[version.value]"
       comment="This value is used in Rule:[RECOMMENDATION_TITLE]"
   />

YAML
^^^^

::

  - artifact-expression:
       artifact-unique-id: [ARTIFACT-OVAL-ID]
       artifact-title: [RECOMMENDATION TITLE]
       artifact:
         type: windows.user_registry_value_v1
         parameters:
         - parameter: 
             name: hive
             type: string
             value: [ARTIFACT TYPE PARAMETER VALUE]
         - parameter: 
               name: key_operator
               type: string
               value: [ARTIFACT TYPE PARAMETER VALUE]
           - parameter: 
                name: key
                type: string
                value: [ARTIFACT TYPE PARAMETER VALUE]
           - parameter: 
                  name: name
                  type: string
                  value: [ARTIFACT TYPE PARAMETER VALUE]
           - parameter: 
                name: check_existence
                type: string
                value: [ARTIFACT TYPE PARAMETER VALUE]
            - parameter: 
                  name: registry_view
                  type: string
                  value: [ARTIFACT TYPE PARAMETER VALUE]
            - parameter: 
                   name: registry_data_type
                   type: string
                   value: [ARTIFACT TYPE PARAMETER VALUE]
           - parameter: 
                 name: name_operation
                 type: string
                 value: [ARTIFACT TYPE PARAMETER VALUE]
   test:
     type: [TestType Name]
     parameters:
       - parameter:
          name: existence_check
          type: string
          value: [existence_check.value]
       - parameter:
          name: check
          type: string
          value: [TestType.check.value]
       - parameter:
           name: registry_type
           type: string
           value: [TestType.registry_type.value]
       - parameter:
           name: registry_type_operator
           type: string
           value: [TestType.registry_type_operator.value]
       - parameter:
           name: registry_value
           type: string
           value: [TestType.registry_value.value]
       - parameter:
           name: registry_value_datatype
           type: string
           value: [TestType.registry_value_datatype.value]
       - parameter:
           name: registry_value_operator
           type: string
           value: [TestType.registry_value_operator.value]
                                                 

JSON
^^^^

::
     
       "artifact-expression": {
         "artifact-unique-id": [
           "ARTIFACT-OVAL-ID"
         ],
         "artifact-title": [
           "RECOMMENDATION TITLE"
         ],
         "artifact": {
           "type": "windows.user_registry_value_v1",
           "parameters": [
             {
               "parameter": {
                 "name": "hive",
                 "type": "string",
                 "value": [
                   "ARTIFACT TYPE PARAMETER VALUE"
                 ]
               }
             },
             {
               "parameter": {
                 "name": "key_operator",
                 "type": "string",
                 "value": [
                   "ARTIFACT TYPE PARAMETER VALUE"
                 ]
               }
             },
             {
               "parameter": {
                 "name": "key",
                 "type": "string",
                 "value": [
                   "ARTIFACT TYPE PARAMETER VALUE"
                 ]
               }
             },
             {
               "parameter": {
                 "name": "name",
                 "type": "string",
                 "value": [
                   "ARTIFACT TYPE PARAMETER VALUE"
                 ]
               }
             },
             {
               "parameter": {
                 "name": "check_existence",
                 "type": "string",
                 "value": [
                   "ARTIFACT TYPE PARAMETER VALUE"
                 ]
               }
             },
             {
               "parameter": {
                 "name": "registry_view",
                 "type": "string",
                 "value": [
                   "ARTIFACT TYPE PARAMETER VALUE"
                 ]
               }
             },
             {
               "parameter": {
                 "name": "registry_data_type",
                 "type": "string",
                 "value": [
                   "ARTIFACT TYPE PARAMETER VALUE"
                 ]
               }
             },
             {
               "parameter": {
                 "name": "name_operation",
                 "type": "string",
                 "value": [
                   "ARTIFACT TYPE PARAMETER VALUE"
                 ]
               }
             }
           ]
         }
       }
     }
   ]},
   "test": {
   "type": [
     "TestType Name"
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
         "name": "check",
         "type": "string",
         "value": [
           "TestType.check.value"
         ]
       }
     },
     {
       "parameter": {
         "name": "registry_type",
         "type": "string",
         "value": [
           "TestType.registry_type.value"
         ]
       }
     },
     {
       "parameter": {
         "name": "registry_type_operator",
         "type": "string",
         "value": [
           "TestType.registry_type_operator.value"
         ]
       }
     },
     {
       "parameter": {
         "name": "registry_value",
         "type": "string",
         "value": [
           "TestType.registry_value.value"
         ]
       }
     },
     {
       "parameter": {
         "name": "registry_value_datatype",
         "type": "string",
         "value": [
           "TestType.registry_value_datatype.value"
         ]
       }
     },
     {
       "parameter": {
         "name": "registry_value_operator",
         "type": "string",
         "value": [
           "TestType.registry_value_operator.value"
         ]
       }
     }
   ]
   }
