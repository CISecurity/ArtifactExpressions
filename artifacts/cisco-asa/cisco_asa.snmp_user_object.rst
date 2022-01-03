Cisco ASA: SNMP User Object
==========================

Description
-----------

The Cisco ASA: SNMP User Object test is used to check the properties of
specific output lines from an SNMP user configuration.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**cisco_asa.snmp_user_object**

======== ====== ====================================
Name     Type   Description
======== ====== ====================================
name     string The SNMP user name. Cannot be blank.
operator string Comparison operator.
======== ====== ====================================

NOTE: The ``operator`` parameter is governed by a constraint allowing only the following values:
  - bitwise and
  - bitwise or
  - case insensitive equals
  - case insensitive not equal
  - equals
  - greater than
  - greater than or equal
  - less than
  - less than or equal
  - pattern match
  - not equal
  - set white list
  - set is empty  

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Cisco ASA: SNMP User Auth And Priv

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**cisco_asa.snmp_user_auth_priv**

============= ====== =======================================
Name          Type   Description
============= ====== =======================================
auth_operator string Comparison operator for the auth value.
auth          string Authentication.
priv_operator string Comparison operator for the priv value.
priv          string Priv.
============= ====== =======================================

NOTE: The ``auth_operator`` and ``priv_operator`` parameters are governed by a constraint allowing only the following values:
  - bitwise and
  - bitwise or
  - case insensitive equals
  - case insensitive not equal
  - equals
  - greater than
  - greater than or equal
  - less than
  - less than or equal
  - pattern match
  - not equal
  - set white list
  - set is empty

NOTE: The ``auth`` parameter is governed by a constraint allowing only the following values:
  - MD5
  - SHA

NOTE: The ``priv`` parameter is governed by a constraint allowing only the following values:
  - DES
  - 3DES
  - AES128
  - AES192
  - AES256

Generated Content
~~~~~~~~~~~~~~~~~

**cisco_asa.snmp_user_auth_priv**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[RECOMMENDATION-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACT-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="name">[name.value]</ae:parameter>
            <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
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

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"/>
    <check-content-ref
      href="[BENCHMARK-NAME]" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]"/>
  </check>

OVAL
''''

Test

::

  <snmp_user_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
    check_existence="[check_existence.value]" 
    check="[check.value]" 
    comment="[RECOMMENDATION-TITLE]" 
    version="[version.value]">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"/>
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"/>
  </snmp_user_test>

Object

::

  <snmp_user_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]" 
    version="[version.value]">
    <name 
      operation="[operation.value]">
      [name.value]
    </name>
  </snmp_user_object>

State

::

  <snmp_user_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]" 
    version="[version.value]">
    <priv 
      operation="[operation.value]" 
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"/>
    <auth 
      operation="[operation.value]" 
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"/>
  </snmp_user_state>

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact-title: "[RECOMMENDATION-TITLE]"
    artifact:
      type: "[ARTIFACT-TYPE-NAME]"
      parameters:
        - parameter:
            name: "name"
            dt: "string"
            value: "[name.value]"
        - parameter:
            name: "operator"
            dt: "string"
            value: "[operator.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "auth_operator"
            dt: "string"
            value: "[auth_operator.value]"
        - parameter:
            name: "auth"
            dt: "string"
            value: "[auth.value]"
        - parameter:
            name: "priv_operator"
            dt: "string"
            value: "[priv_operator.value]"
        - parameter:
            name: "priv"
            dt: "string"
            value: "[priv.value]"

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact-title": "[RECOMMENDATION-TITLE]",
      "artifact": {
        "type": "[ARTIFACT-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "name",
              "type": "string",
              "value": "[name.value]"
            }
          },
          {
            "parameter": {
              "name": "operator",
              "type": "string",
              "value": "[operator.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "auth_operator",
              "type": "string",
              "value": "[auth_operator.value]"
            }
          },
          {
            "parameter": {
              "name": "auth",
              "type": "string",
              "value": "[auth.value]"
            }
          },
          {
            "parameter": {
              "name": "priv_operator",
              "type": "string",
              "value": "[priv_operator.value]"
            }
          },
          {
            "parameter": {
              "name": "priv",
              "type": "string",
              "value": "[priv.value]"
            }
          }
        ]
      }
    }
  }