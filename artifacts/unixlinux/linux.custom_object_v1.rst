Linux: Custom Object
====================

Description
-----------

The Linux: Custom Object test is specified by the Custom Object's specified constraint. Please see below:

- The apparmorstatus test is used to check properties representing the counts of profiles and processes as per the results of the "apparmor_status" or "aa-status" command.
    
    Applicable Constraints:

      - AppArmor has loaded profiles
      - No AppArmor Profiles Are In Complain Mode
      - No AppArmor Processes Are Unconfined

- The Debian Package test is used to check information for a given DPKG package. 

    Applicable Constraints:

      - Ensure the X Window system is not installed

- The File test is used to check the contents of a text file (aka a configuration file) by looking at individual blocks of text. 

    Applicable Constraints:

      - Root Path Directories Are Owned By UID 0 And Not Writable By Group Or Other
      - No User Home Directories Have Permissions ----w-rwx
      - No User Dot Files Have Permissions ----w--w-
      - No User .netrc Files Have Permissions ---rwxrwx
      - syslog Log Files Have Correct Permissions
      - rsyslog Log Files Have Correct Permissions
      - No User Home Directories Contain .rhost Files
      - No User Home Directories Contain .netrc Files
      - No User Home Directories Contain .forward Files
      - All User Home Directories Exist
      - All World Writable Directories Have Sticky Bit Set
      - No World Writable Files Exist
      - No Un-owned Files and Directories
      - No Un-grouped Files and Directories

- The inet listening servers test is used to check what applications are listening on the network.  This is limited to applications that are listening for connections that use the TCP or UDP protocols and have addresses represented as IPv4 or IPv6 addresses (AF_INET or AF_INET6). It is generally using the parsed output of running the command netstat -tuwlnpe with root privilege. 

    Applicable Constraints:

     - No Servers Listening On Port 25

- The Invalid Home Directory Ownership test is used to determine what user owns the Home directory.

    Applicable Constraints:

      - Check User Home Directory Ownership

- The password test is used to check specific policy associated with passwords and the device screen lock. 

    Applicable Constraints:

      - Default Group Set For root User
      - System Accounts Disabled
      - Check That Reserved UIDs Are Assigned to System Accounts
      - No Users Have Shadow Group as Primary Group

- The process58_test is used to check information found in the UNIX processes. It is equivalent to parsing the output of the ps command. 

    Applicable Constraints:

      - There Are No Unconfined Daemons
      - chronyd is running as chrony user

- The shadow test is used to check information from the /etc/shadow file for a specific user. This file contains a user's password, but also their password aging and lockout information. 

    Applicable Constraints:
      - Ensure no users with a Password have password expiration over 365 days
      - Ensure no users with a Password have password expiration over 90 days
      - Ensure no users with a Password have password change minimum under 7 days
      - Ensure no users with a Password have password expiration warning under 7 days
      - Ensure no users with a Password have password inactivation over 30 days
      - System Accounts Locked

- The Shell Command test is used to check the output of executed shell commands.

    Applicable Constraints:

     - Firewall Rule Exists For All Open Ports

- The symlink_test is used to obtain canonical path information for symbolic links.

    Applicable Constraints:

     - systemd Does Not Default To graphical.target

