independent.xmlfilecontent_tomcat_v1
====================================

Description
-----------

The independent.xmlfilecontent_tomcat_v1 is used to explore the contents
of an xml file.

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
|                                     |             | <appname>0       |
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
| xpath                               | string      | Specifies an     |
|                                     |             | XPath 1.0        |
|                                     |             | expression to    |
|                                     |             | evaluate against |
|                                     |             | the XML file     |
|                                     |             | specified by the |
|                                     |             | filename entity. |
|                                     |             | This XPath 1.0   |
|                                     |             | expression must  |
|                                     |             | evaluate to a    |
|                                     |             | list of zero or  |
|                                     |             | more text values |
|                                     |             | which will be    |
|                                     |             | accessible in    |
|                                     |             | OVAL via         |
|                                     |             | instances of the |
|                                     |             | value_of entity. |
|                                     |             | Any results from |
|                                     |             | evaluating the   |
|                                     |             | XPath 1.0        |
|                                     |             | expression other |
|                                     |             | than a list of   |
|                                     |             | text strings     |
|                                     |             | (e.g., a nodes   |
|                                     |             | set) is          |
|                                     |             | considered an    |
|                                     |             | error. The       |
|                                     |             | intention is     |
|                                     |             | that the text    |
|                                     |             | values be drawn  |
|                                     |             | from instances   |
|                                     |             | of a single,     |
|                                     |             | uniquely named   |
|                                     |             | element or       |
|                                     |             | attribute.       |
|                                     |             | However, an OVAL |
|                                     |             | interpreter is   |
|                                     |             | not required to  |
|                                     |             | verify this, so  |
|                                     |             | the author       |
|                                     |             | should define    |
|                                     |             | the XPath        |
|                                     |             | expression       |
|                                     |             | carefully.       |
+-------------------------------------+-------------+------------------+
| check_existence                     | string      | Defines how many |
|                                     |             | items should be  |
|                                     |             | collected.       |
+-------------------------------------+-------------+------------------+
| check                               | string      | Defines how many |
|                                     |             | collected items  |
|                                     |             | must match the   |
|                                     |             | expected state.  |
+-------------------------------------+-------------+------------------+

check_existence NOTE: This parameter is governed by a constraint
allowing only the following values: 
  - all_exist 
  - any_exist 
  - at_least_one_exists 
  - none_satisfy 
  - none_exist 
  - only_one_exists

check NOTE: This parameter is governed by a constraint allowing only the
following values:
  - all
  - at least one
  - none satisfy
  - only one

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Txt-Unix_File_or_Directory_Permissions_v2
  - existence_test
  - independent.xmlfilecontent_v2

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

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

existence_test
^^^^^^^^^^^^^^

===== ====== ==============
Name  Type   Description
===== ====== ==============
value String Value to test.
===== ====== ==============

independent.xmlfilecontent_v2
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| xpath                               | string      | Specifies an     |
|                                     |             | XPath 1.0        |
|                                     |             | expression to    |
|                                     |             | evaluate against |
|                                     |             | the XML file     |
|                                     |             | specified by the |
|                                     |             | filename entity. |
|                                     |             | This XPath 1.0   |
|                                     |             | expression must  |
|                                     |             | evaluate to a    |
|                                     |             | list of zero or  |
|                                     |             | more text values |
|                                     |             | which will be    |
|                                     |             | accessible in    |
|                                     |             | OVAL via         |
|                                     |             | instances of the |
|                                     |             | value_of entity. |
|                                     |             | Any results from |
|                                     |             | evaluating the   |
|                                     |             | XPath 1.0        |
|                                     |             | expression other |
|                                     |             | than a list of   |
|                                     |             | text strings     |
|                                     |             | (e.g., a nodes   |
|                                     |             | set) is          |
|                                     |             | considered an    |
|                                     |             | error. The       |
|                                     |             | intention is     |
|                                     |             | that the text    |
|                                     |             | values be drawn  |
|                                     |             | from instances   |
|                                     |             | of a single,     |
|                                     |             | uniquely named   |
|                                     |             | element or       |
|                                     |             | attribute.       |
|                                     |             | However, an OVAL |
|                                     |             | interpreter is   |
|                                     |             | not required to  |
|                                     |             | verify this, so  |
|                                     |             | the author       |
|                                     |             | should define    |
|                                     |             | the XPath        |
|                                     |             | expression       |
|                                     |             | carefully.       |
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
| value_of                            | string      | The value_of     |
|                                     |             | element checks   |
|                                     |             | the value(s) of  |
|                                     |             | the text node(s) |
|                                     |             | or attribute(s)  |
|                                     |             | found.           |
+-------------------------------------+-------------+------------------+
| valueof_op                          | string      | This specifies   |
|                                     |             | what operation   |
|                                     |             | to perform on    |
|                                     |             | value of.        |
+-------------------------------------+-------------+------------------+

