macos:pwpolicy59
================

Description
-----------

The macos:pwpolicy59 test retrieves password policy data from the 'pwpolicy
-getpolicy -u target_user [-a username] [-p userpass] [-n directory_node]'
output where username, userpass, and directory_node are optional.

The pwpolicy59 object element is used by a pwpolicy59_test to define the object to be evaluated.

The pwpolicy59 state element defines the different information that can be used to evaluate the
password policy for the target user in the specified directory node.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**macos.pwpolicy59_v1**

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| target_user                         | string      | The target_user  |
|                                     |             | element          |
|                                     |             | specifies the    |
|                                     |             | user whose       |
|                                     |             | password policy  |
|                                     |             | information      |
|                                     |             | should be        |
|                                     |             | collected. If an |
|                                     |             | operation other  |
|                                     |             | than equals is   |
|                                     |             | specified, the   |
|                                     |             | users on the     |
|                                     |             | system should be |
|                                     |             | enumerated and   |
|                                     |             | the 'pwpolicy'   |
|                                     |             | command should   |
|                                     |             | be issued for    |
|                                     |             | each user that   |
|                                     |             | matches the      |
|                                     |             | target_user      |
|                                     |             | element. If the  |
|                                     |             | xsi:nil          |
|                                     |             | attribute is     |
|                                     |             | set to true,     |
|                                     |             | the global       |
|                                     |             | policy should be |
|                                     |             | retrieved.       |
+-------------------------------------+-------------+------------------+
| username                            | string      | The username     |
|                                     |             | element          |
|                                     |             | specifies the    |
|                                     |             | username of the  |
|                                     |             | authenticator.   |
|                                     |             | If the xsi:nil   |
|                                     |             | attribute is set |
|                                     |             | to true,         |
|                                     |             | authentication   |
|                                     |             | to the directory |
|                                     |             | node will not be |
|                                     |             | performed (i.e.  |
|                                     |             | the '-a' and     |
|                                     |             | '-p' command     |
|                                     |             | line options     |
|                                     |             | will not be      |
|                                     |             | specified when   |
|                                     |             | issuing the      |
|                                     |             | 'pwpolicy'       |
|                                     |             | command) and the |
|                                     |             | xsi:nil          |
|                                     |             | attribute of the |
|                                     |             | userpass element |
|                                     |             | should also be   |
|                                     |             | set to true.     |
|                                     |             |                  |
+-------------------------------------+-------------+------------------+
| userpass                            | string      | The userpass     |
|                                     |             | element          |
|                                     |             | specifies the    |
|                                     |             | password of the  |
|                                     |             | authenticator as |
|                                     |             | specified by the |
|                                     |             | username         |
|                                     |             | element. If the  |
|                                     |             | xsi:nil          |
|                                     |             | attribute is set |
|                                     |             | to true,         |
|                                     |             | authentication   |
|                                     |             | to the directory |
|                                     |             | node will not be |
|                                     |             | performed (i.e.  |
|                                     |             | the '-a' and     |
|                                     |             | '-p' command     |
|                                     |             | line options     |
|                                     |             | will not be      |
|                                     |             | specified when   |
|                                     |             | issuing the      |
|                                     |             | 'pwpolicy'       |
|                                     |             | command) and the |
|                                     |             | xsi:nil          |
|                                     |             | attribute of the |
|                                     |             | username element |
|                                     |             | should also be   |
|                                     |             | set to true.     |
+-------------------------------------+-------------+------------------+
| directory_node                      | string      | The              |
|                                     |             | directory_node   |
|                                     |             | element          |
|                                     |             | specifies the    |
|                                     |             | directory node   |
|                                     |             | that you would   |
|                                     |             | like to retrieve |
|                                     |             | the password     |
|                                     |             | policy           |
|                                     |             | information      |
|                                     |             | from. If the     |
|                                     |             | xsi:nil          |
|                                     |             | attribute is set |
|                                     |             | to true, the     |
|                                     |             | default          |
|                                     |             | directory node   |
|                                     |             | is used (i.e the |
|                                     |             | '-n' command     |
|                                     |             | line option will |
|                                     |             | will not be      |
|                                     |             | specified when   |
|                                     |             | issuing the      |
|                                     |             | 'pwpolicy'       |
|                                     |             | command).        |
+-------------------------------------+-------------+------------------+
| check_existence                     | string      | Defines how many |
|                                     |             | items should be  |
|                                     |             | collected.       |
+-------------------------------------+-------------+------------------+

