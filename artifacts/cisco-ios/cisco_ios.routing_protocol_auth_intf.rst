Cisco IOS: Routing Protocol Authentication Interface
====================================

Description
-----------

The Cisco IOS: Routing Protocol Authentication Interface test is used to check the properties of routing protocol authentication configured under interfaces in IOS.

The routingprotocolauthintf_object element is used by a routingprotocolauthintf test to define the interface and the routing protocol that is the authenticated entity.

The routingprotocolauthintf_state element defines the different information that can be used to evaluate the result of a specific routing protocol interface authentication configurations. This includes the interface, the protocol, the id, the authentication type, the ospf area, the key chain command and the corresponding config lines. 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**cisco_ios.routing_protocol_auth_intf**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| interface_operator          | string  | Interface Operator.                |
+-----------------------------+---------+------------------------------------+
| interface                   | string  | The name of the interface(s) to    |
|                             |         | collect.                           |
+-----------------------------+---------+------------------------------------+
| protocol_operator           | string  | Protocol Operator.                 |
+-----------------------------+---------+------------------------------------+
| routing_protocol            | string  | The name of the routing            |
|                             |         | protocol(s) to collect.            |
+-----------------------------+---------+------------------------------------+

NOTE: The ``interface_operator`` and ``protocol_operator`` parameters are governed by a constraint allowing only the following values:
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

NOTE: The ``routing_protocol`` parameter is governed by a constraint allowing only the following values:
  - BGP
  - EIGRP
  - OSPF
  - RIP
  - RIPV2
  - ISIS  

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Cisco IOS: Routing Protocol Authentication Key-Chain
  - Cisco IOS: Routing Protocol Authentication Type

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**cisco_ios.routing_protocol_auth_keychain**

======== ====== =========================
Name     Type   Description
======== ====== =========================
operator string Comparison operator.
keychain string Authentication Key Chain.
======== ====== =========================

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

**cisco_ios.routing_protocol_auth_type**

========= ====== =========================================
Name      Type   Description
========= ====== =========================================
auth_type string The routing protocol authentication type.
========= ====== =========================================

NOTE: The ``auth_type`` parameter is governed by a constraint allowing only the following values:
  - CLEARTEXT
  - MESSAGE_DIGEST

Generated Content
~~~~~~~~~~~~~~~~~

