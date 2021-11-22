Unix: Individual File Tomcat V1
===============================

Description
-----------

The Unix: Individual File Tomcat V1 test is used to check metadata
associated with UNIX files, of the sort returned by either an ls
command, stat command or stat() system call.

The file_object element is used to define either the path and
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

unix.individual_file_tomcat_v1
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+-----------------+--------+-----------------------------------------+
| Name            | Type   | Description                             |
+=================+========+=========================================+
| base_path       | string | Base component of path. Either          |
|                 |        | $CATALINA_HOME or $CATALINA_BASE.       |
+-----------------+--------+-----------------------------------------+
| path            | string | Directory component of the absolute     |
|                 |        | path to the file after $CATALINA_HOME   |
|                 |        | or $CATALINA_BASE.                      |
+-----------------+--------+-----------------------------------------+
| concat_path     | string | Directory component after <appname>.    |
+-----------------+--------+-----------------------------------------+
| filename        | string | Filename component of the absolute path |
|                 |        | to the file.                            |
+-----------------+--------+-----------------------------------------+
| check           | string | Defines how many collected items must   |
|                 |        | match the expected state.               |
+-----------------+--------+-----------------------------------------+
| check_existence | string | Defines how many items should be        |
|                 |        | collected. Typically set to 'at least   |
|                 |        | one'.                                   |
+-----------------+--------+-----------------------------------------+

NOTE: The ``check`` parameter is governed by a constraint allowing only the following values:
  - all
  - at least one
  - none satisfy
  - only one

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_satisfy
  - none_exist
  - only_one_exists

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Existence Test

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

existence_test
^^^^^^^^^^^^^^

===== ====== =======================
Name  Type   Description
===== ====== =======================
value string The value to be tested.
===== ====== =======================

NOTE: The ``value`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_satisfy
  - none_exist
  - only_one_exists

Generated Content
~~~~~~~~~~~~~~~~~

**existence_test**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:complex-check operator="OR">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
        <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
          <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
          <ae:title>[RECOMMENDATION-TITLE]</ae:title>
          <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="base_path">[base_path.value]</ae:parameter>
              <ae:parameter dt="string" name="path">[path.value]</ae:parameter>
              <ae:parameter dt="string" name="concat_path">[concat_path.value]</ae:parameter>
              <ae:parameter dt="string" name="filename">[filename.value]</ae:parameter>
              <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
              <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
            </ae:parameters>
          </ae:test>
          <ae:profiles>
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1"/>
          </ae:profiles>
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  </xccdf:complex-check>

SCAP
^^^^

XCCDF
'''''

For ``unix.individual_file_tomcat_v1`` artifacts, an XCCDF Value element
is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" 
    operator="[operator.value]" 
    type="[type.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``unix.individual_file_tomcat_v1`` artifacts, the xccdf:check looks
like this.

::

  <xccdf:complex-check operator="OR">
    <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
      <check-export 
        export-name="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" 
        value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
      <check-content-ref 
        href="CIS_AlmaLinux_OS_8_Benchmark_v1.0.0-oval.xml" 
        name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
    </check>
  </xccdf:complex-check>

OVAL
''''

Test

::

  <file_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]" 
    check="[check.value]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </file_test>

Object

CATALINA_HOME

::

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" 
    comment="\$CATALINA_HOME file object" 
    version="1">
    <behaviors 
      max_depth="1" 
      recurse="directories" 
      recurse_direction="down" />
    <path var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]1" />
    <filename xsi:nil="true" />
  </file_object>

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]" 
    version="1">
    <path var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]2" />
    <filename>[filename.value]</filename>
  </file_object>

CATALINA_BASE

::

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]3" 
    comment="\$CATALINA_BASE file object" 
    version="1">
    <behaviors 
      max_depth="1" 
      recurse="directories" 
      recurse_direction="down" />
    <path var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]" />
    <filename xsi:nil="true" />
  </file_object>

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]" 
    version="1">
    <path var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]3" />
    <filename>[filename.value]</filename>
  </file_object>

State

::

  N/A

Variable

::

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1"
    datatype="string"
    comment="\$CATALINA_BASE directory"
    version="1">
    <concat>
      <end 
        character="/">
        <variable_component
          var_ref="oval:org.cisecurity.benchmarks:var:[ARTIFACT-OVAL-ID]1" />
      </end>
      <literal_component>
        [literal_component.value]
      </literal_component>
    </concat>
  </local_variable>

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]3"
    datatype="string"
    comment="\$CATALINA_HOME directory"
    version="1">
    <concat>
      <end 
        character="/">
        <object_component
          object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]3" 
          item_field="path" />
      </end>
      <literal_component>
        [literal_component.value]
      </literal_component>
    </concat>
  </local_variable>

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
          name: "base_path
          dt: "string"
          value: "[base_path.value]"
        - parameter:
          name: "path"
          dt: "string"
          value: "[path.value]"
        - parameter:
          name: "concat_path"
          dt: "string"
          value: "concat_path.value]"
        - parameter:
          name: "filename"
          dt: "string"
          value: "[filename.value]"
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
      "artifact-title": "[RECOMMENDATION-TITLE]",
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
              "name": "check",
              "type": "string",
              "value": "[check.value]"
            }
          },
          {
            "parameter": {
              "name": "check_existence",
              "type": "string",
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
              "type": "string",
              "value": "[value.value]"
            }
          }
        ]
      }
    }
  }
