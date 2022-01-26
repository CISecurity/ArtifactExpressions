Windows: Privilege Assignment
=============================

Description
-----------

The The Windows: Privilege Assignment test is used to check the properties of a Windows access token as well as individual privileges and rights associated with it.

The accesstoken_object element is used by an accesstoken_test to define those objects to evaluate based on a specified state. An accesstoken_object consists of a single security principle that identifies user, group, or computer account that is associated with the token.

The accesstoken_state element defines the different information that can be used to evaluate the specified access tokens. This includes the multitude of user rights and permissions that can be granted.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**windows.privilegeassignment**

+------------------------------+---------+-----------------------------------+
| Name                         | Type    | Description                       |
+==============================+=========+===================================+
| privilegeassignmentsettings  | string  | The privilege assignment setting  |
|                              |         | to be audited.                    |
+------------------------------+---------+-----------------------------------+

NOTE: The ``privilegeassignmentsettings`` parameter is governed by a constraint allowing only the following values:
  - security_principle
  - seassignprimarytokenprivilege 
  - seauditprivilege
  - sebackupprivilege
  - sechangenotifyprivilege
  - secreateglobalprivilege
  - secreatepagefileprivilege
  - secreatepermanentprivilege
  - secreatesymboliclinkprivilege 
  - secreatetokenprivilege
  - sedebugprivilege
  - seenabledelegationprivilege
  - seimpersonateprivilege
  - seincreasebasepriorityprivilege
  - seincreasequotaprivilege
  - seincreaseworkingsetprivilege
  - seloaddriverprivilege 
  - selockmemoryprivilege
  - semachineaccountprivileg 
  - semanagevolumeprivilege
  - seprofilesingleprocessprivilege
  - serelabelprivilege
  - seremoteshutdownprivilege
  - serestoreprivilege
  - sesecurityprivilege
  - seshutdownprivilege
  - sesyncagentprivilege
  - sesystemenvironmentprivilege
  - sesystemprofileprivilege
  - sesystemtimeprivilege
  - setakeownershipprivilege
  - setcbprivilege
  - setimezoneprivilege
  - seundockprivilege
  - seunsolicitedinputprivilege
  - sebatchlogonright
  - seinteractivelogonright
  - senetworklogonright
  - seremoteinteractivelogonright
  - seservicelogonright
  - sedenybatchLogonright
  - sedenyinteractivelogonright
  - sedenynetworklogonright
  - sedenyremoteInteractivelogonright
  - sedenyservicelogonright
  - setrustedcredmanaccessnameright

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Set Is Empty
  - Set Includes
  - Set White List
  - Equal
  - Equals

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**setisempty**

==== ==== ===========
Name Type Description
==== ==== ===========
N/A
==== ==== ===========

| **equal**
| **equals**
| **set.includes_v1**
| **set.white_list_v1**
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

**setisempty**

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
              <ae:parameter dt="string" name="privilegeassignmentsettings">[privilegeassignmentsettings.value]</ae:parameter>
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

For ``windows.privilegeassignment`` ``setisempty`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-content-ref 
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <accesstoken_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:100000" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </accesstoken_test>

Object

::

  N/A

State

::

  <accesstoken_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
      <[privilege.value] 
        datatype="boolean"
        operation="equals">
          false
      </parameter_constraint>
  </accesstoken_state>

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
            name: "privilegeassignmentsettings"
            dt: "string"
            value: "[privilegeassignmentsettings.value]"
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
              "name": "privilegeassignmentsettings",
              "type": "string",
              "value": "[privilegeassignmentsettings.value]"
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

Generated Content
~~~~~~~~~~~~~~~~~

**set.white_list_v1**

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
              <ae:parameter dt="string" name="privilegeassignmentsettings">[privilegeassignmentsettings.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="data_type">[data_type.value]</ae:parameter>
              <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
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


For ``windows.privilegeassignment`` ``set.white_list_v1`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-content-ref 
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <accesstoken_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </accesstoken_test>

Object

::

  <accesstoken_object>
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1"
    comment="[ARTIFACT-TITLE]"
    version="1"> 
      <security_principle operation="case insensitive equals">
        [security_principle.value]
      </security_principle>
  </accesstoken_object>

  <accesstoken_object>
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1"> 
      [accesstoken_object.value]
  </accesstoken_object>  

State