- The textfilecontent54_test element is used to check the contents of a text file (aka a configuration file) by looking at individual blocks of text. 

    Applicable Constraints:

      - Shadow Group is Empty
      - /etc/profile.d/* contains "umask 077"
      - All Groups In /etc/passwd Exist In /etc/group
      - auditd Collects Privileged Command Use

- The variable test allows the value of a variable to be compared to a defined value. As an example one might use this test to validate that a variable being passed in from an external source falls within a specified range. 

    Applicable Constraints:

      - Root Path Does Not Include ""
      - Root Path Does Not Include "."
      - Check For Duplicate UIDs
      - Check For Duplicate Group Names
      - Check For Duplicate User Names
      - Check For Duplicate GIDs
      - Ensure all users with a Password have password change date in the past

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

Human ID: 
  - linux.custom_object_v1

.. table:: linux.custom_object_v1_parameters
   :widths: 33, 8, 33
=================================  ========  =================================
Name                               Type      Description	
=================================  ========  =================================
object                             string    The custom object being implemented.
=================================  ========  =================================

NOTE: The ``object`` parameter is governed by a constraint allowing only the following values:
  - N/A
  - All World Writable Directories Have Sticky Bit Set
  - No World Writable Files Exist
  - There Are No Unconfined Daemons
  - No Servers Listening On Port 25
  - System Accounts Disabled
  - System Accounts Locked
  - Default Group Set For root User
  - No Un-owned Files and Directories
  - No Un-grouped Files and Directories
  - systemd Does Not Default To graphical.target
  - rsyslog Log Files Have Correct Permissions
  - syslog Log Files Have Correct Permissions
  - auditd Collects Privileged Command Use
  - Check For Duplicate UIDs
  - Check For Duplicate GIDs
  - Check For Duplicate User Names
  - Check For Duplicate Group Names
  - No User Home Directories Have Permissions ----w-rwx
  - No User Dot Files Have Permissions ----w--w-
  - No User .netrc Files Have Permissions ---rwxrwx
  - No User Home Directories Contain .rhost Files
  - No User Home Directories Contain .netrc Files
  - No User Home Directories Contain .forward Files
  - All Groups In /etc/passwd Exist In /etc/group
  - All User Home Directories Exist
  - /etc/profile.d/* contains "umask 077"
  - Check That Reserved UIDs Are Assigned to System Accounts
  - Root Path Does Not Include ""
  - Root Path Does Not Include "."
  - Root Path Directories Are Owned By UID 0 And Not Writable By Group Or Other
  - Check User Home Directory Ownership
  - AppArmor has loaded profiles
  - No AppArmor Profiles Are In Complain Mode
  - No AppArmor Processes Are Unconfined
  - Shadow Group is Empty
  - No Users Have Shadow Group as Primary Group
  - Ensure the X Window system is not installed
  - Ensure no users with a Password have password expiration over 90 days
  - Ensure no users with a Password have password expiration over 365 days
  - Ensure no users with a Password have password change minimum under 7 days
  - Ensure no users with a Password have password expiration warning under 7 days
  - Ensure no users with a Password have password inactivation over 30 days
  - chronyd is running as chrony user
  - Firewall Rule Exists For All Open Ports
  - Ensure all users with a Password have password change date in the past


Supported Test Types
~~~~~~~~~~~~~~~~~~~~

- Null Test

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

Human ID: 
  - null_test_v1

.. table:: null_test_v1_parameters
   :widths: 33, 8, 33
=================================  ========  =================================
Name                               Type      Description
=================================  ========  =================================
N/A
=================================  ========  =================================


Generated Content
~~~~~~~~~~~~~~~~~

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
              <ae:parameter dt="string" name="object">[object.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters />
          </ae:test>
          <ae:profiles>
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

For ``linux.custom_object_v1`` artifacts, the xccdf:check looks like
this. There is no Value element in the XCCDF for this Artifact.

::

  <xccdf:complex-check operator="OR">
    <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
      <check-content-ref 
        href="[BENCHMARK-TITLE]"
        name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]" />
    </check>
  </xccdf:complex-check>


OVAL
''''

.. _apparmorstatus_test:
apparmorstatus_test
"""""""""""""""""""

Test

  - AppArmor has loaded profiles

::

  <apparmorstatus_test     
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"  
    check_existence="at_least_one_exists"
    check="all"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </apparmorstatus_test>

Object

::

  <apparmorstatus_object 
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1" />

State

::

  <apparmorstatus_state 
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#linux" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <loaded_profiles_count
      datatype="int"
      operation="greater than">
      0
    </loaded_profiles_count>  
  </apparmorstatus_state>

------------

Test

  - No AppArmor Profiles Are In Complain Mode

::

  <apparmorstatus_test     
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"  
    check_existence="at_least_one_exists"
    check="all"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </apparmorstatus_test>

Object

::

  <apparmorstatus_object 
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1" />

State

::

  <apparmorstatus_state 
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#linux" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <complain_mode_profiles_count
      datatype="int"
      operation="equals">
      0
    </complain_mode_profiles_count>  
  </apparmorstatus_state>

------------

Test

  - No AppArmor Processes Are Unconfined

::

  <apparmorstatus_test     
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"  
    check_existence="at_least_one_exists"
    check="all"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </apparmorstatus_test>

Object

::

  <apparmorstatus_object 
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#linux"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1" />

State

::

  <apparmorstatus_state 
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#linux" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <unconfined_processes_with_profiles_count
      datatype="int"
      operation="equals">
      0
    </unconfined_processes_with_profiles_count>    
  </apparmorstatus_state>

------------

.. _dpkginfo_test:
dpkginfo_test
"""""""""""""

Test

  - Ensure the X Window system is not installed

::

  <dpkginfo_test     
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]" 
    check_existence="none_exist"
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
    <name 
      operation="pattern match">
      xserver-xorg-core.*
    </name>
  </dpkginfo_object> 

State

::

N/A

------------

.. _file_test:
file_test
"""""""""

Test

  - Root Path Directories Are Owned By UID 0 And Not Writable By Group Or Other

::

  <file_test     
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="all_exist"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </file_test>

Object

::

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <path var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <filename xsi:nil="true" />
  </file_object> 

  <environmentvariable_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <name>
      PATH
    </name>
  </environmentvariable_object>

State

::

  <file_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <user_id 
      datatype="int">
      0
    </user_id>
    <gwrite 
      datatype="boolean">
      false
    </gwrite>
    <owrite 
      datatype="boolean">
      false
    </owrite>
  </file_state>

Variable

::

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    datatype="string" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <split 
      delimiter=":">
      <object_component 
        item_field="value" 
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
    </split>
  </local_variable>

------------

Test

  - No User Home Directories Have Permissions ----w-rwx

::

  <file_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="any_exist"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </file_test>  

Object 

::

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <path var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <filename xsi:nil="true" />
  </file_object> 
  
  <password_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <username
      operation="pattern match">
      ^(?!root|halt|sync|shutdown).*
    </username>
    <filter
      xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5"
      action="exclude">
      oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]2
    </filter>
  </password_object>  
  
State

::

  <file_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <gwrite 
      datatype="boolean">
      false
    </gwrite>
    <oread 
      datatype="boolean">
      false
    </oread>      
    <owrite 
      datatype="boolean">
      false
    </owrite>
    <oexec 
      datatype="boolean">
      false
    </oexec>      
  </file_state>

  <password_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <login_shell
      operation="pattern match">
      (\\/sbin\\/nologin|\\/usr\\/sbin\\/nologin|\\/bin\\/false)
    </login_shell>
  </password_state>

Variable

::

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    datatype="string" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <split 
      delimiter=":">
      <object_component 
        item_field="home_dir" 
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
    </split>
  </local_variable>

------------

Test

  - No User Dot Files Have Permissions ----w--w-

::

  <file_test     
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="any_exist"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </file_test>  

Object

::

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <path var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <filename 
      operation="pattern match">
      ^\\..+
    </filename>
  </file_object> 

  <password_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <username
      operation="pattern match">
      ^(?!root|halt|sync|shutdown).*
    </username>
    <filter
      xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5"
      action="exclude">
      oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]2
    </filter>
  </password_object>

State

::

  <file_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <gwrite 
      datatype="boolean">
      false
    </gwrite>
    <owrite 
      datatype="boolean">
      false
    </owrite>
  </file_state>

  <password_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <login_shell
      operation="pattern match">
      (\\/sbin\\/nologin|\\/usr\\/sbin\\/nologin|\\/bin\\/false)
    </login_shell>
  </password_state>

Variable

::

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    datatype="string" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <split 
      delimiter=":">
      <object_component 
        item_field="home_dir" 
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
    </split>
  </local_variable>

------------

Test

  - No User .netrc Files Have Permissions ---rwxrwx

::

  <file_test     
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="any_exist"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </file_test>  

Object 

::

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <path var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <filename 
      operation="pattern match">
      .netrc
    </filename>
  </file_object> 

  <password_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <username
      operation="pattern match">
      ^(?!root|halt|sync|shutdown).*
    </username>
    <filter
      xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5"
      action="exclude">
      oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]2
    </filter>
  </password_object>  

State

::

  <file_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <gread 
      datatype="boolean">
      false
    </gread>
    <gwrite 
      datatype="boolean">
      false
    </gwrite>
    <gexec 
      datatype="boolean">
      false
    </gexec>
    <oread 
      datatype="boolean">
      false
    </oread>
    <owrite 
      datatype="boolean">
      false
    </owrite>
    <oexec 
      datatype="boolean">
      false
    </oexec>
  </file_state>  

  <password_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <login_shell
      operation="pattern match">
      (\\/sbin\\/nologin|\\/usr\\/sbin\\/nologin|\\/bin\\/false)
    </login_shell>
  </password_state>  

Variable

::

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    datatype="string" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <split 
      delimiter=":">
      <object_component 
        item_field="home_dir" 
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
    </split>
  </local_variable>

------------

Test

  - syslog Log Files Have Correct Permissions

::

  <file_test     
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </file_test>  

Object 

::

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <filepath var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </file_object> 

  <textfilecontent54_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <filepath>
      /etc/syslog.conf
    </filepath>   
    <pattern
      operation="pattern match">
      ^[^#\$\\r\\n](.*\\s+/.*)\$
    </pattern>
    <instance
      operation="greater than or equal"
      datatype="int">
      1
    </instance>
  </textfilecontent54_object>  

State

::

  <file_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <gwrite 
      datatype="boolean">
      false
    </gwrite>
    <gexec 
      datatype="boolean">
      false
    </gexec>
    <oread 
      datatype="boolean">
      false
    </oread>                   
    <owrite 
      datatype="boolean">
      false
    </owrite>
    <oexec 
      datatype="boolean">
      false
    </oexec>      
  </file_state>  

Variable

::

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    datatype="string" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <regex_capture 
      pattern="^[^#\$\\r\\n].*\\s+(/.*)\$">
      <object_component 
        item_field="subexpression" 
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
    </regex_capture>
  </local_variable>  

------------

Test

  - rsyslog Log Files Have Correct Permissions

::

  <file_test     
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </file_test>  

Object 

::

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <filepath var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </file_object> 

  <textfilecontent54_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <filepath>
      /etc/rsyslog.conf
    </filepath>   
    <pattern
      operation="pattern match">
      ^[^#\$\\r\\n](.*\\s+/.*)\$
    </pattern>
    <instance
      operation="greater than or equal"
      datatype="int">
      1
    </instance>
  </textfilecontent54_object>  

State

::

  <file_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <gwrite 
      datatype="boolean">
      false
    </gwrite>
    <gexec 
      datatype="boolean">
      false
    </gexec>
    <oread 
      datatype="boolean">
      false
    </oread>                   
    <owrite 
      datatype="boolean">
      false
    </owrite>
    <oexec 
      datatype="boolean">
      false
    </oexec>      
  </file_state>  

Variable

::

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    datatype="string" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <regex_capture 
      pattern="^[^#\$\\r\\n].*\\s+(/.*)\$">
      <object_component 
        item_field="subexpression" 
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
    </regex_capture>
  </local_variable>  

------------

Test

  - No User Home Directories Contain .rhost Files

::

  <file_test     
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="none_exist"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </file_test>

Object

::

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <path var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <filename
      operation="pattern match">
      .rhost
    </filename>
  </file_object> 

  <password_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <username>
      operation="pattern match">
      ^(?!root|halt|sync|shutdown).*
    </username>
    <filter
      xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5"
      action="exclude">
      oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]2
    </filter>
  </password_object>

State

::

  <password_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <login_shell 
      operation="pattern match">
      (\\/sbin\\/nologin|\\/usr\\/sbin\\/nologin|\\/bin\\/false)
    </login_shell>
  </password_state>

Variable

::

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    datatype="string" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <split 
      delimiter=":">
      <object_component 
        item_field="home_dir" 
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
    </split>
  </local_variable>

------------

Test

  - No User Home Directories Contain .netrc Files

::

  <file_test     
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="none_exist"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </file_test>

Object

::

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <path var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <filename
      operation="pattern match">
      .netrc
    </filename>
  </file_object> 

  <password_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <username>
      operation="pattern match">
      ^(?!root|halt|sync|shutdown).*
    </username>
    <filter
      xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5"
      action="exclude">
      oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]2
    </filter>
  </password_object>

State

::

  <password_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <login_shell 
      operation="pattern match">
      (\\/sbin\\/nologin|\\/usr\\/sbin\\/nologin|\\/bin\\/false)
    </login_shell>
  </password_state>

Variable

::

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    datatype="string" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <split 
      delimiter=":">
      <object_component 
        item_field="home_dir" 
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
    </split>
  </local_variable>

------------

Test

  - No User Home Directories Contain .forward Files

::

  <file_test     
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="none_exist"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </file_test>

Object

::

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <path var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <filename
      operation="pattern match">
      .forward
    </filename>
  </file_object> 

  <password_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <username
      operation="pattern match">
      ^(?!root|halt|sync|shutdown).*
    </username>
    <filter
      xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5"
      action="exclude">
      oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]2
    </filter>
  </password_object>

State

::

  <password_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <login_shell 
      operation="pattern match">
      (\\/sbin\\/nologin|\\/usr\\/sbin\\/nologin|\\/bin\\/false)
    </login_shell>
  </password_state>

Variable

::

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    datatype="string" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <split 
      delimiter=":">
      <object_component 
        item_field="home_dir" 
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
    </split>
  </local_variable>

------------

Test

  - All User Home Directories Exist

::

  <file_test     
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="all_exist"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </file_test>

Object

::

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <path var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <filename xsi:nil="true" />
  </file_object> 

  <password_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <username
      operation="pattern match">
      ^(?!root|halt|sync|shutdown).*
    </username>
    <filter
      xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5"
      action="exclude">
      oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]
    </filter>
  </password_object>

State

::

  <password_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <login_shell 
      operation="pattern match">
      (\\/sbin\\/nologin|\\/usr\\/sbin\\/nologin|\\/bin\\/false)
    </login_shell>
  </password_state>

Variable

::

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    datatype="string" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <split 
      delimiter=":">
      <object_component 
        item_field="home_dir" 
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
    </split>
  </local_variable>

------------

Test

  - All World Writable Directories Have Sticky Bit Set

::

  <file_test     
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="none_exist"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </file_test>

Object

::

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <behaviors
      recurse_direction="down"
      recurse_file_system="local"
      recurse="directories" />
    <path>
      /
    </path>
    <filename
      xsi:nil="true" />
    <filter
      xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5" 
      action="include">
      oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]
    </filter>
  </file_object>

State

::

  <file_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <sticky 
      datatype="boolean">
      false
    </sticky>
    <owrite 
      datatype="boolean">
      true
    </owrite>
  </file_state>

------------

Test

  - No World Writable Files Exist

::

  <file_test     
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="none_exist"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </file_test>

Object

::

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <behaviors
      recurse_direction="down"
      recurse_file_system="local"
      recurse="directories" />
    <path>
      /
    </path>
    <filename>
      .+
    </filename>
    <filter
      xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5" 
      action="include">
      oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]
    </filter>
  </file_object>

State

::

  <file_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <type 
      datatype="string">
      regular
    </type>
    <owrite 
      datatype="boolean">
      true
    </owrite>
  </file_state>

------------

Test

  - No Un-owned Files and Directories

::

  <file_test     
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="none_exist"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </file_test>

Object

::

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <behaviors
      recurse_direction="down"
      recurse_file_system="local"
      recurse="directories" />
    <path>
      /
    </path>
    <filename>
      .*
    </filename>
    <filter
      xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5">
      oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]
    </filter>
  </file_object>

  <password_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <username
      operation="pattern match">
        .*
    </username>
  </password_object>

State

::

  <file_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <user_id 
      datatype="int"
      var_check="at least one">
      oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]
    </user_id>
  </file_state>

Variable

::

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    datatype="string"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object_component 
      item_field="user_id"
      object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
  </local_variable>

------------

Test

  - No Un-grouped Files and Directories

::

  <file_test     
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="none_exist"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </file_test>

Object

::

  <file_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <behaviors
      recurse_direction="down"
      recurse_file_system="local"
      recurse="directories" />
    <path>
      /
    </path>
    <filename>
      .*
    </filename>
    <filter
      xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5">
      oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]
    </filter>
  </file_object>

  <textfilecontent54_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <filepath>
      /etc/group
    </filepath>
    <pattern
      operation="pattern match">
      ^[^:]+:[^:]*:([\\d]+):[^:]*\$
    </pattern>
    <instance
      operation="greater than or equal"
      datatype="int">
      1
    </instance>            
  </textfilecontent54_object>

State

::

  <file_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <group_id 
      datatype="int"
      var_check="at least one">
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    </group_id>
  </file_state>

Variable

::

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    datatype="string"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object_component 
      item_field="subexpression"
      object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
  </local_variable>  

------------

.. _inetlisteningservers_test:
inetlisteningservers_test
"""""""""""""""""""""""""

Test

  - No Servers Listening On Port 25

::

  <inetlisteningservers_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="none_exist"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
  </inetlisteningservers_test>

Object

::

  <inetlisteningservers_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#linux" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <protocol 
      operation="pattern match">
      .*
    </protocol>
    <local_address 
      operation="pattern match">
      ^(?!127\\.0\\.0\\.1|::1).*\$  
    </local_address>
    <local_port 
      datatype="int"
      operation="greater than or equal">
      0
    </local_port>
  </inetlisteningservers_object>

State

::

N/A

------------

.. _invalidhomedirownership_test:
invalidhomedirownership_test
""""""""""""""""""""""""""""

Test

  - Check User Home Directory Ownership

::

  <invalidhomedirownership_test
    xmlns="http://oval.mitre.org/XMLSchema/x-unix-invalidhomedirownership" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="any_exist"
    check="all"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </invalidhomedirownership_test>

Object

::

  <invalidhomedirownership_object 
    xmlns="http://oval.mitre.org/XMLSchema/x-unix-invalidhomedirownership"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[RECOMMENDATION-TITLE]"
    version="1" />  

State

::

N/A

------------

.. _password_test:
password_test
"""""""""""""

Test

  - Default Group Set For root User

::

  <password_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </password_test>

Object

::

  <password_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <username 
      root
    </username>
  </password_object>

State 

::

  <password_state     
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <group_id 
      datatype="int">
      0
    </group_id>
  </password_state>

------------

Test

  - System Accounts Disabled

::

  <password_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </password_test>

Object

::

  <password_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <username 
      operation="pattern match">
      ^(?!root|sync|shutdown|halt).*\$
    </username>
  </password_object>

State 

::

  <password_state     
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <user_id 
      datatype="int"
      operation="less than">
      500
    </user_id>
    <login_shell
      operation="not equal">
      /sbin/nologin
    </login_shell>
  </password_state>

------------

Test

  - Check That Reserved UIDs Are Assigned to System Accounts

::

  <password_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="any_exist"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </password_test>

Object

::

  <password_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <username 
      operation="pattern match">
      ^(?!root|bin|daemon|adm|lp|sync|shutdown|halt|mail|news|uucp|operator|games|gopher|ftp|nobody|nscd|vcsa|rpc|mailnull|smmsp|pcap|ntp|dbus|avahi|sshd|rpcuser|nfsnobody|haldaemon|avahi-autoipd|distcache|apache|oprofile|webalizer|dovecot|squid|named|xfs|gdm|sabayon|usbmuxd|rtkit|abrt|saslauth|pulse|postfix|tcpdump).*\$
    </username>
  </password_object>

State

::

  <password_state     
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <user_id 
      datatype="int"
      operation="greater than or equal">
      500
    </user_id>
  </password_state>

------------

Test

  - No Users Have Shadow Group as Primary Group

::

  <password_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="any_exist"
    check="none satisfy"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </password_test>

Object

::

  <password_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <username 
      operation="pattern match">
      .+
    </username>
  </password_object>

  <textfilecontent54_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1"> 
    <filepath>
      /etc/group
    </filepath>
    <pattern
      operation="pattern match">
      ^shadow:[^:]*:([^:]*):[^:]*\$
    </pattern>
    <instance>
      operation="greater than or equal"
      datatype="int">
      1
    </instance>
  </textfilecontent54_object>

State 

::

  <password_state     
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <group_id 
      datatype="int"
      operation="greater than or equal"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </password_state>  

Variable

::

  <local_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="string"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object_component
      item_field="subexpression"
      object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
  </local_variable>

------------

.. _process58_test:
process58_test
""""""""""""""

Test

  - There Are No Unconfined Daemons

::

  <process58_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"  
    check_existence="none_exist"
    check="all"    
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </process58_test> 

Object

::
 
  <process58_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <command_line 
      operation="pattern match">
      .*
    </command_line>
    <pid 
      datatype="int" 
      operation="greater than">
      0
    </pid>
    <filter 
      xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5" 
      action="include">
      oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]
    </filter>
  </process58_object>

State 

::

  <process58_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">     
    <selinux_domain_label 
      datatype="string" 
      operation="case insensitive equals">
      initrc_t
    </selinux_domain_label>
  </process58_state>

------------

Test

  - chronyd is running as chrony user

::

  <process58_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"  
    check_existence="none_exist"
    check="all"    
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </process58_test> 

Object

::
 
  <process58_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <command_line 
      operation="pattern match">
      ^chronyd
    </command_line>
    <pid 
      datatype="int" 
      operation="greater than">
      0
    </pid>
    <filter 
      xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5" 
      action="include">
      oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]
    </filter>
  </process58_object>

  <password_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <username>
      chrony
    </username>
  </password_object>

State 

::

  <process58_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">     
    <user_id 
      datatype="int" 
      operation="not equal"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </process58_state>

Variable

::

  <local_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="int"
    comment="[RECOMMENDATION-TITLE]">
    <object_component
      item_field="user_id"
      object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
  </local_variable>
 
------------

.. _shadow_test:
shadow_test
"""""""""""

Test

  - Ensure no users with a Password have password expiration over 365 days

::

  <shadow_test 
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"    
    check_existence="any_exist"
    check="none satisfy"    
    comment="[RECOMMENDATION-TITLE]"
    version="1"> 
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </shadow_test>

Object

::

  <shadow_object 
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"  
    comment="[RECOMMENDATION-TITLE]"
    version="1"> 
    <username 
      operation="pattern match">
      .+
    </username>
  </shadow_object>

State

::

  <shadow_state 
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"    
    comment="[RECOMMENDATION-TITLE]"
    version="1"> 
    <password 
      datatype="string" 
      operation="pattern match">
      ^[^!*]
    </password>
    <chg_req
      datatype="int" 
      operation="greater than">
      365
    </chg_req>
  </shadow_state>

------------

Test

  - Ensure no users with a Password have password expiration over 90 days

::

  <shadow_test 
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"    
    check_existence="any_exist"
    check="none satisfy"    
    comment="[RECOMMENDATION-TITLE]"
    version="1"> 
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </shadow_test>

Object

::

  <shadow_object 
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"  
    comment="[RECOMMENDATION-TITLE]"
    version="1"> 
    <username 
      operation="pattern match">
      .+
    </username>
  </shadow_object>

State

::

  <shadow_state 
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"    
    comment="[RECOMMENDATION-TITLE]"
    version="1"> 
    <password 
      datatype="string" 
      operation="pattern match">
      ^[^!*]
    </password>
    <chg_reg
      datatype="int" 
      operation="greater than">
      90
    </chg_reg>
  </shadow_state>

------------

Test

  - Ensure no users with a Password have password change minimum under 7 days

::

  <shadow_test 
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"    
    check_existence="any_exist"
    check="none satisfy"    
    comment="[RECOMMENDATION-TITLE]"
    version="1"> 
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </shadow_test>

Object

::

  <shadow_object 
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"  
    comment="[RECOMMENDATION-TITLE]"
    version="1"> 
    <username 
      operation="pattern match">
      .+
    </username>
  </shadow_object>

State

::

  <shadow_state 
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"    
    comment="[RECOMMENDATION-TITLE]"
    version="1"> 
    <password 
      datatype="string" 
      operation="pattern match">
      ^[^!*]
    </password>
    <chg_allow
      datatype="int" 
      operation="less than">
      7
    </chg_allow>  
  </shadow_state>

------------

Test

  - Ensure no users with a Password have password expiration warning under 7 days
::

  <shadow_test 
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"    
    check_existence="any_exist"
    check="none satisfy"    
    comment="[RECOMMENDATION-TITLE]"
    version="1"> 
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </shadow_test>

Object

::

  <shadow_object 
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"  
    comment="[RECOMMENDATION-TITLE]"
    version="1"> 
    <username 
      operation="pattern match">
      .+
    </username>
  </shadow_object>

State

::

  <shadow_state 
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"    
    comment="[RECOMMENDATION-TITLE]"
    version="1"> 
    <password 
      datatype="string" 
      operation="pattern match">
      ^[^!*]
    </password>
    <exp_warn
      datatype="int" 
      operation="less than">
      7
    </exp_warn>
  </shadow_state>

------------

Test

  - Ensure no users with a Password have password inactivation over 30 days

::

  <shadow_test 
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"    
    check_existence="any_exist"
    check="none satisfy"    
    comment="[RECOMMENDATION-TITLE]"
    version="1"> 
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </shadow_test>

Object

::

  <shadow_object 
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"  
    comment="[RECOMMENDATION-TITLE]"
    version="1"> 
    <username 
      operation="pattern match">
      .+
    </username>
  </shadow_object>

State

::

  <shadow_state 
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"    
    comment="[RECOMMENDATION-TITLE]"
    version="1"> 
    <password 
      datatype="string" 
      operation="pattern match">
      ^[^!*]
    </password>
    <exp_inact
      datatype="int" 
      operation="less than">
      30
    </exp_inact>
  </shadow_state>

------------

Test

  - System Accounts Locked

::

  <shadow_test 
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"    
    check_existence="any_exist"
    check="all"    
    comment="[RECOMMENDATION-TITLE]"
    version="1"> 
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </shadow_test>

Object

::

  <shadow_object 
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"  
    comment="[RECOMMENDATION-TITLE]"
    version="1"> 
    <username 
      operation="equals"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </shadow_object>

  <password_object 
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2"  
    comment="[RECOMMENDATION-TITLE]"
    version="1"> 
    <username 
      operation="pattern match">
      username
    </username>
    <filter 
      xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5" 
      action="include">
      oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]2
    </filter>    
  </password_object>  

State

::

  <shadow_state 
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"    
    comment="[RECOMMENDATION-TITLE]"
    version="1"> 
    <password 
      operation="pattern match">
      ^!
    </password>
  </shadow_state>  

  <password_state 
    xmlns: "http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]2"    
    comment="[RECOMMENDATION-TITLE]"
    version="1"> 
    <user_id 
      operation="less than"
      datatype="int">
      500
    </user_id>
  </password_state> 

Variable

::

  <local_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"    
    datatype="string"
    comment="[RECOMMENDATION-TITLE]"
    version="1"> 
    <object_component
      item_field="username"
      object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
  </local_variable>

------------

.. _shellcommand_test:
shellcommand_test
"""""""""""""""""

Test

  - Firewall Rule Exists For All Open Ports

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

  <inetlisteningservers_test     
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#cmd" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"    
    check_existence="at_least_one_exists"
    check="all"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
  </inetlisteningservers_test> 

Object

::

  <shellcommand_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#cmd" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <command>
      iptables -L INPUT -v -n
    </command>
    <line_selection 
      operation="pattern match" 
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
  </shellcommand_object> 

  <inetlisteningservers_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#cmd" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <protocol
      operation="pattern match">
      .*
    </protocol> 
    <local_address
      operation="pattern match">
      ^(?!127\\.0\\.0\\.1|::1).*$
    </local_address>
    <local_port
      datatype="int"
      operation="greater than or equal">
      0
    </local_port>
  </inetlisteningservers_object>   

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

Variable

::

  <local_variable 
    comment="[RECOMMENDATION-TITLE]"
    datatype="string" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    version="1">
      <concat>
        <literal_component 
          datatype="string">
          \s+dpt:
        </literal_component>
        <object_component 
          item_field="local_port" 
          object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]2" />
        <literal_component 
          datatype="string">
          \s+state\s+NEW\s*$
        </literal_component>
      </concat>
    </local_variable>

------------

.. _symlink_test:
symlink_test
""""""""""""

Test

  - systemd Does Not Default To graphical.target

::

  <symlink_test     
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"    
    check_existence="any_exist"
    check=""none satisfy"    
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </symlink_test> 

Object

::

  <symlink_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <filepath>
      /etc/systemd/system/default.target
    </filepath>
  </symlink_object> 

State

::

  <symlink_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <canonical_path 
      operation="pattern match">
      ^.*/graphical\.target\$
    </canonical_path>
  </symlink_state>

