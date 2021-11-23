Unix: Xinetd Service
====================

Description
-----------

The Unix: Xinetd Service test is used to check information associated
with different Internet services. The textfilecontent54_test elements
are used to check the contents of the inetd configuration file and files
within the /etc/xinetd.d directory, by looking at individual blocks of
text within the files.

The inetd_object element is used to define the specific
protocol-service to be evaluated. An inetd object consists of a protocol
entity and a service_name entity that identifies the specific service to
be tested.

The textfilecontent54_object elements are used to define the
specific block(s) of text of a file(s) to be evaluated. The
textfilecontent54_object will only collect regular files on UNIX
systems.

The set of files to be evaluated may be identified with either a
complete filepath or a path and filename. Only one of these options may
be selected.

The inetd_state element defines the different information
associated with a specific Internet service.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**unix.xinetd_service_v1**

======== ====== ======================================================
Name     Type   Description
======== ====== ======================================================
service  string The name of the service to be tested. Cannot be blank.
protocol string Protocol the service is running on (tcp/udp).
======== ====== ======================================================

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - Unix: Service Enabled
  - Unix: Xinetd Service Enabled

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

| **unix.service_enabled_v1**
| **unix.xinetd_service_enabled_v1**

======= ====== ================================
Name    Type   Description
======= ====== ================================
enabled string Is the service enabled? (Yes/No)
======= ====== ================================

Generated Content
~~~~~~~~~~~~~~~~~
| **unix.service_enabled_v1**
| **unix.xinetd_service_enabled_v1**

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
              <ae:parameter dt="string" name="service_name">[service_name.value]</ae:parameter>
              <ae:parameter dt="string" name="protocol">[protocol.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="enabled">[enabled.value]</ae:parameter>
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

For ``linux.xinetd_service_v1`` artifacts, the xccdf:check looks like this. There is no Value element in the XCCDF for this Artifact.

::

  <xccdf:complex-check operator="OR">
    <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
      <check-content-ref
        href="[BENCHMARK-TITLE]"
        name="oval:org.cisecurity.benchmarks:def:[ARTIFACT-OVAL-ID]" />
    </check>
  </xccdf:complex-check>  

OVAL
''''

Test

::

  <xinetd_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks:tst:[ARTIFACT-OVAL-ID]1" 
    check_existence="[check_existence.value]"
    check="all"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks:obj:[ARTIFACT-OVAL-ID]1" />
    <state state_ref="oval:org.cisecurity.benchmarks:ste:[ARTIFACT-OVAL-ID]1" />
  </xinetd_test>

  <textfilecontent54_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks:tst:[ARTIFACT-OVAL-ID]2" 
    check_existence="[check_existence.value]"
    check="all"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks:obj:[ARTIFACT-OVAL-ID]2" />
  </textfilecontent54_test>

  <textfilecontent54_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks:tst:[ARTIFACT-OVAL-ID]3" 
    check_existence="[check_existence.value]"
    check="all"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks:obj:[ARTIFACT-OVAL-ID]3" />
  </textfilecontent54_test>    

Object

::

  <xinetd_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks:obj:[ARTIFACT-OVAL-ID]1"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <protocol>[protocol.value]</protocol>
    <service_name>[service_name.value]</service_name>
  </xinetd_object>

  <textfilecontent54_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks:obj:[ARTIFACT-OVAL-ID]2"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <filepath>/etc/inetd.conf</filepath>
    <pattern
      operation="pattern match" 
      datatype="string">
      [pattern.value]
    </pattern>
    <instance
      datatype="int"
      operation="equals">
      1
    </instance>    
  </instance>

  <textfilecontent54_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks:obj:[ARTIFACT-OVAL-ID]3"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <path>/etc/inetd.d</path>
    <filename operation="pattern match">
      .+
    </filename>
    <pattern
      operation="pattern match" 
      datatype="string">
      [pattern.value]
    </pattern>
    <instance
      datatype="int"
      operation="equals">
      1
    </instance>    
  </textfilecontent54_object>

State

::

  <xinetd_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks:ste:[ARTIFACT-OVAL-ID]1"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <disabled 
      datatype="boolean" 
      operation="equals">
      [disabled.value]
    </disabled>
  </xinetd_state>

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
            name: "service_name"
            dt: "string"
            value: "[service_name.value]"
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
        "type": "unix.uname_parameter_v1",
        "parameters": [
          {
            "parameter": {
              "name": "service_name",
              "type": "string",
              "value": "[service_name.value]"
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
