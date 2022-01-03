VMware: VM Host: Firewall Exception: All IP
===========================================

Description
-----------

The VMware: VM Host: Firewall Exception: All IP test is used to verify the ESXi host firewall is configured to restrict access to services running on the host.

The vmhost_firewallexception_object element is used by a vmhost_firewallexception_test to define the vmhost name and connection string, and name of the firewall exception to be evaluated.

The vmhost_firewallexception_state element holds information regarding the firewall exception, services, and allowed hosts to be evaluated. 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**vmware.vmhost.firewall_exception.all_ip**

+-------------------------------------+---------+----------------------------+
| Name                                | Type    | Description                |
+=====================================+=========+============================+
| vmhost_name                         | string  | The name of the ESXi host  |
|                                     |         | to limit collection to.    |
|                                     |         | Set to NA if not           |
|                                     |         | applicable.                |
+-------------------------------------+---------+----------------------------+
| firewall_exception_name             | string  | The firewall exceptions to |
|                                     |         | scope collection to. Set   |
|                                     |         | to NA if not applicable.   |
+-------------------------------------+---------+----------------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - VMware: VM Host: Firewall Exception: All IP

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**vmware.vmhost.firewall_exception.all_ip**

==================== ======= =====================
Name                 Type    Description
==================== ======= =====================
operator             string Comparison operation.
allowed_hosts_all_ip boolean Allows Hosts All IP?
==================== ======= =====================

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

**vmware.vmhost.firewall_exception.all_ip**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
    <xccdf:check-content>
      <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
        <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
        <ae:title>[ARTIFACT-TITLE]</ae:title>
        <ae:artifact type="[ARTIFACT-TYPE-NAME]" />
          <ae:parameters>
            <ae:parameter dt="string" name="vmhost_name">[vmhost_name.value]</ae:parameter>
            <ae:parameter dt="string" name="firewall_exception_name">[firewall_exception_name.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
            <ae:parameter dt="string" name="allowed_hosts_all_ip">[allowed_hosts_all_ip.value]</ae:parameter>
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

For ``vmware.vmhost.firewall_exception.all_ip`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks:var:100000"
      value-id="xccdf_org.cisecurity.benchmarks_value_esxi.connection" />
    <check-content-ref 
      href="[BENCHMARK-NAME]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <vmhost_firewallexception_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </vmhost_firewallexception_test>

Object

::

  <vmhost_firewallexception_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <connection_string var_ref="oval:org.cisecurity.benchmarks[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <vmhost_name operation="pattern match">
      .*
    </vmhost_name>
    <firewall_exception_name operation="pattern match">
      .*
    </firewall_exception_name>
  </vmhost_firewallexception_object>      

State

::

  <vmhost_firewallexception_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <exception_enabled 
      datatype="boolean]"
      operation="equals">
        true
    </exception_enabled>
    <service_running 
      datatype="boolean]"
      operation="equals">
        false
    </service_running>
    <allowed_hosts_all_ip 
      datatype="boolean"
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </vmhost_firewallexception_state> 

Variable

::

  <external_variable 
    id="oval:org.cisecurity.benchmarks[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
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
        - parameter: 
            name: "firewall_exception_name"
            dt: "string"
            value: "[firewall_exception_name.value]"            
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "operator"
            dt: "string"
            value: "[operator.value]"
        - parameter: 
            name: "allowed_hosts_all_ip"
            dt: "string"
            value: "[allowed_hosts_all_ip.value]"

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
              "name": "firewall_exception_name",
              "dt": "string",
              "value": "[firewall_exception_name.value]"
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
              "name": "allowed_hosts_all_ip",
              "dt": "string",
              "value": "[allowed_hosts_all_ip.value]"
            }
          }
        ]
      }
    }
  }
