Independent: MySQL TextFileContent v1
======================================

Description
-----------

The Independent: MySQL TextFileContent v1 test The textfilecontent54_test element is used to check the contents of a text file (aka a configuration file) by looking at individual blocks of text.

The textfilecontent54_object element is used by a textfilecontent_test to define the specific block(s) of text of a file(s) to be evaluated. The textfilecontent54_object will only collect regular files on UNIX systems and FILE_TYPE_DISK files on Windows systems. 

The set of files to be evaluated may be identified with either a complete filepath or a path and filename. Only one of these options may be selected.

It is important to note that the 'max_depth' and 'recurse_direction' attributes of the 'behaviors' element do not apply to the 'filepath' element, only to the 'path' and 'filename' elements. This is because the 'filepath' element represents an absolute path to a particular file and it is not possible to recurse over a file.

The textfilecontent54_state element contains entities that are used to check the file path and name, as well as the text block in question and the value of the subexpressions.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**independent.mysql_text_file_content_v1**

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
| prepend_str            | string  | string to be prepended to either th     |
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
|                        |         | through. (Yes/No)                       |
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

  - Pattern Match
  - Pattern Not Match
  - Existence Test
  - SQL-Unix: File Or Directory Permissions
  - Txt-Unix: File Or Directory Permissions
  - Txt-Unix: File Or Directory Permissions v2
  - Independent: Text File Content
  - Independent: Text File Content V2

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

| **pattern match** 
| **pattern not match**
+------------------------+---------+-----------------------------------------+
| Name                   | Type    | Description                             |
+========================+=========+=========================================+
| value                  | string  | Regular expression to be matched.       |
+------------------------+---------+-----------------------------------------+
| data_type              | string  | Data type.                              |
+------------------------+---------+-----------------------------------------+

NOTE: The ``data_type`` parameter is governed by a constraint allowing only the following values:
  - boolean
  - float
  - int
  - string
  - version 
  - set 

**existence_test**

+------------------------+---------+-----------------------------------------+
| Name                   | Type    | Description                             |
+========================+=========+=========================================+
| value                  | string  | Value to test.                          |
+------------------------+---------+-----------------------------------------+

**SQL-Unix_File_or_Directory_Permissions_v1**

+------------------------+---------+-----------------------------------------+
| Name                   | Type    | Description                             |
+========================+=========+=========================================+
| username               | string  | The name of the user that owns the      |
|                        |         | file or directory.                      |
+------------------------+---------+-----------------------------------------+
| group                  | string  | The name of the group that owns the     |
|                        |         | file or directory.                      |
+------------------------+---------+-----------------------------------------+
| uread                  | boolean | Determines whether the user that owns   |
|                        |         | the file/directory is permitted to      |
|                        |         | read the contents of it.                |
+------------------------+---------+-----------------------------------------+
| uwrite                 | boolean | Determines whether the user that owns   |
|                        |         | the file/directory is permitted to      |
|                        |         | write to it.                            |
+------------------------+---------+-----------------------------------------+
| uexec                  | boolean | Determines whether the user that owns   |
|                        |         | the file/directory is permitted to      |
|                        |         | execute the file or change into the     |
|                        |         | directory.                              |
+------------------------+---------+-----------------------------------------+
| gread                  | boolean | Determines whether the group that owns  |
|                        |         | the file/directory is permitted to      |
|                        |         | read the content of it.                 |
+------------------------+---------+-----------------------------------------+
| gwrite                 | boolean | Determines whether the group that owns  |
|                        |         | the file/directory is permitted to      |
|                        |         | write to it.                            |
+------------------------+---------+-----------------------------------------+
| gexec                  | boolean | Determines whether the group that owns  |
|                        |         | the file/directory is permitted to      |
|                        |         | execute the file or change into the     |
|                        |         | directory.                              |
+------------------------+---------+-----------------------------------------+
| oread                  | boolean | Determines whether other users/groups   |
|                        |         | that do not own the file/directory are  |
|                        |         | permitted to read the contents of it.   |
+------------------------+---------+-----------------------------------------+
| owrite                 | boolean | Determines whether other users/groups   |
|                        |         | that do not own the file/directory are  |
|                        |         | permitted to write to it.               |
+------------------------+---------+-----------------------------------------+
| oexec                  | boolean | Determines whether other users/groups   |
|                        |         | that do not own the file/directory are  |
|                        |         | permitted to execute the file or        |
|                        |         | change into thedirectory.               |
+------------------------+---------+-----------------------------------------+
| dir_only               | boolean | If this is checking a directory         |
|                        |         | permissions and no file within a        |
|                        |         | directory then this should be set to    |
|                        |         | true.                                   |
+------------------------+---------+-----------------------------------------+

