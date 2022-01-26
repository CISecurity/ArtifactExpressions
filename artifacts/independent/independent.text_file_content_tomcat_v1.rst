independent.text_file_content_tomcat_v1
=======================================

Description
-----------

The independent.text_file_content_tomcat_v1 is used to check the
contents of a text file (aka a configuration file) by looking at
individual blocks of text.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| base_path                           | string      | Base component   |
|                                     |             | of path either   |
|                                     |             | $CATALINA_HOME   |
|                                     |             | or               |
|                                     |             | $CATALINA_BASE.  |
+-------------------------------------+-------------+------------------+
| path                                | string      | Directory        |
|                                     |             | component of the |
|                                     |             | absolute path to |
|                                     |             | the file after   |
|                                     |             | $CATALINA_HOME   |
|                                     |             | or               |
|                                     |             | $CATALINA_BASE.  |
+-------------------------------------+-------------+------------------+
| concat_path                         | string      | Directory        |
|                                     |             | component after  |
|                                     |             | <appname>.       |
+-------------------------------------+-------------+------------------+
| filename                            | string      | Filename         |
|                                     |             | component of the |
|                                     |             | absolute path to |
|                                     |             | the file.        |
+-------------------------------------+-------------+------------------+
| recurse                             | string      | Should           |
|                                     |             | subdirectories   |
|                                     |             | be recursed      |
|                                     |             | through.         |
+-------------------------------------+-------------+------------------+
| max_depth                           | binary      | Max depth for    |
|                                     |             | recursion. -1    |
|                                     |             | for unlimited    |
|                                     |             | recursion        |
+-------------------------------------+-------------+------------------+
| file_system                         | string      | Filesystem       |
|                                     |             | limitation for   |
|                                     |             | recursion. All   |
|                                     |             | filesystems,     |
|                                     |             | restrict to      |
|                                     |             | local only, or   |
|                                     |             | restrict to      |
|                                     |             | filesystem       |
|                                     |             | defined by Path. |
+-------------------------------------+-------------+------------------+
| pattern                             | string      | This defines a   |
|                                     |             | chunk of text in |
|                                     |             | a file and is    |
|                                     |             | represented      |
|                                     |             | using a regular  |
|                                     |             | expression. A    |
|                                     |             | subexpression    |
|                                     |             | (using           |
|                                     |             | parentheses) can |
|                                     |             | call out a piece |
|                                     |             | of the text      |
|                                     |             | block to test.   |
|                                     |             | Must be a valid  |
|                                     |             | expression       |
|                                     |             | according to     |
|                                     |             | Perl 5's regular |
|                                     |             | expression       |
|                                     |             | specification.   |
+-------------------------------------+-------------+------------------+
| check                               | string      | Defines how many |
|                                     |             | collected items  |
|                                     |             | must match the   |
|                                     |             | expected state.  |
+-------------------------------------+-------------+------------------+

check NOTE: This parameter is governed by a constraint allowing only the
following values:
  - all
  - at least one
  - none satisfy
  - only one

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - pattern match
  - pattern not match
  - existence_test
  - unix.file_permissions_v1
  - Txt-Unix_File_or_Directory_Permissions_v1
  - Txt-Unix_File_or_Directory_Permissions_v2
  - independent.txt_file_content_v1
  - independent.txt_file_content_v2

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

pattern match 
~~~~~~~~~~~~~

+-------------------+---------+----------------------------------------+
| Name              | Type    | Description                            |
+===================+=========+========================================+
| value             | string  | Regular expression to be matched.      |
+-------------------+---------+----------------------------------------+
| data_type         | string  | Data type.                             |
+-------------------+---------+----------------------------------------+

data_type NOTE: This parameter is governed by a constraint allowing only the 
following values:
  - boolean
  - float
  - int
  - string
  - version
  - set 

pattern not match
~~~~~~~~~~~~~~~~~

+-------------------+---------+----------------------------------------+
| Name              | Type    | Description                            |
+===================+=========+========================================+
| value             | string  | Regular expression not to be matched.  |
+-------------------+---------+----------------------------------------+
| data_type         | string  | Data type.                             |
+-------------------+---------+----------------------------------------+

data_type NOTE: This parameter is governed by a constraint allowing only the 
following values:
  - boolean
  - float
  - int
  - string
  - version
  - set 

existence_test
~~~~~~~~~~~~~~

+-------------------+---------+----------------------------------------+
| Name              | Type    | Description                            |
+===================+=========+========================================+
| value             | string  | Value to test.                         |
+-------------------+---------+----------------------------------------+

