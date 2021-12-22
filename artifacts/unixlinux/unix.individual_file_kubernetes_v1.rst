Unix: Individual File Kubernetes V1
===================================

Description
-----------

The Unix: Individual File Kubernetes V1 test is used to check metadata associated with UNIX files, of the sort returned by either an ls command, stat command or stat() system call.

The file_object element is used by a file_test to define either the path and filename or complete filepath of the specific file(s) to be evaluated. The set of files to be evaluated may be identified with either a complete filepath or a path and filename. Only one of these options may be selected.

The textfilecontent54_object is used by a textfilecontent54_test to define either the path and filename or complete filepath of the specific file(s) to be evaluated, along with the pattern to be matched / not matched and the instance of the matched / not matched pattern. 

The set of files to be evaluated may be identified with either a complete filepath or a path and filename. Only one of these options may be selected.

It is important to note that the 'max_depth' and 'recurse_direction' attributes of the 'behaviors' element do not apply to the 'filepath' element, only to the 'path' and 'filename' elements. This is because the 'filepath' element represents an absolute path to a particular file and it is not possible to recurse over a file.

The file_state element defines the different metadata associated with file IDs and permissions.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**unix.individual_file_kubernetes_v1**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| path                        | string  | Directory component of the         |
|                             |         | absolute path to the file after    |
|                             |         | default value.                     |
+-----------------------------+---------+------------------------------------+
| filename                    | string  | Filename component of the absolute |
|                             |         | path to the file.                  |
+-----------------------------+---------+------------------------------------+
| check                       | string  | Defines how many collected items   |
|                             |         | must match the expected state.     |
+-----------------------------+---------+------------------------------------+
| check_existence             | string  | Defines how many items should be   |
|                             |         | collected. Typically set to 'at    |
|                             |         | least one'.                        |
+-----------------------------+---------+------------------------------------+

NOTE: The ``check`` parameter is governed by a constraint allowing only the following values:
  - all
  - at least one
  - none satisfy
  - only one

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_satisfy
  - none_exist
  - only_one_exists

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Unix: File Attributes  
  - Pattern Match
  - Pattern Not Match
  - Null Test

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**null_test_v1**

===== ====== =======================
Name  Type   Description
===== ====== =======================
N/A
===== ====== =======================

| **pattern match**
| **pattern not match**
========= ====== ===========================
Name      Type   Description
========= ====== ===========================
value     string The value to be tested.
data_type string The data type of the value.
========= ====== ===========================

NOTE: The ``data_type`` parameter is governed by a constraint allowing only the following values:
  - boolean
  - float
  - int
  - string
  - version
  - set

**unix.file_attributes_v1**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| uid                         | int     | The User ID of the files owner     |
|                             |         | (Positive integer or blank).       |
+-----------------------------+---------+------------------------------------+
| gid                         | int     | The Group ID of the files owner    |
|                             |         | (Positive integer or blank).       |
+-----------------------------+---------+------------------------------------+
| uread                       | string  | Determines whether the user that   |
|                             |         | owns the file or directory is      |
|                             |         | permitted to read the contents of  |
|                             |         | it.                                |
+-----------------------------+---------+------------------------------------+
| uwrite                      | string  | Determines whether the user that   |
|                             |         | owns the file or directory is      |
|                             |         | permitted to write to it.          |
+-----------------------------+---------+------------------------------------+
| uexec                       | string  | Determines whether the user that   |
|                             |         | owns the file or directory is      |
|                             |         | permitted to execute the file or   |
|                             |         | change into the directory.         |
+-----------------------------+---------+------------------------------------+
| gread                       | string  | Determines whether the group that  |
|                             |         | owns the file or directory is      |
|                             |         | permitted to read the content of   |
|                             |         | it.                                |
+-----------------------------+---------+------------------------------------+
| gwrite                      | string  | Determines whether the group that  |
|                             |         | owns the file or directory is      |
|                             |         | permitted to write to it.          |
+-----------------------------+---------+------------------------------------+
| gexec                       | string  | Determines whether the group that  |
|                             |         | owns the  file or directory is     |
|                             |         | permitted to execute the           |
|                             |         | file or change into the directory. |
+-----------------------------+---------+------------------------------------+
| oread                       | string  | Determines whether other users or  |
|                             |         | groups that do not own the file or |
|                             |         | directory are permitted to read    |
|                             |         | the contents of it.                |
+-----------------------------+---------+------------------------------------+
| owrite                      | string  | Determines whether other users or  |
|                             |         | groups that do not own the file or |
|                             |         | directory are permitted to write   |
|                             |         | to it.                             |
+-----------------------------+---------+------------------------------------+
| oexec                       | string  | Determines whether other users or  |
|                             |         | groups that do not own the file or |
|                             |         | directory are permitted to execute |
|                             |         | the file or change into the        |
|                             |         | directory.                         |
+-----------------------------+---------+------------------------------------+
| suid                        | string  | Determines if the file can execute |
|                             |         | as the owner.                      |
+-----------------------------+---------+------------------------------------+
| sgid                        | string  | Determines if the file can execute |
|                             |         | as the group.                      |
+-----------------------------+---------+------------------------------------+
| sticky                      | string  | Determines if the sticky bit is    |
|                             |         | set.                               |
+-----------------------------+---------+------------------------------------+

