Unix: Individual File
=====================

Description
-----------

The Unix: Individual File test is used to check the contents of a text
file (aka a configuration file) by looking at individual blocks of text.

The file_object element is used to define the specific block(s)
of text of a file(s) to be evaluated. The file_object will only collect
regular files on UNIX systems.

The file to be evaluated may be identified with either a complete
filepath or a path and filename. Only one of these options may be
selected.

The file_state element contains entities that are used to check
the file path and name, as well as the text block in question and the
value of the subexpressions.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**unix.individual_file_v1**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| existence | string | Existence requirement.                        |
+-----------+--------+-----------------------------------------------+
| check     | string | Defines how many collected items must match   |
|           |        | the expected state.                           |
+-----------+--------+-----------------------------------------------+
| filepath  | string | Path the the file. Cannot be blank.           |
+-----------+--------+-----------------------------------------------+

NOTE: The ``existence`` parameter is governed by a constraint allowing only the following values:
  - at_least_one_exists
  - none_exist

NOTE: The ``check`` parameter is governed by a constraint allowing only the following values:
  - all
  - at least one
  - none satisfy
  - only one

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
|                             |         | the file or change into the        |
|                             |         | directory.                         |
+-----------------------------+---------+------------------------------------+
| suid                        | string  | Determines if the file can execute |
|                             |         | as the owner.                      |
+-----------------------------+---------+------------------------------------+
| sgid                        | string  | Determines if the file can execute |
|                             |         | as group.                          |
+-----------------------------+---------+------------------------------------+
| sticky                      | string  | Determines if the sticky bit is    |
|                             |         | set.                               |
+-----------------------------+---------+------------------------------------+

NOTE: All ``unix.file_attributes_v1`` parameters *EXCEPT* ``uid`` and ``gid`` are governed by a constraint allowing only the following values:
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
              <ae:parameter dt="string" name="filepath">[filepath.value]</ae:parameter>
              <ae:parameter dt="string" name="existence">[existence.value]</ae:parameter>
              <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
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

  <file_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iindependent"
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
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iindependent"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <filepath>[filepath.value]</filepath>
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
            name: "filepath"
            dt: "string"
            value: "[filepath.value]"
        - parameter:
            name: "existence"
            dt: "string"
            value: "[existence.value]"
        - parameter:
            name: "check"
            dt: "string"
            value: "[check.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "value"
            dt: "string"
            value: [value.value]
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
              "name": "filepath",
              "type": "string",
              "value": "[filepath.value]"
            }
          },
          {
            "parameter": {
              "name": "existence",
              "type": "string",
              "value": "[existence.value]"
            }
          },
          {
            "parameter": {
              "name": "check",
              "type": "string",
              "value": "[check.value]"
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
              <ae:parameter dt="string" name="filepath">[filepath.value]</ae:parameter>
              <ae:parameter dt="string" name="existence">[existence.value]</ae:parameter>
              <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
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
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iindependent"
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
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iindependent"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <path>[path.value]</path>
    <filename xsi:nil="true">
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
            name: "filepath"
            dt: "string"
            value: "[filepath.value]"
        - parameter:
            name: "existence"
            dt: "string"
            value: "[existence.value]"
        - parameter:
            name: "check"
            dt: "string"
            value: "[check.value]"
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
              "name": "filepath",
              "type": "string",
              "value": "[filepath.value]"
            }
          },
          {
            "parameter": {
              "name": "existence",
              "type": "string",
              "value": "[existence.value]"
            }
          },
          {
            "parameter": {
              "name": "check",
              "type": "string",
              "value": "[check.value]"
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

**unix_file_attributes_v1**

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
              <ae:parameter dt="string" name="filepath">[filepath.value]</ae:parameter>
              <ae:parameter dt="string" name="existence">[existence.value]</ae:parameter>
              <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
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
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
    check="[check.value]" 
    check_existence="[check_existence.value]" 
    comment="[RECOMMENDATION-TITLE]" 
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </file_test> 

Object

::

  <file_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]" 
    version="1">
    <path>[path.value]</path>
    <filename xsi:nil="true" />
    <filepath>[filepath.value]</filepath>
  </file_object>

State

::

  <file_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <group_id datatype="int">
        [group_id.value]
    </group_id>
    <user_id datatype="int">
        [user_id.value]
    </user_id>
    <uread datatype="boolean">
        [uread.value]
    </uread>
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
            name: "filepath"
            dt: "string"
            value: "[filepath.value]"
        - parameter:
            name: "existence"
            dt: "string"
            value: "[existence.value]"
        - parameter:
            name: "check"
            dt: "string"
            value: "[check.value]"
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
            dt: "string"
            value: "[uread.value]"
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
        - parameter:
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
      "artifact-title": "[RECOMMENDATION-TITLE]",
      "artifact": {
        "type": "[ARTIFACT-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "filepath",
              "type": "string",
              "value": "[filepath.value]"
            }
          },
          {
            "parameter": {
              "name": "existence",
              "type": "string",
              "value": "[existence.value]"
            }
          },
          {
            "parameter": {
              "name": "check",
              "type": "string",
              "value": "[check.value]"
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
              "dt": "string",
              "value": "[uread.value]"
            }
          },
          {
            "parameter": {
              "name": "uwrite",
              "dt": "string",
              "value": "[uwrite.value]"
            }
          },
          {
            "parameter": {
              "name": "uexec",
              "dt": "string",
              "value": "[uexec.value]"
            }
          },
          {
            "parameter": {
              "name": "gread",
              "dt": "string",
              "value": "[gread.value]"
            }
          },
          {
            "parameter": {
              "name": "gwrite",
              "dt": "string",
              "value": "[gwrite.value]"
            }
          },
          {
            "parameter": {
              "name": "gexec",
              "dt": "string",
              "value": "[gexec.value]"
            }
          },
          {
            "parameter": {
              "name": "oread",
              "dt": "string",
              "value": "[oread.value]"
            }
          },
          {
            "parameter": {
              "name": "owrite",
              "dt": "string",
              "value": "[owrite.value]"
            }
          },
          {
            "parameter": {
              "name": "oexec",
              "dt": "string",
              "value": "[oexec.value]"
            }
          },
          {
            "parameter": {
              "name": "suid",
              "dt": "string",
              "value": "[suid.value]"
            }
          },
          {
            "parameter": {
              "name": "sgid",
              "dt": "string",
              "value": "[sgid.value]"
            }
          },
          {
            "parameter": {
              "name": "sticky",
              "dt": "string",
              "value": "[sticky.value]"
            }
          }
        ]
      }
    }
  }