unix.file_permissions_v1
~~~~~~~~~~~~~~~~~~~~~~~~

+-------------------+---------+----------------------------------------+
| Name              | Type    | Description                            |
+===================+=========+========================================+
| uread             | string  | Can the owner read the file?           |
+-------------------+---------+----------------------------------------+
| uwrite            | string  | Can the owner write the file?          |
+-------------------+---------+----------------------------------------+
| uexec             | string  | Can the owner execute the file?        |
+-------------------+---------+----------------------------------------+
| gread             | string  | Can the group read the file?           |
+-------------------+---------+----------------------------------------+
| gwrite            | string  | Can the group write the file?          |
+-------------------+---------+----------------------------------------+
| gexec             | string  | Can the group execute the file?        |
+-------------------+---------+----------------------------------------+
| oread             | string  | Can the world read the file?           |
+-------------------+---------+----------------------------------------+
| owrite            | string  | Can the world write the file?          |
+-------------------+---------+----------------------------------------+
| oexec             | string  | Can the world execute the file?        |
+-------------------+---------+----------------------------------------+
| suid              | string  | Can the file execute as the owner?     |
+-------------------+---------+----------------------------------------+
| sgid              | string  | Can the file execute as the group?     |
+-------------------+---------+----------------------------------------+
| sticky            | string  | Is the sticky bit set?                 |
+-------------------+---------+----------------------------------------+

NOTE: These parameters are governed by a constraint allowing only the 
following values: 
  - NA
  - set
  - unset

Txt-Unix_File_or_Directory_Permissions_v1
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| username                            | string      | The name of the  |
|                                     |             | user that owns   |
|                                     |             | the file or      |
|                                     |             | directory.       |
+-------------------------------------+-------------+------------------+
| group                               | string      | The name of the  |
|                                     |             | group that owns  |
|                                     |             | the file or      |
|                                     |             | directory.       |
+-------------------------------------+-------------+------------------+
| uread                               | boolean     | Determines       |
|                                     |             | whether the user |
|                                     |             | that owns the    |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | read the         |
|                                     |             | contents of it.  |
+-------------------------------------+-------------+------------------+
| uwrite                              | boolean     | Determines       |
|                                     |             | whether the user |
|                                     |             | that owns the    |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | write to it.     |
+-------------------------------------+-------------+------------------+
| uexec                               | boolean     | Determines       |
|                                     |             | whether the user |
|                                     |             | that owns the    |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | execute the file |
|                                     |             | or change into   |
|                                     |             | the directory.   |
+-------------------------------------+-------------+------------------+
| gread                               | boolean     | Determines       |
|                                     |             | whether the      |
|                                     |             | group that owns  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | read the content |
|                                     |             | of it.           |
+-------------------------------------+-------------+------------------+
| gwrite                              | boolean     | Determines       |
|                                     |             | whether the      |
|                                     |             | group that owns  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | write to it.     |
+-------------------------------------+-------------+------------------+
| gexec                               | boolean     | Determines       |
|                                     |             | whether the      |
|                                     |             | group that owns  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | execute the file |
|                                     |             | or change into   |
|                                     |             | the directory.   |
+-------------------------------------+-------------+------------------+
| oread                               | boolean     | Determines       |
|                                     |             | whether other    |
|                                     |             | users/groups     |
|                                     |             | that do not own  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | are permitted to |
|                                     |             | read the         |
|                                     |             | contents of it.  |
+-------------------------------------+-------------+------------------+
| owrite                              | boolean     | Determines       |
|                                     |             | whether other    |
|                                     |             | users/groups     |
|                                     |             | that do not own  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | are permitted to |
|                                     |             | write to it.     |
+-------------------------------------+-------------+------------------+
| oexec                               | boolean     | Determines       |
|                                     |             | whether other    |
|                                     |             | users/groups     |
|                                     |             | that do not own  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | are permitted to |
|                                     |             | execute the file |
|                                     |             | or change into   |
|                                     |             | the directory.   |
+-------------------------------------+-------------+------------------+
| dir_only                            | boolean     | If this is       |
|                                     |             | checking a       |
|                                     |             | directory        |
|                                     |             | permissions and  |
|                                     |             | no file within a |
|                                     |             | directory then   |
|                                     |             | this should be   |
|                                     |             | set to true.     |
+-------------------------------------+-------------+------------------+