NOTE: All ``unix.file_attributes_v1`` parameters are governed by a constraint allowing only the following values:
  - NA
  - set
  - unset

Generated Content
~~~~~~~~~~~~~~~~~

**null_test_v1**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[RECOMMENDATION-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACT-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
            <ae:parameter dt="string" name="filename">[filename.value]</ae:parameter>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters />
        </ae:test>
        <ae:profiles>
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1"/>
        </ae:profiles>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``unix.individual_file_kubernetes_v1`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" 
    type="string">
    <title>"Kubernetes Directory"</title>
    <description>"This value allows for user-supplied Kubernetes Directory"</description>
    <value>[value.value]</value>
  </Value>

For ``unix.individual_file_kubernetes_v1`` artifacts, the xccdf:check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
    <check-content-ref 
      href="[BENCHMARK-TITLE]"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <file_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]" 
    check="[check.value]" 
    comment="[ARTIFACT-TITLE]"
    version="1">
      <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </file_test>

Object

::

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2"
    comment="\$CATALINA_HOME file object"
    version="1">
      <path var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]1" />
      <filename xsi:nil="true" />
  </file_object>

State

::

  N/A

Variable

::

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1"
    datatype="string"
    comment="Kubernetes directory"
    version="1">
      <concat>
        <end character="/">
          <variable_component var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]1" />
        </end>
        <literal_component>
            [literal_component.value]
        </literal_component>
      </concat>
  </local_variable>

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
            name: "path"
            dt: "string"
            value: "[path.value]"
        - parameter:
            name: "filename"
            dt: "string"
            value: "[filename.value]"
        - parameter:
            name: "check"
            dt: "string"
            value: "[check.value]"
        - parameter:
            name: "check_existence"
            dt: "string"
            value: "[check_existence.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters: []


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
              "name": "path",
              "dt": "string",
              "value": "[path.value]"
            }
          },
          {
            "parameter": {
              "name": "filename",
              "dt": "string",
              "value": "[filename.value]"
            }
          },
          {
            "parameter": {
              "name": "check",
              "dt": "string",
              "value": "[check.value]"
            }
          },
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
        "type": "[TEST-TYPE-NAME]",
        "parameters": [

        ]
      }
    }
  }

Generated Content
~~~~~~~~~~~~~~~~~

| **pattern match**
| **pattern not match**
XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[RECOMMENDATION-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACT-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
            <ae:parameter dt="string" name="filename">[filename.value]</ae:parameter>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="data_type">[data_type.value]</ae:parameter>
            <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
          </ae:parameters>
        </ae:test>
        <ae:profiles>
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1"/>
        </ae:profiles>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``unix.individual_file_kubernetes_v1`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" 
    operator="[operator.value]" 
    type="[type.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``unix.individual_file_kubernetes_v1`` artifacts, the xccdf:check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
    <check-content-ref 
      href="[BENCHMARK-TITLE]"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <textfilecontent54_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]" 
    check="[check.value]" 
    comment="[ARTIFACT-TITLE]"
    version="1">
      <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </textfilecontent54_test>

Object

::

  <textfilecontent54_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2"
    comment="\$CATALINA_HOME file object"
    version="1">
      <path var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]1" />
      <filename xsi:nil="true" />
      <pattern 
        operation="pattern match" />
        datatype="[datatype.value]>
          [pattern.value]
      </pattern>
      <instance 
        datatype="int"
        operation="equals">
          1
      </instance>
  </textfilecontent54_object>