**Txt-Unix_File_or_Directory_Permissions_v1**

+------------------------+---------+-----------------------------------------+
| Name                   | Type    | Description                             |
+========================+=========+=========================================+
| username               | string  | The name of the user that owns the      |
|                        |         | file or directory.                      |
+------------------------+---------+-----------------------------------------+
| group                  | string  | The name of the group that owns the     |
|                        |         | file or directory.                      |
+------------------------+---------+-----------------------------------------+
| uread                  | boolean | Determines whether the user that owns   |
|                        |         | the file/directory is permitted to      |
|                        |         | read the contents of it.                |
+------------------------+---------+-----------------------------------------+
| uwrite                 | boolean | Determines whether the user that owns   |
|                        |         | the file/directory is permitted to      |
|                        |         | write to it.                            |
+------------------------+---------+-----------------------------------------+
| uexec                  | boolean | Determines whether the user that owns   |
|                        |         | the file/directory is permitted to      |
|                        |         | execute the  file or change into the    |
|                        |         | directory.                              |
+------------------------+---------+-----------------------------------------+
| gread                  | boolean | Determines whether the user that owns   |
|                        |         | the file/directory is permitted to      |
|                        |         | read the content of it.                 |
+------------------------+---------+-----------------------------------------+
| gwrite                 | boolean | Determines whether the group that owns  |
|                        |         | the file/directory is permitted to      |
|                        |         | write to it.                            |
+------------------------+---------+-----------------------------------------+
| gexec                  | boolean | Determines whether the group that owns  |
|                        |         | the file/directory is permitted to      |
|                        |         | execute the file or change into the     |
|                        |         | directory.                              |
+------------------------+---------+-----------------------------------------+
| oread                  | boolean | Determines whether other users/groups   |
|                        |         | that do not own the file/directory are  |
|                        |         | permitted to read the contents of it.   |
+------------------------+---------+-----------------------------------------+
| owrite                 | boolean | Determines whether other users/groups   |
|                        |         | that do not own the file/directory are  |
|                        |         | permitted to write to it.               |
+------------------------+---------+-----------------------------------------+
| oexec                  | boolean | Determines whether other users/groups   |
|                        |         | that do not own the file/directory are  |
|                        |         | permitted to execute the file or        |
|                        |         | change into the directory.              |
+------------------------+---------+-----------------------------------------+
| dir_only               | boolean | If this is checking a directory         |
|                        |         | permissions and no file within a        |
|                        |         | directory then this should be set to    |
|                        |         | true.                                   |
+------------------------+---------+-----------------------------------------+

**Txt-Unix_File_or_Directory_Permissions_v2**

+------------------------+---------+-----------------------------------------+
| Name                   | Type    | Description                             |
+========================+=========+=========================================+
| username               | string  | The name of the user that owns the      |
|                        |         | file or directory.                      |
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
|                        |         | execute the  file or change into the    |
|                        |         | directory.                              |
+------------------------+---------+-----------------------------------------+
| gread                  | string  | Determines whether the user that owns   |
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

**independent.txt_file_content_v1**

+------------------------+---------+-----------------------------------------+
| Name                   | Type    | Description                             |
+========================+=========+=========================================+
| subexpression          | string  | This represents a value to test against |
|                        |         | the subexpression in the specified      |
|                        |         | pattern. If multiple subexpressions are |
|                        |         | specified in the pattern, this value is |
|                        |         | tested against all of them.             |
+------------------------+---------+-----------------------------------------+
| filepath               | string  | This specifies the absolute path for a  |
|                        |         | file on the machine. A directory cannot |
|                        |         | be specified as a filepath.             |
+------------------------+---------+-----------------------------------------+
| path                   | string  | This specifies the directory component  |
|                        |         | of the absolute path to a file on the   |
|                        |         | machine.                                |
+------------------------+---------+-----------------------------------------+
| filename               | string  | This represents a regular expression    |
|                        |         | that is used to define a block of text. |
+------------------------+---------+-----------------------------------------+
| pattern                | binary  | This represents a regular expression    |
|                        |         | that is used to define a block of text. |
+------------------------+---------+-----------------------------------------+
| instance               | binary  | This calls out a specific match of the  |
|                        |         | pattern. This can only be a positive    |
|                        |         | integer or blank.                       |
+------------------------+---------+-----------------------------------------+
| subexp_op              | string  | This specifies what operation to        |
|                        |         | perform on the subexpression.           |
+------------------------+---------+-----------------------------------------+
| inst_op                | string  | This specifies what operation to        |
|                        |         | perform on the instance.                |
+------------------------+---------+-----------------------------------------+
| text                   | string  | Should subdirectories be recursed       |
|                        |         | through.                                |
+------------------------+---------+-----------------------------------------+
| text_op                | int     | This specifies what operation to        |
|                        |         | perform on the text.                    |
+------------------------+---------+-----------------------------------------+

