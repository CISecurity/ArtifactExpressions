windows.registry_guid_sid_v1
=============================

Description
-----------

The windows.registry_guid_v1 is used to check metadata associated with 
Windows registry key. 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

+-------------------+---------+----------------------------------------+
| Name              | Type    | Description                            |
+===================+=========+========================================+
| guid_hive         | string  | The hive of the guid to collect.       |
+-------------------+---------+----------------------------------------+
| guid_key          | string  | The key of the guid to collect. Cannot |
|                   |         | be blank.                              |
+-------------------+---------+----------------------------------------+
| guid_key_operator | string  | The operator used to qualify the guid  |
|                   |         | key. This is typically                 |
|                   |         | 'case_insensitive_equals'. Cannot be   |
|                   |         | blank.                                 |
+-------------------+---------+----------------------------------------+
| guid_name         | string  | The name of the registry guid key to   |
|                   |         | collect. Cannot be blank.              |
+-------------------+---------+----------------------------------------+
| hive              | string  | The hive of the target registry key.   |
+-------------------+---------+----------------------------------------+
| before_guid_key   | string  | The key to collect before GUID, using  |
|                   |         | the above operator. Cannot be blank.   |
+-------------------+---------+----------------------------------------+
| after_guid_key    | string  | The key to collect, using the above    |
|                   |         | operator. Cannot be blank.             |
+-------------------+---------+----------------------------------------+
| after_sid_key     | string  | The key to collect after SID, using    |
|                   |         | the above operator. Cannot be blank.   |
+-------------------+---------+----------------------------------------+
| key_operator      | string  | The operator used to qualify the       |
|                   |         | target key. This is typically          |
|                   |         | 'case_insensitive_equals'.             |
+-------------------+---------+----------------------------------------+
| name              | string  | The name of the registry key to        |
|                   |         | collect. Cannot be blank.              |
+-------------------+---------+----------------------------------------+
| windows_view      | string  | Typically left to 'default'. Set to    |
|                   |         | 32_bit to force collecting 32bit       |
|                   |         | registry on a 64bit OS.                 |
+-------------------+---------+----------------------------------------+

guid_hive NOTE: This parameter is governed by a constraint allowing
only the following values: 
    - HKEY_LOCAL_MACHINE 
    - HKEY_USERS 
    - HKEY_CURRENT_USER 
    - HKEY_CLASSES_ROOT 
    - HKEY_CURRENT_CONFIG

guid_key_operator NOTE: This parameter is governed by a constraint allowing
only the following values: 
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

hive NOTE: This parameter is governed by a constraint allowing
only the following values: 
    - HKEY_LOCAL_MACHINE 
    - HKEY_USERS 
    - HKEY_CURRENT_USER 
    - HKEY_CLASSES_ROOT 
    - HKEY_CURRENT_CONFIG

key_operator NOTE: This parameter is governed by a constraint allowing
only the following values: 
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

windows_view NOTE: This parameter is governed by a constraint allowing
only the following values: default - 32_bit - 64_bit

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

- windows:registry_guid_sid_v1

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

windows.registry_guid_sid_v1 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+-------------------------+---------+----------------------------------+
| Name                    | Type    | Description                      |
+=========================+=========+==================================+
| existence_check         | string  | The existence check determines a |
|                         |         | required number of items to be   |
|                         |         | collected from the target        |
|                         |         | endpoint.                        |
+-------------------------+---------+----------------------------------+
| check                   | string  | The check element describes how  |
|                         |         | many collected items must match  |
|                         |         | the expected state.              |
+-------------------------+---------+----------------------------------+
| registry_type           | string  | The datatype of the collected    |
|                         |         | registry value. Cannot be blank. |
+-------------------------+---------+----------------------------------+
| registry_type_operator  | string  | The registry type operator       |
|                         |         | describes the comparison         |
|                         |         | operation for the registry       |
|                         |         | type field.                      |
+-------------------------+---------+----------------------------------+
| registry_value          | string  | The registry value. Cannot be    |
|                         |         | blank.                           |
+-------------------------+---------+----------------------------------+
| registry_value_datatype | string  | datatype.                        |
+-------------------------+---------+----------------------------------+
| registry_value_operator | string  | The registry value comparison    |
|                         |         | operation.                       |
+-------------------------+---------+----------------------------------+

