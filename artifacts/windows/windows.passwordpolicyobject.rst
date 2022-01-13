windows.passwordpolicyobject
============================

Description
-----------

The password policy test is used to check specific policy associated
with passwords. It is important to note that these policies are specific
to certain versions of Windows. As a result, the documentation for that
version of Windows should be consulted for more information.

The intent of the ``windows.passwordpolicyobject`` artifact type is to
allow users to create specific checks against the Windows password
policy. The ``passwordpolicysetting`` parameter is constrained to the
specific list of values, each representing one of the password policy
attributes that can be collected.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

===================== ====== ==========================================
Name                  Type   Description
===================== ====== ==========================================
passwordpolicysetting String The password policy setting to be audited.
===================== ====== ==========================================

NOTE: This parameter is governed by a constraint allowing only the
following values: - Max Passwd Age - Min Passwd Age - Min Passwd Len -
Password Hist Len - Password Complexity - Reversible Encryption

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Equals
  - Not Equal
  - Less Than
  - Less Than or Equal
  - Greater Than
  - Greater Than or Equal

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

Equal
^^^^^

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| data_type                           | String      | datatype of the  |
|                                     |             | value            |
+-------------------------------------+-------------+------------------+
| value                               | String      | the value        |
|                                     |             | included within  |
|                                     |             | the set of       |
|                                     |             | results/ value   |
|                                     |             | to be tested     |
+-------------------------------------+-------------+------------------+

Equals
^^^^^^

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| data_type                           | String      | datatype of the  |
|                                     |             | value            |
+-------------------------------------+-------------+------------------+
| value                               | String      | the value        |
|                                     |             | included within  |
|                                     |             | the set of       |
|                                     |             | results/ value   |
|                                     |             | to be tested     |
+-------------------------------------+-------------+------------------+

Not Equal
^^^^^^^^^

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| data_type                           | String      | datatype of the  |
|                                     |             | value            |
+-------------------------------------+-------------+------------------+
| value                               | String      | the value        |
|                                     |             | included within  |
|                                     |             | the set of       |
|                                     |             | results/ value   |
|                                     |             | to be tested     |
+-------------------------------------+-------------+------------------+

Less Than
^^^^^^^^^

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| data_type                           | String      | datatype of the  |
|                                     |             | value            |
+-------------------------------------+-------------+------------------+
| value                               | String      | the value        |
|                                     |             | included within  |
|                                     |             | the set of       |
|                                     |             | results/ value   |
|                                     |             | to be tested     |
+-------------------------------------+-------------+------------------+

Less Than or Equal
^^^^^^^^^^^^^^^^^^

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| data_type                           | String      | datatype of the  |
|                                     |             | value            |
+-------------------------------------+-------------+------------------+
| value                               | String      | the value        |
|                                     |             | included within  |
|                                     |             | the set of       |
|                                     |             | results/ value   |
|                                     |             | to be tested     |
+-------------------------------------+-------------+------------------+

Greater Than
^^^^^^^^^^^^

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| data_type                           | String      | datatype of the  |
|                                     |             | value            |
+-------------------------------------+-------------+------------------+
| value                               | String      | the value        |
|                                     |             | included within  |
|                                     |             | the set of       |
|                                     |             | results/ value   |
|                                     |             | to be tested     |
+-------------------------------------+-------------+------------------+

Greater Than or Equal
^^^^^^^^^^^^^^^^^^^^^

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| data_type                           | String      | datatype of the  |
|                                     |             | value            |
+-------------------------------------+-------------+------------------+
| value                               | String      | the value        |
|                                     |             | included within  |
|                                     |             | the set of       |
|                                     |             | results/ value   |
|                                     |             | to be tested     |
+-------------------------------------+-------------+------------------+

data_type NOTE: This parameter is governed by a constraint allowing only
the following values: - boolean - float - int - string - version - set

Generated Content
~~~~~~~~~~~~~~~~~