Txt-Unix_File_or_Directory_Permissions_v2
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| username                            | string      | The name of the  |
|                                     |             | user that owns   |
|                                     |             | the file or      |
|                                     |             | directory.       |
+-------------------------------------+-------------+------------------+
| group                               | string      | The name of the  |
|                                     |             | group that owns  |
|                                     |             | the file or      |
|                                     |             | directory.       |
+-------------------------------------+-------------+------------------+
| uread                               | string      | Determines       |
|                                     |             | whether the user |
|                                     |             | that owns the    |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | read the         |
|                                     |             | contents of it.  |
+-------------------------------------+-------------+------------------+
| uwrite                              | string      | Determines       |
|                                     |             | whether the user |
|                                     |             | that owns the    |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | write to it.     |
+-------------------------------------+-------------+------------------+
| uexec                               | string      | Determines       |
|                                     |             | whether the user |
|                                     |             | that owns the    |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | execute the file |
|                                     |             | or change into   |
|                                     |             | the directory.   |
+-------------------------------------+-------------+------------------+
| gread                               | string      | Determines       |
|                                     |             | whether the      |
|                                     |             | group that owns  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | read the content |
|                                     |             | of it.           |
+-------------------------------------+-------------+------------------+
| gwrite                              | string      | Determines       |
|                                     |             | whether the      |
|                                     |             | group that owns  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | write to it.     |
+-------------------------------------+-------------+------------------+
| gexec                               | string      | Determines       |
|                                     |             | whether the      |
|                                     |             | group that owns  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | is permitted to  |
|                                     |             | execute the file |
|                                     |             | or change into   |
|                                     |             | the directory.   |
+-------------------------------------+-------------+------------------+
| oread                               | string      | Determines       |
|                                     |             | whether other    |
|                                     |             | users/groups     |
|                                     |             | that do not own  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | are permitted to |
|                                     |             | read the         |
|                                     |             | contents of it.  |
+-------------------------------------+-------------+------------------+
| owrite                              | string      | Determines       |
|                                     |             | whether other    |
|                                     |             | users/groups     |
|                                     |             | that do not own  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | are permitted to |
|                                     |             | write to it.     |
+-------------------------------------+-------------+------------------+
| oexec                               | string      | Determines       |
|                                     |             | whether other    |
|                                     |             | users/groups     |
|                                     |             | that do not own  |
|                                     |             | the              |
|                                     |             | file/directory   |
|                                     |             | are permitted to |
|                                     |             | execute the file |
|                                     |             | or change into   |
|                                     |             | the directory.   |
+-------------------------------------+-------------+------------------+
| dir_only                            | boolean     | If this is       |
|                                     |             | checking a       |
|                                     |             | directory        |
|                                     |             | permissions and  |
|                                     |             | no file within a |
|                                     |             | directory then   |
|                                     |             | this should be   |
|                                     |             | set to true.     |
+-------------------------------------+-------------+------------------+

independent.txt_file_content_v1
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| subexpression                       | string      | This represents  |
|                                     |             | a value to test  |
|                                     |             | against the      |
|                                     |             | subexpression in |
|                                     |             | the specified    |
|                                     |             | pattern. If      |
|                                     |             | multiple         |
|                                     |             | subexpressions   |
|                                     |             | are specified in |
|                                     |             | the pattern,     |
|                                     |             | this value is    |
|                                     |             | tested against   |
|                                     |             | all of them.     |
+-------------------------------------+-------------+------------------+
| filepath                            | string      | This specifies   |
|                                     |             | the absolute     |
|                                     |             | path for a file  |
|                                     |             | on the machine.  |
|                                     |             | A directory      |
|                                     |             | cannot be        |
|                                     |             | specified as a   |
|                                     |             | filepath.        |
+-------------------------------------+-------------+------------------+
| path                                | string      | This specifies   |
|                                     |             | the directory    |
|                                     |             | component of the |
|                                     |             | absolute path to |
|                                     |             | a file on the    |
|                                     |             | machine.         |
+-------------------------------------+-------------+------------------+
| filename                            | string      | This represents  |
|                                     |             | the name of a    |
|                                     |             | file.            |
+-------------------------------------+-------------+------------------+
| pattern                             | binary      | This represents  |
|                                     |             | a regular        |
|                                     |             | expression that  |
|                                     |             | is used to       |
|                                     |             | define a block   |
|                                     |             | of text.         |
+-------------------------------------+-------------+------------------+
| instance                            | binary      | This calls out a |
|                                     |             | specific match   |
|                                     |             | of the pattern.  |
|                                     |             | This can only be |
|                                     |             | a positive       |
|                                     |             | integer or blank.|
+-------------------------------------+-------------+------------------+
| subexp_op                           | string      | This specifies   |
|                                     |             | what operation   |
|                                     |             | to perform on    |
|                                     |             | the              |
|                                     |             | subexpression.   |
+-------------------------------------+-------------+------------------+
| inst_op                             | string      | This specifies   |
|                                     |             | what operation to|
|                                     |             | perform on the   |
|                                     |             | instance.        |
+-------------------------------------+-------------+------------------+
| text                                | string      | This represents  |
|                                     |             | the block of     |
|                                     |             | text that        |
|                                     |             | matched the      |
|                                     |             | specified        |
|                                     |             | pattern.         |
+-------------------------------------+-------------+------------------+
| text_op                             | string      | This specifies   |
|                                     |             | what operation   |
|                                     |             | to perform on    |
|                                     |             | the text.        |
+-------------------------------------+-------------+------------------+

