Cisco ASA: Version Object
=========================

Description
-----------

The Cisco ASA: Version Object test is used to check the version of the ASA operating system. It is based off of the SHOW VERSION command. 

The version_object element is used by a version test to define the different version information associated with a ASA system. There is actually only one object relating to version and this is the system as a whole. Therefore, there are no child entities defined. Any OVAL Test written to check version will reference the same version_object which is basically an empty object element.

The version_state element defines the version information held within a Cisco ASA software release. The asa_release element specifies the whole ASA version information. The asa_major_release, asa_minor_release and asa_build elements specify seperated parts of ASA software version information. For instance, if the ASA version is 8.4(2.3)49, then asa_release is 8.4(2.3)49, asa_major_release is 8.4, asa_minor_release is 2.3 and asa_build is 49. See the SHOW VERSION command within ASA for more information.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**cisco_asa.version_object**

==== ==== ===========
Name Type Description
==== ==== ===========
N/A
==== ==== ===========

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Cisco ASA: Major Version
  - Cisco ASA: Major/Minor Version

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**cisco_asa.major_version**

============= ====== ====================
Name          Type   Description
============= ====== ====================
operation     string Comparison operator.
major_version string Major version.
============= ====== ====================

NOTE: The ``operation`` parameter is governed by a constraint allowing only the following values:
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

**cisco_asa.major_minor_version**

+-------------------------+---------+----------------------------------------+
| Name                    | Type    | Description                            |
+=========================+=========+========================================+
| asa_major_release       | string  | The asa_major_releaseis the dotted     |
|                         |         | version that starts a version string.  |
+-------------------------+---------+----------------------------------------+
| major_release_operation | string  | Comparison operator.                   |
+-------------------------+---------+----------------------------------------+
| minor_release_operation | string  | Minor Release Comparison operator.     |
+-------------------------+---------+----------------------------------------+
| asa_minor_release       | string  | The asa_minor_release is the dotted    |
|                         |         | version that starts a version string.  |
+-------------------------+---------+----------------------------------------+

NOTE: The ``major_release_operation`` and ``minor_release_operation`` parameters are governed by a constraint allowing only the following values:
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

Generated Content
~~~~~~~~~~~~~~~~~

**cisco_asa.major_version**

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
            <ae:parameters />
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
              <ae:parameter dt="string" name="major_version">[major_version.value]</ae:parameter>
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

For ``cisco_asa.version_object`` ``cisco_asa.major_version`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    type="string"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``cisco_asa.version_object`` ``cisco_asa.major_version`` artifacts the XCCDF check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
    <check-content-ref 
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <version_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#asa"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </version_test>

Object

::

  <version_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#asa"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1" />

State

::

  <version_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#asa"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <asa_major_release 
      datatype="version" 
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </version_state>

Variable

::

  <external_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="string"
    comment="This value is used in Rule: [RECOMMENDATION-TITLE]"
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
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "operation"
            dt: "string"
            value: "[operation.value]"
        - parameter:
            name: "major_version"
            dt: "string"
            value: "[major_version.value]"

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

        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "operation",
              "type": "string",
              "value": "[operation.value]"
            }
          },
          {
            "parameter": {
              "name": "major_version",
              "type": "string",
              "value": "[major_version.value]"
            }
          }
        ]
      }
    }
  }

Generated Content
~~~~~~~~~~~~~~~~~

**cisco_asa.major_minor_version**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:complex-check operator="AND">
    <xccdf:complex-check operator="OR">
      <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
        <xccdf:check-content>
          <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
            <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
            <ae:title>[ARTIFACT-TITLE]</ae:title>
            <ae:artifact type="[ARTIFACT-TYPE-NAME]">
              <ae:parameters />
            </ae:artifact>
            <ae:test type="[TEST-TYPE-NAME]">
              <ae:parameters>
                <ae:parameter dt="string" name="asa_major_release">[asa_major_release.value]</ae:parameter>
                <ae:parameter dt="string" name="major_release_operation">[major_release_operation.value]</ae:parameter>
                <ae:parameter dt="string" name="asa_minor_release">[asa_minor_release.value]</ae:parameter>
                <ae:parameter dt="string" name="minor_release_operation">[minor_release_operation.value]</ae:parameter>
              </ae:parameters>
            </ae:test>
            <ae:profiles>
              <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1" />
            </ae:profiles>
          </ae:artifact_expression>
        </xccdf:check-content>
      </xccdf:check>
    </xccdf:complex-check>
  </xccdf:complex-check>

SCAP
^^^^

XCCDF
'''''

For ``cisco_asa.version_object`` ``cisco_asa.major_minor_version`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    type="string"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var2"
    type="string"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``cisco_asa.version_object`` ``cisco_asa.major_minor_version`` artifacts, the XCCDF check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
    <check-content-ref 
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <version_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#asa"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </version_test>

Object

::

  <version_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#asa"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1" />

State

::

  <version_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#asa"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <asa_major_release 
      datatype="version" 
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <asa_minor_release 
      datatype="version" 
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2" />
  </version_state>

Variable

::

  <external_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="string"
    comment="This value is used in Rule: [RECOMMENDATION-TITLE]"
    version="1" />

  <external_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2"
    datatype="string"
    comment="This value is used in Rule: [RECOMMENDATION-TITLE]"
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
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "asa_major_release"
            dt: "string"
            value: "[asa_major_release.value]"
        - parameter:
            name: "major_release_operation"
            dt: "string"
            value: "[major_release_operation.value]"
        - parameter:
            name: "asa_minor_release"
            dt: "string"
            value: "[asa_minor_release.value]"
        - parameter:
            name: "minor_release_operation"
            dt: "string"
            value: "[minor_release_operation.value]"            

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact-title": "[ARTIFACT-TITLE]",
      "artifact": {
        "type": "[ARTIFACT-TYPE-NAME]",
        "parameters": []
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "asa_major_release",
              "type": "string",
              "value": "[asa_major_release.value]"
            }
          },
          {
            "parameter": {
              "name": "major_release_operation",
              "type": "string",
              "value": "[major_release_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "asa_minor_release",
              "type": "string",
              "value": "[asa_minor_release.value]"
            }
          },
          {
            "parameter": {
              "name": "minor_release_operation",
              "type": "string",
              "value": "[minor_release_operation.value]"
            }
          }          
        ]
      }
    }
  }
