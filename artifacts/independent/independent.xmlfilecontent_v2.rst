independent.xmlfilecontent_v2
==============================

Description
-----------

The independent.xmlfilecontent_v2 is used to explore the contents of an xml 
file. This test allows specific pieces of an xml document specified using 
xpath to be tested. 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

+-------------------+---------+----------------------------------------+
| Name              | Type    | Description                            |
+===================+=========+========================================+
| path              | string  | Directory component of the absolute    |
|                   |         | path to the file. Cannot be blank.     |
+-------------------+---------+----------------------------------------+
| filename          | string  | Filename component of the absolute     |
|                   |         | path to the file.                      |
+-------------------+---------+----------------------------------------+
| recurse           | string  | Should subdirectories be recursed      |
|                   |         | through.                               |
+-------------------+---------+----------------------------------------+
| max_depth         | int     | Max depth for recursion. -1 for        |
|                   |         | unlimited recursion.                   |
+-------------------+---------+----------------------------------------+
| file_system       | string  | Filesystem limitation for recursion.   |
|                   |         | All filesystems, restrict to local     |
|                   |         | only, or restrict to filesystem        |
|                   |         | defined by Path.                       |
+-------------------+---------+----------------------------------------+
| xpath             | string  | Specifies an XPath 1.0 expression to   |
|                   |         | evaluate against the XML file          |
|                   |         | specified by the filename entity. This |
|                   |         | XPath 1.0 expression must evaluate to  |
|                   |         | a list of zero or more text values     |
|                   |         | which will be accessible in OVAL via   |
|                   |         | instances of the value_of entity. Any  |
|                   |         | results from evaluating the XPath 1.0  |
|                   |         | expression other than a list of text   |
|                   |         | strings (e.g., a nodes set) is         |
|                   |         | considered an error. The intention is  |
|                   |         | that the text values be drawn from     |
|                   |         | instances of a single, uniquely named  |
|                   |         | element or attribute. However, an OVAL |
|                   |         | interpreter is not required to verify  |
|                   |         | this, so the author should define the  |
|                   |         | XPath expression carefully.            |
+-------------------+---------+----------------------------------------+
| check_existence   | string  | Defines how many items should be       |
|                   |         | collected.                             |
+-------------------+---------+----------------------------------------+

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

check_existence NOTE: This parameter is governed by a constraint allowing
only the following values: 
  - all_exist 
  - any_exist 
  - at_least_one_exists 
  - none_satisfy 
  - none_exist 
  - only_one_exists

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - pattern match
  - pattern not match
  - existence_test
  - independent.xmlfilecontent_v2

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

independent.xmlfilecontent_v2
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+-------------------+---------+----------------------------------------+
| Name              | Type    | Description                            |
+===================+=========+========================================+
| xpath             | string  | Specifies an XPath 1.0 expression to   |
|                   |         | evaluate against the XML file          |
|                   |         | specified by the filename entity. This |
|                   |         | XPath 1.0 expression must evaluate to  |
|                   |         | a list of zero or more text values     |
|                   |         | which will be accessible in OVAL via   |
|                   |         | instances of the value_of entity. Any  |
|                   |         | results from evaluating the XPath 1.0  |
|                   |         | expression other than a list of text   |
|                   |         | strings (e.g., a nodes set) is         |
|                   |         | considered an error. The intention is  |
|                   |         | that the text values be drawn from     |
|                   |         | instances of a single, uniquely named  |
|                   |         | element or attribute. However, an OVAL |
|                   |         | interpreter is not required to verify  |
|                   |         | this, so the author should define the  |
|                   |         | XPath expression carefully.            |
+-------------------+---------+----------------------------------------+
| filepath          | string  | This specifies the absolute path for a |
|                   |         | file on the machine. A directory       |
|                   |         | cannot be specified as a filepath.     |
+-------------------+---------+----------------------------------------+
| path              | string  | This specifies the directory component |
|                   |         | of the absolute path to a file on the  |
|                   |         | machine.                               |
+-------------------+---------+----------------------------------------+
| filename          | string  | This represents the name of a file.    |
+-------------------+---------+----------------------------------------+
| value_of          | string  | The value_of element checks the        |
|                   |         | value(s) of the text node(s) or        |
|                   |         | attribute(s) found..                   |
+-------------------+---------+----------------------------------------+
| valueof_op        | string  | This specifies what operation to       |
|                   |         | perform on value of.                   |
+-------------------+---------+----------------------------------------+

Generated Content
~~~~~~~~~~~~~~~~~

pattern match
pattern not match

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION_NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[RECOMMENDATION TITLE]</ae:title>
        <ae:artifact type="[ARTIFACTTYPE NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
            <ae:parameter dt="string" name="filename">[filename.value]</ae:parameter>
            <ae:parameter dt="string" name="recurse">[recurse.value]</ae:parameter>
            <ae:parameter dt="binary" name="max_depth">[max_depth.value]</ae:parameter>
            <ae:parameter dt="string" name="file_system">[pfile_systemath.value]</ae:parameter>
            <ae:parameter dt="string" name="xpath">[xpath.value]</ae:parameter>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TESTTYPE NAME]">
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

For ``pattern match`` artifacts, the xccdf:check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
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

  <xmlfilecontent_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    check="[check.value]" 
    check_existence="[check_existence.value]" 
    comment="[RECOMMENDATION TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
    version="[version.value]">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </xmlfilecontent_test>

Object

::

  <xmlfilecontent_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    comment="[RECOMMENDATION TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    version="[version.value]">
    <path var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <filename var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <pattern 
      operation="[operation.value]">
      [pattern.value]
    </pattern>
    <instance 
      datatype="[datatype.value]" 
      operation="[operation.value]">
      [instance.value]
    </instance>
  </xmlfilecontent_object>

