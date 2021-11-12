cisco_asa.snmp_group_object
===========================

Description
-----------

The cisco_asa.snmp_group_object is used to check the properties of
specific output lines from an SNMP group configuration.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

======== ====== ====================
Name     Type   Description
======== ====== ====================
name     String The SNMP group name.
operator String Comparison Operator.
======== ====== ====================

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

-  cisco_asa.snmp_groups_priv
-  cisco_asa.existence_check

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

cisco_asa.snmp_groups_priv
^^^^^^^^^^^^^^^^^^^^^^^^^^

================ ====== =============================================
Name             Type   Description
================ ====== =============================================
operator         String Comparison Operator.
snmpv3_sec_level String The SNMPv3 security configured for the group.
================ ====== =============================================

cisco_asa.existence_check
^^^^^^^^^^^^^^^^^^^^^^^^^

=============== ====== =========================================
Name            Type   Description
=============== ====== =========================================
existence_check String Number of lines expected to be collected.
=============== ====== =========================================

existence_check NOTE: This parameter is governed by a constraint
allowing only the following values: - all_exist - any_exist -
at_least_one_exists - none_satisfy - none_exist - only_one_exists

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
                       <ae:parameter dt="string" name="name">[name.value]</ae:parameter>
                       <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
                   </ae:parameters>
               </ae:artifact>
               <ae:test type="[TESTTYPE NAME]">
                   <ae:parameters>
                       <ae:parameter dt="string" name="operator">[operator.value]</ae:parameter>
                       <ae:parameter dt="string" name="snmpv3_sec_level">[snmpv3_sec_level.value]</ae:parameter>
                   </ae:parameters>
               </ae:test>
           </ae:artifact_expression>
       </xccdf:check-content>
   </xccdf:check>

SCAP
^^^^

XCCDF
'''''

For ``cisco_asa.snmp_group_object`` artifacts, the xccdf:check looks
like this.

::

   <check system='http://oval.mitre.org/XMLSchema/oval-definitions-5'>
       <check-export 
            export-name='oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]' 
            value-id='xccdf_org.cisecurity.benchmarks_value_[ARTIFACT-OVAL-ID]_var'/>
       <check-content-ref 
           href='[BENCHMARK NAME]' 
           name='oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]'/>
   </check>

OVAL
''''

Test

::

   <snmp_group_test 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]'
       check_existence='[check_existence.value]' 
       check='[check.value]' 
       comment='[RECOMMENDATION TITLE]'
       version='[version.value]'>
       <object object_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
       <state state_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]'/>
   </snmp_group_test>

Object

::

   <snmp_group_object 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
       comment='[RECOMMENDATION TITLE]'
       version='[version.value]'>
       <name operation='[operation.value]'>[name.value]</name>
   </snmp_group_object>

State

::

   <snmp_group_state 
       xmlns='http://oval.mitre.org/XMLSchema/oval-definitions-5#[PLATFORM]' 
       id='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'
       comment='[RECOMMENDATION TITLE]'
       version='[version.value]'>
       <snmpv3_sec_level operation='[operation.value]' 
           var_ref='oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]'/>
   </snmp_group_state>

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
             name: name
             type: string
             value: [name.value]
         - parameter: 
             name: operator
             type: string
             value: [operator.value]
       test:
         type: [TESTTYPE NAME]
         parameters:   
         - parameter: 
              name: operator
              type: string
              value: [operator.value]
         - parameter: 
              name: snmpv3_sec_level
              type: string
              value: [snmpv3_sec_level.value]

JSON
^^^^

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
                            "name": "name",
                            "type": "string",
                            "value": [
                                "name.value"
                            ]
                        }
                    },
                    {
                        "parameter": {
                            "name": "operator",
                            "type": "string",
                            "value": [
                                "operator.value"
                            ]
                        }
                    }
                ]
            },
            "test": {
                "type": [
                    "TESTTYPE NAME"
                ],
                "parameters": [
                    {
                        "parameter": {
                            "name": "operator",
                            "type": "string",
                            "value": [
                                "operator.value"
                            ]
                        }
                    },
                    {
                        "parameter": {
                            "name": "snmpv3_sec_level",
                            "type": "string",
                            "value": [
                                "snmpv3_sec_level.value"
                            ]
                        }
                    }
                ]
            }
        }
    }