Linux: Partition Device
=======================

Description
-----------

The linux.partition_device_v1 test is used to check the information associated with partitions on the local system. 

The required partition_object is used to define which partitions on the local system should be collected. 

The optional partition_state element defines the different information associated with a partition. This includes the name, filesystem type, mount options, total space, space used, and space left. 

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

Human ID: 
  - linux.partition_device_v1

.. table:: linux.partition_device_v1_parameters
   :widths: 33, 8, 33
=================================  ========  =================================
Name                               Type      Description	
=================================  ========  =================================
mount_point                        string    Filesystem mount point being tested. Cannot be blank.
=================================  ========  =================================

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

- Existence Test

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

Human ID: 
  - existence_test

.. table:: existence_test_parameters
   :widths: 33, 8, 33
=================================  ========  =================================
Name                               Type      Description
=================================  ========  =================================
value                              string    The value to be tested.
=================================  ========  =================================

NOTE: The ``value`` parameter is governed by a constraint allowing only the following values:
  - all_exist
  - any_exist
  - at_least_one_exists
  - none_satisfy
  - none_exist
  - only_one_exists


Generated Content
~~~~~~~~~~~~~~~~~

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
              <ae:parameter dt="string" name="mount_point">[mount_point.value]</ae:parameter>
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
          <ae:profiles/>
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  </xccdf:complex-check>


SCAP
^^^^

XCCDF
'''''

For ``linux.partition_options_v1`` artifacts, the xccdf:check looks like
this. There is no Value element in the XCCDF for this Artifact.

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

  <partition_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]" 
    check="all" 
    comment="[RECOMMENDATION-TITLE]" 
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
   </partition_test>

Object      

::

  <partition_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[RECOMMENDATION-TITLE]" 
    version="1">
    <mount_point>
      [mount_point.value]
    </mount_point>
  </partition_object>

State

::

N/A


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
            name: "mount_point"
            dt: "string"
            value: "[mount_point.value]"
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
      "artifact-title": "[RECOMMENDATION-TITLE]",
      "artifact": {
        "type": "[ARTIFACT-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "mount_point",
              "type": "string",
              "value": "[mount_point.value]"
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