subexp_op, inst_op, text_op NOTE: These parameters are governed by a constraint 
allowing only the following values: 
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

independent.txt_file_content_v2
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| subexpression                       | string      | This represents  |
|                                     |             | a value to test  |
|                                     |             | against the      |
|                                     |             | subexpression in |
|                                     |             | the specified    |
|                                     |             | pattern. If      |
|                                     |             | multiple         |
|                                     |             | subexpressions   |
|                                     |             | are specified in |
|                                     |             | the pattern,     |
|                                     |             | this value is    |
|                                     |             | tested against   |
|                                     |             | all of them.     |
+-------------------------------------+-------------+------------------+
| filepath                            | string      | This specifies   |
|                                     |             | the absolute     |
|                                     |             | path for a file  |
|                                     |             | on the machine.  |
|                                     |             | A directory      |
|                                     |             | cannot be        |
|                                     |             | specified as a   |
|                                     |             | filepath.        |
+-------------------------------------+-------------+------------------+
| path                                | string      | This specifies   |
|                                     |             | the directory    |
|                                     |             | component of the |
|                                     |             | absolute path to |
|                                     |             | a file on the    |
|                                     |             | machine.         |
+-------------------------------------+-------------+------------------+
| filename                            | string      | This represents  |
|                                     |             | the name of a    |
|                                     |             | file.            |
+-------------------------------------+-------------+------------------+
| pattern                             | binary      | This represents  |
|                                     |             | a regular        |
|                                     |             | expression that  |
|                                     |             | is used to       |
|                                     |             | define a block   |
|                                     |             | of text.         |
+-------------------------------------+-------------+------------------+
| instance                            | binary      | This calls out a |
|                                     |             | specific match   |
|                                     |             | of the pattern.  |
|                                     |             | This can only be |
|                                     |             | a positive       |
|                                     |             | integer or blank.|
+-------------------------------------+-------------+------------------+
| subexp_op                           | string      | This specifies   |
|                                     |             | what operation   |
|                                     |             | to perform on    |
|                                     |             | the              |
|                                     |             | subexpression.   |
+-------------------------------------+-------------+------------------+
| inst_op                             | string      | This specifies   |
|                                     |             | what operation to|
|                                     |             | perform on the   |
|                                     |             | instance.        |
+-------------------------------------+-------------+------------------+
| text                                | string      | This represents  |
|                                     |             | the block of     |
|                                     |             | text that        |
|                                     |             | matched the      |
|                                     |             | specified        |
|                                     |             | pattern.         |
+-------------------------------------+-------------+------------------+
| text_op                             | string      | This specifies   |
|                                     |             | what operation   |
|                                     |             | to perform on    |
|                                     |             | the text.        |
+-------------------------------------+-------------+------------------+
| entity_check                        | string      | evaluate to true |
|                                     |             | for the entity   |
|                                     |             | check            |
+-------------------------------------+-------------+------------------+

subexp_op, inst_op, text_op NOTE: These parameters are governed by a constraint 
allowing only the following values: 
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

entity_check NOTE: This parameter is governed by a constraint 
allowing only the following values:
  - all
  - at least one
  - none satisfy
  - only one

Generated Content
~~~~~~~~~~~~~~~~~

| pattern match
| pattern not match

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
            <ae:parameter dt="string" name="base_path">[base_path.value]</ae:parameter>
            <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
            <ae:parameter dt="string" name="concat_path">[concat_path.value]</ae:parameter>
            <ae:parameter dt="string" name="filename">[filename.value]</ae:parameter>
            <ae:parameter dt="string" name="recurse">[recurse.value]</ae:parameter>
            <ae:parameter dt="binary" name="max_depth">[max_depth.value]</ae:parameter>
            <ae:parameter dt="string" name="file_system">[pfile_systemath.value]</ae:parameter>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
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