NOTE: The ``target_user`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``username`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``userpass`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``directory_node`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values:
   -  all_exist
   -  any_exist
   -  at_least_one_exists
   -  none_exist
   -  only_one_exists

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

-  macos.pwpolicy59_v1

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**macos.pwpolicy59_v1**

+-------------------------------------+-------------+------------------+
| Name                                | Type        | Description      |
+=====================================+=============+==================+
| check                               | string      | Defines how many |
|                                     |             | collected items  |
|                                     |             | must match the   |
|                                     |             | expected state.  |
+-------------------------------------+-------------+------------------+
| operation                           | string      | Comparison       |
|                                     |             | operation.       |
+-------------------------------------+-------------+------------------+
| datatype                            | string      | The data type of |
|                                     |             | the value.       |
+-------------------------------------+-------------+------------------+
| target_user                         | string      | The target_user  |
|                                     |             | element          |
|                                     |             | specifies the    |
|                                     |             | user whose       |
|                                     |             | password policy  |
|                                     |             | information      |
|                                     |             | should be        |
|                                     |             | collected.       |
+-------------------------------------+-------------+------------------+
| username                            | string      | The username     |
|                                     |             | element          |
|                                     |             | specifies the    |
|                                     |             | username of the  |
|                                     |             | authenticator.   |
+-------------------------------------+-------------+------------------+
| userpass                            | string      | The userpass     |
|                                     |             | element          |
|                                     |             | specifies the    |
|                                     |             | password of the  |
|                                     |             | authenticator as |
|                                     |             | specified by the |
|                                     |             | username         |
|                                     |             | element.         |
+-------------------------------------+-------------+------------------+
| directory_node                      | string      | The              |
|                                     |             | directory_node   |
|                                     |             | element          |
|                                     |             | specifies the    |
|                                     |             | directory node   |
|                                     |             | that you would   |
|                                     |             | like to retrieve |
|                                     |             | the password     |
|                                     |             | policy           |
|                                     |             | information      |
|                                     |             | from.            |
+-------------------------------------+-------------+------------------+
| maxChars                            | integer     | Maximum number   |
|                                     |             | of characters    |
|                                     |             | allowed in a     |
|                                     |             | password.        |
+-------------------------------------+-------------+------------------+
| maxFailedLoginAttempts              | integer     | Maximum number   |
|                                     |             | of failed logins |
|                                     |             | before the       |
|                                     |             | account is       |
|                                     |             | locked.          |
+-------------------------------------+-------------+------------------+
| passwordCannotBeName                | boolean     | Defines if the   |
|                                     |             | password is      |
|                                     |             | allowed to be    |
|                                     |             | the same as the  |
|                                     |             | username or not. |
+-------------------------------------+-------------+------------------+
| requiresAlpha                       | boolean     | Defines if the   |
|                                     |             | password must    |
|                                     |             | contain an       |
|                                     |             | alphabetical     |
|                                     |             | character or     |
|                                     |             | not.             |
+-------------------------------------+-------------+------------------+
| requiresNumeric                     | boolean     | Defines if the   |
|                                     |             | password must    |
|                                     |             | contain an       |
|                                     |             | numeric          |
|                                     |             | character or     |
|                                     |             | not.             |
+-------------------------------------+-------------+------------------+
| maxMinutesUntilChangePassword       | integer     | Maximum number   |
|                                     |             | of minutes until |
|                                     |             | the password     |
|                                     |             | must be changed. |
+-------------------------------------+-------------+------------------+
| minMinutesUntilChangePassword       | integer     | Minimum number   |
|                                     |             | of minutes       |
|                                     |             | between password |
|                                     |             | changes.         |
+-------------------------------------+-------------+------------------+
| requiresMixedCase                   | boolean     | Defines if the   |
|                                     |             | password must    |
|                                     |             | contain upper    |
|                                     |             | and lower case   |
|                                     |             | characters or    |
|                                     |             | not.             |
+-------------------------------------+-------------+------------------+
| requiresSymbol                      | boolean     | Defines if the   |
|                                     |             | password must    |
|                                     |             | contain a symbol |
|                                     |             | character or     |
|                                     |             | not.             |
+-------------------------------------+-------------+------------------+
| minutesUntilFailedLoginReset        | integer     | Number of        |
|                                     |             | minutes after    |
|                                     |             | login has been   |
|                                     |             | disabled due to  |
|                                     |             | too many failed  |
|                                     |             | login attempts   |
|                                     |             | to wait before   |
|                                     |             | reenabling       |
|                                     |             | login.           |
+-------------------------------------+-------------+------------------+
| usingHistory                        | integer     | 0 = user can     |
|                                     |             | reuse the        |
|                                     |             | current          |
|                                     |             | pass-word, 1 =   |
|                                     |             | user cannot      |
|                                     |             | reuse the        |
|                                     |             | current          |
|                                     |             | password,        |
|                                     |             | 2-15 = user      |
|                                     |             | cannot reuse the |
|                                     |             | last n           |
|                                     |             | passwords.       |
+-------------------------------------+-------------+------------------+
| canModifyPasswordforSelf            | boolean     | If true, the     |
|                                     |             | user can change  |
|                                     |             | the password.    |
+-------------------------------------+-------------+------------------+
| usingExpirationDate                 | boolean     | If true, user is |
|                                     |             | required to      |
|                                     |             | change password  |
|                                     |             | on the date in   |
|                                     |             | expirationDate   |
|                                     |             | GMT.              |
+-------------------------------------+-------------+------------------+
| usingHardExpirationDate             | boolean     | If true, user's  |
|                                     |             | account is       |
|                                     |             | disabled on the  |
|                                     |             | date in          |
|                                     |             | hardExpireDate   |
|                                     |             | GMT.             |
+-------------------------------------+-------------+------------------+
| expirationDateGMT                   | string      | Date for the     |
|                                     |             | password to      |
|                                     |             | expire, format   |
|                                     |             | is: mm/dd/yyyy.  |
|                                     |             | NOTE: The        |
|                                     |             | pwpolicy command |
|                                     |             | returns the year |
|                                     |             | as a two digit   |
|                                     |             | value, but OVAL  |
|                                     |             | uses four digit  |
|                                     |             | years; the       |
|                                     |             | pwpolicy value   |
|                                     |             | is converted to  |
|                                     |             | an OVAL          |
|                                     |             | compatible       |
|                                     |             | value.           |
+-------------------------------------+-------------+------------------+
| hardExpireDateGMT                   | string      | Date for the     |
|                                     |             | user's account   |
|                                     |             | to be disabled,  |
|                                     |             | format is: mm/dd |
|                                     |             | /yyyy. NOTE: The |
|                                     |             | pwpolicy command |
|                                     |             | returns the year |
|                                     |             | as a two digit   |
|                                     |             | value, but OVAL  |
|                                     |             | uses four digit  |
|                                     |             | years; the       |
|                                     |             | pwpolicy value   |
|                                     |             | is converted to  |
|                                     |             | an OVAL          |
|                                     |             | compatible       |
|                                     |             | value.           |
+-------------------------------------+-------------+------------------+
| maxMinutesUntilDisabled             | integer     | User's account   |
|                                     |             | is disabled      |
|                                     |             | after this       |
|                                     |             | interval.        |
+-------------------------------------+-------------+------------------+
| maxMinutesOfNonUse                  | integer     | User's account   |
|                                     |             | is disabled if   |
|                                     |             | it is not        |
|                                     |             | accessed by this |
|                                     |             | interval.        |
+-------------------------------------+-------------+------------------+
| newPasswordRequired                 | boolean     | If true, the     |
|                                     |             | user will be     |
|                                     |             | prompted for a   |
|                                     |             | new password at  |
|                                     |             | the next         |
|                                     |             | authentication.  |
+-------------------------------------+-------------+------------------+
| notGuessablePattern                 | boolean     | Defines if the   |
|                                     |             | pattern is       |
|                                     |             | guessable or not |
+-------------------------------------+-------------+------------------+