State

::

  N/A

Variable

::

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1"
    datatype="string"
    comment="Kubernetes directory"
    version="1">
      <concat>
        <end character="/">
          <variable_component var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]1" />
        </end>
        <literal_component>
            [literal_component.value]
        </literal_component>
      </concat>
  </local_variable>

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
            name: "path"
            dt: "string"
            value: "[path.value]"
        - parameter:
            name: "filename"
            dt: "string"
            value: "[filename.value]"
        - parameter:
            name: "check"
            dt: "string"
            value: "[check.value]"
        - parameter:
            name: "check_existence"
            dt: "string"
            value: "[check_existence.value]"
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
      "artifact-title": "[RECOMMENDATION-TITLE]",
      "artifact": {
        "type": "[ARTIFACT-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "path",
              "dt": "string",
              "value": "[path.value]"
            }
          },
          {
            "parameter": {
              "name": "filename",
              "dt": "string",
              "value": "[filename.value]"
            }
          },
          {
            "parameter": {
              "name": "check",
              "dt": "string",
              "value": "[check.value]"
            }
          },
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
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "data_type",
              "dt": "string",
              "value": "[data_type.value]"
            }
          },
          {
            "parameter": {
              "name": "value",
              "dt": "string",
              "value": "[value.value]"
            }
          }
        ]
      }
    }
  }

Generated Content
~~~~~~~~~~~~~~~~~