Generated Content
~~~~~~~~~~~~~~~~~

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION_NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[RECOMMENDATION TITLE]</ae:title>
        <ae:artifact type="[ARTIFACTTYPE NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="base_path">[base_path.value]</ae:parameter>
            <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
            <ae:parameter dt="string" name="concat_path">[concat_path.value]</ae:parameter>
            <ae:parameter dt="string" name="filename">[filename.value]</ae:parameter>
            <ae:parameter dt="string" name="recurse">[recurse.value]</ae:parameter>
            <ae:parameter dt="binary" name="max_depth">[max_depth.value]</ae:parameter>
            <ae:parameter dt="string" name="file_system">[file_system.value]</ae:parameter>
            <ae:parameter dt="string" name="xpath">[xpath.value]</ae:parameter>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TESTTYPE NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
          </ae:parameters>
        </ae:test>
      </ae:artifact_expression>
    </xccdf:check-content>
  </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``independent.xmlfilecontent_tomcat_v1`` artifacts, the xccdf:check
looks like this.

::

  <check system='http://oval.mitre.org/XMLSchema/oval-definitions-5'>
    <check-export 
      export-name='oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]' 
      value-id='xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var'/>
    <check-content-ref 
      href='[BENCHMARK NAME]' 
      name='oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]'/>
  </check>

OVAL
''''

Test

::

  <xmlfilecontent_test 
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]'
    check_existence='[check_existence.value]' 
    check='[check.value]' 
    comment='[RECOMMENDATION TITLE]'
    version='[version.value]'>
    <object object_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
  </xmlfilecontent_test>

Object

::

  <xmlfilecontent_object
    xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
    id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
    comment='[RECOMMENDATION TITLE]'
    version='[version.value]'>
    <behaviors
      recurse_direction='[recurse_direction.value]'/>
      recurse_file_system='[recurse_file_system.value]'
      max_depth='[max_depth.value]'
    <path var_ref='oval:org.cisecurity.benchmarks:var:[ID]'/>
    <filename xsi:nil='[filename.value]'/>
    <xpath/>
  </xmlfilecontent_object>

State

::

  N/A

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: [ARTIFACT-OVAL-ID]
    artifact-title: [RECOMMENDATION TITLE]
    artifact:
      type: [ARTIFACTTYPE NAME]
      parameters:
      - parameter: 
          name: base_path
          type: string
          value: [base_path.value]
      - parameter: 
          name: path
          type: string
          value: [path.value]
      - parameter: 
          name: concat_path
          type: string
          value: concat_path.value]
      - parameter: 
          name: filename
          type: string
          value: [filename.value]
      - parameter: 
          name: recurse
          type: string
          value: [recurse.value]
      - parameter: 
          name: max_depth
          type: binary
          value: [max_depth.value]
      - parameter: 
          name: file_system
          type: string
          value: file_system.value]
      - parameter: 
          name: xpath
          type: string
          value: [xpath.value]
      - parameter: 
          name: check_existence
          type: string
          value: [check_existence.value]
      - parameter: 
          name: check
          type: string
          value: [check.value]
    test:
      type: [TESTTYPE NAME]
      parameters:   
      - parameter: 
          name: value
          type: string
          value: [value.value]

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": [
        "ARTIFACT-OVAL-ID"
      ],
      "artifact-title": [
        "RECOMMENDATION TITLE"
      ],
      "artifact": {
        "type": [
          "ARTIFACTTYPE NAME"
        ],
        "parameters": [
          {
            "parameter": {
              "name": "base_path",
              "type": "string",
              "value": [
                "base_path.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "path",
              "type": "string",
              "value": [
                "path.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "concat_path",
              "type": "string",
              "value": "concat_path.value]"
            }
          },
          {
            "parameter": {
              "name": "filename",
              "type": "string",
              "value": [
                "filename.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "recurse",
              "type": "string",
              "value": [
                "recurse.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "max_depth",
              "type": "binary",
              "value": [
                "max_depth.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "file_system",
              "type": "string",
              "value": "file_system.value]"
            }
          },
          {
            "parameter": {
              "name": "xpath",
              "type": "string",
              "value": [
                "xpath.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "check_existence",
              "type": "string",
              "value": [
                "check_existence.value"
              ]
            }
          },
          {
            "parameter": {
              "name": "check",
              "type": "string",
              "value": [
                "check.value"
              ]
            }
          }
        ]
      },
      "test": {
        "type": [
          "TESTTYPE NAME"
        ],
        "parameters": [
          {
            "parameter": {
              "name": "value",
              "type": "string",
              "value": [
                "value.value"
              ]
            }
          }
        ]
      }
    }
  }