NOTE: The ``subexp_op``, ``inst_op``, and ``text_op`` parameters are governed by a constraint allowing only the following values:
  - equals
  - not equal
  - case insensitive equals
  - case insensitive not equal
  - greater than
  - less than
  - greater than or equal
  - less than or equal
  - bitwise and
  - bitwise or
  - pattern match
  - subset of
  - superset of

**independent.txt_file_content_v2**

+------------------------+---------+-----------------------------------------+
| Name                   | Type    | Description                             |
+========================+=========+=========================================+
| subexpression          | string  | This represents a value to test         |
|                        |         | against the subexpression in the        |
|                        |         | specified pattern. If multiple          |
|                        |         | subexpressions are specified in the     |
|                        |         | pattern, this value is tested against   |
|                        |         | all of them.                            |
+------------------------+---------+-----------------------------------------+
| filepath               | string  | This specifies the absolute path for    |
|                        |         | a file on the machine. A directory      |
|                        |         | cannot be specified as a filepath.      |
+------------------------+---------+-----------------------------------------+
| path                   | string  | This specifies the directory            |
|                        |         | component of the absolute path to a     |
|                        |         | file on the machine.                    |
+------------------------+---------+-----------------------------------------+
| filename               | string  | This represents the name of a file.     |
+------------------------+---------+-----------------------------------------+
| pattern                | binary  | This represents a regular expression    |
+------------------------+---------+-----------------------------------------+
| instance               | binary  | This calls out a specific match of the  |
|                        |         | pattern. This can only be a positive    |
|                        |         | integer or blank.                       |
+------------------------+---------+-----------------------------------------+
| subexp_op              | string  | This specifies what operation to        |
|                        |         | perform on the subexpression.           |
+------------------------+---------+-----------------------------------------+
| inst_op                | string  | This specifies what operation to        |
|                        |         | perform on the instance.                |
+------------------------+---------+-----------------------------------------+
| text                   | string  | This represents the block of text that  |
|                        |         | matched the specified pattern.          |
+------------------------+---------+-----------------------------------------+
| text_op                | string  | This specifies what operation to        |
|                        |         | perform on the text.                    |
+------------------------+---------+-----------------------------------------+
| entity_check           | string  | Defines how many items must evaluate    |
|                        |         | to true for the entity check            |
+------------------------+---------+-----------------------------------------+

NOTE: The ``subexp_op``, ``inst_op``, and ``text_op`` parameters are governed by a constraint allowing only the following values:
  - equals
  - not equal
  - case insensitive equals
  - case insensitive not equal
  - greater than
  - less than
  - greater than or equal
  - less than or equal
  - bitwise and
  - bitwise or
  - pattern match
  - subset of
  - superset of

NOTE: The ``entity_check`` parameter is governed by a constraint allowing only the following values:
  - all
  - at least one
  - none satisfy
  - only one

Generated Content
~~~~~~~~~~~~~~~~~