State

::

  <xmlfilecontent_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION TITLE]" 
    version=|"[version.value]">
    <subexpression 
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </xmlfilecontent_state>

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact-title: "[RECOMMENDATION TITLE]"
    artifact:
      type: "[ARTIFACTTYPE NAME]"
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
    test:
      type: "[TESTTYPE NAME]"
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
      "artifact-title": "[RECOMMENDATION TITLE]",
      "artifact": {
        "type": "[ARTIFACTTYPE NAME]",
        "parameters": [
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
              "name": "xpath",
              "dt": "string",
              "value": "[xpath.value]"
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
        "type": "[TESTTYPE NAME]",
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

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[RECOMMENDATION-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACTTYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
            <ae:parameter dt="string" name="filename">[filename.value]</ae:parameter>
            <ae:parameter dt="string" name="recurse">[recurse.value]</ae:parameter>
            <ae:parameter dt="binary" name="max_depth">[max_depth.value]</ae:parameter>
            <ae:parameter dt="string" name="file_system">[pfile_systemath.value]</ae:parameter>
            <ae:parameter dt="string" name="xpath">[xpath.value]</ae:parameter>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TESTTYPE-NAME]">
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

For ``existence_test`` artifacts, the xccdf:check looks like this.

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

  <xmlfilecontent_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    check="[check.value]" 
    check_existence="[check_existence.value]" 
    comment="[RECOMMENDATION-TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
    version="[version.value]">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </xmlfilecontent_test> 

Object

::

  <xmlfilecontent_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    comment="[RECOMMENDATION-TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    version="[version.value]">
    <path var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" />
    <filename xsi:nil="[xsi:nil.value]" />
    <connection_string var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" />
    <xpath>[xpath.value]</<xpath>
  </xmlfilecontent_object>

State

::

  N/A 


YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact-title: "[RECOMMENDATION TITLE]"
    artifact:
      type: "[ARTIFACTTYPE NAME]"
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
    test:
      type: "[TESTYPE-NAME]"
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
      "artifact-title": "[RECOMMENDATION TITLE]",
      "artifact": {
        "type": "[ARTIFACTTYPE NAME]",
        "parameters": [
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
              "name": "xpath",
              "dt": "string",
              "value": "[xpath.value]"
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
        "type": "[TESTYPE-NAME]",
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

independent.xmlfilecontent_v2

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION_NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[RECOMMENDATION TITLE]</ae:title>
        <ae:artifact type="[ARTIFACTTYPE NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
            <ae:parameter dt="string" name="filename">[filename.value]</ae:parameter>
            <ae:parameter dt="string" name="recurse">[recurse.value]</ae:parameter>
            <ae:parameter dt="binary" name="max_depth">[max_depth.value]</ae:parameter>
            <ae:parameter dt="string" name="file_system">[pfile_systemath.value]</ae:parameter>
            <ae:parameter dt="string" name="xpath">[xpath.value]</ae:parameter>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TESTTYPE NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="xpath">[xpath.value]</ae:parameter>
            <ae:parameter dt="string" name="filepath">[filepath.value]</ae:parameter>
            <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
            <ae:parameter dt="string" name="filename">[filename.value]</ae:parameter>
            <ae:parameter dt="binary" name="value_of">[value_of.value]</ae:parameter>
            <ae:parameter dt="binary" name="valueof_op">[valueof_op.value]</ae:parameter>
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

For ``independent.xmlfilecontent_v2`` artifacts, the xccdf:check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
    <check-content-ref 
      href="[BENCHMARK_TITLE]" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <xmlfilecontent_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    check="[check.value]" 
    check_existence="[check_existence.value]" 
    comment="[RECOMMENDATION TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
    version="[version.value]">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </xmlfilecontent_test>

Object

::

  <xmlfilecontent_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    comment="[RECOMMENDATION TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    version="[version.value]">
    <path var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <filename var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <xpath>[xpath.value]</xpath>
  </xmlfilecontent_object>

State

::

  <xmlfilecontent_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    comment="[RECOMMENDATION TITLE]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    version="[version.value]">
    <value_of 
      operation="[operation.value]" 
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </xmlfilecontent_state>

Variable
        
::

  <external_variable 
    comment="[RECOMMENDATION TITLE]" 
    datatype="[data_type.value]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    version="[version.value]" />  

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact-title: "[RECOMMENDATION TITLE]"
    artifact:
      type: "[ARTIFACTTYPE NAME]"
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
    test:
      type: "[TESTTYPE NAME]"
      parameters:   
        - parameter:
            name: "xpath"
            dt: "string"
            value: "[xpath.value]"
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
            name: "value_of"
            dt: "binary"
            value: "[value_of.value]"
        - parameter:
            name: "valueof_op"
            dt: "binary"
            value: "[valueof_op.value]"

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
      "artifact-title": "[RECOMMENDATION TITLE]",
      "artifact": {
        "type": "[ARTIFACTTYPE NAME]",
        "parameters": [       
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
              "name": "xpath",
              "dt": "string",
              "value": "[xpath.value]"
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
        "type": "[TESTTYPE NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "xpath",
              "dt": "string",
              "value": "[xpath.value]"
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
              "name": "value_of",
              "dt": "binary",
              "value": "[value_of.value]"
            }
          },
          {
            "parameter": {
              "name": "valueof_op",
              "dt": "binary",
              "value": "[valueof_op.value]"
            }
          }
        ]
      }
    }
  }