NOTE: The ``check`` parameter is governed by a constraint allowing only the following values:
   -  all
   -  at least one
   -  none satisfy
   -  only one

NOTE: The ``operation`` parameter is governed by a constraint allowing only the following values:
   -  equals
   -  not equal
   -  case insensitive equals
   -  case insensitive not equal
   -  greater than
   -  less than
   -  greater than or equal
   -  less than or equal
   -  bitwise and
   -  bitwise or
   -  pattern match
   -  subset of
   -  superset of

NOTE: The ``datatype`` parameter is governed by a constraint allowing only the following values:
   -  boolean
   -  float
   -  int
   -  string
   -  version
   -  set

NOTE: The ``target_user`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``username`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``userpass`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``directory_node`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``maxChars`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``maxFailedLoginAttempts`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``minChars`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``passwordCannotBeName`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``requiresAlpha`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``requiresNumeric`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``maxMinutesUntilChangePassword`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``minMinutesUntilChangePassword`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``requiresMixedCase`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``requiresSymbol`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``minutesUntilFailedLoginReset`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``usingHistory`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``canModifyPasswordforSelf`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``usingExpirationDate`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``usingHardExpirationDate`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``expirationDateGMT`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``hardExpireDateGMT`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``maxMinutesUntilDisabled`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``maxMinutesOfNonUse`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``newPasswordRequired`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

