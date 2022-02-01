independent.sql57_textfilecontent_v1
====================================

Description
-----------

The independent.sql57_textfilecontent_v1 test is used to check the contents of a text file (aka a configuration file) by looking at individual blocks of text.

The file_object element is used by a file test to define the specific file(s) to be evaluated. The file_object will collect directories and all file types.

A file object defines the path and filename of the file(s). In addition, a number of behaviors may be provided that help guide the collection of objects. 

The set of files to be evaluated may be identified with either a complete filepath or a path and filename. Only one of these options may be selected.

It is important to note that the 'max_depth' and 'recurse_direction' attributes of the 'behaviors' element do not apply to the 'filepath' element, only to the 'path' and 'filename' elements. This is because the 'filepath' element represents an absolute path to a particular file and it is not possible to recurse over a file.

The file_state element defines the different metadata associate with a UNIX file. This includes the path, filename, type, group id, user id, size, etc. In addition, the permission associated with the file are also included.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**independent.sql57_textfilecontent_v1**

+------------------------+---------+-----------------------------------------+
| Name                   | Type    | Description                             |
+========================+=========+=========================================+
| engine                 | string  | The engine entity defines a specific    |
|                        |         | database engine.                        |
+------------------------+---------+-----------------------------------------+
| sql                    | string  | The sql entity defines a query used to  |
|                        |         | identify the object(s) to test against. |
+------------------------+---------+-----------------------------------------+
| version                | string  | The version entity defines the specific |
|                        |         | version of the database engine to use.  |
|                        |         | This is also important in determining   |
|                        |         | the correct driver to use for           |
|                        |         | establishing a connection.              |
+------------------------+---------+-----------------------------------------+
| prepend_str            | string  | string to be prepended to either the    |
|                        |         | SQL query or the result of the SQL      |
|                        |         | query. Leave empty if no string is to   |
|                        |         | be prepended.                           |
+------------------------+---------+-----------------------------------------+
| append_str             | string  | string to be appended to the result of  |
|                        |         | the SQL query. Leave empty if no        |
|                        |         | string is to be appended.               |
+------------------------+---------+-----------------------------------------+
| prepend_type           | string  | Select ‘string’ if the prepend string   |
|                        |         | is straight text to be prepended to     |
|                        |         | the result. Select ‘SQL’ if it is a     |
|                        |         | query fromwhich the result should be    |
|                        |         | prepended. Otherwise leave empty.       |
+------------------------+---------+-----------------------------------------+
| append_type            | string  | Select ‘string’ if the append string    |
|                        |         | is straight text to be appended to the  |
|                        |         | result of the SQL query. Select ‘SQL’   |
|                        |         | if it is a query from which the result  |
|                        |         | should be appended to the result of     |
|                        |         | the SQL query. Otherwise leave empty.   |
+------------------------+---------+-----------------------------------------+
| path                   | string  | Directory component of the absolute     |
|                        |         | path to the file.                       |
+------------------------+---------+-----------------------------------------+
| filename               | string  | Filename component of the absolute      |
|                        |         | path to the file.                       |
+------------------------+---------+-----------------------------------------+
| recurse                | string  | Should subdirectories be recursed       |
|                        |         | through.                                |
+------------------------+---------+-----------------------------------------+
| max_depth              | binary  | Max depth for recursion. -1 for         |
|                        |         | unlimited recursion.                    |
+------------------------+---------+-----------------------------------------+
| file_system            | string  | Filesystem limitation for recursion.    |
|                        |         | All filesystems, restrict to local      |
|                        |         | only, or restrict to filesystem         |
|                        |         | defined by Path.                        |
+------------------------+---------+-----------------------------------------+
| pattern                | string  | This defines a chunk of text in a file  |
|                        |         | and is represented using a regular      |
|                        |         | expression. A subexpression (using      |
|                        |         | parentheses) can call out a piece of    |
|                        |         | the text block to test. Must be a       |
|                        |         | validexpression according to Perl 5's   |
|                        |         | regular expression specification.       |
+------------------------+---------+-----------------------------------------+

