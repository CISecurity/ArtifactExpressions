Independent: XML File Content Tomcat v1
=======================================

Description
-----------

The Independent: XML File Content Tomcat v1 test element is used to explore the contents of an xml file. This test allows specific pieces of an xml document specified using xpath to be tested.

The xmlfilecontent_object element is used by a xml file content test to define the specific piece of an xml file(s) to be evaluated. The xmlfilecontent_object will only collect regular files on UNIX systems and FILE_TYPE_DISK files on Windows systems. 

The set of files to be evaluated may be identified with either a complete filepath or a path and filename. Only one of these options may be selected.

It is important to note that the 'max_depth' and 'recurse_direction' attributes of the 'behaviors' element do not apply to the 'filepath' element, only to the 'path' and 'filename' elements. This is because the 'filepath' element represents an absolute path to a particular file and it is not possible to recurse over a file.

The xmlfilecontent_state element contains entities that are used to check the file path and name, as well as the xpath used and the value of the this xpath.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**independent.xmlfilecontent_tomcat_v1**

+------------------------+---------+-----------------------------------------+
| Name                   | Type    | Description                             |
+========================+=========+=========================================+
| base_path              | string  | Base component of path (either          |
|                        |         | $CATALINA_HOME or $CATALINA_BASE).      |
+------------------------+---------+-----------------------------------------+
| path                   | string  | Directory component of the absolute     |
|                        |         | path to the file after $CATALINA_HOME   |
|                        |         | or $CATALINA_BASE.                      |
+------------------------+---------+-----------------------------------------+
| concat_path            | string  | Directory component after <appname>     |
|                        |         | (Yes/No).                               |
+------------------------+---------+-----------------------------------------+
| filename               | string  | Filename component of the absolute path |
|                        |         | to the file.                            |
+------------------------+---------+-----------------------------------------+
| recurse                | string  | Should subdirectories be recursed       |
|                        |         | through. (Yes/No)                       |
+------------------------+---------+-----------------------------------------+
| max_depth              | binary  | Max depth for recursion. -1 for         |
|                        |         | unlimited recursion.                    |
+------------------------+---------+-----------------------------------------+
| file_system            | string  | Filesystem limitation for recursion.    |
|                        |         | All filesystems, restrict to local      |
|                        |         | only, or restrict to filesystem defined |
|                        |         | by Path.                                |
+------------------------+---------+-----------------------------------------+
| xpath                  | string  | Specifies an XPath 1.0 expression to    |
|                        |         | evaluate against the XML file specified |
|                        |         | by the filename entity. This XPath 1.0  |
|                        |         | expression must evaluate to a list of   |
|                        |         | zero or more text values which will be  |
|                        |         | accessible in OVAL via instances of     |
|                        |         | the value_of entity. Any results from   |
|                        |         | evaluating the XPath 1.0 expression     |
|                        |         | other than a list of text strings       |
|                        |         | (e.g., a nodes set) is considered an    |
|                        |         | error. The intention is that the text   |
|                        |         | values be drawn from instances of a     |
|                        |         | single, uniquely named element or       |
|                        |         | attribute. However, an OVAL             |
|                        |         | interpreter is not required to verify   |
|                        |         | this, so  the author should define the  |
|                        |         | XPath expression carefully.             |
+------------------------+---------+-----------------------------------------+
| check_existence        | string  | Defines how many items should be        |
|                        |         | collected.                              |
+------------------------+---------+-----------------------------------------+
| check                  | string  | Defines how many collected items must   |
|                        |         | match the expected state.               |
+------------------------+---------+-----------------------------------------+

NOTE: The ``file_system`` parameter is governed by a constraint allowing only the following values:
  - NA
  - local
  - all
  - defined

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values: 
  - all_exist 
  - any_exist 
  - at_least_one_exists 
  - none_exist 
  - only_one_exists

NOTE: The ``check`` parameter is governed by a constraint allowing only the following values:
  - all
  - at least one
  - none satisfy
  - only one

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Pattern Match
  - Pattern Not Match
  - Existence Test
  - Independent: XML File Content_v2

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

===== ====== ==============
Name  Type   Description
===== ====== ==============
value string Value to test.
===== ====== ==============

**independent.xmlfilecontent_v2**