equal, equals, not equal, less than, less than or equal, greater than, greater than or equal
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

   <xccdf:complex-check operator="AND">
       <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
           <xccdf:check-content>
               <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
                   <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
                   <ae:title>[ARTIFACT-TITLE]</ae:title>
                   <ae:artifact type="[ARTIFACT-TYPE-NAME]">
                       <ae:parameters>
                           <ae:parameter dt="string" name="passwordpolicysetting">[passwordpolicysetting.value]</ae:parameter>
                       </ae:parameters>
                   </ae:artifact>
                   <ae:test type="[TEST-TYPE-NAME]">
                       <ae:parameters>
                           <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
                           <ae:parameter dt="string" name="data_type">[data_type.value]</ae:parameter>
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

For ``windows.passwordpolicyobject`` artifacts, an XCCDF Value element
is generated:

::

   <xccdf:complex-check operator="AND">
     <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
       <check-export export-name="oval:org.cisecurity.benchmarks.windows_10:var:[ARTIFACT-OVAL-ID]"
         value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"/>
       <check-content-ref
         href="CIS_Microsoft_Windows_10_Enterprise_Release_2004_Benchmark_v1.9.0-oval.xml"
         name="oval:org.cisecurity.benchmarks.windows_10:def:[ARTIFACT-OVAL-ID]"/>
     </check>
   </xccdf:complex-check>

   <Value id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" 
          operator="test_type" type="data_type.value">
     <title>[ARTIFACT-TITLE]</title>
     <description>This value is used in Rule: [ARTIFACT-TITLE]</description>
     <value>[value.value]</value>
   </Value>

OVAL
''''

Test

::

   <passwordpolicy_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows" 
                        check="all" 
              check_existence="at_least_one_exists" 
                      comment="[ARTIFACT-TITLE]" 
                           id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
                      version="1">
      <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"/>
      <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"/>
   </passwordpolicy_test>

Object

::

   <passwordpolicy_object 
       xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows" 
     comment="[ARTIFACT-TITLE]" 
          id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
     version="[version.value]"/>

State

::

   <passwordpolicy_state 
      xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows" 
    comment="[ARTIFACT-TITLE]" 
         id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" version="1">
      <[passwordpolicysetting.value] datatype="[data_type.value]" 
         operation="[test_type]" 
           var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"/>
   </passwordpolicy_state>

Variable
        

::

   <external_variable comment="This value is used in [ARTIFACT-TITLE]" 
                     datatype="[data_type.value]" 
                           id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
                      version="[version.value]"/>

YAML
^^^^

::

  - artifact-expression:
       artifact-unique-id: "[ARTIFACT-OVAL-ID]"
       artifact-title: "[ARTIFACT-TITLE]"
       artifact:
         type: "[ARTIFACT-TYPE-NAME]"
         parameters:
         - parameter: 
             name: passwordpolicysetting
             dt: "string"
             value: "[passwordpolicysetting.value]
       test:
         type: "[TEST-TYPE-NAME]"
         parameters:
         - parameter:
             name: value
             dt: "string"
             value: "[value.value]
         - parameter: 
             name: data_type
             dt: "string"
             value: "[data_type.value]

JSON
^^^^

::

   "artifact-expression": {
     "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
     "artifact-title": "[ARTIFACT-TITLE]",
     "artifact": {
       "type": "[ARTIFACT-TYPE-NAME]",
       "parameters": [
         {
           "parameter": {
             "name": "passwordpolicysetting",
             "type": "string",
             "value": [passwordpolicysetting.value]
           }
         }
       ]
     },
     "test": {
       "type": "[TEST-TYPE-NAME]",
       "parameters": [
         {
           "parameter": {
             "name": "value",
             "type": "string",
             "value": "[value.value]"
           }
         },
         {
           "parameter": {
             "name": "data_type",
             "type": "string",
             "value": "[data_type.value]"
           }
         }
       ]
     }
   }
