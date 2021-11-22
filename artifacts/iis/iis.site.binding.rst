iis.site.binding
================

Description
-----------

The bindings_test is used to determine the bindings for sites managed in
IIS, including http and https bindings. It extends the standard TestType
as defined in the oval-definitions-schema and one should refer to the
TestType description for more information. The object element
references a vmhost_modules_object and the state element
specifies the data to check.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

========= ====== ===============================================
Name      Type   Description
========= ====== ===============================================
site_name String The name of the site to collect. Can be a regex
========= ====== ===============================================

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - iis.site.binding.host_header

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

=========== ====== ====================
Name        Type   Description
=========== ====== ====================
operator    String comparison operation
host_header String 
=========== ====== ====================

Generated Content
~~~~~~~~~~~~~~~~~

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF

::

   <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
     <xccdf:check-content>
       <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION_NUMBER]">
         <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
         <ae:title>[RECOMMENDATION TITLE]</ae:title>
         <ae:artifact type="[ARTIFACTTYPE NAME]">
           <ae:parameters>
             <ae:parameter dt="string" name="site_name"
               >[site_name.value]</ae:parameter>
           </ae:parameters>
         </ae:artifact>
         <ae:test type="[TESTTYPE NAME]">
           <ae:parameters>
             <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
             <ae:parameter dt="string" name="host_header"
               >[host_header.value]</ae:parameter>
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

::

   <xccdf:check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
     <xccdf:check-export
        export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
        value-id="[VALUE ID NAME]"/>
     <xccdf:check-content-ref href="CIS_Microsoft_IIS_10_Benchmark_v1.1.1-oval.xml"
        name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]"/>
   </xccdf:check>

   <xccdf:Value id="xccdf_org.cisecurity.benchmarks_value_4.9.1_var" operator="[operator.value]"
     type="string">
     <xccdf:title>[RECOMMENDATION TITLE]</xccdf:title>
     <xccdf:description>This variable is used in [RECOMMENDATION TITLE]</xccdf:description>
     <xccdf:value>[host_header.value]</xccdf:value>
   </xccdf:Value>

OVAL
''''

Test

::

   <iis:bindings_test check="all" check_existence="any_exist"
      comment="[RECOMMENDATION TITLE]"
      id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" version="[version.value]">
      <iis:object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:"/>
      <iis:state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"/>
   </iis:bindings_test>

Object

::

   <iis:bindings_object id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
      version="[version.value]">
      <iis:site_name operation="[operator.value]">[site_name.value]</iis:site_name>
   </iis:bindings_object>   

State

::

   <iis:bindings_state
      id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" version="[version.value]">
      <host_header xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iis"
         datatype="string" operation="[operator.value]"
         var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"/>
   </iis:bindings_state>   

Variable
        

::

   <external_variable
     comment="This value is used in [RECOMMENDATION TITLE]"
     datatype="[data_type.value]" id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" version="[version.value]"/>                   

YAML
^^^^

::

  - artifact-expression:
       artifact-unique-id: [ARTIFACT-OVAL-ID]
       artifact-title: [RECOMMENDATION TITLE]
       artifact:
         type: [ARTIFACTTYPE NAME]
         parameters:
         - parameter: 
             name: site_name
             type: string
             value: [site_name.value]
       test:
         type: [TESTTYPE NAME]
         parameters:
         - parameter:
             name: operator
             type: string
             value: [operator.value]
         - parameter: 
             name: host_header
             type: string
             value: [host_header.value]
          

JSON
^^^^

::

   "artifact-expression": {
     "artifact-unique-id": [ARTIFACT-OVAL-ID],
     "artifact-title": [RECOMMENDATION TITLE],
     "artifact": {
       "type": "[ARTIFACTTYPE NAME]",
       "parameters": [
         {
           "parameter": {
             "name": "site_name",
             "type": "string",
             "value": [site_name.value]
           }
         }
       ]
     },
     "test": {
       "type": [TESTTYPE NAME],
       "parameters": [
         {
           "parameter": {
             "name": "operator",
             "type": "string",
             "value": [operator.value]
           }
         },
         {
           "parameter": {
             "name": "host_header",
             "type": "string",
             "value": [host_header.value]
           }
         }
       ]
     }
   }