NOTE: The ``notGuessablePattern`` parameter is governed by a constraint allowing only the following values:
   -  ^.+$

Generated Content
~~~~~~~~~~~~~~~~~

**macos.pwpolicy59_v1**

XCCDF+AE
^^^^^^^^

This is what the AE check looks like, inside a Rule, in the XCCDF.

::

  <xccdf:complex-check operator="AND">
    <xccdf:check system="https://benchmarks.cisecurity.org/ae/0.5">
      <xccdf:check-content>
        <ae:artifact_expression id="xccdf_org.cisecurity.benchmarks_ae_[SECTION-NUMBER]">
          <ae:artifact_oval_id>[ARTIFACT-OVAL-ID]</ae:artifact_oval_id>
          <ae:title>[RECOMMENDATION-TITLE]</ae:title>
          <ae:artifact type="[ARTIFACT-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="target_user">[target_user.value]</ae:parameter>
              <ae:parameter dt="string" name="username">[username.value]</ae:parameter>
              <ae:parameter dt="string" name="userpass">[userpass.value]</ae:parameter>
              <ae:parameter dt="string" name="directory_node">[directory_node.value]</ae:parameter>
              <ae:parameter dt="string" name="check_existence">[check_existence.value]</ae:parameter>
            </ae:parameters>
          </ae:artifact>
          <ae:test type="[TEST-TYPE-NAME]">
            <ae:parameters>
              <ae:parameter dt="string" name="check">[check.value]</ae:parameter>
              <ae:parameter dt="string" name="operation">[operation.value]</ae:parameter>
              <ae:parameter dt="string" name="datatype">[datatype.value]</ae:parameter>
              <ae:parameter dt="string" name="target_user">[target_user.value]</ae:parameter>
              <ae:parameter dt="string" name="username">[username.value]</ae:parameter>
              <ae:parameter dt="string" name="userpass">[userpass.value]</ae:parameter>
              <ae:parameter dt="string" name="directory_node">[directory_node.value]</ae:parameter>
              <ae:parameter dt="integer" name="maxChars">[maxChars.value]</ae:parameter>
              <ae:parameter dt="integer" name="maxFailedLoginAttempts">[maxFailedLoginAttempts.value]</ae:parameter>
              <ae:parameter dt="integer" name="minChars">[minChars.value]</ae:parameter>
              <ae:parameter dt="boolean" name="passwordCannotBeName">[passwordCannotBeName.value]</ae:parameter>
              <ae:parameter dt="boolean" name="requiresAlpha">[requiresAlpha.value]</ae:parameter>
              <ae:parameter dt="boolean" name="requiresNumeric">[requiresNumeric.value]</ae:parameter>
              <ae:parameter dt="integer" name="maxMinutesUntilChangePassword">[maxMinutesUntilChangePassword.value]</ae:parameter>
              <ae:parameter dt="integer" name="minMinutesUntilChangePassword">[minMinutesUntilChangePassword.value]</ae:parameter>
              <ae:parameter dt="boolean" name="requiresMixedCase">[requiresMixedCase.value]</ae:parameter>
              <ae:parameter dt="boolean" name="requiresSymbol">[requiresSymbol.value]</ae:parameter>
              <ae:parameter dt="integer" name="minutesUntilFailedLoginReset">[minutesUntilFailedLoginReset.value]</ae:parameter>
              <ae:parameter dt="integer" name="usingHistory">[usingHistory.value]</ae:parameter>
              <ae:parameter dt="boolean" name="canModifyPasswordforSelf">[canModifyPasswordforSelf.value]</ae:parameter>
              <ae:parameter dt="boolean" name="usingExpirationDate">[usingExpirationDate.value]</ae:parameter>
              <ae:parameter dt="boolean" name="usingHardExpirationDate">[usingHardExpirationDate.value]</ae:parameter>
              <ae:parameter dt="string" name="expirationDateGMT">[expirationDateGMT.value]</ae:parameter>
              <ae:parameter dt="string" name="hardExpireDateGMT">[hardExpireDateGMT.value]</ae:parameter>
              <ae:parameter dt="integer" name="maxMinutesUntilDisabled">[maxMinutesUntilDisabled.value]</ae:parameter>
              <ae:parameter dt="integer" name="maxMinutesOfNonUse">[maxMinutesOfNonUse.value]</ae:parameter>
              <ae:parameter dt="boolean" name="newPasswordRequired">[newPasswordRequired.value]</ae:parameter>
              <ae:parameter dt="boolean" name="notGuessablePattern">[notGuessablePattern.value]</ae:parameter>
            </ae:parameters>
          </ae:test>
          <ae:profiles>
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1"/>
          </ae:profiles>
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  </xccdf:complex-check>

