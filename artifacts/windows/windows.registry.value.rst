Windows: Registry Value
=======================

Description
-----------

The Windows: Registry Value test is used to check metadata associated with Windows registry key. 

The registry_object element is used by a registry_test to define those objects to evaluate based on a specified state. A registry_object consists of the hive the registry key belongs to, the registry key to be collected, and the name of the registry key to be evaluated.

The registry_state element defines the different metadata associate with a Windows registry key. This includes the hive, key, name, type, and value. 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**windows.registry.value**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| hive                        | string  | The hive of the target registry    |
|                             |         | key.                               |
+-----------------------------+---------+------------------------------------+
| key_operator                | string  | The operator used to qualify the   |
|                             |         | target key. This is typically      |
|                             |         | 'case_insensitive_equals'.         |
+-----------------------------+---------+------------------------------------+
| key                         | string  | The key to collect, using the      |
|                             |         | above operator.                    |
+-----------------------------+---------+------------------------------------+
| name                        | string  | The name of the registry key to    |
|                             |         | collect.                           |
+-----------------------------+---------+------------------------------------+
| check_existence             | string  | Typically set to 'at least one'.   |
|                             |         | Set to 'any exist' to pass even if |
|                             |         | the key does not exist.            |
+-----------------------------+---------+------------------------------------+
| windows_view                | string  | Typically left to 'default'. Set   |
|                             |         | to 32bit to force collecting 32bit |
|                             |         | registry on a 64bit OS.            |
+-----------------------------+---------+------------------------------------+
| registry_data_type          | string  | The type of registry value to      |
|                             |         | collect.                           |
+-----------------------------+---------+------------------------------------+

NOTE: The ``hive`` parameter is governed by a constraint allowing only the following values:
  - HKEY_LOCAL_MACHINE 
  - HKEY_USER 
  - HKEY_CURRENT_USER 
  - HKEY_CLASSES_ROOT 
  - HKEY_CURRENT_CONFIG

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_satisfy
  - none_exist
  - only_one_exists

NOTE: The ``windows_view`` parameter is governed by a constraint allowing only the following values:
  - default 
  - 32_bit 
  - 64_bit

NOTE: The ``registry_data_type`` parameter is governed by a constraint allowing only the following values:
  - reg_dword
  - reg_sz
  - reg_dword_little_endian
  - reg_dword_big_endian
  - reg_expand_sz
  - reg_multi_sz
  - reg_binary
  - reg_link
  - reg_none
  - reg_qword_little_endian

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Windows: Registry Value
  - Existence Test
  - Equal
  - Equals

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**windows.registry.value**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| operator                    | string  | The operation to perform on the    |
|                             |         | collected registry values.         |
+-----------------------------+---------+------------------------------------+
| value_data_type             | string  | The data type of the collected     |
|                             |         | value.                             |
+-----------------------------+---------+------------------------------------+
| value                       | string  | The value to compare against the   |
|                             |         | collected registry value.          |
+-----------------------------+---------+------------------------------------+
| check                       | string  | Determines how many of the         |
|                             |         | collected registry values must     |
|                             |         | satisfy the operator/value test.   |
|                             |         | Typically set to 'at least one'.   |
+-----------------------------+---------+------------------------------------+

NOTE: The ``operator`` parameter is governed by a constraint allowing only the following values:
  - bitwise and
  - bitwise or
  - case insensitive equals
  - case insensitive not equal
  - equals
  - greater than
  - greater than or equal
  - less than
  - less than or equal
  - pattern match
  - not equal
  - set white list
  - set is empty  

NOTE: The ``value_data_type`` parameter is governed by a constraint allowing only the following values:
  - boolean
  - float
  - int
  - string
  - version
  - set

NOTE: The ``check`` parameter is governed by a constraint allowing only the following values:
  - all
  - at least one
  - none satisfy
  - only one

**existence_test**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| value                       | string  | the value included within the set  |
|                             |         | of results / value to be tested.   |
+-----------------------------+---------+------------------------------------+

| **equal**
| **equals**
+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| data_type                   | string  | Datatype of the value.             |
+-----------------------------+---------+------------------------------------+
| value                       | string  | The value included within the set  |
|                             |         | of results / value to be tested.   |
+-----------------------------+---------+------------------------------------+

NOTE: The ``data_type`` parameter is governed by a constraint allowing only the following values:
  - boolean
  - float
  - int
  - string
  - version
  - set

Generated Content
~~~~~~~~~~~~~~~~~