existence_check NOTE: This parameter is governed by a constraint allowing only
the following values: 
  - all_exist 
  - any_exist 
  - at_least_one_exists 
  - none_satisfy 
  - none_exist 
  - only_one_exists 

check NOTE: This parameter is governed by a constraint allowing only the 
following values: all - at least one - none satisfy - only one

registry_type_operator NOTE: This parameter is governed by a constraint
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

registry_value_datatype NOTE: This parameter is governed by a constraint
allowing only the following values: 
  - boolean 
  - float 
  - int 
  - string 
  - version 
  - set

registry_value_operator NOTE: This parameter is governed by a constraint
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

Generated Content
~~~~~~~~~~~~~~~~~

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
            <ae:parameter dt="string" name="guid_hive">[guid_hive.value]</ae:parameter>
            <ae:parameter dt="string" name="guid_key">[guid_key.value]</ae:parameter>
            <ae:parameter dt="string" name="guid_key_operator">[guid_key_operator.value]</ae:parameter>
            <ae:parameter dt="string" name="guid_name">[guid_name.value]</ae:parameter>
            <ae:parameter dt="string" name="hive">[hive.value]</ae:parameter>
            <ae:parameter dt="string" name="before_guid_key">[before_guid_key.value]</ae:parameter>
            <ae:parameter dt="string" name="after_guid_key">[after_guid_key.value]</ae:parameter>
            <ae:parameter dt="string" name="after_sid_key">[after_sid_key.value]</ae:parameter>
            <ae:parameter dt="string" name="key_operator">[key_operator.value]</ae:parameter>
            <ae:parameter dt="string" name="name">[name.value]</ae:parameter>
            <ae:parameter dt="string" name="windows_view">[windows_view.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TESTTYPE NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="existence_check">[existence_check.value]</ae:parameter>
            <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
            <ae:parameter dt="string" name="registry_type">[registry_type.value]</ae:parameter>
            <ae:parameter dt="string" name="registry_type_operator">[registry_type_operator.value]</ae:parameter>
            <ae:parameter dt="string" name="registry_value">[registry_value.value]</ae:parameter>
            <ae:parameter dt="string" name="registry_value_datatype">[registry_value_datatype.value]</ae:parameter>
            <ae:parameter dt="string" name="registry_value_operator">[registry_value_operator.value]</ae:parameter>
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

For ``independent.mysql_text_file_content_v1`` artifacts, the xccdf:check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var2" />
    <check-content-ref 
      href="[BENCHMARK_TITLE]" 
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <registry_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]"
    check="[check.value]"
    check_existence="[check_existence.value]"
    comment="[RECOMMENDATION TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    version="[version.value]">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </registry_test>

Object
      

::

  <registry_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]"
    comment="[RECOMMENDATION TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    version="[version.value]">
    <hive>[hive.value]</hive>
    <key operation="[operation.value]" />
    <name>[name.value]</name>
  </registry_object>

State
     

::

  <registry_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM-ID]" 
    comment="[RECOMMENDATION TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    version="[version.value]">
    <type operation="[operation.value]">[type.value]</type>
    <value 
      datatype="[datatype.value]" 
      operation="[operation.value]" 
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </registry_state>    

YAML
^^^^

