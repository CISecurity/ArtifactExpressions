windows.privilegeassignment
===========================

Description
  -----------

The accesstoken_test is used to check the properties of a Windows access
token as well as individual privileges and rights associated with it.

Technical Details
  -----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| privilegeassignmentsettings         | String      | The privilege    |
|                                     |             | assignment       |
|                                     |             | setting to be    |
|                                     |             | audited.         |
+-------------------------------------+-------------+------------------+

| NOTE: This parameter is governed by a constraint allowing only the
  following values: - security_principle - seassignprimarytokenprivilege
  - seauditprivilege - sebackupprivilege - sechangenotifyprivilege
| - secreateglobalprivilege - secreatepagefileprivilege -
  secreatepermanentprivilege - secreatesymboliclinkprivilege -
  secreatetokenprivilege
| - sedebugprivilege
| - seenabledelegationprivilege - seimpersonateprivilege
| - seincreasebasepriorityprivilege
| - seincreasequotaprivilege
| - seincreaseworkingsetprivilege - seloaddriverprivilege -
  selockmemoryprivilege - semachineaccountprivileg -
  semanagevolumeprivilege
| - seprofilesingleprocessprivilege
| - serelabelprivilege
| - seremoteshutdownprivilege - serestoreprivilege
| - sesecurityprivilege
| - seshutdownprivilege
| - sesyncagentprivilege - sesystemenvironmentprivilege
| - sesystemprofileprivilege
| - sesystemtimeprivilege - setakeownershipprivilege
| - setcbprivilege
| - setimezoneprivilege
| - seundockprivilege - seunsolicitedinputprivilege
| - sebatchlogonright - seinteractivelogonright
| - senetworklogonright
| - seremoteinteractivelogonright - seservicelogonright
| - sedenybatchLogonright - sedenyinteractivelogonright
| - sedenynetworklogonright
| - sedenyremoteInteractivelogonright - sedenyservicelogonright
| - setrustedcredmanaccessnameright

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - setisempty
  - equal
  - set.includes_v1
  - set.white_list_v1
  - equals

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

setisempty
^^^^^^^^^^

==== ==== ===========
Name Type Description
==== ==== ===========
==== ==== ===========

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

set.includes_v1
^^^^^^^^^^^^^^^

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

set.white_list_v1
^^^^^^^^^^^^^^^^^

========= ====== ========================================
Name      Type   Description
========= ====== ========================================
data_type String datatype of the value
values    String Comma separated list of permitted values
========= ====== ========================================

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

data_type NOTE: This parameter is governed by a constraint allowing only
the following values: - boolean - float - int - string - version - set

Generated Content
~~~~~~~~~~~~~~~~~

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

   <xccdf:complex-check operator="OR">
       <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
           <xccdf:check-content>
               <ae:artifact_expression
                   id="xccdf_org.cisecurity.benchmarks_ae_13.1.4">
                   <ae:artifact_oval_id>[ARTIFACT_OVAL_ID]</ae:artifact_oval_id>
                   <ae:title>[RECOMMENDATION_TITLE]</ae:title>
                   <ae:artifact type="[ARTIFACTTYPE_NAME]">
                       <ae:parameters>
                           <ae:parameter dt="string"
                           name="privilegeassignmentsettings>[privilegeassignmentsettings.value]</ae:parameter>
                       </ae:parameters>
                   </ae:artifact>
                   <ae:test type="equals">
                       <ae:parameters>
                           <ae:parameter dt="string" name="value"
                           >[value.value]</ae:parameter>
                           <ae:parameter dt="string" name="data_type"
                           >[datatype.value]</ae:parameter>
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

For ``windows.privilegeassignment`` artifacts, an XCCDF:check element
looks like this. There is no value in the xccdf for this Artifact.

::

     <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
               <check-content-ref
                   href="[BENCHMARK_NAME]"
                   name="oval:org.cisecurity.benchmarks.windows_server_2012_r2:def:[ARTIFACT_OVAL_ID]"/>
           </check>

OVAL
''''

Test

::

   <accesstoken_test xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
               id="oval:org.cisecurity.benchmarks.windows_server_2012_r2:tst:[ARTIFACT_OVAL_ID]"
               check_existence="at_least_one_exists" check="all"
               comment="[RECOMMENDATION_TITLE"
               version="[version.value]">
               <object object_ref="oval:org.cisecurity.benchmarks.windows_server_2012_r2:obj:[ARTIFACT_OVAL_ID]"/>
               <state state_ref="oval:org.cisecurity.benchmarks.windows_server_2012_r2:ste:[ARTIFACT_OVAL_ID]"/>
   </accesstoken_test>

Object

::

    <accesstoken_object xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
               id="oval:org.cisecurity.benchmarks.windows_server_2012_r2:obj:[ARTIFACT_OVAL_ID]"
               comment="[RECOMMENDATION_TITLE]"
               version="[version.value]">
               <[parameter_constraint] operation="case insensitive equals">[parameter_constraint_value]</[parameter_constraint]>
           </accesstoken_object>

State

::

   <accesstoken_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
               id="oval:org.cisecurity.benchmarks.windows_server_2012_r2:ste:6484"
               comment="Ensure &apos;senetworklogonright&apos; is set to &apos;Set White List&apos; - DC"
               version="[version.value]">
               <[parameter_constraint] datatype="boolean" operation="[test_type_name]">false</parameter_constraint>
   </accesstoken_state>

YAML
^^^^

::

  - artifact-expression:
       artifact-unique-id: [ARTIFACT-OVAL-ID]
       artifact-title: [RECOMMENDATION TITLE]
       artifact:
         type: windows.privilegeassignment
         parameters:
         - parameter: 
             name: privilegeassignmentsettings
             type: string
             value: [ARTIFACT TYPE PARAMETER VALUE]
       test:
         type: [TestType Name]
         parameters:
         - parameter:
             name: value
             type: string
             value: [TestType.value.value]
         - parameter: 
             name: data_type
             type: string
             value: [TestType.data_type.value]

JSON
^^^^

::

   "artifact-expression": {
     "artifact-unique-id": [ARTIFACT-OVAL-ID],
     "artifact-title": [RECOMMENDATION TITLE],
     "artifact": {
       "type": "windows.privilegeassignment",
       "parameters": [
         {
           "parameter": {
             "name": "privilegeassignmentsettings",
             "type": "string",
             "value": [ARTIFACT TYPE PARAMETER VALUE]
           }
         }
       ]
     },
     "test": {
       "type": [TestType Name],
       "parameters": [
         {
           "parameter": {
             "name": "value",
             "type": "string",
             "value": [TestType.value.value]
           }
         },
         {
           "parameter": {
             "name": "data_type",
             "type": "string",
             "value": [TestType.data_type.value]
           }
         }
       ]
     }
   }
