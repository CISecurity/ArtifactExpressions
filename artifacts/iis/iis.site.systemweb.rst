IIS: Site: System Web
=====================

Description
-----------

The IIS: Site: System Web test is used to determine certain aspects of an IIS Site’s configuration. 

The systemweb_object element is used by a systemweb_test to define the names of the site, application, and virtual directory to be evaluated, as well as the filter by which they should be evaluated.

The systemweb_state element defines the IIS site configuration information to be evaluated.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**iis.site.systemweb**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| site_name                   | string  | Name of the site to collect. Can   |
|                             |         | be a regex.                        |
+-----------------------------+---------+------------------------------------+
| application_name            | string  | Name of the application to         |
|                             |         | collect. Can be a regex. Set to    |
|                             |         | NULL to collect only information   |
|                             |         | for the specified sites.           |
+-----------------------------+---------+------------------------------------+
| virtual_directory_name      | string  | The name of a virtual directory to |
|                             |         | collect. Can bea regex. Set to     |
|                             |         | NULL to collect only information   |
|                             |         | for the specified                  |
|                             |         | sites/applications.                |
+-----------------------------+---------+------------------------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - IIS: Site: System Web

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**iis.site.systemweb**

+-----------------------------+---------+------------------------------------+
| Name                        | Type    | Description                        |
+=============================+=========+====================================+
| configuration_setting       | string  | The web.config setting to test.    |
+-----------------------------+---------+------------------------------------+
| operator                    | string  | Comparison operation.              |
+-----------------------------+---------+------------------------------------+
| data_type                   | string  | The data type of theweb.config     |
|                             |         | setting.                           |
+-----------------------------+---------+------------------------------------+
| value                       | string  | The value to compare to the        |
|                             |         | collected web.config setting.      |
+-----------------------------+---------+------------------------------------+

Generated Content
~~~~~~~~~~~~~~~~~

**iis.site.systemweb**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

   <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
     <xccdf:check-content>
       <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
         <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
         <ae:title>[ARTIFACT-TITLE]</ae:title>
         <ae:artifact type="[ARTIFACT-TYPE-NAME]">
           <ae:parameters>
             <ae:parameter dt="string" name="site_name">[site_name.value]</ae:parameter>
             <ae:parameter dt="string" name="application_name">[application_name.value]</ae:parameter>  
             <ae:parameter dt="string" name="virtual_directory_name">[virtual_directory_name.value]</ae:parameter>
           </ae:parameters>
         </ae:artifact>
         <ae:test type="[TEST-TYPE-NAME]">
           <ae:parameters>
             <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
             <ae:parameter dt="string" name="configuration_setting">[configuration_setting.value]</ae:parameter>
             <ae:parameter dt="string" name="data_type">[data_type.value]</ae:parameter>
             <ae:parameter dt="string" name="value">[value.value]</ae:parameter>
           </ae:parameters>
         </ae:test>
         <ae:profiles>
           <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1"
           />
         </ae:profiles>
       </ae:artifact_expression>
     </xccdf:check-content>
   </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``iis.site.systemweb`` ``iis.site.systemweb`` artifacts, an XCCDF Value element is generated.

::

  <Value 
    id="xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var"
    type="[type.value]"
    operator="[operator.value]">
    <title>[RECOMMENDATION-TITLE]</title>
    <description>This value is used in Rule: [RECOMMENDATION-TITLE]</description>
    <value>[value.value]</value>
  </Value>

For ``iis.site.systemweb`` ``iis.site.systemweb`` artifacts, the XCCDF check looks like this.  

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

  <systemweb_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iis"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="any_exist"
    check="all"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  <systemweb_test>

Object

::

  <systemweb_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iis"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <site_name operation="pattern match">[site_name.value]<site_name>
    <application_name operation="pattern match">[application_name.value]<application_name>
    <virtual_directory_name operation="pattern match">[virtual_directory_name.value]</virtual_directory_name>
    <filter
      xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5" 
      action="include">
        oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]
    </filter>
  <systemweb_object> 
  
State

::

  <systemweb_state    
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iis"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <[configuration_setting.value] 
      datatype="[datatype.value]"
      operation="[operation.value]"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  <systemweb_state> 

Variable

::

  <external_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="boolean"
    comment="This value is used in [RECOMMENDATION-TITLE]"
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
            name: "site_name"
            dt: "string"
            value: "[site_name.value]"
        - parameter: 
            name: "application_name"
            dt: "string"
            value: "[application_name.value]"
        - parameter: 
            name: "virtual_directory_name"
            dt: "string"
            value: "[virtual_directory_name.value]"        
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "operator"
            dt: "string"
            value: "[operator.value]"
        - parameter: 
            name: "configuration_setting"
            dt: "string"
            value: "[configuration_setting.value]"
        - parameter:
            name: "data_type"
            dt: "string"
            value: "[data_type.value]"
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
      "artifact-title": "[ARTIFACT-TITLE]",
      "artifact": {
        "type": "[ARTIFACT-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "site_name",
              "type": "string",
              "value": "[site_name.value]"
            }
          },
          {
            "parameter": {
              "name": "application_name",
              "type": "string",
              "value": "[application_name.value]"
            }
          },
          {
            "parameter": {
              "name": "virtual_directory_name",
              "type": "string",
              "value": "[virtual_directory_name.value]"
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
              "name": "configuration_setting",
              "type": "string",
              "value": "[configuration_setting.value]"
            }
          },
          {
            "parameter": {
              "name": "data_type",
              "type": "string",
              "value": "[data_type.value]"
            }
          },
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