For ``pattern match`` or ``pattern not match`` artifacts, the xccdf:check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-content-ref 
      href="[BENCHMARK_TITLE]" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>


OVAL
''''

Test

::

  <textfilecontent54_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    check="[check.value]" 
    check_existence="[check_existence.value]" 
    comment="[ARTIFACT-TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </textfilecontent54_test>

Object

::

  <textfilecontent54_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    comment="[ARTIFACT-TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    version="1">
    <path var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <filename>[filename.value]</filename>
    <pattern 
      operation="[operation.value]">
      [pattern.value]
    </pattern>
    <instance 
      datatype="[datatype.value]" 
      operation="[operation.value]">
      [instance.value]
    </instance>
  </textfilecontent54_object>

State

::

  <textfilecontent54_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[ARTIFACT-TITLE]" 
    version=|"[version.value]">
    <subexpression 
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </textfilecontent54_state>

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
            name: "base_path"
            dt: "string"
            value: "[base_path.value]"
        - parameter:
            name: "path"
            dt: "string"
            value: "[path.value]"
        - parameter:
            name: "concat_path"
            dt: "string"
            value: "[concat_path.value]"          
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
            name: "xpath"
            dt: "string"
            value: "[xpath.value]"
        - parameter:
            name: "check_existence"
            dt: "string"
            value: "[check_existence.value]"          
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
              "name": "base_path",
              "type": "string",
              "value": "[base_path.value]"
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
              "name": "concat_path",
              "type": "string",
              "value": "[concat_path.value]"
            }
          },                    
          {
            "parameter": {
              "name": "filename",
              "type": "string",
              "value": "[filename.value]"
            }
          {
            "parameter": {
              "name": "check_existence",
              "dt": "string",
              "value": "[check_existence.value]"
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
              "name": "xpath",
              "dt": "string",
              "value": "[xpath.value]"
            }
          },
          {
            "parameter": {
              "name": "check",
              "dt": "string",
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

existence_test

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
            <ae:parameter dt="string" name="base_path">[base_path.value]</ae:parameter>
            <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
            <ae:parameter dt="string" name="concat_path">[concat_path.value]</ae:parameter>
            <ae:parameter dt="string" name="filename">[filename.value]</ae:parameter>
            <ae:parameter dt="string" name="file_system">[pfile_systemath.value]</ae:parameter>
            <ae:parameter dt="string" name="check">[pacheckth.value]</ae:parameter>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
          </ae:parameters>
        </ae:test>
        <ae:profiles>
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_2" />
        </ae:profiles>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``existence_test`` artifacts, the xccdf:check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity_value_[PLATFORM_ID]" />
    <check-content-ref 
      href="[BENCHMARK_TITLE]" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <textfilecontent54_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    check="[check.value]" 
    check_existence="[check_existence.value]" 
    comment="[ARTIFACT-TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </textfilecontent54_test> 

Object

::

  <textfilecontent54_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    comment="[ARTIFACT-TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    version="1">
    <path var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" />
    <filename>[filename.value]</filename>
    <pattern operation="[operation.value]">
      [pattern.value]
    </pattern>
    <instance 
      datatype="[datatype.value]" 
      operation="[operation.value]">
      [instance.value]
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
    artifact-title: "[ARTIFACT-TITLE]"
    artifact:
      type: "[ARTIFACT-TYPE-NAME]"
      parameters:
        - parameter:
            name: "base_path"
            dt: "string"
            value: "[base_path.value]"
        - parameter:
            name: "path"
            dt: "string"
            value: "[path.value]"
        - parameter:
            name: "concat_path"
            dt: "string"
            value: "[concat_path.value]"          
        - parameter:
            name: "filename"
            dt: "string"
            value: "[filename.value]"
        - parameter:
            name: "file_system"
            dt: "string"
            value: "[file_system.value]"          
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
              "name": "base_path",
              "type": "string",
              "value": "[base_path.value]"
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
              "name": "concat_path",
              "type": "string",
              "value": "[concat_path.value]"
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
              "name": "file_system",
              "dt": "string",
              "value": "[file_system.value]"
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

unix.file_permissions_v1

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
            <ae:parameter dt="string" name="base_path">[base_path.value]</ae:parameter>
            <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
            <ae:parameter dt="string" name="concat_path">[concat_path.value]</ae:parameter>
            <ae:parameter dt="string" name="filename">[filename.value]</ae:parameter>
            <ae:parameter dt="string" name="recurse">[recurse.value]</ae:parameter>
            <ae:parameter dt="binary" name="max_depth">[max_depth.value]</ae:parameter>
            <ae:parameter dt="string" name="file_system">[pfile_systemath.value]</ae:parameter>
            <ae:parameter dt="string" name="check">[pacheckth.value]</ae:parameter>
            <ae:parameter dt="string" name="pattern">[pattern.value]</ae:parameter>
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

SCAP
^^^^

XCCDF
'''''

