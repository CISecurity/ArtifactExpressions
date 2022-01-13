independent.sql57_textfilecontent_v1
======================================

Description
-----------

The independent.sql57_textfilecontent_v1 is used to check the contents of a 
text file (aka a configuration file) by looking at individual blocks of text. 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

+-------------------+---------+----------------------------------------+
| Name              | Type    | Description                            |
+===================+=========+========================================+
| engine            | String  | The engine entity defines a specific   |
|                   |         | database engine.                       |
+-------------------+---------+----------------------------------------+
| sql               | String  | The sql entity defines a query used to |
|                   |         | identify the object(s) to test against.|
+-------------------+---------+----------------------------------------+
| version           | String  | The version entity defines the specific|
|                   |         | version of the database engine to use. |
|                   |         | This is also important in determining  |
|                   |         | the correct driver to use for          |
|                   |         | establishing a connection.             |
+-------------------+---------+----------------------------------------+
| prepend_str       | String  | String to be prepended to either th    |
|                   |         | SQL query or the result of the SQL     |
|                   |         | query. Leave empty if no string is to  |
|                   |         | be prepended.                          |
+-------------------+---------+----------------------------------------+
| append_str        | String  | String to be appended to the result of |
|                   |         | the SQL query. Leave empty if no       |
|                   |         | string is to be appended.              |
+-------------------+---------+----------------------------------------+
| prepend_type      | String  | Select ‘string’ if the prepend string  |
|                   |         | is straight text to be prepended to    |
|                   |         | the result. Select ‘SQL’ if it is a    |
|                   |         | query fromwhich the result should be   |
|                   |         | prepended. Otherwise leave empty.      |
+-------------------+---------+----------------------------------------+
| append_type       | String  | Select ‘string’ if the append string   |
|                   |         | is straight text to be appended to the |
|                   |         | result of the SQL query. Select ‘SQL’  |
|                   |         | if it is a query from which the result |
|                   |         | should be appended to the result of    |
|                   |         | the SQL query. Otherwise leave empty.  |
+-------------------+---------+----------------------------------------+
| path              | String  | Directory component of the absolute    |
|                   |         | path to the file.                      |
+-------------------+---------+----------------------------------------+
| filename          | String  | Filename component of the absolute     |
|                   |         | path to the file.                      |
+-------------------+---------+----------------------------------------+
| recurse           | String  | Should subdirectories be recursed      |
|                   |         | through.                               |
+-------------------+---------+----------------------------------------+
| max_depth         | Binary  | Max depth for recursion. -1 for        |
|                   |         | unlimited recursion.                   |
+-------------------+---------+----------------------------------------+
| file_system       | String  | Filesystem limitation for recursion.   |
|                   |         | All filesystems, restrict to local     |
|                   |         | only, or restrict to filesystem        |
|                   |         | defined by Path.                       |
+-------------------+---------+----------------------------------------+
| pattern           | String  | This defines a chunk of text in a file |
|                   |         | and is represented using a regular     |
|                   |         | expression. A subexpression (using     |
|                   |         | parentheses) can call out a piece of   |
|                   |         | the text block to test. Must be a      |
|                   |         | validexpression according to Perl 5's  |
|                   |         | regular expression specification.      |
+-------------------+---------+----------------------------------------+

engine NOTE: This parameter is governed by a constraint allowing only
the following values: 
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

prepend_type NOTE: This parameter is governed by a constraint allowing
only the following values:
  - String
  - SQL

append_type NOTE: This parameter is governed by a constraint allowing
only the following values:
  - String
  - SQL

recurse NOTE: This parameter is governed by a constraint allowing
only the following values:
  - Yes
  - No

file_system NOTE: This parameter is governed by a constraint allowing
only the following values:
  - NA
  - local
  - all
  - defined

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Txt-Unix_File_or_Directory_Permissions_v2

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

Txt-Unix_File_or_Directory_Permissions_v2
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+-------------------+---------+----------------------------------------+
| Name              | Type    | Description                            |
+===================+=========+========================================+
| username          | string  | The name of the user that owns the     |
|                   |         | file or directory.                     |
+-------------------+---------+----------------------------------------+
| group             | string  | The name of the group that owns the    |
|                   |         | file or directory.                     |
+-------------------+---------+----------------------------------------+
| uread             | string  |Determines whether the user that owns   |
|                   |         | the file/directory is permitted to     |
|                   |         | read the contents of it.               |
+-------------------+---------+----------------------------------------+
| uwrite            | string  | Determines whether the user that owns  |
|                   |         | the file/directory is permitted to     |
|                   |         | write to it.                           |
+-------------------+---------+----------------------------------------+
| uexec             | string  | Determines whether the user that owns  |
|                   |         | the file/directory is permitted to     |
|                   |         | execute the file or change into the    |
|                   |         | directory.                             |
+-------------------+---------+----------------------------------------+
| gread             | string  | Determines whether the group that owns |
|                   |         | the file/directory is permitted to     |
|                   |         | read the content of it.                |
+-------------------+---------+----------------------------------------+
| gwrite            | string  | Determines whether the group that owns |
|                   |         | the file/directory is permitted to     |
|                   |         | write to it.                           |
+-------------------+---------+----------------------------------------+
| gexec             | string  | Determines whether the group that owns |
|                   |         | the file/directory is permitted to     |
|                   |         | execute the file or change into the    |
|                   |         | directory.                             |
+-------------------+---------+----------------------------------------+
| oread             | string  | Determines whether other users/groups  |
|                   |         | that do not own the file/directory are |
|                   |         | permitted to read the contents of it.  |
+-------------------+---------+----------------------------------------+
| owrite            | string  | Determines whether other users/groups  |
|                   |         | that do not own the file/directory are |
|                   |         | permitted to write to it.              |
+-------------------+---------+----------------------------------------+
| oexec             | string  | Determines whether other users/groups  |
|                   |         | that do not own the file/directory are |
|                   |         | permitted to execute the file or       |
|                   |         | change into the directory.             |
+-------------------+---------+----------------------------------------+
| dir_only          | boolean | If this is checking a directory        |
|                   |         | permissions and no file within a       |
|                   |         | directory then this should be set to   |
|                   |         | true.                                  |
+-------------------+---------+----------------------------------------+