**cisco_ios.routing_protocol_auth_keychain**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:complex-check operator="OR">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
        <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
          <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
          <ae:title>[ARTIFACT-TITLE]</ae:title>
          <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="interface_operator">[interface_operator.value]</ae:parameter>
              <ae:parameter dt="string" name="interface">[interface.value]</ae:parameter>
              <ae:parameter dt="string" name="protocol_operator">[protocol_operator.value]</ae:parameter>
              <ae:parameter dt="string" name="routing_protocol">[routing_protocol.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
              <ae:parameter dt="string" name="keychain">[keychain.value]</ae:parameter>
            </ae:parameters>
          </ae:test>
          <ae:profiles>
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_2" />
          </ae:profiles>          
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  </xccdf:complex-check>   

SCAP
^^^^

XCCDF
'''''

For ``cisco_ios.routing_protocol_auth_intf `` ``cisco_ios.routing_protocol_auth_keychain`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    type="string"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``cisco_ios.routing_protocol_auth_intf`` ``cisco_ios.routing_protocol_auth_keychain`` artifacts, the XCCDF check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
    <check-content-ref 
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <routingprotocolauthintf_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#ios"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </routingprotocolauthintf_test>

Object

::

  <routingprotocolauthintf_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#ios"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <interface operation="[operation.value]">[interface.value]</interface>
    <protocol operation="[operation.value]">[protocol.value]</protocol>
  </routingprotocolauthintf_object>

State

::

  <routingprotocolauthintf_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#ios"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <key_chain 
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </routingprotocolauthintf_state>

Variable

::

  <external_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="string"
    comment="This value is used in Rule: [RECOMMENDATION-TITLE]"
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
            name: "interface_operator"
            dt: "string"
            value: "[interface_operator.value]"
        - parameter: 
            name: "interface"
            dt: "string"
            value: "[interface.value]"
        - parameter: 
            name: "protocol_operator"
            dt: "string"
            value: "[protocol_operator.value]"
        - parameter: 
            name: "routing_protocol"
            dt: "string"
            value: "[routing_protocol.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:   
        - parameter: 
            name: "operator"
            dt: "string"
            value: "[operator.value]"
        - parameter: 
            name: "keychain"
            dt: "string"
            value: "[keychain.value]"

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
              "name": "interface_operator",
              "type": "string",
              "value": "[interface_operator.value]"
            }
          },
          {
            "parameter": {
              "name": "interface",
              "type": "string",
              "value": "[interface.value]"
            }
          },
          {
            "parameter": {
              "name": "protocol_operator",
              "type": "string",
              "value": "[protocol_operator.value]"
            }
          },
          {
            "parameter": {
              "name": "routing_protocol",
              "type": "string",
              "value": "[routing_protocol.value]"
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
              "name": "keychain",
              "type": "string",
              "value": "[keychain.value]"
            }
          }
        ]
      }
    }
  }

Generated Content
~~~~~~~~~~~~~~~~~

**cisco_ios.routing_protocol_auth_type**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:complex-check operator="OR">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
        <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
          <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
          <ae:title>[ARTIFACT-TITLE]</ae:title>
          <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="interface_operator">[interface_operator.value]</ae:parameter>
              <ae:parameter dt="string" name="interface">[interface.value]</ae:parameter>
              <ae:parameter dt="string" name="protocol_operator">[protocol_operator.value]</ae:parameter>
              <ae:parameter dt="string" name="routing_protocol">[routing_protocol.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="auth_type">[auth_type.value]</ae:parameter>
            </ae:parameters>
          </ae:test>
          <ae:profiles>
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_2" />
          </ae:profiles>          
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  </xccdf:complex-check>   

SCAP
^^^^

XCCDF
'''''

For ``cisco_ios.routing_protocol_auth_intf`` ``cisco_ios.routing_protocol_auth_type`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    type="string"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``cisco_ios.routing_protocol_auth_intf`` ``cisco_ios.routing_protocol_auth_type`` artifacts, the XCCDF check looks like this.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-export 
      export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
      value-id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var" />
    <check-content-ref 
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
  </check>

OVAL
''''

Test

::

  <routingprotocolauthintf_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#ios"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </routingprotocolauthintf_test>

Object

::

  <routingprotocolauthintf_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#ios"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <interface operation="[operation.value]">[interface.value]</interface>
    <protocol operation="[operation.value]">[protocol.value]</protocol>
  </routingprotocolauthintf_object>

State

::

  <routingprotocolauthintf_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#ios"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <auth_type 
      operation="equals"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </routingprotocolauthintf_state>

Variable

::

  <external_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="string"
    comment="This value is used in Rule: [RECOMMENDATION-TITLE]"
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
            name: "interface_operator"
            dt: "string"
            value: "[interface_operator.value]"
        - parameter: 
            name: "interface"
            dt: "string"
            value: "[interface.value]"
        - parameter: 
            name: "protocol_operator"
            dt: "string"
            value: "[protocol_operator.value]"
        - parameter: 
            name: "routing_protocol"
            dt: "string"
            value: "[routing_protocol.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:   
        - parameter: 
            name: "auth_type"
            dt: "string"
            value: "[auth_type.value]"

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
              "name": "interface_operator",
              "type": "string",
              "value": "[interface_operator.value]"
            }
          },
          {
            "parameter": {
              "name": "interface",
              "type": "string",
              "value": "[interface.value]"
            }
          },
          {
            "parameter": {
              "name": "protocol_operator",
              "type": "string",
              "value": "[protocol_operator.value]"
            }
          },
          {
            "parameter": {
              "name": "routing_protocol",
              "type": "string",
              "value": "[routing_protocol.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "auth_type",
              "type": "string",
              "value": "[auth_type.value]"
            }
          }
        ]
      }
    }
  }
