Linux: Debian Package
=======================

Description
-----------

The Linux: Debian Package test is used to check information for a given DPKG package. 

The required dpkginfo_object element is used to define the object being evaluated. A dpkginfo object consists of a single name entity that identifies the package being checked.

The optional dpkginfo_state element defines the different information that can be used to evaluate the specified DPKG package. This includes the architecture, epoch number, release, and version numbers. 

Warning: There are differences in the algorithms for how the version strings of Debian and RPM packages are compared. As a result, a debian_evr_string datatype should be used for this entity, instead of the evr_string datatype. This represents the epoch, upstream_version, and debian_revision fields, for a Debian package, as a single version string. It has the form "EPOCH:UPSTREAM_VERSION-DEBIAN_REVISION". Note that a null epoch (or '(none)' as returned by dpkg) is equivalent to '0' and would hence have the form 0:UPSTREAM_VERSION-DEBIAN_REVISION.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

Human ID: 
  - linux.debian_package_v1

.. table:: linux.debian_package_v1_parameters
   :widths: 33, 8, 33
=================================  ========  =================================
Name                               Type      Description	
=================================  ========  =================================
name                               string    The name of the package being checked. Cannot be blank.
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
              <ae:parameter dt="string" name="name">[name.name]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
            </ae:parameters>
          </ae:test>
          <ae:profiles>
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1" />
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

For ``linux.debian_package_v1`` artifacts, the xccdf:check looks like
this. There is no Value element in the XCCDF for this Artifact.

::

  <xccdf:complex-check operator="AND">
    <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
      <check-content-ref 
        href="[BENCHMARK-TITLE]" 
        name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
    </check>
  </xccdf:complex-check>    


OVAL
''''

Test    

::

  <dpkginfo_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"     
    check_existence="[check_existence.value]" 
    check="all" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </dpkginfo_test>

Object      

::

  <dpkginfo_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"     
    comment="[RECOMMENDATION-TITLE]"    
    version="1">
    <name>
      value
    </name>
  </dpkginfo_object>

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
          name: "name"
          dt: "string"
          value: "[name.value]"
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
              "name": "name",
              "type": "string",
              "value": "[name.value]"
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