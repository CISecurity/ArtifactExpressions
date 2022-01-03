windows.auditeventsubcategories
==================================

Description
-----------

The auditeventpolicysubcategories_test is used to check the audit event
policy settings on a Windows system. These settings are used to specify
which system and network events are monitored. For example, if the
credential_validation element has a value of AUDIT_FAILURE, it means
that the system is configured to log all unsuccessful attempts to
validate a user account on a system.

The intent of the ``windows.auditeventsubcategories`` artifact type is
to allow users to create specific checks against the the audit event
policy settings on a Windows system. The ``auditeventpolicsubcatgeory``
parameter is constrained to the specific list of values, each
representing one of the audit event policy attributes that can be
collected.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

========================== ====== ==============================
Name                       Type   Description
========================== ====== ==============================
auditeventpolicsubcatgeory String Audit Event Policy Subcategory
========================== ====== ==============================

  - credential_validation
  - kerberos_authentication_service 
  - kerberos_service_ticket_operations
  - kerberos_ticket_events (Deprecated) 
  - other_account_logon_event
  - application_group_management 
  - computer_account_management
  - distribution_group_management 
  - other_account_management_events
  - security_group_management 
  - user_account_management dpapi_activity
  - process_creation
  - process_termination rpc_events
  - directory_service_access directory_service_change
  - directory_service_replication detailed_directory_service
  - ccount_lockout ipsec_extended_mode ipsec_main_mode ipsec_quick_mode
  - logoff
  - logon network_policy_server 
  - other_logon_logoff_event special_logon
  - logon_claims
  - application_generated
  - certification_services
  - detailed_file_share file_share
  - file_system filtering_platform_connection filtering_platform_packet
  - handle_manipulation kernel_object
  - other_object_access_event registry
  - sam removable_storage
  - central_access_policy_staging audit_policy_change
  - authentication_policy_change authorization_policy_change
  - filtering_platform_policy mpssvc_rule_level_policy_change
  - other_policy_change_event non_sensitive_privilege_use
  - other_privilege_use_event sensitive_privilege_use ipsec_driver
  - other_system_events security_state_change
  - security_system_extension system_integrity
  - group_membership pnp_activity
  - user_device_claims
  - audit_detailedtracking_tokenrightadjusted

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Equals
  - Equal
  - Not Equal
  - Less Than
  - Less Than or Equal
  - Greater Than
  - Greater Than or Equal

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

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
                   <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION_NUMBER]">
                       <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
                       <ae:title>[RECOMMENDATION_TITLE]</ae:title>
                       <ae:artifact type="[ARTIFACTTYPE NAME]">
                           <ae:parameters>
                               <ae:parameter dt="string" name="auditeventpolicsubcatgeory"
                                   >[auditeventpolicysubcategory.value]</ae:parameter>
                           </ae:parameters>
                       </ae:artifact>
                       <ae:test type="[TESTTYPE NAME]">
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

For ``windows.auditeventsubcategories`` artifacts, an XCCDF Value
element is generated:

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
          operator="[test_type]" type="data_type.value">
     <title>[RECOMMENDATION TITLE]</title>
     <description>This value is used in Rule: [RECOMMENDATION TITLE]</description>
     <value>[value.value]</value>
   </Value>

OVAL
''''

Test

::

     <auditeventpolicysubcategories_test
                xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
                id="oval:org.cisecurity.benchmarks.windows_10:tst:[ARTIFACT-OVAL-ID]"
                check_existence="at_least_one_exists" check="all"
                comment="[RECOMMENDATION TITLE]"
                version="[version.value]">
                <object object_ref="oval:org.cisecurity.benchmarks.windows_10:obj:[ARTIFACT-OVAL-ID]"/>
                <state state_ref="oval:org.cisecurity.benchmarks.windows_10:ste:[ARTIFACT-OVAL-ID]"/>
    </auditeventpolicysubcategories_test>

Object

::

    <auditeventpolicysubcategories_object
               xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
               id="oval:org.cisecurity.benchmarks.windows_10:obj:[ARTIFACT-OVAL-ID]"
               comment="[RECOMMENDATION TITLE]"
               version="[version.value]"/>

State

::

   <auditeventpolicysubcategories_state
               xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
               id="oval:org.cisecurity.benchmarks.windows_10:ste:[ARTIFACT_OVAL_ID]"
               comment="[RECOMMENDATION TITLE]"
               version="[version.value]">
               <pnp_activity operation="[test_type]" datatype="[data_type.value]"
                   var_ref="oval:org.cisecurity.benchmarks.windows_10:var:[ARTIFACT-OVAL-ID]"/>
   </auditeventpolicysubcategories_state>

Variable
        

::

   <external_variable comment="This value is used in [RECOMMENDATION TITLE]" 
                     datatype="[data_type.value]" 
                           id="oval:org.cisecurity.benchmarks.PLATFORM:var:ARTIFACT-OVAL-ID" 
   version="[version.value]"/>

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
             name: auditeventpolicsubcatgeory
             type: string
             value: [auditeventpolicsubcatgeory.value]
       test:
         type: [TESTTYPE NAME]
         parameters:
         - parameter:
             name: value
             type: string
             value: [value.value]
         - parameter: 
             name: data_type
             type: string
             value: [data_type.value]

JSON
^^^^

::

   "artifact-expression": {
     "artifact-unique-id": [ARTIFACT-OVAL-ID],
     "artifact-title": [RECOMMENDATION TITLE],
     "artifact": {
       "type": "[ARTIFACTTYPE NAME]",
       "parameters": [
         {
           "parameter": {
             "name": "auditeventpolicsubcatgeory",
             "type": "string",
             "value": "[auditeventpolicsubcatgeory.value]"
           }
         }
       ]
     },
     "test": {
       "type": "[TESTTYPE NAME]",
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