SCAP
^^^^

XCCDF
'''''

For ``macos.pwpolicy59_v1`` artifacts, the xccdf:check looks like this.
There is no Value in the xccdf for this Artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-content-ref
      href="[BENCHMARK-NAME]"
        name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]">
    </check-content-ref>
  </check>

OVAL
''''

Test

::

  <pwpolicy59_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    check="[check.value]"
    check_existence="[check_existence.value]"
    comment="[ARTIFACT-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </pwpolicy59_test>

Object

::

  <pwpolicy59_object
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    comment="[ARTIFACT-TITLE]"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    version="1">
    <target_user>
        [target_user.value]
    </target_user>
    <username>
        [username.value]
    </username>
    <userpass>
        [password.value]
    </userpass>
    <directory_node>
        [directory_node.value]
    </directory_node>
  </pwpolicy59_object>

State

::

  <pwpolicy59_state
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    comment="[ARTIFACT-TITLE]"
    id="oval:org.cisecurity.benchmarks.apple_mac_os_x_10:ste:2142225"
    version="1">
    <target_user
      datatype="string"
      operation="equals">
        [target_user.value]
    </target_user>
    <username
      datatype="string"
      operation="equals">
        [username.value]
    </username>
    <userpass
      datatype="string"
      operation="equals">
        [userpass.value]
    </userpass>
    <directory_node
      datatype="string"
      operation="equals">
        [directory_node.value]
    </directory_node>
    <maxChars
      datatype="int"
      operation="equals">
        [maxChars.value]
    </maxChars>
    <maxFailedLoginAttempts
      datatype="int"
      operation="equals">
        [maxFailedLoginAttempts.value]
    </maxFailedLoginAttempts>
    <minChars
      datatype="int"
      operation="equals">
        [minChars.value]
    </minChars>
    <passwordCannotBeName
      datatype="boolean"
      operation="equals">
        [passwordCannotBeName.value]
    </passwordCannotBeName>
    <requiresAlpha
      datatype="boolean"
      operation="equals">
        [requiresAlpha.value]
    </requiresAlpha>
    <requiresNumeric
      datatype="boolean"
      operation="equals">
        [requiresNumeric.value]
    </requiresNumeric>
    <maxMinutesUntilChangePassword
      datatype="int"
      operation="equals">
        [maxMinutesUntilChangePassword.value]
    </maxMinutesUntilChangePassword>
    <minMinutesUntilChangePassword
      datatype="int"
      operation="equals">
        [minMinutesUntilChangePassword.value]
    </minMinutesUntilChangePassword>
    <requiresMixedCase
      datatype="boolean"
      operation="equals">
        [requiresMixedCase.value]
    </requiresMixedCase>
    <requiresSymbol
      datatype="boolean"
      operation="equals">
        [requiresSymbol.value]
    </requiresSymbol>
    <minutesUntilFailedLoginReset
      datatype="int"
      operation="equals">
        [minutesUntilFailedLoginReset.value]
    </minutesUntilFailedLoginReset>
    <usingHistory
      datatype="int"
      operation="equals">
        [usingHistory.value]
    </usingHistory>
    <canModifyPasswordforSelf
      datatype="boolean"
      operation="equals">
        [canModifyPasswordforSelf.value]
    </canModifyPasswordforSelf>
    <usingExpirationDate
      datatype="boolean"
      operation="equals">
        [usingExpirationDate.value]
    </usingExpirationDate>
    <usingHardExpirationDate
      datatype="boolean"
      operation="equals">
        [usingHardExpirationDate.value]
    </usingHardExpirationDate>
    <expirationDateGMT
      datatype="string"
      operation="equals">
        [expirationDateGMT.value]
    </expirationDateGMT>
    <hardExpireDateGMT
      datatype="string"
      operation="equals">
        [hardExpireDateGMT.value]
    </hardExpireDateGMT>
    <maxMinutesUntilDisabled
      datatype="int"
      operation="equals">
        [maxMinutesUntilDisabled.value]
    </maxMinutesUntilDisabled>
    <maxMinutesOfNonUse
      datatype="int"
      operation="equals">
        [maxMinutesOfNonUse.value]
    </maxMinutesOfNonUse>
    <newPasswordRequired
      datatype="boolean"
      operation="equals">
        [newPasswordRequired.value]
    </newPasswordRequired>
    <notGuessablePattern
      datatype="boolean"
      operation="equals">
        [notGuessablePattern.value]
    </notGuessablePattern>
  </pwpolicy59_state>

