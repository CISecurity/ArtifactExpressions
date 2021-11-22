macos.systemprofiler_v1
=======================

Description
-----------

The systemprofiler_test is used to check the properties of the
plist-style XML output from the “system_profiler -xml ” command, for
reading information about system inventory data on MacOSX. It extends
the standard TestType as defined in the oval-definitions-schema and one
should refer to the TestType description for more information. The
object element references an systemprofiler_object and the
optional state element specifies the data to check.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| data_type                           | String      | The data_type    |
|                                     |             | entity provides  |
|                                     |             | the datatype     |
|                                     |             | value that is    |
|                                     |             | desired.         |
+-------------------------------------+-------------+------------------+
| xpath                               | String      | Specifies an     |
|                                     |             | Xpath expression |
|                                     |             | describing the   |
|                                     |             | text node(s) or  |
|                                     |             | attribute(s) to  |
|                                     |             | look at. Any     |
|                                     |             | valid Xpath 1.0  |
|                                     |             | statement is     |
|                                     |             | usable with one  |
|                                     |             | exception, at    |
|                                     |             | most one field   |
|                                     |             | may be           |
|                                     |             | identified in    |
|                                     |             | the Xpath. This  |
|                                     |             | is because the   |
|                                     |             | value_of element |
|                                     |             | in the data      |
|                                     |             | section is only  |
|                                     |             | designed to work |
|                                     |             | against a single |
|                                     |             | field. The only  |
|                                     |             | valid operator   |
|                                     |             | for xpath is     |
|                                     |             | equals since     |
|                                     |             | there is an      |
|                                     |             | infinite number  |
|                                     |             | of possible      |
|                                     |             | xpaths and       |
|                                     |             | determinining    |
|                                     |             | all those that   |
|                                     |             | do not equal a   |
|                                     |             | given xpath      |
|                                     |             | would be         |
|                                     |             | impossible.      |
+-------------------------------------+-------------+------------------+

data_type NOTE: This parameter is governed by a constraint allowing
only the following values: 
  - SPHardwareDataType
  - SPNetworkDataType 
  - SPSoftwareDataType
  - SPParallelATADataType
  - SPAudioDataType
  - SPBluetoothDataType
  - SPDiagnosticsDataType
  - SPDiscBurningDataType
  - SPEthernetDataType
  - SPFibreChannelDataType
  - SPFireWireDataType
  - SPDisplaysDataType
  - SPHardwareRAIDDataType
  - SPMemoryDataType
  - SPPCIDataType
  - SPParallelSCSIDataType
  - SPPowerDataType
  - SPPrintersDataType
  - SPSASDataType
  - SPSerialATADataType
  - SPUSBDataType
  - SPAirPortDataType
  - SPFirewallDataType
  - SPNetworkLocationDataType
  - SPModemDataType
  - SPNetworkVolumeDataType
  - SPWWANDataType
  - SPApplicationsDataType
  - SPDeveloperToolsDataType
  - SPExtensionsDataType
  - SPFontsDataType
  - SPFrameworksDataType
  - SPLogsDataType
  - SPManagedClientDataType
  - SPPrefPaneDataType
  - SPStartupItemDataType
  - SPSyncServicesDataType
  - SPUniversalAccessDataType
  - The empty string value is permitted here to allow for empty elements associated with variable references.

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

  - macos.systemprofiler_v1

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| check_existence                     | String      | Define how many  |
|                                     |             | items should be  |
|                                     |             | collected        |
+-------------------------------------+-------------+------------------+
| check                               | String      | Defines how many |
|                                     |             | collected items  |
|                                     |             | must match the   |
|                                     |             | expected state   |
+-------------------------------------+-------------+------------------+
| operation                           | String      | comparison       |
|                                     |             | operation        |
+-------------------------------------+-------------+------------------+
| datatype                            | String      | datatype         |
+-------------------------------------+-------------+------------------+
| value_of                            | String      | The value_of     |
|                                     |             | element checks   |
|                                     |             | the value(s) of  |
|                                     |             | the text node(s) |
|                                     |             | or attribute(s)  |
|                                     |             | found.           |
+-------------------------------------+-------------+------------------+

