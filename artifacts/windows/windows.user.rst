Windows: User
=============

Description
-----------

The Windows: User test is used to check information about Windows users. When the user_test collects the users on the system, it should only include the local and built-in user accounts and not domain user accounts. However, it is important to note that domain user accounts can still be looked up. Also, note that the collection of groups, for which a user is a member, is not recursive. The only groups that will be collected are those for which the user is a direct member. For example, if a user is a member of group A, and group A is a member of group B, the only group that will be collected is group A.

The user_object element is used by a user_test to define the user to be evaluated.

The user_state element enumerates the different groups (identified by name) that a Windows user might belong to.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**windows.user**

========= ====== ======================
Name      Type   Description
========= ====== ======================
user      string username.
existence string existence of the user.
========= ====== ======================

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Null Test

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**null_test_v1**

========= ====== ======================
Name      Type   Description
========= ====== ======================
N/A
========= ====== ======================

Generated Content
~~~~~~~~~~~~~~~~~

**null_test_v1**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:complex-check operator="OR">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
        <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
          <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
          <ae:title>[ARTIFACT-TITLE]</ae:title>
          <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="user">[user.value]</ae:parameter>
              <ae:parameter dt="string" name="existence">[existence.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters />
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

For ``windows.user`` artifacts, the xccdf:check looks like this. There is no Value element in the xccdf for this Artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
    <check-content-ref 
      href="[BENCHMARK-TITLE]"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>  

OVAL
''''

Test

::

  <user_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </user_test>

Object

::

  <user_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
      id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <user 
      datatype="[datatype.value]"
      operation="equals">
        [user.value]
    </user>
  </user_object>

State

::

  N/A

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
            name: "user"
            dt: "string"
            value: "[user.value]"
        - parameter: 
            name: "existence"
            dt: "string"
            value: "[existence.value]"            
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:

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
              "name": "user",
              "type": "string",
              "value": "[user.value]"
            }
          },
          {
            "parameter": {
              "name": "existence",
              "type": "string",
              "value": "[existence.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": []
      }
    }
  }