| **pattern match**
| **pattern not match**
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
            <ae:parameter dt="string" name="append_type">[append_type.value]</ae:parameter>
            <ae:parameter dt="string" name="pattern">[pattern.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
            <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
          </ae:parameters>
        </ae:test>
        <ae:profiles>
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1" />
        </ae:profiles>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``independent.mysql_text_file_content_v1`` ``pattern match`` and ``pattern not match`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this artifact.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    type="[type.value]"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``independent.mysql_text_file_content_v1`` ``pattern match`` and ``pattern not match`` artifacts, the XCCDF check looks like this. 

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:2000000"
      value-id="xccdf_org.cisecurity_value_jdbc.url" />
    <check-content-ref
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <textfilecontent54_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"     
    check_existence="at_least_one_exists"    
    check="all" 
    comment="[ARTIFACT-TITLE]" 
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </textfilecontent54_test>

Object   

::

  <textfilecontent54_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"    
    comment="[ARTIFACT-TITLE]"  
    version="1">
    <behaviors
      recurse_direction="down"
      recurse_file_system="[recurse_file_system.value]"
      max_depth="[max_depth.value]" />
    <path var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1" />
    <filename var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2" />
    <pattern 
      operation="pattern match">
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2"
    </pattern>
    <instance 
      datatype="int" 
      operation="greater than or equal">
        0
    </instance>
  </textfilecontent54_object>

  <sql57_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1" 
    comment="[ARTIFACT-TITLE]" 
    version="1">
    <engine>[engine.value]</engine>
    <version>[version.value]</version>
    <connection_string 
      var_ref="oval:org.cisecurity.benchmarks:var:2000000" />
    <sql>[sql.value]</sql>
  </sql57_object>

State  

::

  <textfilecontent54_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[ARTIFACT-TITLE]" 
    version="1">
    <subexpression
      operation="pattern match"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </textfilecontent54_state>

Variable

::

  <external_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    comment="[ARTIFACT-TITLE]" 
    datatype="[datatype.value]"
    version="1" />

  <local_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1" 
    comment="Capture the directory path for the PostgreSQL config file." 
    datatype="string"
    version="1">
    <regex_capture pattern="^([\/a-zA-Z0-9_\.\-]+\/)[a-zA-Z0-9_\.\-]+\$">
      <object_component
        item_field="result"
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1"
        record_field="variable_path" />
    </regex_capture>
  </local_variable>

  <local_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2" 
    comment="Capture the directory path for the PostgreSQL config file." 
    datatype="string"
    version="1">
    <regex_capture pattern="^[\/a-zA-Z0-9_\.\-]+\/([a-zA-Z0-9_\.\-]+)\$">
      <object_component
        item_field="result"
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1"
        record_field="variable_path" />
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
      parameters:
        - parameter: 
            name: "value"
            dt: "string"
            value: "[value.value]"
        - parameter: 
            name: "datatype"
            dt: "string"
            value: "[datatype.value]"

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
              "name": "value",
              "dt": "string",
              "value": "[value.value]"
            }
          },
          {
            "parameter": {
              "name": "datatype",
              "dt": "string",
              "value": "[datatype.value]"
            }
          }
        ]
      }
    }
  }

Generated Content
~~~~~~~~~~~~~~~~~

**existence_test**

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
            <ae:parameter dt="string" name="append_type">[append_type.value]</ae:parameter>
            <ae:parameter dt="string" name="pattern">[pattern.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
          </ae:parameters>
        </ae:test>
        <ae:profiles>
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1" />
        </ae:profiles>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``independent.mysql_text_file_content_v1`` ``existence_test`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:2000000"
      value-id="xccdf_org.cisecurity_value_jdbc.url" />
    <check-content-ref
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <textfilecontent54_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"     
    check_existence="[check_existence.value]"
    check="all" 
    comment="[ARTIFACT-TITLE]" 
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </textfilecontent54_test> 

Object

::

  <textfilecontent54_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"    
    comment="[ARTIFACT-TITLE]"  
    version="1">
    <path var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <filenamevar_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1" />
    <pattern
      operation="pattern match"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2" />
    <instance
      datatype="int"
      operation="greater than or equal">
        0
    </instance>
  </textfilecontent54_object>

  <sql57_object>
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"    
    comment="[ARTIFACT-TITLE]"  
    version="1">
    <engine>[engine.value]</engine>
    <version>[version.value]</version>
    <connection_string 
      var_ref="oval:org.cisecurity.benchmarks:var:2000000" />
    <sql>[sql.value]</sql>
  </sql57_object>

State

::

  N/A

Variable

::

  <local_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    comment="Capture the directory path for the PostgreSQL config file." 
    datatype="string"
    version="1">
    <regex_capture pattern="^([\\/a-zA-Z0-9_\\.\\-]+\\/)[a-zA-Z0-9_\\.\\-]+\$"> 
        <object_component
          item_field="result"
          object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1"
          record_field="variable_path" />
    </regex_capture>
  </local_variable>

  <local_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1" 
    comment="Capture the directory path for the PostgreSQL config file." 
    datatype="string"
    version="1">
    <regex_capture pattern="^[\/a-zA-Z0-9_\.\-]+\/([a-zA-Z0-9_\.\-]+)\$"> 
        <object_component
          item_field="result"
          object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1"
          record_field="variable_path" />
    </regex_capture>
  </local_variable>  

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact_title: "[ARTIFACT-TITLE]" 
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
      parameters:
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

**SQL-Unix_File_or_Directory_Permissions_v1**

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
            <ae:parameter dt="string" name="append_type">[append_type.value]</ae:parameter>
            <ae:parameter dt="string" name="pattern">[pattern.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="username">[username.value]</ae:parameter>
            <ae:parameter dt="string" name="group">[group.value]</ae:parameter>
            <ae:parameter dt="boolean" name="uread">[uread.value]</ae:parameter>
            <ae:parameter dt="boolean" name="uwrite">[uwrite.value]</ae:parameter>
            <ae:parameter dt="boolean" name="uexec">[uexec.value]</ae:parameter>
            <ae:parameter dt="boolean" name="gread">[gread.value]</ae:parameter>
            <ae:parameter dt="boolean" name="gwrite">[gwrite.value]</ae:parameter>
            <ae:parameter dt="boolean" name="gexec">[gexec.value]</ae:parameter>
            <ae:parameter dt="boolean" name="oread">[oread.value]</ae:parameter>
            <ae:parameter dt="boolean" name="owrite">[owrite.value]</ae:parameter>
            <ae:parameter dt="boolean" name="oexec">[oexec.value]</ae:parameter>
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

For ``independent.mysql_text_file_content_v1`` ``SQL-Unix_File_or_Directory_Permissions_v1`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:2000000"
      value-id="xccdf_org.cisecurity_value_jdbc.url" />
    <check-content-ref
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
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

  <textfilecontent54_object>
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2"    
    version="1">
    <path>[path.value]</path>
    <filename>[filename.value]</filename>
    <pattern
      datatype="string"
      operation="pattern match">
        [pattern.value]
    </pattern>
    <instance
      datatype="int"
      operation="equals">
        1
    </instance>
  </textfilecontent54_object> 

  <password_object>
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]3"    
    version="1">
    <username datatype="string">[username.value]</username>
  </password_object>

  <textfilecontent54_object>
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]4"    
    version="1">
    <filepath datatype="string">/etc/group</filepath>
    <pattern
      datatype="string"
      operation="pattern match">
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

  <file_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"    
    comment="[ARTIFACT-TITLE]"  
    version="1">
    <group_id 
      datatype="int" 
      var_ref="oval:org.cisecurity.benchmarks:var:1000002" />
    <user_id 
      datatype="int" 
      var_ref="oval:org.cisecurity.benchmarks:var:1000003" />
    <uread datatype="boolean">[oread.value]</uread>
    <uwrite datatype="boolean">[owrite.value]</uwrite>
    <uexec datatype="boolean">[oexec.value]</uoexec>
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
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]" 
    datatype="string"
    version="1">
    <object_component 
      item_field="result" 
      object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
      record_field="value" />
  </local_variable>

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact_title: "[ARTIFACT-TITLE]" 
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
              "name": "dir_only",
              "dt": "boolean",
              "value": "[dir_only.value]"
            }
          }
        ]
      }
    }
  }

Generated Content
~~~~~~~~~~~~~~~~~

**Txt-Unix_File_or_Directory_Permissions_v1**

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
            <ae:parameter dt="string" name="append_type">[append_type.value]</ae:parameter>
            <ae:parameter dt="string" name="pattern">[pattern.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="username">[username.value]</ae:parameter>
            <ae:parameter dt="string" name="group">[group.value]</ae:parameter>
            <ae:parameter dt="boolean" name="uread">[uread.value]</ae:parameter>
            <ae:parameter dt="boolean" name="uwrite">[uwrite.value]</ae:parameter>
            <ae:parameter dt="boolean" name="uexec">[uexec.value]</ae:parameter>
            <ae:parameter dt="boolean" name="gread">[gread.value]</ae:parameter>
            <ae:parameter dt="boolean" name="gwrite">[gwrite.value]</ae:parameter>
            <ae:parameter dt="boolean" name="gexec">[gexec.value]</ae:parameter>
            <ae:parameter dt="boolean" name="oread">[oread.value]</ae:parameter>
            <ae:parameter dt="boolean" name="owrite">[owrite.value]</ae:parameter>
            <ae:parameter dt="boolean" name="oexec">[oexec.value]</ae:parameter>
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

For ``independent.mysql_text_file_content_v1`` ``Txt-Unix_File_or_Directory_Permissions_v1`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-content-ref
      href="[BENCHMARK_TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
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

  <textfilecontent54_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    version="1">
    <path>[path.value]</path>
    <filename>[filename.value]</filename>
    <pattern
      datatype="string"
      operation="pattern match">
        [pattern.value]
    </pattern>
    <instance
      datatype="int"
      operation="equals">
        1
    </instance>
  </textfilecontent54_object>

  <password_object>
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2"    
    version="1">
    <username datatype="string">[username.value]</username>
  </password_object>

  <textfilecontent54_object>
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]3"    
    version="1">
    <filepath datatype="string">/etc/group</filepath>
    <pattern
      datatype="string"
      operation="pattern match">
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
    <uexec datatype="boolean">[oexec.value]</uoexec>
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
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1" 
    comment="[ARTIFACT-TITLE]" 
    datatype="int"
    version="1">
    <object_component 
      item_field="user_id" 
      object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2"
      record_field="variable_value" />
  </local_variable>

  <local_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2" 
    comment="[ARTIFACT-TITLE]" 
    datatype="int"
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
    artifact_title: "[ARTIFACT-TITLE]" 
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
              "name": "dir_only",
              "dt": "boolean",
              "value": "[dir_only.value]"
            }
          }
        ]
      }
    }
  }

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
            <ae:parameter dt="string" name="append_type">[append_type.value]</ae:parameter>
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