NOTE: The ``engine`` parameter is governed by a constraint allowing only the following values: 
  - access 
  - db2 
  - cache 
  - firebird 
  - firstsql 
  - foxpro 
  - informix 
  - ingres 
  - interbase 
  - lightbase 
  - maxdb 
  - monetdb 
  - mimer 
  - mysql 
  - oracle 
  - paradox 
  - pervasive 
  - postgre 
  - sqlbase 
  - sqlite 
  - sqlserver 
  - sybase

NOTE: The ``prepend_type`` and ``append_type`` parameters are governed by a constraint allowing only the following values:
  - String
  - SQL

NOTE: The ``recurse`` parameter is governed by a constraint allowing only the following values:
  - Yes
  - No

NOTE: The ``file_system`` parameter is governed by a constraint allowing only the following values:
  - NA
  - local
  - all
  - defined

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Txt-Unix: File Or Directory Permissions v2

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**Txt-Unix_File_or_Directory_Permissions_v2**

+------------------------+---------+-----------------------------------------+
| Name                   | Type    | Description                             |
+========================+=========+=========================================+
| username               | string  | The name of the user that owns the file |
|                        |         | or directory.                           |
+------------------------+---------+-----------------------------------------+
| group                  | string  | The name of the group that owns the     |
|                        |         | file or directory.                      |
+------------------------+---------+-----------------------------------------+
| uread                  | string  | Determines whether the user that owns   |
|                        |         | the file/directory is permitted to      |
|                        |         | read the contents of it.                |
+------------------------+---------+-----------------------------------------+
| uwrite                 | string  | Determines whether the user that owns   |
|                        |         | the file/directory is permitted to      |
|                        |         | write to it.                            |
+------------------------+---------+-----------------------------------------+
| uexec                  | string  | Determines whether the user that owns   |
|                        |         | the file/directory is permitted to      |
|                        |         | execute the file or change into the     |
|                        |         | directory.                              |
+------------------------+---------+-----------------------------------------+
| gread                  | string  | Determines whether the group that owns  |
|                        |         | the file/directory is permitted to      |
|                        |         | read the content of it.                 |
+------------------------+---------+-----------------------------------------+
| gwrite                 | string  | Determines whether the group that owns  |
|                        |         | the file/directory is permitted to      |
|                        |         | write to it.                            |
+------------------------+---------+-----------------------------------------+
| gexec                  | string  | Determines whether the group that owns  |
|                        |         | the file/directory is permitted to      |
|                        |         | execute the file or change into the     |
|                        |         | directory.                              |
+------------------------+---------+-----------------------------------------+
| oread                  | string  | Determines whether other users/groups   |
|                        |         | that do not own the file/directory are  |
|                        |         | permitted to read the contents of it.   |
+------------------------+---------+-----------------------------------------+
| owrite                 | string  | Determines whether other users/groups   |
|                        |         | that do not own the file/directory are  |
|                        |         | permitted to write to it.               |
+------------------------+---------+-----------------------------------------+
| oexec                  | string  | Determines whether other users/groups   |
|                        |         | that do not own the file/directory are  |
|                        |         | permitted to execute the file or        |
|                        |         | change into the directory.              |
+------------------------+---------+-----------------------------------------+
| dir_only               | boolean | If this is checking a directory         |
|                        |         | permissions and no file within a        |
|                        |         | directory then this should be set to    |
|                        |         | true.                                   |
+------------------------+---------+-----------------------------------------+

NOTE: The ``read``, ``write``, and ``exec`` parameters are governed by a constraint allowing only the following values:
  - NA
  - set
  - unset 

Generated Content
~~~~~~~~~~~~~~~~~

