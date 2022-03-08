VMware: VM Host: Bus Adapter: ISCSI: CHAP: Mutual
=================================================

Description
-----------

The VMware: VM Host: Bus Adapter: ISCSI: CHAP: Mutual test is used to verify if Bidirectional (Mutual) CHAP Authentication is enabled for the qualified iSCSI Adapter on a VMware ESXi Host Client. 

The vmhost_busadapter_object element is used by a vmhost_busadapter_test to define the vmhost name and connection string, and name of the busadapter to be evaluated.

The vmhost_busadapter_state element holds information regarding the Bidirectional (Mutual) CHAP Authentication status of the specified busadapter. 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**vmware.vmhost.bus_adapter.iscsi.chap.mutual**

+-------------------------------------+---------+----------------------------+
| Name                                | Type    | Description                |
+=====================================+=========+============================+
| vmhost_name                         | string  | The name of the ESXi host  |
|                                     |         | to limit collection to.    |
|                                     |         | Set to NA if not           |
|                                     |         | applicable.                |
+-------------------------------------+---------+----------------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - VMware: VM Host: Bus Adapter: ISCSI: CHAP: Mutual

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**vmware.vmhost.bus_adapter.iscsi.chap.mutual**

=================== ======= ======================
Name                Type    Description
=================== ======= ======================
operator            string  Comparison operation.
mutual_chap_enabled boolean Mutual Chap Enabled?
=================== ======= ======================

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

Generated Content
~~~~~~~~~~~~~~~~~

**vmware.vmhost.bus_adapter.iscsi.chap.mutual**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[ARTIFACT-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACT-TYPE-NAME]" />
          <ae:parameters>
            <ae:parameter dt="string" name="vmhost_name">[vmhost_name.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
            <ae:parameter dt="string" name="mutual_chap_enabled">[mutual_chap_enabled.value]</ae:parameter>
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

For ``vmware.vmhost.bus_adapter.iscsi.chap.mutual`` ``vmware.vmhost.bus_adapter.iscsi.chap.mutual`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    operator="[operator.value]"
    type="boolean">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>  

For ``vmware.vmhost.bus_adapter.iscsi.chap.mutual`` ``vmware.vmhost.bus_adapter.iscsi.chap.mutual`` artifacts, the XCCDF check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />    
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:100000"
      value-id="xccdf_org.cisecurity.benchmarks_value_esxi.connection" />
    <check-content-ref 
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <vmhost_busadapter_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </vmhost_busadapter_test>

Object

::

  <vmhost_busadapter_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <connection_string var_ref="oval:org.cisecurity.benchmarks:var:100000" />
    <vmhost_name operation="pattern match">.*</vmhost_name>
    <busadapter_type>IScsi</busadapter_type>
  </vmhost_busadapter_object>   

State

::

  <vmhost_busadapter_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <mutual_chap_enabled 
      datatype="boolean"
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </vmhost_busadapter_state> 

Variable

::

  <external_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="boolean"
    version="1"
    comment="This value is used in Rule: [RECOMMENDATION-TITLE]" />

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
            name: "vmhost_name"
            dt: "string"
            value: "[vmhost_name.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "operator"
            dt: "string"
            value: "[operator.value]"
        - parameter: 
            name: "mutual_chap_enabled"
            dt: "string"
            value: "[mutual_chap_enabled.value]"

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
              "name": "vmhost_name",
              "dt": "string",
              "value": "[vmhost_name.value]"
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
              "dt": "string",
              "value": "[operator.value]"
            }
          },
          {
            "parameter": {
              "name": "mutual_chap_enabled",
              "dt": "string",
              "value": "[mutual_chap_enabled.value]"
            }
          }
        ]
      }
    }
  }