For ``independent.mysql_text_file_content_v1`` ``Txt-Unix_File_or_Directory_Permissions_v2`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-content-ref
      href="[BENCHMARK_TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
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
    <path
      datatype="string"
      operation="equals"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />    
    <filename xsi:nil="true" />
  </file_object>

  <textfilecontent54_object>
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1" 
    version="1">
    <path>[path.value]</path>
    <filename>[filename.value]</filename>
    <pattern
      datatype="string"
      operation="pattern match">
        [pattern.value]
    </pattern>
    <instance
      datatype="int"
      operation="equals">
        1
    </instance>
  </textfilecontent54_object>

  <password_object>
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2"
    version="1">
    <username datatype="string">[username.value]</username>
  </password_object>

  <textfilecontent54_object>
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]3" 
    version="1">
    <filepath datatype="string">/etc/group</filepath>
    <pattern
      datatype="string"
      operation="pattern match">
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
    <uexec datatype="boolean">[oexec.value]</uoexec>
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
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    comment="[ARTIFACT-TITLE]" 
    datatype="int"
    version="1">
    <object_component 
      item_field="subexpression" 
      object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1"
      record_field="variable_value" />
  </local_variable>

  <local_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1" 
    comment="[ARTIFACT-TITLE]" 
    datatype="int"
    version="1">
    <object_component 
      item_field="user_id" 
      object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2"
      record_field="variable_value" />
  </local_variable>

  <local_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2" 
    comment="[ARTIFACT-TITLE]" 
    datatype="int"
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
    artifact_title: "[ARTIFACT-TITLE]" 
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

Generated Content
~~~~~~~~~~~~~~~~~

**independent.txt_file_content_v1**

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
            <ae:parameter dt="string" name="append_type">[append_type.value]</ae:parameter>
            <ae:parameter dt="string" name="pattern">[pattern.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="subexpression">[subexpression.value]</ae:parameter>
            <ae:parameter dt="string" name="filepath">[filepath.value]</ae:parameter>
            <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
            <ae:parameter dt="string" name="filename">[filename.value]</ae:parameter>
            <ae:parameter dt="binary" name="pattern">[pattern.value]</ae:parameter>
            <ae:parameter dt="binary" name="instance">[instance.value]</ae:parameter>
            <ae:parameter dt="string" name="subexp_op">[subexp_op.value]</ae:parameter>
            <ae:parameter dt="string" name="inst_op">[inst_op.value]</ae:parameter>
            <ae:parameter dt="string" name="text">[text.value]</ae:parameter>
            <ae:parameter dt="string" name="text_op">[text_op.value]</ae:parameter>
          </ae:parameters>
        </ae:test>
        <ae:profiles>
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1" />
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_2" />
        </ae:profiles>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>

XCCDF
'''''

For ``independent.mysql_text_file_content_v1`` ``independent.txt_file_content_v1`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    operator="equals"
    type="string">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>