**windows.registry.value**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:complex-check operator="AND">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
          <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
            <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
            <ae:title>[ARTIFACT-TITLE]</ae:title>
            <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="hive">[hive.value]</ae:parameter>
              <ae:parameter dt="string" name="key_operator">[key_operator.value]</ae:parameter>
              <ae:parameter dt="string" name="key">[key.value]</ae:parameter>
              <ae:parameter dt="string" name="name">[name.value]</ae:parameter>
              <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
              <ae:parameter dt="string" name="windows_view">[windows_view.value]</ae:parameter>
              <ae:parameter dt="string" name="registry_data_type">[registry_data_type.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
              <ae:parameter dt="string" name="value_data_type">[value_data_type.value]</ae:parameter>
              <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
              <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            </ae:parameters>
          </ae:test>
          <ae:profiles>
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1" />
          </ae:profiles>
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  </xccdf:complex-check>

SCAP
^^^^

XCCDF
'''''

For ``windows.registry_value_v1 windows.registry.value`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var1"
    type="string"
    operator="equals">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var2"
    type="[type.value]"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``windows.registry_value_v1 windows.registry.value`` artifacts, the xccdf:check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID1]"
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var1" />
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2"
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var2" />      
    <check-content-ref 
      href="[BENCHMARK-TITLE]"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <registry_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"	
    check_existence="[check_existence.value]"	
    check="[check.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </registry_test>

Object

::

  <registry_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <behaviors windows_view="[windows_view.value]" />
    <hive>[hive.value]</hive>
    <key operation="[operation.value]">[key.value]</key>
    <name operation="[operation.value]">[name.value]</name>
  </registry_object>

State

::

  <registry_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <type>[type.value]</type>
    <value 
      entity_check="none exist" 
      operation="pattern match">
        .+
    </value>
  </registry_state>

Variable

::

  <external_variable>
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]1"
    datatype="string"
    comment=""This value is used in Rule: [RECOMMENDATION-TITLE] for the registry data type"
    version="1" /> 

  <external_variable>
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2"
    datatype="[datatype.value]"
    comment=""This value is used in Rule: [RECOMMENDATION-TITLE] for the registry value"
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
            name: "hive"
            dt: "string"
            value: "[hive.value]"
        - parameter: 
            name: "key_operator"
            dt: "string"
            value: "[key_operator.value]"
        - parameter: 
            name: "key"
            dt: "string"
            value: "[key.value]"
        - parameter: 
              name: "name"
              dt: "string"
            value: "[name.value]"
        - parameter: 
            name: "check_existence"
            dt: "string"
            value: "[check_existence.value]"
        - parameter: 
            name: "windows_view"
            dt: "string"
            value: "[windows_view.value]"
        - parameter: 
            name: "registry_data_type"
            dt: "string"
            value: "[registry_data_type.value]"
        - parameter: 
            name: "name_operation"
            dt: "string"
            value: "[name_operation.value]"                  
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "operator"
            dt: "string"
            value: "[operator.value]"
        - parameter:
            name: "value_data_type"
            dt: "string"
            value: "[value_data_type.value]"
        - parameter:
            name: "value"
            dt: "string"
            value: "[value.value]"
        - parameter:
            name: "check"
            dt: "string"
            value: "[check.value]"       

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
              "name": "hive",
              "type": "string",
              "value": "[hive.value]"
            }
          },
          {
            "parameter": {
              "name": "key_operator",
              "type": "string",
              "value": "[key_operator.value]"
            }
          },
          {
            "parameter": {
              "name": "key",
              "type": "string",
              "value": "[key.value]"
            }
          },
          {
            "parameter": {
              "name": "name",
              "type": "string",
              "value": "[name.value]"
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
              "name": "windows_view",
              "type": "string",
              "value": "[windows_view.value]"
            }
          },
          {
            "parameter": {
              "name": "registry_data_type",
              "type": "string",
              "value": "[registry_data_type.value]"
            }
          },
          {
            "parameter": {
              "name": "operation",
              "type": "string",
              "value": "[operation.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "operator",
              "type": "string",
              "value": "[operator.value]"
            }
          },
          {
            "parameter": {
              "name": "value_data_type",
              "type": "string",
              "value": "[value_data_type.value]"
            }
          },
          {
            "parameter": {
              "name": "value",
              "type": "string",
              "value": "[value.value]"
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

  <xccdf:complex-check operator="AND">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
          <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
            <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
            <ae:title>[ARTIFACT-TITLE]</ae:title>
            <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="hive">[hive.value]</ae:parameter>
              <ae:parameter dt="string" name="key_operator">[key_operator.value]</ae:parameter>
              <ae:parameter dt="string" name="key">[key.value]</ae:parameter>
              <ae:parameter dt="string" name="name">[name.value]</ae:parameter>
              <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
              <ae:parameter dt="string" name="windows_view">[windows_view.value]</ae:parameter>
              <ae:parameter dt="string" name="registry_data_type">[registry_data_type.value]</ae:parameter>
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
  </xccdf:complex-check>

SCAP
^^^^

XCCDF
'''''

For ``windows.registry_value_v1 existence_test`` artifacts, the xccdf:check looks like this. There is no Value element in the xccdf for this Artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">    
    <check-content-ref 
      href="[BENCHMARK-TITLE]"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <registry_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"	
    check_existence="[check_existence.value]"	
    check="[check.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </registry_test>

Object

::

  <registry_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <hive>[hive.value]</hive>
    <key operation="[operation.value]">[key.value]</key>
    <name>[name.value]</name>
  </registry_object>

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
            name: "hive"
            dt: "string"
            value: "[hive.value]"
        - parameter: 
            name: "key_operator"
            dt: "string"
            value: "[key_operator.value]"
        - parameter: 
            name: "key"
            dt: "string"
            value: "[key.value]"
        - parameter: 
              name: "name"
              dt: "string"
            value: "[name.value]"
        - parameter: 
            name: "check_existence"
            dt: "string"
            value: "[check_existence.value]"
        - parameter: 
            name: "windows_view"
            dt: "string"
            value: "[windows_view.value]"
        - parameter: 
            name: "registry_data_type"
            dt: "string"
            value: "[registry_data_type.value]"
        - parameter: 
            name: "name_operation"
            dt: "string"
            value: "[name_operation.value]"                  
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
              "name": "hive",
              "type": "string",
              "value": "[hive.value]"
            }
          },
          {
            "parameter": {
              "name": "key_operator",
              "type": "string",
              "value": "[key_operator.value]"
            }
          },
          {
            "parameter": {
              "name": "key",
              "type": "string",
              "value": "[key.value]"
            }
          },
          {
            "parameter": {
              "name": "name",
              "type": "string",
              "value": "[name.value]"
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
              "name": "windows_view",
              "type": "string",
              "value": "[windows_view.value]"
            }
          },
          {
            "parameter": {
              "name": "registry_data_type",
              "type": "string",
              "value": "[registry_data_type.value]"
            }
          },
          {
            "parameter": {
              "name": "operation",
              "type": "string",
              "value": "[operation.value]"
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

| **equal**
| **equals**
XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:complex-check operator="AND">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
          <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
            <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
            <ae:title>[ARTIFACT-TITLE]</ae:title>
            <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="hive">[hive.value]</ae:parameter>
              <ae:parameter dt="string" name="key_operator">[key_operator.value]</ae:parameter>
              <ae:parameter dt="string" name="key">[key.value]</ae:parameter>
              <ae:parameter dt="string" name="name">[name.value]</ae:parameter>
              <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
              <ae:parameter dt="string" name="windows_view">[windows_view.value]</ae:parameter>
              <ae:parameter dt="string" name="registry_data_type">[registry_data_type.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="data_type">[data_type.value]</ae:parameter>
              <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
            </ae:parameters>
          </ae:test>
          <ae:profiles>
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1" />
          </ae:profiles>
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  </xccdf:complex-check>

SCAP
^^^^

XCCDF
'''''

For ``windows.registry_value_v1 equal`` or ``equals`` artifacts, the xccdf:check looks like this. There is no Value element in the xccdf for this Artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">    
    <check-content-ref 
      href="[BENCHMARK-TITLE]"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <registry_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"	
    check_existence="[check_existence.value]"	
    check="[check.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </registry_test>

Object

::

  <registry_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#windows"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <hive>[hive.value]</hive>
    <key operation="[operation.value]">[key.value]</key>
    <name>[name.value]</name>
  </registry_object>

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
            name: "hive"
            dt: "string"
            value: "[hive.value]"
        - parameter: 
            name: "key_operator"
            dt: "string"
            value: "[key_operator.value]"
        - parameter: 
            name: "key"
            dt: "string"
            value: "[key.value]"
        - parameter: 
              name: "name"
              dt: "string"
            value: "[name.value]"
        - parameter: 
            name: "check_existence"
            dt: "string"
            value: "[check_existence.value]"
        - parameter: 
            name: "windows_view"
            dt: "string"
            value: "[windows_view.value]"
        - parameter: 
            name: "registry_data_type"
            dt: "string"
            value: "[registry_data_type.value]"
        - parameter: 
            name: "name_operation"
            dt: "string"
            value: "[name_operation.value]"                  
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "data_type"
            dt: "string"
            value: "[data_type.value]"
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
              "name": "hive",
              "type": "string",
              "value": "[hive.value]"
            }
          },
          {
            "parameter": {
              "name": "key_operator",
              "type": "string",
              "value": "[key_operator.value]"
            }
          },
          {
            "parameter": {
              "name": "key",
              "type": "string",
              "value": "[key.value]"
            }
          },
          {
            "parameter": {
              "name": "name",
              "type": "string",
              "value": "[name.value]"
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
              "name": "windows_view",
              "type": "string",
              "value": "[windows_view.value]"
            }
          },
          {
            "parameter": {
              "name": "registry_data_type",
              "type": "string",
              "value": "[registry_data_type.value]"
            }
          },
          {
            "parameter": {
              "name": "operation",
              "type": "string",
              "value": "[operation.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "data_type",
              "type": "string",
              "value": "[data_type.value]"
            }
          }, 
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

