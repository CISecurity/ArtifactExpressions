Unix: File Collection (v2)
==========================

Description
-----------

The Unix: File Collection (v2) test is used to check the contents of a
text file (aka a configuration file) by looking at individual blocks of
text.

The textfilecontent54_object element is used by a textfilecontent54_test to define the
specific block(s) of text of a file(s) to be evaluated. The
textfilecontent54_object will only collect regular files on UNIX
systems.

The set of files to be evaluated may be identified with either a
complete filepath or a path and filename. Only one of these options may
be selected.

The textfilecontent54_state element contains entities that are
used to check the file path and name, as well as the text block in
question and the value of the subexpressions.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**unix.file_collection_v2**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| existence                   | string  | Existence requirement.             |
+-----------------------------+---------+------------------------------------+
| check                       | string  | Defines how many collected items   |
|                             |         | must match the expected state.     |
+-----------------------------+---------+------------------------------------+
| path                        | string  | Path to the file. Cannot be blank. |
+-----------------------------+---------+------------------------------------+
| file_name                   | string  | The name of the file. Cannot be    |
|                             |         | blank.                             |
+-----------------------------+---------+------------------------------------+
| recurse                     | string  | Should subdirectories be recursed  |
|                             |         | through? (Yes/No)                  |
+-----------------------------+---------+------------------------------------+
| file_system                 | string  | File system limitation for         |
|                             |         | recursion.                         |
+-----------------------------+---------+------------------------------------+

NOTE: The ``existence`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_satisfy
  - none_exist
  - only_one_exists

NOTE: The ``check`` parameter is governed by a constraint allowing only the following values:
  - all
  - at least one
  - none satisfy
  - only one

NOTE: The ``file_system`` parameter is governed by a constraint allowing only the following values:
  - NA
  - local
  - all
  - defined

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Pattern Match
  - Pattern Not Match
  - Null Test
  - Unix: File Attributes

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

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

**null_test_v1**

==== ==== ===========
Name Type Description
==== ==== ===========
N/A       
==== ==== ===========

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

| **pattern match**
| **pattern not match**
XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:complex-check operator="AND">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
        <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
          <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
          <ae:title>[RECOMMENDATION-TITLE]</ae:title>
          <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="existence">[existence.value]</ae:parameter>
              <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
              <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
              <ae:parameter dt="string" name="file_name">[file_name.value]</ae:parameter>
              <ae:parameter dt="string" name="recurse">[recurse.value]</ae:parameter>
              <ae:parameter dt="string" name="file_system">[file_system.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
              <ae:parameter dt="string" name="data_type">[data_type.value]</ae:parameter>
            </ae:parameters>
          </ae:test>
          <ae:profiles>
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1 "/>
          </ae:profiles>          
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  </xccdf:complex-check>

SCAP
^^^^

XCCDF
'''''

For ``unix.file_collection_v2`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

::

  <xccdf:complex-check operator="AND">
    <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
      <check-content-ref 
        href="[BENCHMARK-TITLE]"
        name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
    </check>
  </xccdf:complex-check>  