**unix.file_attributes_v1**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[RECOMMENDATION-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACT-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
            <ae:parameter dt="string" name="filename">[filename.value]</ae:parameter>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="int" name="uid">[uid.value]</ae:parameter>
            <ae:parameter dt="int" name="gid">[gid.value]</ae:parameter>
            <ae:parameter dt="string" name="uread">[uread.value]</ae:parameter>
            <ae:parameter dt="string" name="uwrite">[uwrite.value]</ae:parameter>
            <ae:parameter dt="string" name="uexec">[uexec.value]</ae:parameter>
            <ae:parameter dt="string" name="gread">[gread.value]</ae:parameter>
            <ae:parameter dt="string" name="gwrite">[gwrite.value]</ae:parameter>
            <ae:parameter dt="string" name="gexec">[gexec.value]</ae:parameter>
            <ae:parameter dt="string" name="oread">[oread.value]</ae:parameter>
            <ae:parameter dt="string" name="owrite">[owrite.value]</ae:parameter>
            <ae:parameter dt="string" name="oexec">[oexec.value]</ae:parameter>
            <ae:parameter dt="string" name="suid">[suid.value]</ae:parameter>
            <ae:parameter dt="string" name="sgid">[sgid.value]</ae:parameter>
            <ae:parameter dt="string" name="sticky">[sticky.value]</ae:parameter>   
          </ae:parameters>          
        </ae:test>
        <ae:profiles>
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1"/>
        </ae:profiles>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``unix.individual_file_kubernetes_v1`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" 
    operator="[operator.value]" 
    type="[type.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``unix.individual_file_kubernetes_v1`` artifacts, the xccdf:check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
    <check-content-ref 
      href="[BENCHMARK-TITLE]"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <file_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]" 
    check="[check.value]" 
    comment="[ARTIFACT-TITLE]"
    version="1">
      <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
      <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </file_test>

Object

::

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2"
    comment="[ARTIFACT-TITLE]"
    version="1">
      <path var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]1" />
      <filename xsi:nil="true" />
  </file_object>

State

::

  <file_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2"
    comment="[ARTIFACT-TITLE]"
    version="1"> 
      <uid datatype="int">[uid.value]</uid>
      <gid datatype="int">[gid.value]</gid>
      <uread datatype="boolean">[uread.value]</uread>
      <uwrite datatype="boolean">[uwrite.value]</uwrite>
      <uexec datatype="boolean">[uexec.value]</uexec>
      <gread datatype="boolean">[gread.value]</gread>
      <gwrite datatype="boolean">[gwrite.value]</gwrite>
      <gexec datatype="boolean">[gexec.value]</gexec>
      <oread datatype="boolean">[oread.value]</oread>
      <owrite datatype="boolean">[owrite.value]</owrite>
      <oexec datatype="boolean">[oexec.value]</oexec>
      <suid datatype="boolean">[suid.value]</suid>
      <sgid datatype="boolean">[sgid.value]</sgid>
      <sticky datatype="boolean">[sticky.value]</sticky>
  </file_state>

Variable

::

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1"
    datatype="string"
    comment="Kubernetes directory"
    version="1">
      <concat>
        <end character="/">
          <variable_component var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]1" />
        </end>
        <literal_component>
            [literal_component.value]
        </literal_component>
      </concat>
  </local_variable>

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
            name: "path"
            dt: "string"
            value: "[path.value]"
        - parameter:
            name: "filename"
            dt: "string"
            value: "[filename.value]"
        - parameter:
            name: "check"
            dt: "string"
            value: "[check.value]"
        - parameter:
            name: "check_existence"
            dt: "string"
            value: "[check_existence.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters: 
        - parameter:
            name: "uid"
            dt: "int"
            value: "[uid.value]"
        - parameter:
            name: "gid"
            dt: "int"
            value: "[gid.value]"
        - parameter:
            name: "uread"
            dt: "boolean"
            value: "[uread.value]"
        - parameter:
            name: "uwrite"
            dt: "boolean"
            value: "[uwrite.value]"
        - parameter:
            name: "uexec"
            dt: "boolean"
            value: "[uexec.value]"
        - parameter:
            name: "gread"
            dt: "boolean"
            value: "[gread.value]"
        - parameter:
            name: "gwrite"
            dt: "boolean"
            value: "[gwrite.value]"
        - parameter:
            name: "gexec"
            dt: "boolean"
            value: "[gexec.value]"
        - parameter:
            name: "oread"
            dt: "boolean"
            value: "[oread.value]"
        - parameter:
            name: "owrite"
            dt: "boolean"
            value: "[owrite.value]"
        - parameter:
            name: "oexec"
            dt: "boolean"
            value: "[oexec.value]"
        - parameter:
            name: "suid"
            dt: "boolean"
            value: "[suid.value]"
        - parameter:
            name: "sgid"
            dt: "boolean"
            value: "[sgid.value]"
        - parameter:
            name: "sticky"
            dt: "boolean"
            value: "[sticky.value]"

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
              "name": "path",
              "dt": "string",
              "value": "[path.value]"
            }
          },
          {
            "parameter": {
              "name": "filename",
              "dt": "string",
              "value": "[filename.value]"
            }
          },
          {
            "parameter": {
              "name": "check",
              "dt": "string",
              "value": "[check.value]"
            }
          },
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
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "uid",
              "dt": "int",
              "value": "[uid.value]"
            }
          },
          {
            "parameter": {
              "name": "gid",
              "dt": "int",
              "value": "[gid.value]"
            }
          },
          {
            "parameter": {
              "name": "uread",
              "dt": "boolean",
              "value": "[uread.value]"
            }
          },
          {
            "parameter": {
              "name": "uwrite",
              "dt": "boolean",
              "value": "[uwrite.value]"
            }
          },
          {
            "parameter": {
              "name": "uexec",
              "dt": "boolean",
              "value": "[uexec.value]"
            }
          },
          {
            "parameter": {
              "name": "gread",
              "dt": "boolean",
              "value": "[gread.value]"
            }
          },
          {
            "parameter": {
              "name": "gwrite",
              "dt": "boolean",
              "value": "[gwrite.value]"
            }
          },
          {
            "parameter": {
              "name": "gexec",
              "dt": "boolean",
              "value": "[gexec.value]"
            }
          },
          {
            "parameter": {
              "name": "oread",
              "dt": "boolean",
              "value": "[oread.value]"
            }
          },
          {
            "parameter": {
              "name": "owrite",
              "dt": "boolean",
              "value": "[owrite.value]"
            }
          },
          {
            "parameter": {
              "name": "oexec",
              "dt": "boolean",
              "value": "[oexec.value]"
            }
          },
          {
            "parameter": {
              "name": "suid",
              "dt": "boolean",
              "value": "[suid.value]"
            }
          },
          {
            "parameter": {
              "name": "sgid",
              "dt": "boolean",
              "value": "[sgid.value]"
            }
          },
          {
            "parameter": {
              "name": "sticky",
              "dt": "boolean",
              "value": "[sticky.value]"
            }
          }
        ]
      }
    }
  }