Unix: File Collection
=====================

Description
-----------

The Unix: File Collection test is used to check metadata associated with
UNIX files, of the sort returned by either an ls command, stat command
or stat() system call.

The file_object element is used by a file_test to define either the path and
filename or complete filepath of the specific file(s) to be evaluated.
The set of files to be evaluated may be identified with either a
complete filepath or a path and filename. Only one of these options may
be selected.

It is important to note that the 'max_depth' and 'recurse_direction'
attributes of the 'behaviors' element do not apply to the 'filepath'
element, only to the 'path' and 'filename' elements. This is because the
'filepath' element represents an absolute path to a particular file and
it is not possible to recurse over a file.

The file_state element defines the different metadata associate
with a file, including the path, filename, owner, size, last modified
time, version, etc.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**unix.file_collection_v1**

=========== ====== ====================================================
Name        Type   Description
=========== ====== ====================================================
existence   string Existence requirement.
path        string Path to the file. Cannot be blank.
file_name   string The name of the file. Cannot be blank.
recurse     string Should subdirectories be recursed through? (Yes/No)
max_depth   int    Max depth for recursion. -1 for unlimited recursion.
file_system string File system limitation for recursion.
=========== ====== ====================================================

NOTE: The ``existence`` parameter is governed by a constraint allowing only the following values:
  -  all_exist
  -  any_exist
  -  at_least_one_exists
  -  none_satisfy
  -  none_exist
  -  only_one_exists

NOTE: The ``file_system`` parameter is governed by a constraint allowing only the following values:
  -  NA
  -  local
  -  all
  -  defined

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  -  Unix File Permissions
  -  Unix File Ownership
  -  Null Test

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**unix.file_permissions_v1**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
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
|                             |         | permitted to read the contents of  |
|                             |         | it.                                |
+-----------------------------+---------+------------------------------------+
| gwrite                      | string  | Determines whether the group that  |
|                             |         | owns the file or directory is      |
|                             |         | permitted to write to it.          |
+-----------------------------+---------+------------------------------------+
| gexec                       | string  | Determines whether the group that  |
|                             |         | owns the file or directory is      |
|                             |         | permitted to execute the file or   |
|                             |         | change into the directory.         |
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
|                             |         | the file or change into            |
|                             |         | the directory.                     |
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

NOTE: All ``unix.file_permissions_v1`` parameters are governed by a constraint allowing only the following values:
  -  NA
  -  set
  -  unset

**unix.file_ownership_v1**

==== ==== ============================================================
Name Type Description
==== ==== ============================================================
uid  int  The User ID of the files owner (Positive integer or blank).
gid  int  The Group ID of the files owner (Positive integer or blank).
==== ==== ============================================================

**null_test_v1**

==== ==== ===========
Name Type Description
==== ==== ===========
N/A       
==== ==== ===========

Generated Content
~~~~~~~~~~~~~~~~~