+------------------------+---------+-----------------------------------------+
| Name                   | Type    | Description                             |
+========================+=========+=========================================+
| xpath                  | string  | Specifies an XPath 1.0 expression to    |
|                        |         | evaluate against the XML file specified |
|                        |         | by the filename entity. This XPath 1.0  |
|                        |         | expression must evaluate to a list of   |
|                        |         | zero or more text values which will be  |
|                        |         | accessible in OVAL via instances of the |
|                        |         | value_of entity. Any results from       |
|                        |         | evaluating the XPath 1.0 expression     |
|                        |         | other than a list of text strings       |
|                        |         | (e.g., a nodes set) is considered an    |
|                        |         | error. The intention is that the text   |
|                        |         | values be drawn from instances of a     |
|                        |         | single, uniquely named element or       |
|                        |         | attribute. However, an OVAL interpreter |
|                        |         | is not required to verify this, so the  |
|                        |         | author should define the XPath          |
|                        |         | expression carefully.                   |
+------------------------+---------+-----------------------------------------+
| filepath               | string  | This specifies the absolute path for a  |
|                        |         | file on the machine. A directory cannot |
|                        |         | be specified as a filepath.             |
+------------------------+---------+-----------------------------------------+
| path                   | string  | This specifies the directory component  |
|                        |         | of the absolute path to a file on the   |
|                        |         | machine.                                |
+------------------------+---------+-----------------------------------------+
| filename               | string  | This represents the name of a file.     |
+------------------------+---------+-----------------------------------------+
| value_of               | string  | The value_of element checks the         |
|                        |         | value(s) of the text node(s) or         |
|                        |         | attribute(s) found.                     |
+------------------------+---------+-----------------------------------------+
| valueof_op             | string  | This specifies what operation to        |
|                        |         | perform on value of.                    |
+------------------------+---------+-----------------------------------------+

NOTE: The ``valueof_op`` parameter is governed by a constraint allowing only the following values:
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

For ``independent.xmlfile_content_tomcat_v1`` ``pattern match`` and ``pattern not match`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]4_var"
    type="[type.value]"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``independent.xmlfile_content_tomcat_v1`` ``pattern match`` and ``pattern not match`` artifacts, the XCCDF check looks like this. 

- CATALINA_HOME

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:4000000"
      value-id="xccdf_org.cisecurity_value_tomcat.home" />
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]1_var" />      
    <check-content-ref
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

- CATALINA_BASE

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:4000001"
      value-id="xccdf_org.cisecurity_value_tomcat.base" />
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]1_var" />      
    <check-content-ref
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <xmlfilecontent_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"     
    check_existence="[check_existence]"    
    check="[check.value]" 
    comment="[ARTIFACT-TITLE]" 
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </textfilecontent54_test>

Object

::

  <xmlfilecontent_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"    
    comment="[ARTIFACT-TITLE]"  
    version="1">
    <behaviors
      recurse_direction="down"
      recurse_file_system="[recurse_file_system.value]"
      max_depth="[max_depth.value]" />
    <path var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1">
    <filename>[filename.value]</filename>
    <xpath
    <xpath>[path.value]</path>
  </xmlfilecontent_object>

- CATALINA_HOME

::

  <file_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2"    
    comment="$CATALINA_HOME file object"  
    version="1">
    <behaviors
      max_depth="1"    
      recurse="directories"
      recurse_direction="down" />
    <path var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1" />
    <filename xsi:nil="true" />
  </file_object>

- CATALINA_BASE

::

  <file_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]3"    
    comment="$CATALINA_BASE file object"  
    version="1">
    <behaviors
      max_depth="1"    
      recurse="directories"
      recurse_direction="down" />
    <path var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1" />
    <filename xsi:nil="true" />
  </file_object>

State  

::

  <textfilecontent54_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[ARTIFACT-TITLE]" 
    version="1">
    <text
      operation="pattern match"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </textfilecontent54_state>

Variable

::

  <external_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1" 
    comment="[ARTIFACT-TITLE]" 
    datatype="[datatype.value]"
    version="1" />

- CATALINA_HOME

::

  <local_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1" 
    comment="$CATALINA_HOME directory" 
    datatype="string"
    version="1">
    <concat
      <end character="/">
        <variable_component var_ref="oval:org.cisecurity.benchmarks:var:4000000">
      </end>  
      <literal_component>[literal_component.value]</literal_component>
    </concat>
  </local_variable>

  <local_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2" 
    comment="$CATALINA_HOME directory" 
    datatype="string"
    version="1">
    <concat
      <end character="/">
        <object_component 
          object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2"
          item_field="path" />
      </end>  
      <literal_component>[literal_component.value]</literal_component>
    </concat>
  </local_variable>

- CATALINA_BASE

::

   <local_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1" 
    comment="$CATALINA_BASE directory" 
    datatype="string"
    version="1">
    <concat
      <end character="/">
        <variable_component var_ref="oval:org.cisecurity.benchmarks:var:4000001">
      </end>  
      <literal_component>[literal_component.value]</literal_component>
    </concat>
  </local_variable>

  <local_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]3" 
    comment="$CATALINA_BASE directory" 
    datatype="string"
    version="1">
    <concat
      <end character="/">
        <object_component 
          object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]3"
          item_field="path" />
      </end>  
      <literal_component>[literal_component.value]</literal_component>
    </concat>
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
              "type": "string",
              "value": "file_system.value]"
            }
          },
          {
            "parameter": {
              "name": "xpath",
              "type": "string",
              "value": "[xpath.value]"
            }
          },
          {
            "parameter": {
              "name": "check_existence",
              "type": "string",
              "value": "[check_existence.value]"
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

For ``independent.xmlfilecontent_tomcat_v1`` ``existence_test`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this artifact.