OVAL
''''

Test

::

  <textfilecontent54_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </textfilecontent54_test>

Object

::

  <textfilecontent54_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <behaviors 
      recurse_direction="down"
      recurse_file_system="[recurse_file_system.value]"
      max_depth="[max_depth.value]" />
    <path>[path.value]</path>
    <filename operation="pattern match">
        [filename.value]
    </filename>
    <pattern 
      operation="pattern match"
      datatype="[datatype.value]">
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
            name: "existence"
            dt: "string"
            value: "[existence.value]"
        - parameter:
            name: "path"
            dt: "string"
            value: "[path.value]"
        - parameter:
            name: "file_name"
            dt: "string"
            value: "[file_name.value]"
        - parameter:
            name: "recurse"
            dt: "string"
            value: "[recurse.value]"
        - parameter:
            name: "check"
            dt: "string"
            value: "[filesystem.value]"
        - parameter:
            name: "file_system"
            dt: "string"
            value: "[file_system.value]"
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
      "artifact-title": "[RECOMMENDATION-TITLE]",
      "artifact": {
        "type": "[ARTIFACT-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "existence",
              "type": "string",
              "value": "[existence.value]"
            }
          },
          {
            "parameter": {
              "name": "path",
              "type": "string",
              "value": "[path.value]"
            }
          },
          {
            "parameter": {
              "name": "file_name",
              "type": "string",
              "value": "[file_name.value]"
            }
          },
          {
            "parameter": {
              "name": "recurse",
              "type": "string",
              "value": "[recurse.value]"
            }
          },
          {
            "parameter": {
              "name": "check",
              "type": "string",
              "value": "[filesystem.value]"
            }
          },
          {
            "parameter": {
              "name": "file_system",
              "type": "string",
              "value": "[file_system.value]"
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

Generated Content
~~~~~~~~~~~~~~~~~

**null_test_v1**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:complex-check operator="AND">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
        <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
          <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
          <ae:title>[RECOMMENDATION-TITLE]</ae:title>
          <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="existence">[existence.value]</ae:parameter>
              <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
              <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
              <ae:parameter dt="string" name="file_name">[file_name.value]</ae:parameter>
              <ae:parameter dt="string" name="recurse">[recurse.value]</ae:parameter>
              <ae:parameter dt="string" name="file_system">[file_system.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters />
          </ae:test>
          <ae:profiles>
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1 "/>
          </ae:profiles>          
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  </xccdf:complex-check>

SCAP
^^^^

XCCDF
'''''

For ``unix.file_collection_v2`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

::

  <xccdf:complex-check operator="AND">
    <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
      <check-content-ref 
        href="[BENCHMARK-TITLE]"
        name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
    </check>
  </xccdf:complex-check>  

OVAL
''''

Test

::

  <file_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </file_test>

Object

::

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <behaviors 
      recurse_direction="down"
      recurse_file_system="[recurse_file_system.value]"
      max_depth="-1" />
    <path>[path.value]</path>
    <filename operation="pattern match">
        [filename.value]
    </filename>
  </file_object>

State

::

  N/A

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
            name: "existence"
            dt: "string"
            value: "[existence.value]"
        - parameter:
            name: "path"
            dt: "string"
            value: "[path.value]"
        - parameter:
            name: "file_name"
            dt: "string"
            value: "[file_name.value]"
        - parameter:
            name: "recurse"
            dt: "string"
            value: "[recurse.value]"
        - parameter:
            name: "check"
            dt: "string"
            value: "[filesystem.value]"
        - parameter:
            name: "file_system"
            dt: "string"
            value: "[file_system.value]"
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
              "name": "existence",
              "type": "string",
              "value": "[existence.value]"
            }
          },
          {
            "parameter": {
              "name": "path",
              "type": "string",
              "value": "[path.value]"
            }
          },
          {
            "parameter": {
              "name": "file_name",
              "type": "string",
              "value": "[file_name.value]"
            }
          },
          {
            "parameter": {
              "name": "recurse",
              "type": "string",
              "value": "[recurse.value]"
            }
          },
          {
            "parameter": {
              "name": "check",
              "type": "string",
              "value": "[filesystem.value]"
            }
          },
          {
            "parameter": {
              "name": "file_system",
              "type": "string",
              "value": "[file_system.value]"
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

**unix.file_attributes_v1**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:complex-check operator="AND">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
        <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
          <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
          <ae:title>[RECOMMENDATION-TITLE]</ae:title>
          <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="existence">[existence.value]</ae:parameter>
              <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
              <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
              <ae:parameter dt="string" name="file_name">[file_name.value]</ae:parameter>
              <ae:parameter dt="string" name="recurse">[recurse.value]</ae:parameter>
              <ae:parameter dt="string" name="file_system">[file_system.value]</ae:parameter>
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
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  </xccdf:complex-check>

SCAP
^^^^

XCCDF
'''''

For ``unix.file_collection_v2`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

::

  <xccdf:complex-check operator="AND">
    <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
      <check-content-ref 
        href="[BENCHMARK-TITLE]"
        name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
    </check>
  </xccdf:complex-check>  