For ``independent.mysql_text_file_content_v1`` ``independent.txt_file_content_v1`` artifacts, the XCCDF check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks,[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity_value_[ARTIFACT-OVAL-ID]1_var" />
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:2000000"
      value-id="xccdf_org.cisecurity_value_jdbc.url" />
    <check-content-ref
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <textfilecontent54_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"     
    check_existence="at_least_one_exists"    
    check="all" 
    comment="[ARTIFACT-TITLE]" 
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </<textfilecontent54_test> 
  
Object

::

  <textfilecontent54_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"    
    comment="[ARTIFACT-TITLE]"  
    version="1">
    <path var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1" />
    <filename var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2" />
    <pattern 
      operation="pattern match"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2" />
    </pattern>
    <instance 
      datatype="int" 
      operation="greater than or equal">
        0
    </instance>
  </textfilecontent54_object>

  <sql57_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"    
    comment="[ARTIFACT-TITLE]"  
    version="1">
      <engine>[engine.value]</engine>
    <version>[version.value]</version>
    <connection_string 
      var_ref="oval:org.cisecurity.benchmarks:var:2000000" />
    <sql>[sql.value]</sql>
  </sql57_object>

  
State

::

  <textfilecontent54_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"     
    comment="[ARTIFACT-TITLE]"  
    version="1">
    <subexpression 
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </textfilecontent54_state>
  
Variable

::

  <external_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    comment="[ARTIFACT-TITLE]" 
    datatype="string"
    version="1" />

  <external_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1" 
    comment="[ARTIFACT-TITLE]" 
    datatype="string"
    version="1">
    <regex_capture pattern="^([\/a-zA-Z0-9_\.\-]+\/)[a-zA-Z0-9_\.\-]+\$">
      <object_component
        item_field="result"
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1"
        record_field="variable_path" />
    </regex_capture>
  </local_variable>

  <local_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2" 
    comment="Capture the directory path for the PostgreSQL config file." 
    datatype="string"
    version="1">
    <regex_capture pattern="^[\/a-zA-Z0-9_\.\-]+\/([a-zA-Z0-9_\.\-]+)\$">
      <object_component
        item_field="result"
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1"
        record_field="variable_path" />
    </regex_capture>
  </local_variable>      

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact_title: "[ARTIFACT-TITLE]" 
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
      parameters:
        - parameter: 
            name: "subexpression"
            dt: "string"
            value: "[subexpression.value]"
        - parameter: 
            name: "filepath"
            dt: "string"
            value: "[filepath.value]"
        - parameter: 
            name: "path"
            dt: "string"
            value: "[path.value]"
        - parameter: 
            name: "filename"
            dt: "string"
            value: "[filename.value]"
        - parameter: 
            name: "pattern"
            dt: "binary"
            value: "[pattern.value]"
        - parameter: 
            name: "instance"
            dt: "binary"
            value: "[instance.value]"
        - parameter: 
            name: "subexp_op"
            dt: "string"
            value: "[subexp_op.value]"
        - parameter: 
            name: "inst_op"
            dt: "string"
            value: "[inst_op.value]"
        - parameter: 
            name: "text"
            dt: "string"
            value: "[text.value]"
        - parameter: 
            name: "text_op"
            dt: "string"
            value: "[text_op.value]"

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
              "name": "subexpression",
              "dt": "string",
              "value": "[subexpression.value]"
            }
          },
          {
            "parameter": {
              "name": "filepath",
              "dt": "string",
              "value": "[filepath.value]"
            }
          },
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
              "name": "pattern",
              "dt": "binary",
              "value": "[pattern.value]"
            }
          },
          {
            "parameter": {
              "name": "instance",
              "dt": "binary",
              "value": "[instance.value]"
            }
          },
          {
            "parameter": {
              "name": "subexp_op",
              "dt": "string",
              "value": "[subexp_op.value]"
            }
          },
          {
            "parameter": {
              "name": "inst_op",
              "dt": "string",
              "value": "[inst_op.value]"
            }
          },
          {
            "parameter": {
              "name": "text",
              "dt": "string",
              "value": "[text.value]"
            }
          },
          {
            "parameter": {
              "name": "text_op",
              "dt": "string",
              "value": "[text_op.value]"
            }
          }
        ]
      }
    }
  }