check_existence NOTE: This parameter is governed by a constraint
allowing only the following values: - all_exist - any_exist -
at_least_one_exists - none_satisfy - none_exist - only_one_exists

check NOTE: This parameter is governed by a constraint allowing only the
following values: - all - at least one - none satisfy - only one

operation NOTE: This parameter is governed by a constraint allowing only
the following values: - equals - not equal - case insensitive equals -
case insensitive not equal - greater than - less than - greater than or
equal - less than or equal - bitwise and - bitwise or - pattern match -
subset of - superset of

datatype NOTE: This parameter is governed by a constraint allowing only
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
         <ae:artifact type="[ARTIFACTTYPE NAME]">
           <ae:parameters>
             <ae:parameter dt="string" name="data_type"
               >[data_type.value]</ae:parameter>
             <ae:parameter dt="string" name="xpath"
               >[xpath.value]</ae:parameter>
           </ae:parameters>
         </ae:artifact>
         <ae:test type="[TESTTYPE NAME]">
           <ae:parameters>
             <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
             <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
             <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
             <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
             <ae:parameter dt="string" name="value_of">[value_of.value]</ae:parameter>
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

For ``macos.systemprofiler_v1`` artifacts, the xccdf:check looks like this. There is no Value in the xccdf for this Artifact.

::

   <xccdf:check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
      <xccdf:check-content-ref xmlns:ae="http://benchmarks.cisecurity.org/ae/0.5"
         xmlns:cpe="http://cpe.mitre.org/language/2.0"
         xmlns:ecl="http://cisecurity.org/check"
         href="[BENCHMARK NAME]"
         name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]"/>
   </xccdf:check>

OVAL
''''

Test

::

   <macos:systemprofiler_test check="[check.value]" check_existence="[check_existence.value]"
     comment="[RECOMMENDATION TITLE]"
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" version="[version.value]">
     <macos:object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"/>
     <macos:state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"/>
   </macos:systemprofiler_test>

Object

::

   <macos:systemprofiler_object
     comment="[RECOMMENDATION TITLE]"
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" version="[version.value]">
     <macos:data_type>[data_type.value]</macos:data_type>
     <macos:xpath>[xpath.value]</macos:xpath>
   </macos:systemprofiler_object>

State

::

   <macos:systemprofiler_state
     comment="[RECOMMENDATION TITLE]"
     id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" version="[version.value]">
     <macos:value_of datatype="[datatype.value]" operation="[operation.value]">[value_of.value]</macos:value_of>
   </macos:systemprofiler_state>    

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
             name: data_type
             type: string
             value: [data_type.value]
         - parameter: 
           name: xpath
           type: string
           value: [xpath.value]    
       test:
         type: [TESTTYPE NAME]
         parameters:
         - parameter:
             name: check_existence
             type: string
             value: [check_existence.value]
         - parameter: 
             name: check
             type: string
             value: [check.value]
         - parameter:
             name: operation
             type: string
             value: [operation.value]
         - parameter: 
             name: datatype
             type: string
             value: [datatype.value]  
         - parameter: 
             name: value_of
             type: string
             value: [value_of.value]      

JSON
^^^^

::

   "artifact-expression": {
     "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
     "artifact-title": "[RECOMMENDATION TITLE]",
     "artifact": {
       "type": "[ARTIFACTTYPE NAME]",
       "parameters": [
         {
           "parameter": {
             "name": "data_type",
             "type": "string",
             "value": "[data_type.value]"
           }
         },
         {
           "parameter": {
             "name": "xpath",
             "type": "string",
             "value": "[xpath.value]"
           }
         }
       ]
     },
     "test": {
       "type": "[TESTTYPE NAME]",
       "parameters": [
         {
           "parameter": {
             "name": "check_existence",
             "type": "string",
             "value": "[check_existence.value]"
           }
         },
         {
           "parameter": {
             "name": "check",
             "type": "string",
             "value": "[check.value]"
           }
         },
         {
           "parameter": {
             "name": "operation",
             "type": "string",
             "value": "[operation.value]"
           }
         },
         {
           "parameter": {
             "name": "datetype",
             "type": "string",
             "value": "[datatype.value]"
           }
         },
         {
           "parameter": {
             "name": "value_of",
             "type": "string",
             "value": "[value_of.value]"
           }
         }
       ]
     }
   }
