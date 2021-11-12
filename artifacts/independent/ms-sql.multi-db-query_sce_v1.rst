ms-sql.multi-db-query_sce_v1
============================

Description
-----------

The ms-sql.multi-db-query_sce_v1 is used by a sql test to define the
specific database and query to be evaluated. Connection information is
supplied allowing the tool to connect to the desired database and a
query is supplied to call out the desired setting.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| sql                                 | String      | The sql entity   |
|                                     |             | defines a query  |
|                                     |             | used to identify |
|                                     |             | the object(s) to |
|                                     |             | test against.    |
+-------------------------------------+-------------+------------------+
| sysdbs                              | String      | This determines  |
|                                     |             | whether the      |
|                                     |             | system databases |
|                                     |             | will be assessed |
|                                     |             | for compliance.  |
+-------------------------------------+-------------+------------------+

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

-  null_test_v1

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

There are no Test Type Parameters.

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
                       <ae:parameter dt="string" name="sql">[sql.value]</ae:parameter>
                       <ae:parameter dt="string" name="sysdbs">[sysdbs.value]</ae:parameter>
                   </ae:parameters>
               </ae:artifact>
               <ae:test type="[TESTTYPE NAME]">
                   <ae:parameters/>
               </ae:test>
           </ae:artifact_expression>
       </xccdf:check-content>
   </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``ms-sql.multi-db-query_sce_v1`` artifacts, the xccdf:check looks
like this.

::

   <check system='http://open-scap.org/page/SCE'>
       <check-import 
           import-name='[import-name.value]'/>
       <check-export 
            export-name='oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]' 
            value-id='xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var'/>
       <check-export 
            export-name='oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]' 
            value-id='xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var'/>
       <check-export 
            export-name='oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]' 
            value-id='xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var'/>
       <check-content-ref 
           href='[BENCHMARK NAME]'/>
   </check>

OVAL
''''

Test

::

   n/a

Object

::

   n/a

State

::

   n/a

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
              name: sql
              type: string
              value: [sql.value]
         - parameter: 
              name: sysdbs
              type: string
              value: [sysdbs.value]
       test:
         type: [TESTTYPE NAME]
         parameters:   

JSON
^^^^

::

   {
       "artifact-expression": {
         "artifact-unique-id": [
           "ARTIFACT-OVAL-ID"
         ],
         "artifact-title": [
           "RECOMMENDATION TITLE"
         ],
         "artifact": {
           "type": [
             "ARTIFACTTYPE NAME"
           ],
           "parameters": [
             {
               "parameter": {
                 "name": "sql",
                 "type": "string",
                 "value": [
                   "sql.value"
                 ]
               }
             },
             {
               "parameter": {
                 "name": "sysdbs",
                 "type": "string",
                 "value": [
                   "sysdbs.value"
                 ]
               }
             }
           ]
         },
         "test": {
           "type": [
             "TESTTYPE NAME"
           ],
           "parameters": null
         }
       }
     }
