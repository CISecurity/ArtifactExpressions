macos.softwareupdate_v1
===================

Description
-----------

The softwareupdate_test is used to check the status of automatic software updates
on MacOSX. It is a singleton object. It extends the standard TestType as defined
in the oval-definitions-schema and one should refer to the TestType description
for more information. The state element specifies the softwareupdate elements
to check.


Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| check_existence                     | String      | Defines how many |
|                                     |             | items should be  |
|                                     |             | collected. mac   |
|                                     |             |                  |
|                                     |             |                  |
+-------------------------------------+-------------+------------------+

check_existence NOTE: This parameter is governed by a constraint
allowing only the following values: - all_exist - any_exist - at_least_one_exists - none_exist - only_one_exists


Supported Test Types
~~~~~~~~~~~~~~~~~~~~

-  macos.softwareupdate_v1

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
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
| schedule                            | Boolean     | Specifies        |
|                                     |             | whether          |
|                                     |             | automatic        |
|                                     |             | checking is      |
|                                     |             | enabled (true).  |
+-------------------------------------+-------------+------------------+
| software_title                      |             | Specifies the    |
|                                     |             | title string for |
|                                     |             | an available     |
|                                     |             | (not installed)  |
|                                     |             | software update. |
+-------------------------------------+-------------+------------------+

check NOTE: This parameter is governed by a constraint allowing only the
following values: - all - at least one - none satisfy - only one

operation NOTE: This parameter is governed by a constraint allowing only
the following values: - equals - not equal - case insensitive equals -
case insensitive not equal - greater than - less than - greater than or
equal - less than or equal - bitwise and - bitwise or - pattern match -
subset of - superset of

datatype NOTE: This parameter is governed by a constraint allowing only
the following values: - boolean - float - int - string - version - set

schedule NOTE: This parameter is governed by a constraint allowing only
the following values: - true - false

software_title NOTE: This parameter is governed by a constraint allowing only
the following values: - ^.+$

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
              <ae:parameter dt="string" name="check_existence"
                >[check_existence.value]</ae:parameter>
			</ae:parameters>
		 </ae:artifact>
		 <ae:test type="[TESTTYPE NAME]">
           <ae:parameters>
			 <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
			 <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
			 <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
			 <ae:parameter dt="boolean" name="schedule">[schedule.value]</ae:parameter>
			 <ae:parameter dt="string" name="software_title">[software_title.value]</ae:parameter>
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

For ``macos.softwareupdate_v1`` artifacts, the xccdf:check looks like this.
There is no Value in the xccdf for this Artifact.

::

   <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
      <check-content-ref
         href="[BENCHMARK NAME]"
         name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]">
      </check-content-ref>
   </check>

OVAL
''''

Test


::

   <softwareupdate_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos" check="[check.value]" check_existence="[check_existence.value]"
     comment="[RECOMMENDATION TITLE]"
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" version="[version.value]">
     <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"></object>
     <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"></state>
   </softwareupdate_test>

Object


::

   <softwareupdate_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
     comment="[RECOMMENDATION TITLE]"
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" version="[version.value]">
   </softwareupdate_object>

State


::

   <softwareupdate_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
     comment="Update Software"
     id="oval:org.cisecurity.benchmarks.apple_mac_os_x_10:ste:2029251" version="1">
     <schedule datatype="boolean" operation="equals">false</schedule>
     <software_title datatype="string" operation="equals">Software title to test</software_title>
   </softwareupdate_state>

YAML
^^^^

::

   - artifact-expression:
       artifact-unique-id: "[ARTIFACT-OVAL-ID]"
       artifact_title: "[RECOMMENDATION TITLE]"
       artifact:
         type: "[ARTIFACTTYPE NAME]"
         parameters:
         - parameter:
             name: "check_existence"
             dt: "string"
             value: "[check_existence.value]"
       test:
         type: "[TESTTYPE NAME]"
         parameters:
         - parameter:
             name: "check"
             dt: "string"
             value: "[check.value]"
         - parameter:
             name: "operation"
             dt: "string"
             value: "[operation.value]"
         - parameter:
             name: "datatype"
             dt: "string"
             value: "[datatype.value]"
         - parameter:
             name: "schedule"
             dt: "boolean"
             value: "[schedule.value]"
         - parameter:
             name: "software_title"
             dt: "string"
             value: "[software_title.value]"

JSON
^^^^

::


   "artifact-expression": {
     "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
     "artifact_title": "[RECOMMENDATION TITLE]",
     "artifact": {
       "type": "[ARTIFACTTYPE NAME]",
       "parameters": [
         {
           "parameter": {
             "name": "check_existence",
             "dt": "string",
             "value": "[check_existence.value]"
           }
         }
       ]
     },
     "test": {
       "type": "[TESTTYPE NAME]",
       "parameters": [
         {
           "parameter": {
             "name": "check",
             "dt": "string",
             "value": "[check.value]"
           }
         },
         {
           "parameter": {
             "name": "operation",
             "dt": "string",
             "value": "[operation.value]"
           }
         },
         {
           "parameter": {
             "name": "datatype",
             "dt": "string",
             "value": "[datatype.value]"
           }
         },
         {
           "parameter": {
             "name": "schedule",
             "dt": "boolean",
             "value": "[schedule.value]"
           }
         },
         {
           "parameter": {
             "name": "software_title",
             "dt": "string",
             "value": "[software_title.value]"
           }
         }
       ]
     }
   }