**Txt-Unix_File_or_Directory_Permissions_v2**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::
   
  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[ARTIFACT-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACT-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="engine">[engine.value]</ae:parameter>
            <ae:parameter dt="string" name="sql">[sql.value]</ae:parameter>
            <ae:parameter dt="string" name="version">[version.value]</ae:parameter>
            <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
            <ae:parameter dt="string" name="filename">[filename.value]</ae:parameter>
            <ae:parameter dt="string" name="recurse">[recurse.value]</ae:parameter>
            <ae:parameter dt="binary" name="max_depth">[max_depth.value]</ae:parameter>
            <ae:parameter dt="string" name="file_system">[file_system.value]</ae:parameter>
            <ae:parameter dt="string" name="prepend_str">[prepend_str.value]</ae:parameter>
            <ae:parameter dt="string" name="append_str">[append_str.value]</ae:parameter>
            <ae:parameter dt="string" name="prepend_type">[prepend_type.value]</ae:parameter>
            <ae:parameter dt="string" name="append_type">[append_type.value]</ae:parameter>.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="username">[username.value]</ae:parameter>
            <ae:parameter dt="string" name="group">[group.value]</ae:parameter>
            <ae:parameter dt="string" name="uread">[uread.value]</ae:parameter>
            <ae:parameter dt="string" name="uwrite">[uwrite.value]</ae:parameter>
            <ae:parameter dt="string" name="uexec">[uexec.value]</ae:parameter>
            <ae:parameter dt="string" name="gread">[gread.value]</ae:parameter>
            <ae:parameter dt="string" name="gwrite">[gwrite.value]</ae:parameter>
            <ae:parameter dt="string" name="gexec">[gexec.value]</ae:parameter>
            <ae:parameter dt="string" name="oread">[oread.value]</ae:parameter>
            <ae:parameter dt="string" name="owrite">[owrite.value]</ae:parameter>
            <ae:parameter dt="string" name="oexec">[oexec.value]</ae:parameter>
            <ae:parameter dt="boolean" name="dir_only">[dir_only.value]</ae:parameter>
          </ae:parameters>
        </ae:test>
        <ae:profiles>
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1" />
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_2" />
        </ae:profiles>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``independent.sql57_textfilecontent_v1`` ``Txt-Unix_File_or_Directory_Permissions_v2`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-content-ref
      href="[BENCHMARK-TITLE]-oval.xml" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]">
    </check-content-ref>
  </check>

OVAL
''''

Test

::

  <file_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"     
    check_existence="at_least_one_exists"    
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
    <filepath
      datatype="string" 
      operation="equals"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </file_object>

  <textfilecontent54_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1"
    comment="[ARTIFACT-TITLE]" 
    version="1">
    <behaviors
      recurse_direction="down"
      recurse_file_system="[recurse_file_system.value]"
      max_depth="[max_depth.value]">
    <path var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]3" />
    <filename var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]4" />
    <pattern
      operation="pattern match"
      datatype="string">
        [pattern.pattern]
    </pattern>
    <instance
      datatype="int"      
      operation="equals">
        1
    </instance>
  </textfilecontent54_object>

  <sql57_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]11"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <engine>[engine.value]</engine>
    <version>[version.value]</version> 
    <connection_string
      var_ref="oval:org.cisecurity.benchmarks:var:2000000" />
    <sql>[sql.value]</sql>
  </sql57_object>

  <password_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2"
    version="1">
    <username datatype="string">[username.value]</username>
  </password_object>

  <textfilecontent54_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]3"
    <filepath datatype="string">/etc/group</filepath>
    <pattern      
      datatype="string"
      operation="pattern match">
        ^mysql[^:]*:[^:]*:([^:]*):.*\$
    </pattern>
    <instance
      datatype="int"      
      operation="equals">
        1
    </instance>
  </textfilecontent54_object>

State

::

  <file_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"   
    version="1">
    <group_id 
      datatype="int" 
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2" />
    <user_id 
      datatype="int" 
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1" />
    <uread datatype="boolean">[oread.value]</uread>
    <uwrite datatype="boolean">[owrite.value]</uwrite>
    <uexec datatype="boolean">[oexec.value]</uexec>
    <gread datatype="boolean">[oread.value]</gread>
    <gwrite datatype="boolean">[owrite.value]</gwrite>
    <gexec datatype="boolean">[oexec.value]</gexec>
    <oread datatype="boolean">[oread.value]</oread>
    <owrite datatype="boolean">[owrite.value]</owrite>
    <oexec datatype="boolean">[oexec.value]</oexec>    
  </file_state>

Variable

::

  <local_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]3"
    datatype="string"
    comment="[ARTIFACT-TITLE]"   
    version="1">
    <regex_capture pattern="^([\/a-zA-Z0-9_\.\-]+\/)[a-zA-Z0-9_\.\-]+\$">
      <object_component 
        item_field="result" 
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]11" 
        record_field="variable_path" />
    </regex_capture>
  </local_variable>

  <local_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]4"
    datatype="string"
    comment="[ARTIFACT-TITLE]"   
    version="1">
    <regex_capture pattern="^[\/a-zA-Z0-9_\.\-]+\/([a-zA-Z0-9_\.\-]+)\$">
      <object_component 
        item_field="result" 
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]11" 
        record_field="variable_path" />
    </regex_capture>
  </local_variable>

  <local_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="string"
    comment="[ARTIFACT-TITLE]"   
    version="1">
    <object_component 
      item_field="subexpression" 
      object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1" />
  </local_variable>

  <local_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1"
    datatype="int"
    comment="[ARTIFACT-TITLE]"   
    version="1">
    <object_component 
      item_field="user_id" 
      object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2"
      record_field="variable_value" />
  </local_variable>

  <local_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2"
    datatype="int"
    comment="[ARTIFACT-TITLE]"   
    version="1">
    <object_component 
      item_field="subexpression" 
      object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]3"
      record_field="variable_value" />
  </local_variable>

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
            name: "engine"
            dt: "string"
            value: "[engine.value]"
        - parameter: 
            name: "sql"
            dt: "string"
            value: "[sql.value]"
        - parameter: 
            name: "version"
            dt: "string"
            value: "[version.value]"
        - parameter: 
            name: "path"
            dt: "string"
            value: "[path.value]"
        - parameter: 
            name: "filename"
            dt: "string"
            value: "[filename.value]"
        - parameter: 
            name: "recurse"
            dt: "string"
            value: "[recurse.value]"
        - parameter: 
            name: "max_depth"
            dt: "binary"
            value: "[max_depth.value]"
        - parameter: 
            name: "file_system"
            dt: "string"
            value: "[file_system.value]"
        - parameter: 
            name: "prepend_str"
            dt: "string"
            value: "[prepend_str.value]"
        - parameter: 
            name: "append_str"
            dt: "string"
            value: "[append_str.value]"
        - parameter: 
            name: "prepend_type"
            dt: "string"
            value: "[prepend_type.value]"
        - parameter: 
            name: "append_type"
            dt: "string"
            value: "[append_type.value]"
        - parameter: 
            name: "pattern"
            dt: "string"
            value: "[pattern.value]"
    test:
      type: "[TEST-TYPE-NAME]"
        - parameter:
            name: "username"
            dt: "string"
            value: "[username.value]"
        - parameter:
            name: "group"
            dt: "string"
            value: "[group.value]"
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
            name: "dir_only"
            dt: "boolean"
            value: "[dir_only.value]"

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
              "name": "engine",
              "type": "string",
              "value": "[engine.value]"
            }
          },
          {
            "parameter": {
              "name": "sql",
              "type": "string",
              "value": "[sql.value]"
            }
          },
          {
            "parameter": {
              "name": "version",
              "type": "string",
              "value": "[version.value]"
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
              "name": "filename",
              "type": "string",
              "value": "[filename.value]"
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
              "type": "binary",
              "value": "[max_depth.value]"
            }
          },
          {
            "parameter": {
              "name": "file_system",
              "dt": "string",
              "value": "[file_system.value]"
            }
          },
          {
            "parameter": {
              "name": "prepend_str",
              "dt": "string",
              "value": "[prepend_str.value]"
            }
          },
          {
            "parameter": {
              "name": "append_str",
              "dt": "string",
              "value": "[append_str.value]"
            }
          },
          {
            "parameter": {
              "name": "prepend_type",
              "dt": "string",
              "value": "[prepend_type.value]"
            }
          },
          {
            "parameter": {
              "name": "append_type",
              "dt": "string",
              "value": "[append_type.value]"
            }
          },
          {
            "parameter": {
              "name": "pattern",
              "dt": "string",
              "value": "[pattern.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "username",
              "dt": "string",
              "value": "[username.value]"
            }
          },
          {
            "parameter": {
              "name": "group",
              "dt": "string",
              "value": "[group.value]"
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
              "name": "dir_only",
              "dt": "boolean",
              "value": "[dir_only.value]"
            }
          }
        ]
      }
    }
  }