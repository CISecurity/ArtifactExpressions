iis.applicationhostconfig
=========================

Description
-----------

The Application Host Configuration Test evaluates global configuration
settings that are used by the Windows Process Activation Service (WAS)
in Internet Information Services (IIS). This element defines many of the
server-level configuration settings in the IIS 7 ApplicationHost.config
file. Of significant importance, the Application Host Configuration Item
contains the configuration settings for the Application Pools and Sites,
which respectively define the collection of application pools and Web
sites on an IIS server. Note: Unlike the settings that are found in
system.webServer, settings in the Application Host Configuration Item
element cannot be delegated.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

+------+------+-----------------------------------------------------------------+
| Name | Type | Description                                                     |
+======+======+=================================================================+
|      |      | iis.applicationhostconfig is a singleton and has no parameters. |
+------+------+-----------------------------------------------------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

-  iis.applicationhostconfig

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| operator                            | String      | comparison       |
|                                     |             | operation        |
+-------------------------------------+-------------+------------------+
| configuration_setting               | String      | Defines how many |
|                                     |             | collected items  |
|                                     |             | must match the   |
|                                     |             | expected state   |
+-------------------------------------+-------------+------------------+
| data_type                           | String      | The data type of |
|                                     |             | the web.config   |
|                                     |             | setting          |
+-------------------------------------+-------------+------------------+
| value                               | String      | The value to     |
|                                     |             | compare to the   |
|                                     |             | collected        |
|                                     |             | web.config       |
|                                     |             | setting          |
+-------------------------------------+-------------+------------------+

operator NOTE: This parameter is governed by a constraint allowing only
the following values: - equals - not equal - case insensitive equals -
case insensitive not equal - greater than - less than - greater than or
equal - less than or equal - bitwise and - bitwise or - pattern match -
subset of - superset of

data_type NOTE: This parameter is governed by a constraint allowing only
the following values: - boolean - float - int - string - version - set

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
         <ae:artifact type="[ARTIFACTTYPE NAME]" \>
         <ae:test type="[TESTTYPE NAME]">
           <ae:parameters>
             <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
             <ae:parameter dt="string" name="configuration_setting"
               >[configuration_setting.value]</ae:parameter>
             <ae:parameter dt="string" name="data_type"
               >[data_type.value]</ae:parameter>
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

::

   <xccdf:check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
     <xccdf:check-export
        export-name="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
        value-id="[VALUE ID NAME]"/>
     <xccdf:check-content-ref href="CIS_Microsoft_IIS_10_Benchmark_v1.1.1-oval.xml"
        name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]"/>
   </xccdf:check>

   <xccdf:Value id="xccdf_org.cisecurity.benchmarks_value_4.9.1_var" operator="[operator.value]"
     type="[data_type.value]">
     <xccdf:title>[RECOMMENDATION TITLE]</xccdf:title>
     <xccdf:description>This variable is used in [RECOMMENDATION TITLE]</xccdf:description>
     <xccdf:value>[value.value]</xccdf:value>
   </xccdf:Value>

OVAL
''''

Test
    

::

   <iis:applicationhostconfig_test check="all" check_existence="any_exist"
      comment="[RECOMMENDATION TITLE]"
      id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" version="[version.value]">
      <iis:object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:"/>
      <iis:state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"/>
   </iis:applicationhostconfig_test>

Object
      

::

   <iis:applicationhostconfig_object
      id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" version="[version.value]"/>  

State
     

::

   <iis:applicationhostconfig_state
      id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" version="[version.value]">
      <allow_unlisted_isapis xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#iis"
         datatype="[data_type.value]" operation="[operator.value]"
         var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"/>
   </iis:applicationhostconfig_state>   

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
       test:
         type: [TESTTYPE NAME]
         parameters:
         - parameter:
             name: operator
             type: string
             value: [operator.value]
         - parameter: 
             name: configuration_setting
             type: string
             value: [configuration_setting.value]
         - parameter:
             name: data_type
             type: string
             value: [data_type.value]
         - parameter: 
             name: value
             type: string
             value: [value.value]       

JSON
^^^^

::

   "artifact-expression": {
     "artifact-unique-id": [ARTIFACT-OVAL-ID],
     "artifact-title": [RECOMMENDATION TITLE],
     "artifact": {
       "type": "[ARTIFACTTYPE NAME]"
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
             "name": "configuration_setting",
             "type": "string",
             "value": [configuration_setting.value]
           }
         },
         {
           "parameter": {
             "name": "data_type",
             "type": "string",
             "value": [data_type.value]
           }
         },
         {
           "parameter": {
             "name": "value",
             "type": "string",
             "value": [value.value]
           }
         }
       ]
     }
   }