Generated Content
~~~~~~~~~~~~~~~~~

**independent.txt_file_content_v2**

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
            <ae:parameter dt="string" name="append_type">[append_type.value]</ae:parameter>
            <ae:parameter dt="string" name="pattern">[pattern.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="subexpression">[subexpression.value]</ae:parameter>
            <ae:parameter dt="string" name="filepath">[filepath.value]</ae:parameter>
            <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
            <ae:parameter dt="string" name="filename">[filename.value]</ae:parameter>
            <ae:parameter dt="binary" name="pattern">[pattern.value]</ae:parameter>
            <ae:parameter dt="binary" name="instance">[instance.value]</ae:parameter>
            <ae:parameter dt="string" name="subexp_op">[subexp_op.value]</ae:parameter>
            <ae:parameter dt="string" name="inst_op">[inst_op.value]</ae:parameter>
            <ae:parameter dt="string" name="text">[text.value]</ae:parameter>
            <ae:parameter dt="string" name="text_op">[text_op.value]</ae:parameter>
            <ae:parameter dt="string" name="entity_check">[entity_check.value]</ae:parameter>            
          </ae:parameters>
        </ae:test>
        <ae:profiles>
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1" />
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_2" />
        </ae:profiles>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>

XCCDF
'''''

For ``independent.mysql_text_file_content_v1`` ``independent.txt_file_content_v2`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    operator="equals"
    type="string">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>


For ``independent.mysql_text_file_content_v1`` ``independent.txt_file_content_v2`` artifacts, the XCCDF check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks,[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity_value_[ARTIFACT-OVAL-ID]1_var" />
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:2000000"
      value-id="xccdf_org.cisecurity_value_jdbc.url" />
    <check-content-ref
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <textfilecontent54_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"     
    check_existence="at_least_one_exists"    
    check="all" 
    comment="[ARTIFACT-TITLE]" 
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </<textfilecontent54_test> 
  
Object

::

  <textfilecontent54_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"    
    comment="[ARTIFACT-TITLE]"  
    version="1">
    <path var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1" />
    <filename var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2" />
    <pattern 
      datatype="pattern match" 
      operation="string">
      [pattern.value]
    </pattern>
    <instance 
      datatype="int" 
      operation="equals">
        1
    </instance>
  </textfilecontent54_object>

  <sql57_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1"    
    comment="[ARTIFACT-TITLE]"  
    version="1">  
    <engine>[engine.value]</engine>
    <version>[version.value]</version>
    <connection_string 
      var_ref="oval:org.cisecurity.benchmarks:var:2000000" />
    <sql>[sql.value]</sql>
  </sql57_object>
  
State

::

  <textfilecontent54_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"     
    comment="[ARTIFACT-TITLE]"  
    version="1">
    <subexpression 
      entity_check="[entity_check.value]"
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </textfilecontent54_state>
  
Variable

::

  <external_variable
    comment="[ARTIFACT-TITLE]" 
    datatype="string" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    version="1" />

  <local_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1" 
    comment="Capture the directory path for the PostgreSQL config file." 
    datatype="string"
    version="1">
    <regex_capture pattern="^([\/a-zA-Z0-9_\.\-]+\/)[a-zA-Z0-9_\.\-]+\$">
      <object_component
        item_field="result"
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1"
        record_field="variable_path" />
    </regex_capture>
  </local_variable>

  <local_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2" 
    comment="Capture the directory path for the PostgreSQL config file." 
    datatype="string"
    version="1">
    <regex_capture pattern="^[\/a-zA-Z0-9_\.\-]+\/([a-zA-Z0-9_\.\-]+)\$">
      <object_component
        item_field="result"
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]1"
        record_field="variable_path" />
    </regex_capture>
  </local_variable>  

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact_title: "[ARTIFACT-TITLE]" 
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
      parameters:
        - parameter: 
            name: "subexpression"
            dt: "string"
            value: "[subexpression.value]"
        - parameter: 
            name: "filepath"
            dt: "string"
            value: "[filepath.value]"
        - parameter: 
            name: "path"
            dt: "string"
            value: "[path.value]"
        - parameter: 
            name: "filename"
            dt: "string"
            value: "[filename.value]"
        - parameter: 
            name: "pattern"
            dt: "binary"
            value: "[pattern.value]"
        - parameter: 
            name: "instance"
            dt: "binary"
            value: "[instance.value]"
        - parameter: 
            name: "subexp_op"
            dt: "string"
            value: "[subexp_op.value]"
        - parameter: 
            name: "inst_op"
            dt: "string"
            value: "[inst_op.value]"
        - parameter: 
            name: "text"
            dt: "string"
            value: "[text.value]"
        - parameter: 
            name: "text_op"
            dt: "string"
            value: "[text_op.value]"
        - parameter: 
            name: "entity_check"
            dt: "string"
            value: "[entity_check.value]"

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
              "name": "subexpression",
              "dt": "string",
              "value": "[subexpression.value]"
            }
          },
          {
            "parameter": {
              "name": "filepath",
              "dt": "string",
              "value": "[filepath.value]"
            }
          },
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
              "name": "pattern",
              "dt": "binary",
              "value": "[pattern.value]"
            }
          },
          {
            "parameter": {
              "name": "instance",
              "dt": "binary",
              "value": "[instance.value]"
            }
          },
          {
            "parameter": {
              "name": "subexp_op",
              "dt": "string",
              "value": "[subexp_op.value]"
            }
          },
          {
            "parameter": {
              "name": "inst_op",
              "dt": "string",
              "value": "[inst_op.value]"
            }
          },
          {
            "parameter": {
              "name": "text",
              "dt": "string",
              "value": "[text.value]"
            }
          },
          {
            "parameter": {
              "name": "text_op",
              "dt": "string",
              "value": "[text_op.value]"
            }
          },
          {
            "parameter": {
              "name": "entity_check",
              "dt": "string",
              "value": "[entity_check.value]"
            }
          }          
        ]
      }
    }
  }