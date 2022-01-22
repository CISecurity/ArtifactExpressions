VMware: VM Host: NTP Server
===========================

Description
-----------

The VMware: VM Host: NTP Server test is used to verify NTP time synchronization is configured correctly and enabled on each VMware ESXi host.

The vmhost_ntpserver_object element is used by a vmhost_ntpserver_test to define the vmhost name and connection string, and name of the ntp_server to be evaluated.

The vmhost_ntpserver_state element holds information regarding the specified ntp_server. 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**vmware.vmhost.ntp_server**

+-------------------------------------+---------+----------------------------+
| Name                                | Type    | Description                |
+=====================================+=========+============================+
| vmhost_name                         | string  | The name of the ESXi host  |
|                                     |         | to scope collection to.    |
|                                     |         | Set to NA ifnot applicable.|
+-------------------------------------+---------+----------------------------+
| ntp_server_name                     | string  | Set to NA if not           |
|                                     |         | applicable.                |
+-------------------------------------+---------+----------------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - VMware: VM Host: NTP Server

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**vmware.vmhost.ntp_server**

======== ====== =====================
Name     Type   Description
======== ====== =====================
operator string Comparison operation.
======== ====== =====================

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

**vmware.vmhost.ntp_server**

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
            <ae:parameter dt="string" name="ntp_server_name">[ntp_server_name.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="operator">[cheoperatorck.value]</ae:parameter>
            <ae:parameter dt="string" name="ntp_server_name">[ntp_server_name.value]</ae:parameter>
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

For ``vmware.vmhost.ntp_server`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
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

  <vmhost_ntpserver_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="at least one"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </vmhost_ntpserver_test>

Object

::

  <vmhost_ntpserver_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <connection_string var_ref="oval:org.cisecurity.benchmarks[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <vmhost_name operation="pattern match">
      .*
    </vmhost_name>
    <ntp_server_name operation="pattern match">
      .*
    </ntp_server_name>
  </vmhost_ntpserver_object>      

State

::

  <vmhost_ntpserver_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <ntp_server_name 
      datatype="string"
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </vmhost_ntpserver_state> 

Variable

::

  <external_variable 
    id="oval:org.cisecurity.benchmarks[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="string"
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
        - parameter: 
            name: "ntp_server_name"
            dt: "string"
            value: "[ntp_server_name.value]"            
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "operator"
            dt: "string"
            value: "[operator.value]"
        - parameter: 
            name: "ntp_server_name"
            dt: "string"
            value: "[ntp_server_name.value]"

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
          },
          {
            "parameter": {
              "name": "ntp_server_name",
              "dt": "string",
              "value": "[ntp_server_name.value]"
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
              "name": "ntp_server_name",
              "dt": "string",
              "value": "[ntp_server_name.value]"
            }
          }
        ]
      }
    }
  }