For ``unix.file_permissions_v1`` artifacts, the xccdf:check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-content-ref 
      href="[BENCHMARK_TITLE]" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
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
    <path>[path.value]</path>
    <filename>[filename.value]</filename>
  </file_object>

State

::

  <file_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    comment="[ARTIFACT-TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    version="1">
    <gread datatype="boolean">[gread.value]</gread>
    <gwrite datatype="boolean">[gwrite.value]</gwrite>
    <gexec datatype="boolean">[gexec.value]</gexec>
    <oread datatype="boolean">[oread.value]</oread>
    <owrite datatype="boolean">[owrite.value]</owrite>
    <oexec datatype="boolean">[oexec.value]</oexec>
  </file_state>

Variable

::

<external_variable 
  comment="[ARTIFACT-TITLE]"    
  datatype="[datatype.value]" 
  id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
  "[version.value]" />

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
            name: "base_path"
            dt: "string"
            value: "[base_path.value]"
        - parameter:
            name: "path"
            dt: "string"
            value: "[path.value]"
        - parameter:
            name: "concat_path"
            dt: "string"
            value: "[concat_path.value]"          
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
            name: "xpath"
            dt: "string"
            value: "[xpath.value]"
        - parameter:
            name: "check_existence"
            dt: "string"
            value: "[check_existence.value]"          
        - parameter:
            name: "check"
            dt: "string"
            value: "[check.value]"                
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
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
      "artifact-title": "[ARTIFACT-TITLE]",
      "artifact": {
        "type": "[ARTIFACT-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "base_path",
              "type": "string",
              "value": "[base_path.value]"
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
              "name": "concat_path",
              "type": "string",
              "value": "[concat_path.value]"
            }
          },                    
          {
            "parameter": {
              "name": "filename",
              "type": "string",
              "value": "[filename.value]"
            }
          {
            "parameter": {
              "name": "check_existence",
              "dt": "string",
              "value": "[check_existence.value]"
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
              "name": "xpath",
              "dt": "string",
              "value": "[xpath.value]"
            }
          },
          {
            "parameter": {
              "name": "check",
              "dt": "string",
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

Generated Content
~~~~~~~~~~~~~~~~~

Txt-Unix_File_or_Directory_Permissions_v1

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
            <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
            <ae:parameter dt="string" name="filename">[filename.value]</ae:parameter>
            <ae:parameter dt="string" name="recurse">[recurse.value]</ae:parameter>
            <ae:parameter dt="binary" name="max_depth">[max_depth.value]</ae:parameter>
            <ae:parameter dt="string" name="file_system">[pfile_systemath.value]</ae:parameter>
            <ae:parameter dt="string" name="pattern">[pattern.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="Txt-Unix_File_or_Directory_Permissions_v1">
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
          <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_2" />
        </ae:profiles>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``Txt-Unix_File_or_Directory_Permissions_v1`` artifacts, the xccdf:check 
looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity_value_[ARTIFACT-OVAL-ID]_var " />
    <check-content-ref 
      href="[BENCHMARK_TITLE]" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <textfilecontent54_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    check="[check.value]" 
    check_existence="[check_existence.value]" 
    comment="[ARTIFACT-TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </textfilecontent54_test> 

Object

::

  <textfilecontent54_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    comment="[ARTIFACT-TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    version="1">
    <path var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" />
    <filename>[filename.value]</filename>
    <pattern operation="[operation.value]>[pattern.value]</pattern>
    <instance 
      datatype="int" 
      operation="[operation.value]">
      [instance.value]
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
    artifact-title: "[ARTIFACT-TITLE]"
    artifact:
      type: "[ARTIFACT-TYPE-NAME]"
      parameters:
        - parameter:
            name: "base_path"
            dt: "string"
            value: "[base_path.value]"
        - parameter:
            name: "path"
            dt: "string"
            value: "[path.value]"
        - parameter:
            name: "concat_path"
            dt: "string"
            value: "[concat_path.value]"          
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
            name: "check"
            dt: "string"
            value: "[check.value]"
        - parameter:
            name: "pattern"
            dt: "string"
            value: "[pattern.value]"          
    test:
      type: "existence_test"
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
              "name": "base_path",
              "type": "string",
              "value": "[base_path.value]"
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
              "name": "concat_path",
              "type": "string",
              "value": "[concat_path.value]"
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
              "name": "check",
              "dt": "string",
              "value": "[check.value]"
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
        "type": "existence_test",
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

Txt-Unix_File_or_Directory_Permissions_v2

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
            <ae:parameter dt="string" name="base_path">[base_path.value]</ae:parameter>
            <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
            <ae:parameter dt="string" name="concat_path">[concat_path.value]</ae:parameter>
            <ae:parameter dt="string" name="filename">[filename.value]</ae:parameter>
            <ae:parameter dt="string" name="recurse">[recurse.value]</ae:parameter>
            <ae:parameter dt="binary" name="max_depth">[max_depth.value]</ae:parameter>
            <ae:parameter dt="string" name="file_system">[pfile_systemath.value]</ae:parameter>
            <ae:parameter dt="string" name="check">[pacheckth.value]</ae:parameter>
            <ae:parameter dt="string" name="pattern">[pattern.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="Txt-Unix_File_or_Directory_Permissions_v2">
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
        </ae:profiles>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``Txt-Unix_File_or_Directory_Permissions_v2`` artifacts, the xccdf:check looks like this.

::

  <check system='http://oval.mitre.org/XMLSchema/oval-definitions-5'>
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity_value_[ARTIFACT-OVAL-ID]_var " />
    <check-content-ref 
      href="[BENCHMARK-TITLE]" 
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
    <path var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <filepath xsi:nil="[xsi:nil.value]" />
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
    <gwrite datatype="[datatype.value]">[gwrite.value]</gwrite>
    <oread datatype="[datatype.value]">[oread.value]</oread>
    <owrite datatype="[datatype.value]">[owrite.value]</owrite>
    <oexec datatype="[datatype.value]">[oexec.value]</oexec>
  </file_state>

Variable

::

  <local_variable 
    comment="[ARTIFACT-TITLE]" 
    datatype="[datatype.value]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    version="1">
    <end character="[character.value]">
      <variable_component var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    </end>
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
            name: "base_path"
            dt: "string"
            value: "[base_path.value]"
        - parameter:
            name: "path"
            dt: "string"
            value: "[path.value]"
        - parameter:
            name: "concat_path"
            dt: "string"
            value: "[concat_path.value]"          
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
            name: "check"
            dt: "string"
            value: "[check.value]"
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
              "name": "base_path",
              "type": "string",
              "value": "[base_path.value]"
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
              "name": "concat_path",
              "type": "string",
              "value": "[concat_path.value]"
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
              "name": "check",
              "dt": "string",
              "value": "[check.value]"
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

independent.txt_file_content_v1

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
            <ae:parameter dt="string" name="base_path">[base_path.value]</ae:parameter>
            <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
            <ae:parameter dt="string" name="concat_path">[concat_path.value]</ae:parameter>
            <ae:parameter dt="string" name="filename">[filename.value]</ae:parameter>
            <ae:parameter dt="string" name="recurse">[recurse.value]</ae:parameter>
            <ae:parameter dt="binary" name="max_depth">[max_depth.value]</ae:parameter>
            <ae:parameter dt="string" name="file_system">[pfile_systemath.value]</ae:parameter>
            <ae:parameter dt="string" name="check">[pacheckth.value]</ae:parameter>
            <ae:parameter dt="string" name="pattern">[pattern.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="independent.txt_file_content_v1">
          <ae:parameters>
            <ae:parameter dt="string" name="subexpression">[subexpression.value]</ae:parameter>
            <ae:parameter dt="string" name="filepath">[filepath.value]</ae:parameter>
            <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
            <ae:parameter dt="string" name="filename">[filename.value]</ae:parameter>
            <ae:parameter dt="string" name="pattern">[pattern.value]</ae:parameter>
            <ae:parameter dt="string" name="instance">[instance.value]</ae:parameter>
            <ae:parameter dt="string" name="subexp_op">[subexp_op.value]</ae:parameter>
            <ae:parameter dt="string" name="inst_op">[inst_op.value]</ae:parameter>
            <ae:parameter dt="string" name="text">[text.value]</ae:parameter>
            <ae:parameter dt="string" name="text_op">[text_op.value]</ae:parameter>
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

For ``independent.txt_file_content_v1`` artifacts, the xccdf:check looks like this.

::

  <check system='http://oval.mitre.org/XMLSchema/oval-definitions-5'>
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity_value_[ARTIFACT-OVAL-ID]_var" />
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity_value_[ARTIFACT-OVAL-ID]_var " />      
    <check-content-ref 
      href="[BENCHMARK-TITLE]" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]">
    </check-content-ref>
  </check>

OVAL
''''

Test

::

  <textfilecontent54_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    check="[check.value]" 
    check_existence="[check_existence.value]" 
    comment="[ARTIFACT-TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </textfilecontent54_test>

Object

::

  <textfilecontent54_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    comment="[ARTIFACT-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    version="1">
    <path var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <filename>[filename.value]</filename>
    <pattern operation="[operation.value]">[pattern.value]</pattern>
    <instance 
      datatype="int" 
      operation="[operation.value]">
      [instance.value]
    </instance>
  </textfilecontent54_object>

State

::

  <textfilecontent54_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]"
    comment="[ARTIFACT-TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    version="1">
    <subexpression 
      operation="[operation.value]" 
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </textfilecontent54_state>

Variable

::

  <external_variable 
    comment="[ARTIFACT-TITLE]" 
    datatype="[datatype.value]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
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
        - parameter:
            name: "base_path"
            dt: "string"
            value: "[base_path.value]"
        - parameter:
            name: "path"
            dt: "string"
            value: "[path.value]"
        - parameter:
            name: "concat_path"
            dt: "string"
            value: "[concat_path.value]"          
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
            name: "check"
            dt: "string"
            value: "[check.value]"
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
              "name": "base_path",
              "type": "string",
              "value": "[base_path.value]"
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
              "name": "concat_path",
              "type": "string",
              "value": "[concat_path.value]"
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
                "name": "check",
                "dt": "string",
                "value": "[check.value]"
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

independent.txt_file_content_v2

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
            <ae:parameter dt="string" name="base_path">[base_path.value]</ae:parameter>
            <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
            <ae:parameter dt="string" name="concat_path">[concat_path.value]</ae:parameter>
            <ae:parameter dt="string" name="filename">[filename.value]</ae:parameter>
            <ae:parameter dt="string" name="recurse">[recurse.value]</ae:parameter>
            <ae:parameter dt="binary" name="max_depth">[max_depth.value]</ae:parameter>
            <ae:parameter dt="string" name="file_system">[pfile_systemath.value]</ae:parameter>
            <ae:parameter dt="string" name="check">[pacheckth.value]</ae:parameter>
            <ae:parameter dt="string" name="pattern">[pattern.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="independent.txt_file_content_v2">
          <ae:parameters>
            <ae:parameter dt="string" name="subexpression">[subexpression.value]</ae:parameter>
            <ae:parameter dt="string" name="filepath">[filepath.value]</ae:parameter>
            <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
            <ae:parameter dt="string" name="filename">[filename.value]</ae:parameter>
            <ae:parameter dt="string" name="pattern">[pattern.value]</ae:parameter>
            <ae:parameter dt="string" name="instance">[instance.value]</ae:parameter>
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

For ``independent.txt_file_content_v2`` artifacts, the xccdf:check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity_value_[ARTIFACT-OVAL-ID]_var" />
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity_value_[ARTIFACT-OVAL-ID]_var " />
    <check-content-ref 
      href="[BENCHMARK_TITLE]" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <textfilecontent54_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    check="[check.value]" 
    check_existence="[check_existence.value]" 
    comment="[ARTIFACT-TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </<textfilecontent54_test> 
  
Object

::

  <textfilecontent54_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    comment="[ARTIFACT-TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    version="1">
    <path var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <filename var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <pattern 
      datatype="string" 
      operation="[operation.value]">
      [pattern.value]
    </pattern>
    <instance 
      datatype="int" 
      operation="equals">
      [instance.value]
    </instance>
  </textfilecontent54_object>
  
State

::

  <textfilecontent54_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    comment="[ARTIFACT-TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
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
  datatype="[datatype.value]" 
  id="oval:org.cisecurity.benchmarks.oracle_mysql_8:var:1777180"
  version="1" />

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact_title: "[RECOMMENDATION-TITLE]" 
    artifact:
      type: "[ARTIFACT-TYPE-NAME]"
      parameters:
        - parameter:
            name: "base_path"
            dt: "string"
            value: "[base_path.value]"
        - parameter:
            name: "path"
            dt: "string"
            value: "[path.value]"
        - parameter:
            name: "concat_path"
            dt: "string"
            value: "[concat_path.value]"
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
            name: "check"
            dt: "string"
            value: "[check.value]"
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
            "name": "base_path",
            "type": "string",
            "value": "[base_path.value]"
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
            "name": "concat_path",
            "type": "string",
            "value": "[concat_path.value]"
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
              "name": "check",
              "dt": "string",
              "value": "[check.value]"
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