uread NOTE: This parameter is governed by a constraint allowing only the 
following values:
  - NA
  - set
  - unset 

uwrite NOTE: This parameter is governed by a constraint allowing only the 
following values:
  - NA
  - set
  - unset 

uexec NOTE: This parameter is governed by a constraint allowing only the 
following values:
  - NA
  - set
  - unset 

gread NOTE: This parameter is governed by a constraint allowing only the 
following values:
  - NA
  - set
  - unset 

gwrite NOTE: This parameter is governed by a constraint allowing only the 
following values:
  - NA
  - set
  - unset 

gexec NOTE: This parameter is governed by a constraint allowing only the 
following values:
  - NA
  - set
  - unset 

oread NOTE: This parameter is governed by a constraint allowing only the 
following values:
  - NA
  - set
  - unset 

owrite NOTE: This parameter is governed by a constraint allowing only the 
following values:
  - NA
  - set
  - unset 

oexec NOTE: This parameter is governed by a constraint allowing only the 
following values:
  - NA
  - set
  - unset 

Generated Content
~~~~~~~~~~~~~~~~~

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
            <ae:parameter dt="string" name="path"/>
            <ae:parameter dt="string" name="filename"/>
            <ae:parameter dt="string" name="recurse">[recurse.value]</ae:parameter>
            <ae:parameter dt="binary" name="max_depth"/>
            <ae:parameter dt="string" name="file_system">[file_system.value]</ae:parameter>
            <ae:parameter dt="string" name="prepend_str"/>
            <ae:parameter dt="string" name="append_str"/>
            <ae:parameter dt="string" name="prepend_type"/>
            <ae:parameter dt="string" name="append_type"/>
            <ae:parameter dt="string" name="pattern">[pattern.value]</ae:parameter>
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

For ``independent.sql57_textfilecontent_v1`` artifacts, the xccdf:check looks like this.

::

  <check system='http://oval.mitre.org/XMLSchema/oval-definitions-5'>
    <check-content-ref 
      href="[BENCHMARK-NAME]" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]">
    </check-content-ref>
  </check>

OVAL
''''

Test

::

  <file_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    check="[check.value]" 
    check_existence="[check_existence.value]" 
    comment="[ARTIFACT-TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </file_test>

Object

::

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    comment="[ARTIFACT-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    version="1">
    <filepath
      datatype="[datatype.value]" 
      operation="[operation.value]"
      var_ref="[var_ref.value]" />
  </file_object>

State

::

  <file_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    comment="[ARTIFACT-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    version="1">
    <group_id 
      datatype="[datatype.value]" 
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <user_id 
      datatype="[datatype.value]" 
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <gwrite datatype="string">[gwrite.value]</gwrite>
    <oread datatype="string">[oread.value]</oread>
    <owrite datatype="string">[owrite.value]</owrite>
    <oexec datatype="string">[oexec.value]</oexec>
  </file_state>

Variable

::

  <local_variable 
    comment="[ARTIFACT-TITLE]" 
    datatype="[datatype.value]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    version="1">
    <regex_capture pattern="[pattern.value]">
      <object_component 
        item_field="[item_field.value]" 
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
        record_field="[record_field.value]" />
    </regex_capture>
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
            type: "string"
            value: "[engine.value]"
        - parameter: 
            name: "sql"
            type: "string"
            value: "[sql.value]"
        - parameter: 
            name: "version"
            type: "string"
            value: "[version.value]"
        - parameter: 
            name: "path"
            type: "string"
            value: "[path.value]"
        - parameter: 
            name: "filename"
            type: "string"
            value: "[filename.value]"
        - parameter: 
            name: "recurse"
            type: "string"
            value: "[recurse.value]"
        - parameter: 
            name: "max_depth"
            type: "binary"
            value: "[max_depth.value]"
        - parameter: 
            name: "file_system"
            type: "string"
            value: "[file_system.value]"
        - parameter: 
            name: "prepend_str"
            type: "string"
            value: "[prepend_str.value]"
        - parameter: 
            name: "append_str"
            type: "string"
            value: "[append_str.value]"
        - parameter: 
            name: "prepend_type"
            type: "string"
            value: "[prepend_type.value]"
        - parameter: 
            name: "append_type"
            type: "string"
            value: "[append_type.value]"
        - parameter: 
            name: "pattern"
            type: "string"
            value: "[pattern.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:   
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