**unix.file_permissions_v1**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:complex-check operator="AND">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
        <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
          <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
          <ae:title>[ARTIFACT-TITLE]</ae:title>
          <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="existence">[existence.value]</ae:parameter>
              <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
              <ae:parameter dt="string" name="file_name">[file_name.value]</ae:parameter>
              <ae:parameter dt="string" name="recurse">[recurse.value]</ae:parameter>
              <ae:parameter dt="int" name="max_depth"> [max_depth.value] </ae:parameter>
              <ae:parameter dt="string" name="file_system">[file_system.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
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

For ``unix.file_collection_v1 unix.file_permissions_v1`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

::

  <xccdf:complex-check operator="AND">
    <check 
      system="http://oval.mitre.org/XMLSchema/oval-definitions-5"
      href="[BENCHMARK-TITLE]"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </xccdf:complex-check>

OVAL
''''

Test

::

  <file_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"    
    check="all"    
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </file_test>

Object

::

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <path>[path.value]</path>
    <filename xsi:nil="[xsi:nil.value]">
      [filename.value]
    </filename>
    <behaviors 
      recurse_direction="down"
      recurse_file_system="[recurse_file_system.value]"
      max_depth="[max_depth.value]" />
  </file_object>

State

::

  <file_state xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <gread datatype="boolean">[gread.value]</gread>
    <gwrite datatype="boolean">[gwrite.value]</gwrite>
    <gexec datatype="boolean">[gexec.value]</gexec>
    <oread datatype="boolean">[oread.value]</oread>
    <owrite datatype="boolean">[owrite.value]</owrite>
    <oexec datatype="boolean">[oexec.value]</oexec>
  </file_state>

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
            name: "max_depth"
            dt: "int"
            value: "[max_depth.value]"
        - parameter:
            name: "file_system"
            dt: "string"
            value: "[file_system.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "uread"
            dt: "string"
            value: [uread.value]
        - parameter:
            name: "uwrite"
            dt: "string"
            value: "[uwrite.value]"
        - parameter:
            name: "uexec"
            dt: "string"
            value: "[uexec.value]"
        - parameter:
            name: "gread"
            dt: "string"
            value: "[gread.value]"
        - parameter: "
            name: "gwrite"
            dt: "string"
            value: "[gwrite.value]"
        - parameter:
            name: "gexec"
            dt: "string"
            value: "[gexec.value]"
        - parameter:
            name: "oread"
            dt: "string"
            value: "[oread.value]"
        - parameter:
            name: "owrite"
            dt: "string"
            value: "[owrite.value]"
        - parameter:
            name: "oexec"
            dt: "string"
            value: "[oexec.value]"
        - parameter:
            name: "suid"
            dt: "string"
            value: "[suid.value]"
        - parameter:
            name: "sgid"
            dt: "string"
            value: "[sgid.value]"
        - parameter:
            name: "sticky"
            dt: "string"
            value: "[sticky.value]"

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
              "name": "max_depth",
              "type": "int",
              "value": "[max_depth.value]"
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
              "name": "uread",
              "type": "string",
              "value": "[uread.value]"
            }
          },
          {
            "parameter": {
              "name": "uwrite",
              "type": "string",
              "value": "[uwrite.value]"
            }
          },
          {
            "parameter": {
              "name": "uexec",
              "type": "string",
              "value": "[uexec.value]"
            }
          },
          {
            "parameter": {
              "name": "gread",
              "type": "string",
              "value": "[gread.value]"
            }
          },
          {
            "parameter": {
              "name": "gwrite",
              "type": "string",
              "value": "[gwrite.value]"
            }
          },
          {
            "parameter": {
              "name": "gexec",
              "type": "string",
              "value": "[gexec.value]"
            }
          },
          {
            "parameter": {
              "name": "oread",
              "type": "string",
              "value": "[oread.value]"
            }
          },
          {
            "parameter": {
              "name": "owrite",
              "type": "string",
              "value": "[owrite.value]"
            }
          },
          {
            "parameter": {
              "name": "oexec",
              "type": "string",
              "value": "[oexec.value]"
            }
          },
          {
            "parameter": {
              "name": "suid",
              "type": "string",
              "value": "[suid.value]"
            }
          },
          {
            "parameter": {
              "name": "sgid",
              "type": "string",
              "value": "[sgid.value]"
            }
          },
          {
            "parameter": {
              "name": "sticky",
              "type": "string",
              "value": "[sticky.value]"
            }
          }
        ]
      }
    }
  }

Generated Content
~~~~~~~~~~~~~~~~~

**unix_file_ownership_v1**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:complex-check operator="AND">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
        <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
          <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
          <ae:title>[ARTIFACT-TITLE]</ae:title>
          <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="existence">[existence.value]</ae:parameter>
              <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
              <ae:parameter dt="string" name="file_name">[file_name.value]</ae:parameter>
              <ae:parameter dt="string" name="recurse">[recurse.value]</ae:parameter>
              <ae:parameter dt="int" name="max_depth"> [max_depth.value] </ae:parameter>
              <ae:parameter dt="string" name="file_system">[file_system.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="int" name="uid">[uid.value]</ae:parameter>
              <ae:parameter dt="int" name="gid">[gid.value]</ae:parameter>
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

For ``unix.file_collection_v1 unix_file_ownership_v1`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

::

  <xccdf:complex-check operator="AND">
    <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
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
    check="all"    
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </file_test>

Object

::

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <path>[path.value]</path>
    <filename xsi:nil="[xsi:nil.value]">
      [filename.value]
    </filename>
    <behaviors 
      recurse_direction="down"
      recurse_file_system="[recurse_file_system.value]"
      max_depth="[max_depth.value]" />
  </file_object>

State

::

  <file_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <group_id datatype="int">
      [group_id.value]
    </group_id>
    <user_id datatype="int">
      [user_id.value]
    </user_id>
  </file_state>

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
            name: "max_depth"
            dt: "int"
            value: "[max_depth.value]"
        - parameter:
            name: "file_system"
            dt: "string"
            value: "[file_system.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "uid"
            dt: "int"
            value: [uid.value]
        - parameter:
            name: "gid"
            dt: "int"
            value: "[gid.value]"

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
              "name": "max_depth",
              "type": "int",
              "value": "[max_depth.value]"
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
              "name": "uid",
              "type": "int",
              "value": "[uid.value]"
            }
          },
          {
            "parameter": {
              "name": "gid",
              "type": "int",
              "value": "[gid.value]"
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
          <ae:title>[ARTIFACT-TITLE]</ae:title>
          <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="existence">[existence.value]</ae:parameter>
              <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
              <ae:parameter dt="string" name="file_name">[file_name.value]</ae:parameter>
              <ae:parameter dt="string" name="recurse">[recurse.value]</ae:parameter>
              <ae:parameter dt="int" name="max_depth"> [max_depth.value] </ae:parameter>
              <ae:parameter dt="string" name="file_system">[file_system.value]</ae:parameter>
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

For ``unix.file_collection_v1 null_test_v1`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

::

  <xccdf:complex-check operator="AND">
    <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
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
    check="all"    
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </file_test>

Object

::

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <path>[path.value]</path>
    <filename xsi:nil="[xsi:nil.value]">
      [filename.value]
    </filename>
    <behaviors 
      recurse_direction="down"
      recurse_file_system="[recurse_file_system.value]"
      max_depth="[max_depth.value]" />
  </file_object>

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
            name: "max_depth"
            dt: "int"
            value: "[max_depth.value]"
        - parameter:
            name: "file_system"
            dt: "string"
            value: "[file_system.value]"
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
              "name": "max_depth",
              "type": "int",
              "value": "[max_depth.value]"
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