YAML
^^^^

::

  artifact-expression:
    artifact-unique-id: "[ARTIFACT-OVAL-ID]"
    artifact_title: "[ARTIFACT-TITLE]"
    artifact:
      type: "macos.pwpolicy59_v1"
      parameters:
        - parameter:
            name: "target_user"
            dt: "string"
            value: "[target_user.value]"
        - parameter:
            name: "username"
            dt: "string"
            value: "[username.value]"
        - parameter:
            name: "userpass"
            dt: "string"
            value: "[password.value]"
        - parameter:
            name: "directory_node"
            dt: "string"
            value: "[directory_node.value]"
        - parameter:
            name: "check_existence"
            dt: "string"
            value: "[check_existence.value]"
    test:
      type: "[TEST-TYPE-NAME]"
      parameters:
        - parameter:
            name: "check"
            dt: "string"
            value: "[check.value]"
        - parameter:
            name: "operation"
            dt: "string"
            value: "[operation.value]"
        - parameter:
            name: "datatype"
            dt: "string"
            value: "[datatype.value]"
        - parameter:
            name: "target_user"
            dt: "string"
            value: "[target_user.value]"
        - parameter:
            name: "username"
            dt: "string"
            value: "[username.value]"
        - parameter:
            name: "userpass"
            dt: "string"
            value: "[userpass.value]"
        - parameter:
            name: "directory_node"
            dt: "string"
            value: "[directory_node.value]"
        - parameter:
            name: "maxChars"
            dt: "integer"
            value: "[maxChars.value]"
        - parameter:
            name: "maxFailedLoginAttempts"
            dt: "integer"
            value: "[maxFailedLoginAttempts.value]"
        - parameter:
            name: "minChars"
            dt: "integer"
            value: "[minChars.value]"
        - parameter:
            name: "passwordCannotBeName"
            dt: "boolean"
            value: "[passwordCannotBeName.value]"
        - parameter:
            name: "requiresAlpha"
            dt: "boolean"
            value: "[requiresAlpha.value]"
        - parameter:
            name: "requiresNumeric"
            dt: "boolean"
            value: "[requiresNumeric.value]"
        - parameter:
            name: "maxMinutesUntilChangePassword"
            dt: "integer"
            value: "[maxMinutesUntilChangePassword.value]"
        - parameter:
            name: "minMinutesUntilChangePassword"
            dt: "integer"
            value: "[minMinutesUntilChangePassword.value]"
        - parameter:
            name: "requiresMixedCase"
            dt: "boolean"
            value: "[requiresMixedCase.value]"
        - parameter:
            name: "requiresSymbol"
            dt: "boolean"
            value: "[requiresSymbol.value]"
        - parameter:
            name: "minutesUntilFailedLoginReset"
            dt: "integer"
            value: "[minutesUntilFailedLoginReset.value]"
        - parameter:
            name: "usingHistory"
            dt: "integer"
            value: "[usingHistory.value]"
        - parameter:
            name: "canModifyPasswordforSelf"
            dt: "boolean"
            value: "[canModifyPasswordforSelf.value]"
        - parameter:
            name: "usingExpirationDate"
            dt: "boolean"
            value: "[usingExpirationDate.value]"
        - parameter:
            name: "usingHardExpirationDate"
            dt: "boolean"
            value: "[usingHardExpirationDate.value]"
        - parameter:
            name: "expirationDateGMT"
            dt: "string"
            value: "[expirationDateGMT.value]"
        - parameter:
            name: "hardExpireDateGMT"
            dt: "string"
            value: "[hardExpireDateGMT.value]"
        - parameter:
            name: "maxMinutesUntilDisabled"
            dt: "integer"
            value: "[maxMinutesUntilDisabled.value]"
        - parameter:
            name: "maxMinutesOfNonUse"
            dt: "integer"
            value: "[maxMinutesOfNonUse.value]"
        - parameter:
            name: "newPasswordRequired"
            dt: "boolean"
            value: "[newPasswordRequired.value]"
        - parameter:
            name: "notGuessablePattern"
            dt: "boolean"
            value: "[notGuessablePattern.value]"

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT_OVAL_ID]",
      "artifact_title": "[ARTIFACT-TITLE]",
      "artifact": {
        "type": "[ARTIFACT-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "target_user",
              "dt": "string",
              "value": "[target_user.value]"
            }
          },
          {
            "parameter": {
              "name": "username",
              "dt": "string",
              "value": "[username.value]"
            }
          },
          {
            "parameter": {
              "name": "userpass",
              "dt": "string",
              "value": "[userpass.value]"
            }
          },
          {
            "parameter": {
              "name": "directory_node",
              "dt": "string",
              "value": "[directory_node.value]"
            }
          },
          {
            "parameter": {
              "name": "check_existence",
              "dt": "string",
              "value": "[check_existence.value]"
            }
          }
        ]
      },
      "test": {
        "type": "[TEST-TYPE-NAME]",
        "parameters": [
          {
            "parameter": {
              "name": "check",
              "dt": "string",
              "value": "[check.value]"
            }
          },
          {
            "parameter": {
              "name": "operation",
              "dt": "string",
              "value": "[operation.value]"
            }
          },
          {
            "parameter": {
              "name": "datatype",
              "dt": "string",
              "value": "[datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "target_user",
              "dt": "string",
              "value": "[target_user.value]"
            }
          },
          {
            "parameter": {
              "name": "username",
              "dt": "string",
              "value": "[username.value]"
            }
          },
          {
            "parameter": {
              "name": "userpass",
              "dt": "string",
              "value": "[userpass.value]"
            }
          },
          {
            "parameter": {
              "name": "directory_node",
              "dt": "string",
              "value": "[directory_node.value]"
            }
          },
          {
            "parameter": {
              "name": "maxChars",
              "dt": "integer",
              "value": "[maxChars.value]"
            }
          },
          {
            "parameter": {
              "name": "maxFailedLoginAttempts",
              "dt": "integer",
              "value": "[maxFailedLoginAttempts.value]"
            }
          },
          {
            "parameter": {
              "name": "minChars",
              "dt": "integer",
              "value": "[minChars.value]"
            }
          },
          {
            "parameter": {
              "name": "passwordCannotBeName",
              "dt": "boolean",
              "value": "[passwordCannotBeName.value]"
            }
          },
          {
            "parameter": {
              "name": "requiresAlpha",
              "dt": "boolean",
              "value": "[requiresAlpha.value]"
            }
          },
          {
            "parameter": {
              "name": "requiresNumeric",
              "dt": "boolean",
              "value": "[requiresNumeric.value]"
            }
          },
          {
            "parameter": {
              "name": "maxMinutesUntilChangePassword",
              "dt": "integer",
              "value": "[maxMinutesUntilChangePassword.value]"
            }
          },
          {
            "parameter": {
              "name": "minMinutesUntilChangePassword",
              "dt": "integer",
              "value": "[minMinutesUntilChangePassword.value]"
            }
          },
          {
            "parameter": {
              "name": "requiresMixedCase",
              "dt": "boolean",
              "value": "[requiresMixedCase.value]"
            }
          },
          {
            "parameter": {
              "name": "requiresSymbol",
              "dt": "boolean",
              "value": "[requiresSymbol.value]"
            }
          },
          {
            "parameter": {
              "name": "minutesUntilFailedLoginReset",
              "dt": "integer",
              "value": "[minutesUntilFailedLoginReset.value]"
            }
          },
          {
            "parameter": {
              "name": "usingHistory",
              "dt": "integer",
              "value": "[usingHistory.value]"
            }
          },
          {
            "parameter": {
              "name": "canModifyPasswordforSelf",
              "dt": "boolean",
              "value": "[canModifyPasswordforSelf.value]"
            }
          },
          {
            "parameter": {
              "name": "usingExpirationDate",
              "dt": "boolean",
              "value": "[usingExpirationDate.value]"
            }
          },
          {
            "parameter": {
              "name": "usingHardExpirationDate",
              "dt": "boolean",
              "value": "[usingHardExpirationDate.value]"
            }
          },
          {
            "parameter": {
                "name": "expirationDateGMT",
                "dt": "string",
                "value": "[expirationDateGMT.value]"
            }
          },
          {
            "parameter": {
              "name": "hardExpireDateGMT",
              "dt": "string",
              "value": "[hardExpireDateGMT.value]"
            }
          },
          {
            "parameter": {
              "name": "maxMinutesUntilDisabled",
              "dt": "integer",
              "value": "[maxMinutesUntilDisabled.value]"
            }
          },
          {
            "parameter": {
              "name": "maxMinutesOfNonUse",
              "dt": "integer",
              "value": "[maxMinutesOfNonUse.value]"
            }
          },
          {
            "parameter": {
              "name": "newPasswordRequired",
              "dt": "boolean",
              "value": "[newPasswordRequired.value]"
            }
          },
          {
            "parameter": {
              "name": "notGuessablePattern",
              "dt": "boolean",
              "value": "[notGuessablePattern.value]"
            }
          }
        ]
      }
    }
  }