- CATALINA_HOME

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:4000000" 
      value-id="xccdf_org.cisecurity_value_tomcat.home" />
    <check-content-ref
      href="[BENCHMARK-TITLE]-oval.xml" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

- CATALINA_BASE

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:4000001" 
      value-id="xccdf_org.cisecurity_value_tomcat.base" />
    <check-content-ref
      href="[BENCHMARK-TITLE]-oval.xml" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <xmlfilecontent_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </xmlfilecontent_test>

Object

::

  <xmlfilecontent_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <behaviors
      recurse_direction="down" />
      recurse_file_system="[recurse_file_system.value]"
      max_depth="[max_depth.value]"
    <path var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ID]1" />
    <filename>[filename.value]</<filename>
    <xpath>[xpath.value]</xpath>
  </xmlfilecontent_object>

- CATALINA_HOME

::

  <file_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2"
    comment="$CATALINA_HOME file object"
    version="1">
    <behaviors
      max_depth="1"
      recurse="directories"
      recurse_direction="down" />
    <path
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1" />
    <filename xsi:nil="true" />
  </file_object>

- CATALINA_BASE

::

  <file_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]3"
    comment="$CATALINA_BASE file object"
    version="1">
    <behaviors
      max_depth="1"
      recurse="directories"
      recurse_direction="down" />
    <path
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1" />
    <filename xsi:nil="true" />
  </file_object>

State

::

  N/A

Variable

- CATALINA_HOME

::

  <local_variable
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1"
    comment="$CATALINA_HOME directory"
    datatype="string"
    version="1">
    <concat
      <end character="/">
        <variable_component var_ref="oval:org.cisecurity.benchmarks:var:4000000" />
      </end>  
      <literal_component>[literal_component.value]</literal_component>
    </concat>
  </local_variable>

  <local_variable
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2"
    comment="$CATALINA_HOME directory"
    datatype="string"
    version="1">
    <concat
      <end character="/">
        <object_component 
          object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2"
          item_field="path" />
      </end>  
      <literal_component>[literal_component.value]</literal_component>
    </concat>
  </local_variable>

- CATALINA_BASE

::

  <local_variable
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1"
    comment="$CATALINA_BASE directory"
    datatype="string"
    version="1">
    <concat
      <end character="/">
        <variable_component var_ref="oval:org.cisecurity.benchmarks:var:4000001" />
      </end>  
      <literal_component>[literal_component.value]</literal_component>
    </concat>
  </local_variable>

  <local_variable
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]3"
    comment="$CATALINA_BASE directory"
    datatype="string"
    version="1">
    <concat
      <end character="/">
        <object_component 
          object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]3"
          item_field="path" />
      </end>  
      <literal_component>[literal_component.value]</literal_component>
    </concat>
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
              "type": "string",
              "value": "file_system.value]"
            }
          },
          {
            "parameter": {
              "name": "xpath",
              "type": "string",
              "value": "[xpath.value]"
            }
          },
          {
            "parameter": {
              "name": "check_existence",
              "type": "string",
              "value": "[check_existence.value]"
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
              "name": "value",
              "type": "string",
              "value": "[value.value]"
            }
          }
        ]
      }
    }
  }

Generated Content
~~~~~~~~~~~~~~~~~

