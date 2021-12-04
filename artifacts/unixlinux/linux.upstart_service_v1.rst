Linux: Upstart Service
======================

Description
-----------

The Linux: Upstart Service test executes a shell command and evaluates
the lines of output to determine if a service is enabled.

The shellcommand_object element is used to define the shell
command being run.

The shellcommand_state element specifies the output value to
check.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**linux.upstart_service_v1**

======= ====== =====================================
Name    Type   Description
======= ====== =====================================
service string The name of the service to be tested.
======= ====== =====================================

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Unix: Service Enabled

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**unix.service_enabled_v1**

======= ====== ================================
Name    Type   Description
======= ====== ================================
enabled string Is the service enabled? (Yes/No)
======= ====== ================================

Generated Content
~~~~~~~~~~~~~~~~~

**unix.service_enabled_v1**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

  <xccdf:complex-check operator="AND">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
        <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
          <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
          <ae:title>[RECOMMENDATION-TITLE]</ae:title>
          <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="service">chargen</ae:parameter>
              <ae:parameter dt="string" name="protocol" />
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TESTTYPE_NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="enabled">[enabled.value]</ae:parameter>
            </ae:parameters>
          </ae:test>
          <ae:profiles>
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1 "/>
          </ae:profiles>          
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  </xccdf:complex-check>

SCAP
^^^^

XCCDF
'''''

For ``linux.upstart_service_v1`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

::

  <xccdf:complex-check operator="AND">
    <check system="http://open-SCAP.org/page/SCE">
      <check-content-ref 
        href="[BENCHMARK-TITLE]"
        name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
    </check>
  </xccdf:complex-check>

OVAL
''''

Test

::

  <shellcommand_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#cmd"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="all"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </shellcommand_test>

Object

::

  <shellcommand_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#cmd"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <command>[command.value]</command>
    <line_selection operation="pattern match">
        "^\\s+start on
    </line_selection>
  </shellcommand_object>

State

::

  <shellcommand_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#cmd"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <stdout_line 
      entity_check="at least one"
      operation="pattern match">
        .+
    </stdout_line>
  </shellcommand_state> 

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
            name: "service"
            dt: "string"
            value: "[service.value]"
        - parameter:
            name: "protocol"
            dt: "string"
            value: "[protocol.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "enabled"
            dt: "string"
            value: "[enabled.value]"

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
              "name": "service",
              "type": "string",
              "value": "[service.value]"
            }
          },
          {
            "parameter": {
              "name": "protocol",
              "type": "string",
              "value": "[protocol.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "enabled",
              "type": "string",
              "value": "[enabled.value]"
            }
          }
        ]
      }
    }
  }