OVAL
''''

Test

::

  <file_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </file_test>

Object

::

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <behaviors 
      recurse_direction="down"
      recurse_file_system="[recurse_file_system.value]"
      max_depth="-1" />
    <path>[path.value]</path>
    <filename operation="pattern match">
        [filename.value]
    </filename>
  </file_object>

State

::

   <file_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <group_id datatype="int">
        [group_id.value]
    </group_id>
    <user_id datatype="int">
        [user_id.value]
    </user_id>
    <suid datatype="boolean">
        [suid.value]
    </suid>
    <sgid datatype="boolean">
        [sgid.value]
    </sgid>
    <sticky datatype="boolean">
        [sticky.value]
    </sticky>
    <uread datatype="boolean">
        [uread.value]
    </uread>
    <uwrite datatype="boolean">
        [uwrite.value]
    </uwrite>
    <uexec datatype="boolean">
        [uexec.value]
    </uexec>
    <gread datatype="boolean">
        [gread.value]
    </gread>
    <gwrite datatype="boolean">
        [gwrite.value]
    </gwrite>
    <gexec datatype="boolean">
        [gexec.value]
    </gexec>
    <oread datatype="boolean">
        [oread.value]
    </oread>
    <owrite datatype="boolean">
        [owrite.value]
    </owrite>
    <oexec datatype="boolean">
        [oexec.value]
    </oexec>
  </file_state>

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
            name: "existence"
            dt: "string"
            value: "[existence.value]"
        - parameter:
            name: "path"
            dt: "string"
            value: "[path.value]"
        - parameter:
            name: "file_name"
            dt: "string"
            value: "[file_name.value]"
        - parameter:
            name: "recurse"
            dt: "string"
            value: "[recurse.value]"
        - parameter:
            name: "check"
            dt: "string"
            value: "[filesystem.value]"
        - parameter:
            name: "file_system"
            dt: "string"
            value: "[file_system.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "group_id"
            dt: "int"
            value: "[group_id.value]"
        - parameter:
            name: "user_id"
            dt: "int"
            value: "[user_id.value]"
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
              "name": "existence",
              "type": "string",
              "value": "[existence.value]"
            }
          },
          {
            "parameter": {
              "name": "path",
              "type": "string",
              "value": "[path.value]"
            }
          },
          {
            "parameter": {
              "name": "file_name",
              "type": "string",
              "value": "[file_name.value]"
            }
          },
          {
            "parameter": {
              "name": "recurse",
              "type": "string",
              "value": "[recurse.value]"
            }
          },
          {
            "parameter": {
              "name": "check",
              "type": "string",
              "value": "[filesystem.value]"
            }
          },
          {
            "parameter": {
              "name": "file_system",
              "type": "string",
              "value": "[file_system.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "group_id",
              "type": "int",
              "value": "[group_id.value]"
            }
          },
          {
            "parameter": {
              "name": "user_id",
              "type": "int",
              "value": "[user_id.value]"
            }
          },
          {
            "parameter": {
              "name": "suid",
              "type": "boolean",
              "value": "[suid.value]"
            }
          },
          {
            "parameter": {
              "name": "sgid",
              "type": "boolean",
              "value": "[sgid.value]"
            }
          },
          {
            "parameter": {
              "name": "sticky",
              "type": "boolean",
              "value": "[sticky.value]"
            }
          },
          {
            "parameter": {
              "name": "uread",
              "type": "boolean",
              "value": "[uread.value]"
            }
          },
          {
            "parameter": {
              "name": "uwrite",
              "type": "boolean",
              "value": "[uwrite.value]"
            }
          },
          {
            "parameter": {
              "name": "uexec",
              "type": "boolean",
              "value": "[uexec.value]"
            }
          },
          {
            "parameter": {
              "name": "gread",
              "type": "boolean",
              "value": "[gread.value]"
            }
          },
          {
            "parameter": {
              "name": "gwrite",
              "type": "boolean",
              "value": "[gwrite.value]"
            }
          },
          {
            "parameter": {
              "name": "gexec",
              "type": "boolean",
              "value": "[gexec.value]"
            }
          },
          {
            "parameter": {
              "name": "oread",
              "type": "boolean",
              "value": "[oread.value]"
            }
          },
          {
            "parameter": {
              "name": "owrite",
              "type": "boolean",
              "value": "[owrite.value]"
            }
          },
          {
            "parameter": {
              "name": "oexec",
              "type": "boolean",
              "value": "[oexec.value]"
            }
          }
        ]
      }
    }
  }