**independent.xmlfilecontent_v2**

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
            <ae:parameter dt="string" name="file_system">[file_system.value]</ae:parameter>
            <ae:parameter dt="string" name="xpath">[xpath.value]</ae:parameter>
            <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="xpath">[xpath.value]</ae:parameter>
            <ae:parameter dt="string" name="filepath">[filepath.value]</ae:parameter>
            <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
            <ae:parameter dt="string" name="filename">[filename.value]</ae:parameter>
            <ae:parameter dt="string" name="value_of">[value_of.value]</ae:parameter>
            <ae:parameter dt="string" name="valueof_op">[valueof_op.value]</ae:parameter>
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

For ``independent.xmlfile_content_tomcat_v1`` ``independent.xmlfilecontent_v2`` artifacts, an XCCDF Value element is generated.

::

  <Value
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]1_var"
    type="string"
    operator="equals">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>


For ``independent.xmlfile_content_tomcat_v1`` ``independent.xmlfilecontent_v2`` artifacts, the XCCDF check looks like this.

- CATALINA_HOME

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:4000000" 
      value-id="xccdf_org.cisecurity_value_tomcat.home" />
    <check-export
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]1_var" />
    <check-content-ref
      href="[BENCHMARK-TITLE]-oval.xml" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

- CATALINA_BASE

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:4000001" 
      value-id="xccdf_org.cisecurity_value_tomcat.base" />
    <check-export
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]1_var" />
    <check-content-ref
      href="[BENCHMARK-TITLE]-oval.xml" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <xmlfilecontent_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </xmlfilecontent_test>

Object

::

  <xmlfilecontent_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <behaviors
      recurse_direction="down" />
      recurse_file_system="[recurse_file_system.value]"
      max_depth="[max_depth.value]"
    <path var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ID]1" />
    <filename>[filename.value]</<filename>
    <xpath>[xpath.value]</xpath>
  </xmlfilecontent_object>

- CATALINA_HOME

::

  <file_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2"
    comment="$CATALINA_HOME file object"
    version="1">
    <behaviors
      max_depth="1"
      recurse="directories"
      recurse_direction="down" />
    <path var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1" />
    <filename xsi:nil="true" />
  </file_object>

- CATALINA_BASE

::

  <file_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]3"
    comment="$CATALINA_BASE file object"
    version="1">
    <behaviors
      max_depth="1"
      recurse="directories"
      recurse_direction="down" />
    <path var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1" />
    <filename xsi:nil="true" />
  </file_object>

State

::

  <xmlfilecontent_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <value_of
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />

Variable

::

  <external_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    datatype="string"
    version="1" />

- CATALINA_HOME

::

  <local_variable
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1"
    comment="$CATALINA_HOME directory"
    datatype="string"
    version="1">
    <concat
      <end character="/">
        <variable_component var_ref="oval:org.cisecurity.benchmarks:var:4000000" />
      </end>  
      <literal_component>[literal_component.value]</literal_component>
    </concat>
  </local_variable>

  <local_variable
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2"
    comment="$CATALINA_HOME directory"
    datatype="string"
    version="1">
    <concat
      <end character="/">
        <object_component 
          object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2"
          item_field="path" />
      </end>  
      <literal_component>[literal_component.value]</literal_component>
    </concat>
  </local_variable>

- CATALINA_BASE

::

  <local_variable
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1"
    comment="$CATALINA_BASE directory"
    version="1">
    <concat
      <end character="/">
        <variable_component var_ref="oval:org.cisecurity.benchmarks:var:4000001" />
      </end>  
      <literal_component>[literal_component.value]</literal_component>
    </concat>
  </local_variable>

  <local_variable
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]3"
    comment="$CATALINA_BASE directory"
    version="1">
    <concat
      <end character="/">
        <object_component 
          object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]3"
          item_field="path" />
      </end>  
      <literal_component>[literal_component.value]</literal_component>
    </concat>
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
            dt: "string"
            value: "[value_of.value]"
        - parameter:
            name: "valueof_op"
            dt: "string"
            value: "[valueof_op.value]"

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
              "type": "string",
              "value": "file_system.value]"
            }
          },
          {
            "parameter": {
              "name": "xpath",
              "type": "string",
              "value": "[xpath.value]"
            }
          },
          {
            "parameter": {
              "name": "check_existence",
              "type": "string",
              "value": "[check_existence.value]"
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
              "name": "xpath",
              "type": "string",
              "value": "[xpath.value]"
            }
          },
          {
            "parameter": {
              "name": "filepath",
              "type": "string",
              "value": "[filepath.value]"
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
              "name": "value_of",
              "type": "string",
              "value": "[value_of.value]"
            }
          },
          {
            "parameter": {
              "name": "valueof_op",
              "type": "string",
              "value": "[valueof_op.value]"
            }
          }
        ]
      }
    }
  }