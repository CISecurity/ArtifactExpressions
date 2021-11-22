macos.keychain_v1
=================

Description
-----------

The keychain_test is used to check the properties of the plist-style XML
output from the “security show-keychain-info >keychain<” command, for
reading information about keychain settings on MacOSX. It extends the
standard TestType as defined in the oval-definitions-schema and one
should refer to the TestType description for more information. The
object element references an keychain_object and the state element specifies the data to check.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| filepath                            | String      | Specifies the    |
|                                     |             | filepath of the  |
|                                     |             | keychain to be   |
|                                     |             | queried. The     |
|                                     |             | default keychain |
|                                     |             | for a user is    |
|                                     |             | normally located |
|                                     |             | at               |
|                                     |             | ~/L              |
|                                     |             | ibrary/Keychains |
|                                     |             | /login.keychain. |
+-------------------------------------+-------------+------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - macos.keychain_timeout_v1
  - macos.keychain_lock_on_sleep_v1

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

macos.keychain_timeout_v1
^^^^^^^^^^^^^^^^^^^^^^^^^

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
| timeout                             | Integer     | Specifies the    |
|                                     |             | inactivity       |
|                                     |             | timeout (in      |
|                                     |             | seconds) for the |
|                                     |             | keychain, or 0   |
|                                     |             | if there is no   |
|                                     |             | timeout.         |
+-------------------------------------+-------------+------------------+

macos.keychain_lock_on_sleep_v1
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
| lock_on_sleep                       | Boolean     | Specifies        |
|                                     |             | whether the      |
|                                     |             | keychain is      |
|                                     |             | configured to    |
|                                     |             | lock when the    |
|                                     |             | computer sleeps. |
+-------------------------------------+-------------+------------------+

check_existence NOTE: This parameter is governed by a constraint
allowing only the following values: - all_exist - any_exist -
at_least_one_exists - none_satisfy - none_exist - only_one_exists

check NOTE: This parameter is governed by a constraint allowing only the
following values: - all - at least one - none satisfy - only one

operation NOTE: This parameter is governed by a constraint allowing only
the following values: - equals - not equal - case insensitive equals -
case insensitive not equal - greater than - less than - greater than or
equal - less than or equal - bitwise and - bitwise or - pattern match -
subset of - superset of

datatype NOTE: This parameter is governed by a constraint allowing only
the following values: - boolean - float - int - string - version - set

Generated Content
~~~~~~~~~~~~~~~~~

macos.keychain_timeout_v1
^^^^^^^^^^^^^^^^^^^^^^^^^

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
             <ae:parameter dt="string" name="filepath"
               >[filepath.value]</ae:parameter>
           </ae:parameters>
         </ae:artifact>
         <ae:test type="[TESTTYPE NAME]">
           <ae:parameters>
             <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
             <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
             <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
             <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
             <ae:parameter dt="integer" name="timeout">[timeout.value]</ae:parameter>
           </ae:parameters>
         </ae:test>
         <ae:profiles>
           <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_2"/>
         </ae:profiles>
       </ae:artifact_expression>
     </xccdf:check-content>
   </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``macos.keychain_v1`` artifacts, the xccdf:check looks like this. There is no Value in the xccdf for this Artifact.

::

   <xccdf:check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
     <xccdf:check-content-ref xmlns:ae="http://benchmarks.cisecurity.org/ae/0.5"
        xmlns:cpe="http://cpe.mitre.org/language/2.0" xmlns:ecl="http://cisecurity.org/check"
        href="CIS_Apple_macOS_10.13_Benchmark_v1.0.0.1-oval.xml"
        name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]"/>
   </xccdf:check>

OVAL
''''

Test

::

   <macos:keychain_test check="[check.value]" check_existence="[check_existence.value]"
     comment="[RECOMMENDATION TITLE]"
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" version="[version.value]">
     <macos:object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"/>
     <macos:state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"/>
   </macos:keychain_test>

Object

::

   <macos:keychain_object
     comment="[RECOMMENDATION TITLE]"
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" version="[version.value]">
     <macos:filepath>[filepath.value]</macos:filepath>
   </macos:keychain_object>

State

::

   <macos:keychain_state
     comment="[RECOMMENDATION TITLE]"
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" version="[version.value]">
     <macos:timeout datatype="[datatype.value]" operation="[operation.value]">[timeout.value]</macos:timeout>
   </macos:keychain_state>

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
             name: timeout
             type: string
             value: [timeout.value]  

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
             "name": "timeout",
             "type": "string",
             "value": "[timeout.value]"
           }
         }
       ]
     }
   }

Generated Content
~~~~~~~~~~~~~~~~~

macos.keychain_lock_on_sleep_v1
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
             <ae:parameter dt="string" name="filepath"
               >[filepath.value]</ae:parameter>
           </ae:parameters>
         </ae:artifact>
         <ae:test type="[TESTTYPE NAME]">
           <ae:parameters>
             <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
             <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
             <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
             <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
             <ae:parameter dt="integer" name="lock_on_sleep">[lock_on_sleep.value]</ae:parameter>
           </ae:parameters>
         </ae:test>
         <ae:profiles>
           <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_2"/>
         </ae:profiles>
       </ae:artifact_expression>
     </xccdf:check-content>
   </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``macos.keychain_v1`` artifacts, the xccdf:check looks like this. There is no Value in the xccdf for this Artifact.

::

   <xccdf:check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
     <xccdf:check-content-ref xmlns:ae="http://benchmarks.cisecurity.org/ae/0.5"
        xmlns:cpe="http://cpe.mitre.org/language/2.0" xmlns:ecl="http://cisecurity.org/check"
        href="CIS_Apple_macOS_10.13_Benchmark_v1.0.0.1-oval.xml"
        name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]"/>
   </xccdf:check>

OVAL
''''

Test

::

   <macos:keychain_test check="[check.value]" check_existence="[check_existence.value]"
     comment="[RECOMMENDATION TITLE]"
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" version="[version.value]">
     <macos:object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"/>
     <macos:state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"/>
   </macos:keychain_test>

Object

::

   <macos:keychain_object
     comment="[RECOMMENDATION TITLE]"
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" version="[version.value]">
     <macos:filepath>[filepath.value]</macos:filepath>
   </macos:keychain_object>

State

::

   <macos:keychain_state
     comment="[RECOMMENDATION TITLE]"
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" version="[version.value]">
     <macos:lock_on_sleep datatype="[datatype.value]" operation="[operation.value]">[lock_on_sleep.value]</macos:lock_on_sleep>
   </macos:keychain_state>

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
             name: lock_on_sleep
             type: string
             value: [lock_on_sleep.value]  

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
             "name": "lock_on_sleep",
             "type": "string",
             "value": "[lock_on_sleep.value]"
           }
         }
       ]
     }
   }