------------

.. _textfilecontent54_test:
textfilecontent54_test
""""""""""""""""""""""

Test

  - Shadow Group is Empty

::

  <textfilecontent54_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"    
    check_existence="none_exist"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </textfilecontent54_test> 

Object

::

  <textfilecontent54_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <filepath>
      /etc/group
    </filepath>
    <pattern
      operation="pattern match">
      ^shadow:[^:]*:[^:]*:[^:]+\$
    </pattern>
    <instance 
      operation="greater than or equal"
      datatype="int">
      1
    </instance>
  </textfilecontent54_object>

State

::

N/A

------------

Test

  - /etc/profile.d/* contains "umask 077"

::

  <textfilecontent54_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"    
    check_existence="all_exist"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </textfilecontent54_test> 

Object

::

  <textfilecontent54_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <filepath>
      /etc/group
    </filepath>
    <pattern
      operation="pattern match" 
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]">
      ^\s*umask\s+077\s*\$
    </pattern>
    <instance 
      operation="greater than or equal"
      datatype="int">
      1
    </instance>
  </textfilecontent54_object>

  <password_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <username
      operation="pattern match">
      ^(?!root|halt|sync|shutdown).*
    </username>
    <filter
      xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5"
      action-"exclude">
      oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID] 
    </filter>
  </password_object>

State

::

  <password_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1"> 
    <login_shell>
      /sbin/nologin
    </login_shell>
  </password_state>

Variable

::

  <local_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="string" 
    comment="[RECOMMENDATION-TITLE]"
    version="1"> 
    <concat>
      <literal_component
        datatype="string">
        ^[^:]*:[^:]*:
      </literal_component>
      <object_component
        item_field="group_id"
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
      <literal_component
        datatype="string">
        :[^:]*\$
      </literal_component> 
    </concat>
  </local_variable>

------------

Test

  - All Groups In /etc/passwd Exist In /etc/group

::

  <textfilecontent54_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"    
    check_existence="all_exist"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </textfilecontent54_test> 

Object

::

  <textfilecontent54_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <filepath>
      /etc/group
    </filepath>
    <pattern
      operation="pattern match" 
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" />
    <instance 
      operation="greater than or equal"
      datatype="int">
      1
    </instance>
  </textfilecontent54_object>

  <password_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <username
      operation="pattern match">
      ^(?!root|halt|sync|shutdown).*
    </username>
    <filter
      xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5"
      action-"exclude">
      oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID] 
    </filter>
  </password_object>

State

::

  <password_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1"> 
    <login_shell>
      /sbin/nologin
    </login_shell>
  </password_state>

Variable

::

  <local_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="string" 
    comment="[RECOMMENDATION-TITLE]"
    version="1"> 
    <concat>
      <literal_component
        datatype="string">
        ^[^:]*:[^:]*:
      </literal_component>
      <object_component
        item_field="group_id"
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
      <literal_component
        datatype="string">
        :[^:]*\$
      </literal_component> 
    </concat>
  </local_variable>

------------

Test

  - auditd Collects Privileged Command Use

::

  <textfilecontent54_test 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"    
    check_existence= "all_exist"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
  </textfilecontent54_test> 

Object

::

  <textfilecontent54_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <filepath>
      /etc/audit/audit.rules
    </filepath>
    <pattern
      operation="pattern match" 
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]">
    </pattern>
    <instance 
      operation="greater than or equal"
      datatype="int">
      1
    </instance>
  </textfilecontent54_object>

  <file_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <behaviors
      recurse_direction="down"
      recurse_file_system="local"
      recurse="directories"
    </behaviors>
    <path>
      /
    </path>
    <filename
      operation="pattern match">
      .+
    </filename>
    <filter
      xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5" 
      action="exclude">
      oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]
    </filter>
  </file_object>

State

::

  <file_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <suid
      datatype="boolean"> 
      false
    </suid>
    <sgid
      datatype="boolean">
      false
    </sgid>
  </file_state>

Variable

::

  <local_variable
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]"
    datatype="string" 
    comment="[RECOMMENDATION-TITLE]"
    version="1"> 
    <concat>
      <literal_component
        datatype="string">
        ^\-a (always,exit|exit,always) \-F path=
      </literal_component>
      <object_component
        item_field="filepath"
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
      <literal_component
        datatype="string">
         \\-F perm=x \\-F auid>=500 \\-F auid!=4294967295 \\-k privileged\$
      </literal_component> 
    </concat>
  </local_variable>

------------

.. _variable_test:
variable_test
"""""""""""""

Test

  - Root Path Does Not Include ""

::

  <variable_test     
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="all_exist"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </variable_test>   

Object      

::

  <variable_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <var_ref>
      oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]
    </var_ref>
  </variable_object>  

  <environmentvariable_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <name>
      PATH
    </name>
  </environmentvariable_object>

State     

::

  <variable_state 
    xmlns= "http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <value 
      datatype="string" 
      operation="not equal" />
    <value 
      datatype="string" 
      operation="not equal" />    
  </variable_state>

Variable

::

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    datatype="string"
    comment="[RECOMMENDATION-TITLE]"      
    version="1">
    <split 
      delimiter=":">
      <object_component 
        item_field="value" 
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
    </split>
  </local_variable>

------------

Test

  - Root Path Does Not Include "."

::

  <variable_test     
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="all_exist"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </variable_test>   

Object      

::

  <variable_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <var_ref>
      oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]
    </var_ref>
  </variable_object>  

  <environmentvariable_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <name>
      PATH
    </name>
  </environmentvariable_object>

State     

::

  <variable_state 
    xmlns= "http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <value 
      datatype="string" 
      operation="not equal" />
    <value 
      datatype="string" 
      operation="not equal">
      .
    </value>      
  </variable_state>

Variable

::

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    datatype="string"
    comment="[RECOMMENDATION-TITLE]"      
    version="1">
    <split 
      delimiter=":">
      <object_component 
        item_field="value" 
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
    </split>
  </local_variable>

------------

Test

  - Check For Duplicate UIDs

::

  <variable_test     
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </variable_test>   

Object

::

  <variable_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <var_ref>
      oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]
    </var_ref>
  </variable_object>  

  <password_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <username
      datatype="string"
      operation="pattern match">
      .*
    </username>
  </password_object>

State

::

  <variable_state 
    xmlns= "http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <value 
      datatype="int" 
      operation="equals"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2">
      .
  </variable_state>

Variable

::

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    datatype="int"
    comment="[RECOMMENDATION-TITLE]"      
    version="1">
    <count>
      <object_component 
        item_field="user_id" 
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
    </count>
  </local_variable>

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2" 
    datatype="int"
    comment="[RECOMMENDATION-TITLE]"      
    version="1">
    <count>
      <unique>
        <object_component 
          item_field="user_id" 
          object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
      </unique>
    </count>
  </local_variable>  

------------

Test

  - Check For Duplicate Group Names

::

  <variable_test     
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </variable_test>   

Object

::

  <variable_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <var_ref>
      oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]
    </var_ref>
  </variable_object>  

  <textfilecontent54_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <filepath>
      /etc/group
    <filepath>
    <pattern
      operation="pattern match">
      ^[^:]+:[^:]+:([\\d]+):[^:]*\$
    </pattern>
    <instance
      operation="greater than or equal"
      datatype="int">
      1
    </instance>
  </textfilecontent54_object>

State

::

  <variable_state 
    xmlns= "http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <value
      datatype="int"
      operation="equals"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2" />
    </value>
  </variable_state>

Variable

::

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    datatype="int"
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <count>
      <object_component 
        item_field="subexpression" 
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
    </count>
  </local_variable>

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2" 
    datatype="int"
    comment="[RECOMMENDATION-TITLE]"      
    version="1">
    <count>
      <unique>
        <object_component 
          item_field="item_field" 
          object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
      </unique>
    </count>
  </local_variable>

------------

Test

  - Check For Duplicate User Names

::

  <variable_test     
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </variable_test>   

Object

::

  <variable_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <var_ref>
      oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]
    </var_ref>
  </variable_object>  

  <textfilecontent54_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <filepath>
      /etc/passwd
    <filepath>
    <pattern
      operation="pattern match">
      ^([^:]+):[^:]*:[^:]*:[^:]*:[^:]*:[^:]*:[^:]*\$
    </pattern>
    <instance
      operation="greater than or equal"
      datatype="int">
      1
    </instance>
  </textfilecontent54_object>

State

::

  <variable_state 
    xmlns= "http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <value
      datatype="int
      operation="equals"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2" />
  </variable_state>

Variable

::

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    datatype="int"
    comment="[RECOMMENDATION-TITLE]"      
    version="1">
    <count>
      <object_component 
        item_field="subexpression" 
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
    </count>
  </local_variable>

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2" 
    datatype="int"
    comment="[RECOMMENDATION-TITLE]"      
    version="1">
    <count>
      <unique>
        <object_component 
          item_field="subexpression" 
          object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
      </unique>
    </count>
  </local_variable>  

------------

Test

  - Check For Duplicate GIDs

::

  <variable_test     
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </variable_test>   

Object

::

  <variable_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <var_ref>
      oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]
    </var_ref>
  </variable_object>  

  <textfilecontent54_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <filepath>
      /etc/group
    </filepath>
    <pattern
      operation="pattern match">
      ^([^:]+):[^:]+:[\\d]+:[^:]*\$
    </pattern>
    <instance
      operation="greater than or equal"
      datatype="int">
      1
    </instance>
  </textfilecontent54_object>

State

::

  <variable_state 
    xmlns= "http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <value
      datatype="int
      operation="equals"
      var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2" />
  </variable_state>

Variable

::

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    datatype="int"
    comment="[RECOMMENDATION-TITLE]"      
    version="1">
    <count>
      <object_component 
        item_field="subexpression" 
        object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
    </count>
  </local_variable>

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2" 
    datatype="int"
    comment="[RECOMMENDATION-TITLE]"      
    version="1">
    <count>
      <unique>
        <object_component 
          item_field="subexpression" 
          object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" />
      </unique>
    </count>
  </local_variable> 

------------

Test

  - Ensure all users with a Password have password change date in the past

::

  <variable_test     
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="at_least_one_exists"
    check="all"  
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </variable_test>   

Object

::

  <shadow_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#unix 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <username
      operation="pattern match">
      .+
    </username>
  </shadow_object>  

  <variable_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]2" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <var_ref>
      oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2
    </var_ref>
  </variable_object>  

  <variable_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#independent 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]3" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <var_ref>
      oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]3
    </var_ref>      
  </variable_object>

State

::

  <variable_state 
    xmlns= "http://oval.mitre.org/XMLSchema/oval-definitions-5#independent" 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" 
    comment="[RECOMMENDATION-TITLE]"
    version="1">
    <value 
      datatype="int" 
      operation="greater than or equal">
      0
    </value>
  </variable_state>

Variable

::

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]" 
    datatype="int"
    comment="[RECOMMENDATION-TITLE]"      
    version="1">
    <time_difference
      format_1="seconds_since_epoch"
      format_2="seconds_since_epoch">
      <variable_component 
        var_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2" />
    </count>
  </local_variable>  

  <local_variable 
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:var:[ARTIFACT-OVAL-ID]2" 
    datatype="int"
    comment="[RECOMMENDATION-TITLE]"      
    version="1">
    <arithmetic
      arithmetic_operation="multiply">
        <object_component 
          object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
          item_field="chg_lst" />
        <literal_component 
          datatype="int">
          86400
        </literal_component>
    </arithmetic>
  </local_variable>      

------------


YAML
^^^^

::

  - artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact-title: "[RECOMMENDATION-TITLE]"
    artifact:
      type: "[ARTIFACT-TYPE-NAME]"
      parameters:
      - parameter: 
          name: "object"
          dt: "string"
          value: "[object.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters: []


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
              "name": "object",
              "type": "string",
              "value": "[object.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [

        ]
      }
    }
  }