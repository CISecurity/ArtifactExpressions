Windows: Audit Event Policy Subcategory
=======================================

Description
-----------

The Windows: Audit Event Policy Subcategory test is used to check the audit event policy settings on a Windows system. These settings are used to specify which system and network events are monitored.  For example, if the credential_validation element has a value of AUDIT_FAILURE, it means that the system is configured to log all unsuccessful attempts to validate a user account on a system. It is important to note that these audit event policy settings are specific to certain versions of Windows. As a result, the documentation for that version of Windows should be consulted for more information on each setting.

The auditeventpolicysubcategories_object element is used by an auditeventpolicysubcategories_test to define those objects to evaluate based on a specified state. There is actually only one object relating to audit event policy subcategories and this is the system as a whole. Therefore, there are no child entities defined.

The auditeventpolicysubcategories_state element specifies the different system activities that can be audited. An audit event policy subcategories test will reference a specific instance of this state that defines the exact subcategories that need to be evaluated.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**windows.auditeventsubcategories**

========================== ====== ===============================
Name                       Type   Description
========================== ====== ===============================
auditeventpolicsubcatgeory string Audit Event Policy Subcategory.
========================== ====== ===============================

NOTE: The ``auditeventpolicsubcatgeory`` parameter is governed by a constraint allowing only the following values:
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

  - Equal
  - Equals
  - Not Equal
  - Less Than
  - Less Than or Equal
  - Greater Than
  - Greater Than or Equal

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

| **equal**
| **equals**
| **not equal**
| **less than**
| **less than or equal**
| **greater than**
| **greater than or equal**
+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| data_type                   | string  | Datatype of the  value.            |
+-----------------------------+---------+------------------------------------+
| value                       | string  | The value included within the set  |
|                             |         | of results / value to be tested.   |
+-----------------------------+---------+------------------------------------+

NOTE: The ``data_type`` parameter is governed by a constraint allowing only the following values:
    - boolean
    - float
    - int
    - string
    - version
    - set

Generated Content
~~~~~~~~~~~~~~~~~

| **equal**
| **equals**
| **not equal**
| **less than**
| **less than or equal**
| **greater than**
| **greater than or equal**
XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:complex-check operator="AND">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
        <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
          <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
          <ae:title>[ARTIFACT-TTILE]</ae:title>
          <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="auditeventpolicsubcatgeory">[auditeventpolicysubcategory.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
              <ae:parameter dt="string" name="data_type">[data_type.value]</ae:parameter>
            </ae:parameters>
          </ae:test>
          <ae:profiles>
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1" />
          </ae:profiles>
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  </xccdf:complex-check>

SCAP
^^^^

XCCDF
'''''

For ``windows.auditeventsubcategories`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    operator="[operator.value]"
    type="string">
    <title>[RECOMMENDATION-TTILE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``windows.auditeventsubcategories`` artifacts, the xccdf:check looks like this.

::

  <xccdf:complex-check operator="AND">
    <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
      <check-export 
        export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
        value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
      <check-content-ref 
        href="[BENCHMARK-TITLE]"
        name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
    </check>
  </xccdf:complex-check>

OVAL
''''

Test

::

  <auditeventpolicysubcategories_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </auditeventpolicysubcategories_test>

Object

::

  <auditeventpolicysubcategories_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1" />

State

::

  <auditeventpolicysubcategories_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <pnp_activity 
      operation="[operation.value]"
      datatype="[datatype.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </auditeventpolicysubcategories_state>

Variable

::

  <external_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    comment="This value is used in [RECOMMENDATION-TITLE]"
    datatype="[datatype.value]"
    version="1" />

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact-title: "[ARTIFACT-TITLE]"
    artifact:
      type: "[ARTIFACT-TYPE-NAME]"
      parameters:
        - parameter: 
            name: "auditeventpolicsubcatgeory"
            dt: "string"
            value: "[auditeventpolicsubcatgeory.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "value"
            dt: "string"
            value: "[value.value]"
        - parameter: 
            name: "data_type"
            dt: "string"
            value: "[data_type.value]"

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact-title": "[ARTIFACT-TITLE]",
      "artifact": {
        "type": "[ARTIFACT-TYPE-NAME]",
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
  }