::

  <accesstoken_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
      <[privilege.value] 
        datatype="boolean"
        operation="equals">
          false
      </parameter_constraint>
  </accesstoken_state>

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
            name: "privilegeassignmentsettings"
            dt: "string"
            value: "[privilegeassignmentsettings.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter: 
            name: "data_type"
            dt: "string"
            value: "[data_type.value]"
        - parameter: 
            name: "value"
            dt: "string"
            value: "[value.value]"

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
              "name": "privilegeassignmentsettings",
              "type": "string",
              "value": "[privilegeassignmentsettings.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "data_type",
              "type": "string",
              "value": "[data_type.value]"
            },
            "parameter": {
              "name": "value",
              "type": "string",
              "value": "[value.value]"
            }
          }
        ]
      }
    }
  }  

Generated Content
~~~~~~~~~~~~~~~~~

**set.includes_v1**

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
              <ae:parameter dt="string" name="privilegeassignmentsettings">[privilegeassignmentsettings.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="data_type">[data_type.value]</ae:parameter>
              <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
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


For ``windows.privilegeassignment`` ``set.includes_v1`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-content-ref 
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <accesstoken_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="any_exist"
    check="all"
    comment="[comment.value]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </accesstoken_test>

Object

::

  <accesstoken_object>
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1"
    comment="[comment.value]"
    version="1"> 
      <security_principle operation="case insensitive equals">
        [security_principle.value]
      </security_principle>
  </accesstoken_object>

State

::

  <accesstoken_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
      <[privilege.value] 
        datatype="boolean"
        operation="equals">
          true
      </parameter_constraint>
  </accesstoken_state>

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
            name: "privilegeassignmentsettings"
            dt: "string"
            value: "[privilegeassignmentsettings.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter: 
            name: "data_type"
            dt: "string"
            value: "[data_type.value]"
        - parameter: 
            name: "value"
            dt: "string"
            value: "[value.value]"

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
              "name": "privilegeassignmentsettings",
              "type": "string",
              "value": "[privilegeassignmentsettings.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "data_type",
              "type": "string",
              "value": "[data_type.value]"
            },
            "parameter": {
              "name": "value",
              "type": "string",
              "value": "[value.value]"
            }
          }
        ]
      }
    }
  }

Generated Content
~~~~~~~~~~~~~~~~~

| **equal**
| **equals**
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
              <ae:parameter dt="string" name="privilegeassignmentsettings">[privilegeassignmentsettings.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="data_type">[data_type.value]</ae:parameter>
              <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
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


For ``windows.privilegeassignment`` ``equal`` and ``equals`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-content-ref 
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <accesstoken_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]1"
    check_existence="at_least_one_exists"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]1" />
  </accesstoken_test>

  <accesstoken_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]2"
    check_existence="at_least_one_exists"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]2" />
  </accesstoken_test>

Object

::

  <accesstoken_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <security_principle 
      operation="case insensitive equals">
        [security_principle.value]
    </security_principle>
  </accesstoken_object>

  <accesstoken_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <set 
      set_operator="COMPLEMENT"
      xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5">
      <object_reference>
        oval:org.cisecurity.benchmarks.[PLATFORM]:obj:100000
      </object_reference>
      <object_reference>
        oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1
      </object_reference>
    </set>
  </accesstoken_object>

State

::

  <accesstoken_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]1"
    comment="[ARTIFACT-TITLE]"
    version="1">
      <[privilege.value] 
        datatype="boolean"
        operation="equals">
          true
      </parameter_constraint>
  </accesstoken_state>

  <accesstoken_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]2"
    comment="[ARTIFACT-TITLE]"
    version="1">
      <[privilege.value] 
        datatype="boolean"
        operation="equals">
          false
      </parameter_constraint>
  </accesstoken_state>  

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
            name: "privilegeassignmentsettings"
            dt: "string"
            value: "[privilegeassignmentsettings.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter: 
            name: "data_type"
            dt: "string"
            value: "[data_type.value]"
        - parameter: 
            name: "value"
            dt: "string"
            value: "[value.value]"

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
              "name": "privilegeassignmentsettings",
              "type": "string",
              "value": "[privilegeassignmentsettings.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "data_type",
              "type": "string",
              "value": "[data_type.value]"
            },
            "parameter": {
              "name": "value",
              "type": "string",
              "value": "[value.value]"
            }
          }
        ]
      }
    }
  }