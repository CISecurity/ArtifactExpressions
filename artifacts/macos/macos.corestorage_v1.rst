macos:corestorage
=================

Description
-----------

The macos:corestorage test is used to check the properties of the plist-style XML output from the "diskutil cs list -plist" command, for reading information about the CoreStorage setup on MacOSX.

The corestorage_object element consists of a uuid entity that contains the UUID of the volume whose information should be read (i.e., 'diskutil cs info -plist [UUID]'). The resulting plist data can be queried using the xpath entity.

The corestorage_state element defines a value used to evaluate the result of a specific corestorage_object item.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

macos.corestorage_v1
^^^^^^^^^^^^^^^^^^^^

+-----------------------------+--------+---------------------------------------+
| Name                        | Type   | Description                           |
+=============================+========+=======================================+
| uuid                        | string | Specifies the UUID of the volume      |
|                             |        | about which the plist information     |
|                             |        | should be retrieved. Cannot be blank. |
+-----------------------------+--------+---------------------------------------+
| xpath                       | string | Specifies an Xpath expression         |
|                             |        | describing the text node(s) or        |
|                             |        | attribute(s) to look at. Any valid    |
|                             |        | Xpath 1.0 statement is usable with    |
|                             |        | one exception, at most one field may  |
|                             |        | be identified in the Xpath. This is   |
|                             |        | because the value_of element in the   |
|                             |        | data section is only designed to work |
|                             |        | against a single field. The only      |
|                             |        | valid operator for xpath is equals    |
|                             |        | since there is an infinite number of  |
|                             |        | possible xpaths and determinining all |
|                             |        | those that do not equal a given xpath |
|                             |        | would be impossible. Cannot be blank. |
+-----------------------------+--------+---------------------------------------+
| check_existence             | string | Defines how many items should be      |
|                             |        | collected.                            |
+-----------------------------+--------+---------------------------------------+

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_satisfy
  - none_exist
  - only_one_exists

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - macos:corestorage

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

macos.corestorage_v1
^^^^^^^^^^^^^^^^^^^^

+-----------------------------+--------+---------------------------------------+
| Name                        | Type   | Description                           |
+=============================+========+=======================================+
| check                       | string | Defines how many collecteditems must  |
|                             |        | match the expected state.             |
+-----------------------------+--------+---------------------------------------+
| operation                   | string | Comparison operation                  |
+-----------------------------+--------+---------------------------------------+
| datatype                    | string | The data type of the value            |
+-----------------------------+--------+---------------------------------------+
| value_of                    | string | The value_of element checks the       |
|                             |        | value(s) of the text node(s) or       |
|                             |        | attribute(s) found. Cannot be blank.  |
+-----------------------------+--------+---------------------------------------+

NOTE: The ``check`` parameter is governed by a constraint allowing only the following values:
  - all
  - at least one
  - none satisfy
  - only one

NOTE: The ``operation`` parameter is governed by a constraint allowing only the following values:
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

NOTE: The ``datatype`` parameter is governed by a constraint allowing only the following values:
  - boolean
  - float
  - int
  - string
  - version
  - set

Generated Content
~~~~~~~~~~~~~~~~~

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
        <xccdf:check-content>
            <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
            <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
            <ae:title>[RECOMMENDATION-TITLE]</ae:title>
            <ae:artifact type="[ARTIFACT-TYPE-NAME]">
                <ae:parameters>
                <ae:parameter dt="string" name="uuid">[uuid.value]</ae:parameter>
                <ae:parameter dt="string" name="xpath">[xpath.value]</ae:parameter>
                <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
                </ae:parameters>
            </ae:artifact>
            <ae:test type="[TEST-TYPE-NAME]">
                <ae:parameters>
                <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
                <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
                <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
                <ae:parameter dt="string" name="value_of">[value_of.value]</ae:parameter>
                </ae:parameters>
            </ae:test>
            <ae:profiles>
                <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1"/>
            </ae:profiles>
            </ae:artifact_expression>
        </xccdf:check-content>
    </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``macos.corestorage_v1`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

::

    <xccdf:check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
        <xccdf:check-content-ref
            href="[BENCHMARK-NAME]"
            name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
    </xccdf:check>

OVAL
''''

Test

::

    <corestorage_test 
        xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#Linux"
        check="[check.value]"    
        check_existence="[check_existence.value]"
        comment="[RECOMMENDATION-TITLE]"
        id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
        version="1">
        <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
        <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
    </corestorage_test>

Object

::

    <corestorage_object 
        xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#Linux"
        comment="[RECOMMENDATION-TITLE]"
        id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"    
        version="1">
        <uuid>[uuid.value]</uuid>
        <xpath>[xpath.value]</xpath>
    </corestorage_object>

State

::

    <corestorage_state 
        xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#Linux"
        comment="[RECOMMENDATION-TITLE]"
        id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"    
        version="1">
        <value_of 
            datatype="string" 
            operation="equals">
            [value_of.value]
        </value_of>
    </corestorage_state>

YAML
^^^^

::

  - artifact-expression:
     artifact-unique-id: "[ARTIFACT-OVAL-ID]"
     artifact-title: "[RECOMMENDATION-TITLE]"
     artifact:
       type: "[ARTIFACT-TYPE-NAME]"
       parameters:
         - parameter: 
             name: "uuid"
             dt: "string"
             value: "[uuid.value]"
         - parameter: 
             name: xpath
             dt: "string"
             value: "[xpath.value]" 
         - parameter:
             name: "check_existence"
             dt: "string"
             value: "[check_existence.value]"             
     test:
       type: "[TEST-TYPE-NAME]"
       parameters:

         - parameter: 
             name: "check"
             dt: "string"
             value: "[check.value]"
         - parameter:
             name: "operation"
             dt: "string"
             value: "[operation.value]"
         - parameter: 
             name: "datatype"
             dt: "string"
             value: "[datatype.value]"
         - parameter: 
             name: "value_of"
             dt: "string"
             value: "[value_of.value]"

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
                            "name": "uuid",
                            "dt": "string",
                            "value": "[uuid.value]"
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
                            "name": "check",
                            "type": "string",
                            "value": "[check.value]"
                        }
                    },
                    {
                        "parameter": {
                            "name": "operation",
                            "type": "string",
                            "value": "[operation.value]"
                        }
                    },
                    {
                        "parameter": {
                            "name": "datatype",
                            "type": "string",
                            "value": "[datatype.value]"
                        }
                    },
                    {
                        "parameter": {
                            "name": "value_of",
                            "type": "string",
                            "value": "[value_of.value]"
                        }
                    }
                ]
            }
        }
    }