::

  - artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact-title: "[RECOMMENDATION TITLE]"
    artifact:
      type: "[ARTIFACTTYPE NAME]"
      parameters:
      - parameter:
        name: "guid_hive"
        dt: "string"
        value: "[guid_hive.value]"
      - parameter:
        name: "guid_key"
        dt: "string"
        value: "[guid_key.value]"
      - parameter:
        name: "guid_key_operator"
        dt: "string"
        value: "[guid_key_operator.value]"
      - parameter:
        name: "guid_name"
        dt: "string"
        value: "[guid_name.value]"
      - parameter:
        name: "hive"
        dt: "string"
        value: "[hive.value]"
      - parameter:
        name: "before_guid_key"
        dt: "string"
        value: "[before_guid_key.value]"
      - parameter:
        name: "after_guid_key"
        dt: "string"
        value: "[after_guid_key.value]"
      - parameter:
        name: "after_sid_key"
        dt: "string"
        value: "[after_sid_key.value]"                
      - parameter:
        name: "key_operator"
        dt: "string"
        value: "[key_operator.value]"
      - parameter:
        name: "name"
        dt: "string"
        value: "[name.value]"
      - parameter:
        name: "windows_view"
        dt: "string"
        value: "[windows_view.value]"                
    test:
      type: "[TESTTYPE NAME]"
      parameters:   
      - parameter:
        name: "existence_check"
        dt: "string"
        value: "[existence_check.value]"
      - parameter:
        name: "check"
        dt: "string"
        value: "[check.value]"
      - parameter:
        name: "registry_type"
        dt: "string"
        value: "[registry_type.value]"
      - parameter:
        name: "registry_type_operator"
        dt: "string"
        value: "[registry_type_operator.value]"
      - parameter:
        name: "registry_value"
        dt: "binary"
        value: "[registry_value.value]"
      - parameter:
        name: "registry_value_datatype"
        dt: "binary"
        value: "[registry_value_datatype.value]"
      - parameter:
        name: "registry_value_operator"
        dt: "binary"
        value: "[registry_value_operator.value]"                

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
              "name": "guid_hive",
              "type": "string",
              "value": "[guid_hive.value]"
            }
          },
          {
            "parameter": {
              "name": "guid_key",
              "type": "string",
              "value": "[guid_key.value]"
            }
          },
          {
            "parameter": {
              "name": "guid_key_operator",
              "type": "string",
              "value": "[guid_key_operator.value]"
            }
          },
          {
            "parameter": {
              "name": "guid_name",
              "type": "string",
              "value": "[guid_name.value]"
            }
          },
          {
            "parameter": {
              "name": "hive",
              "dt": "string",
              "value": "[hive.value]"
            }
          },
          {
            "parameter": {
              "name": "before_guid_key",
              "dt": "string",
              "value": "[before_guid_key.value]"
            }
          },
          {
            "parameter": {
              "name": "after_guid_key",
              "dt": "string",
              "value": "[after_guid_key.value]"
            }
          },
          {
            "parameter": {
              "name": "after_sid_key",
              "dt": "string",
              "value": "[after_sid_key.value]"
            }
          },
          {
            "parameter": {
              "name": "key_operator",
              "dt": "string",
              "value": "[key_operator.value]"
            }
          },
          {
            "parameter": {
              "name": "name",
              "dt": "string",
              "value": "[name.value]"
            }
          },
          {
            "parameter": {
              "name": "windows_view",
              "dt": "string",
              "value": "[windows_view.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TESTTYPE NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "existence_check",
              "dt": "string",
              "value": "[existence_check.value]"
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
              "name": "registry_type",
              "dt": "string",
              "value": "[registry_type.value]"
            }
          },
          {
            "parameter": {
              "name": "registry_type_operator",
              "dt": "string",
              "value": "[registry_type_operator.value]"
            }
          },
          {
            "parameter": {
              "name": "registry_value",
              "dt": "binary",
              "value": "[registry_value.value]"
            }
          },
          {
            "parameter": {
              "name": "registry_value_datatype",
              "dt": "binary",
              "value": "[registry_value_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "registry_value_operator",
              "dt": "binary",
              "value": "[registry_value_operator.value]"
            }
          }
        ]
      }
    }
  }