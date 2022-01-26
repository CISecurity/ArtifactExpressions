VMware: VM Host: Service State
==============================

Description
-----------

The VMware: VM Host: Service State is used to verify the Direct Console User Interface (DCUI) is disabled to prevent any local administration from the Host.

The vmhost_service_object element is used by a vmhost_service_test to define the vmhost name and connection string, and name of the service to be evaluated.

The vmhost_service_state element holds information regarding the specified service policy. 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**vmware.vmhost.service.state**

+-------------------------------------+---------+----------------------------+
| Name                                | Type    | Description                |
+=====================================+=========+============================+
| service_name                        | string  | The name of the service.   |
|                                     |         | i.e. DCUI.                 |
+-------------------------------------+---------+----------------------------+
| vm_host                             | string  | Name of the ESXi host to   |
|                                     |         | scope collection to. Set   |
|                                     |         | to NA if not applicable.   |
+-------------------------------------+---------+----------------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - VMware: VM Host: Service State Test

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**vmware.vmhost.service.state**

============== ====== =====================================
Name           Type   Description
============== ====== =====================================
service_policy string Value from Service Policy Constraint.
============== ====== =====================================

NOTE: The ``service_policy`` parameter is governed by a constraint allowing only the following values:
  - Automatic 
  - Off 
  - On

Generated Content
~~~~~~~~~~~~~~~~~

**vmware.vmhost.service.state**

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
            <ae:parameter dt="string" name="service_name">[service_name.value]</ae:parameter>
            <ae:parameter dt="string" name="vmhost_name">[vmhost_name.value]</ae:parameter>
          </ae:parameters>
        </ae:artifact>
        <ae:test type="[TEST-TYPE-NAME]">
          <ae:parameters>
            <ae:parameter dt="string" name="service_policy">[service_policy.value]</ae:parameter>
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

For ``vmware.vmhost.service.state`` ``vmware.vmhost.service.state`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this artifact.

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

  <vmhost_service_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="any_exist"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </vmhost_service_test>

Object

::

  <vmhost_service_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <connection_string var_ref="oval:org.cisecurity.benchmarks:var:100000" />
    <vmhost_name operation="pattern match">.*</vmhost_name>
    <service_name>[service_name.value]</service_name>
  </vmhost_service_object>      

State

::

  <vmhost_service_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#esxi"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <service_policy 
      datatype="string"
      operation="case insensitive equals">
        [service_policy.value]
    </service_policy>
  </vmhost_service_state> 

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
            name: "service_name"
            dt: "string"
            value: "[service_name.value]"
        - parameter: 
            name: "vmhost_name"
            dt: "string"
            value: "[vmhost_name.value]"            
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "service_policy"
            dt: "string"
            value: "[service_policy.value]"

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
              "name": "service_name",
              "dt": "string",
              "value": "[service_name.value]"
            }
          },
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
              "name": "service_policy",
              "dt": "string",
              "value": "[service_policy.value]"
            }
          }
        ]
      }
    }
  }
