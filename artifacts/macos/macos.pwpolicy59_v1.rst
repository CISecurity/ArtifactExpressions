macos:pwpolicy59
================

Description
-----------

The macos:pwpolicy59 test retrieves password policy data from the 'pwpolicy -getpolicy -u target_user [-a username] [-p userpass] [-n directory_node]' output where username, userpass, and directory_node are optional.

The pwpolicy59 object element is used by a pwpolicy59_test to define the target user, username, user password, and the directory node from which the password policy information is retrieved.

The pwpolicy59 state element defines the different information that can be used to evaluate the
password policy for the target user in the specified directory node.

Technical Details
-----------------

Artifact Parameters
~~~~~~~~~~~~~~~~~~~

**macos.pwpolicy59_v1**

+-------------------------------+---------+----------------------------------+
| Name                          | Type    | Description                      |
+===============================+=========+==================================+
| target_user                   | string  | The target_user element          |
|                               |         | specifies the user whose         |
|                               |         | password policy information      |
|                               |         | should be collected. If an       |
|                               |         | operation other than equals is   |
|                               |         | specified, the users on the      |
|                               |         | system should be enumerated and  |
|                               |         | the 'pwpolicy'command should be  |
|                               |         | issued for each user that        |
|                               |         | matches the target_user element. |
|                               |         | If the xsi:nil attribute is set  |
|                               |         | to true, the global policy       |
|                               |         | should be retrieved. Cannot be   |
|                               |         | blank.                           |
+-------------------------------+---------+----------------------------------+
| username                      | string  | The username element specifies   |
|                               |         | the username of the              |
|                               |         | authenticator. If the xsi:nil    |
|                               |         | attribute is set to true,        |
|                               |         | authentication to the directory  |
|                               |         | node will not be performed (i.e. |
|                               |         | the '-a' and '-p' command line   |
|                               |         | options will not be specified    |
|                               |         | when issuing the 'pwpolicy'      |
|                               |         | command) and the xsi:nil         |
|                               |         | attribute of the userpass        |
|                               |         | element should also be set to    |
|                               |         | true. Cannot be blank.           |
+-------------------------------+---------+----------------------------------+
| userpass                      | string  | The userpass element specifies   |
|                               |         | the password of the              |
|                               |         | authenticator as specified by    |
|                               |         | the username element. If the     |
|                               |         | xsi:nil attribute is set to      |
|                               |         | true, authentication to the      |
|                               |         | directory node will not be       |
|                               |         | performed (i.e. the '-a' and     |
|                               |         | '-p' command line options will   |
|                               |         | not be specified when issuing    |
|                               |         | the 'pwpolicy' command) and the  |
|                               |         | xsi:nil attribute of the         |
|                               |         | username element should also be  |
|                               |         | set to true. Cannot be blank.    |
+-------------------------------+---------+----------------------------------+
| directory_node                | string  | The directory_node element       |
|                               |         | specifies the directory node     |
|                               |         | that you would like to retrieve  |
|                               |         | the password policy information  |
|                               |         | from. If the xsi:nil attribute   |
|                               |         | is set to true, the default      |
|                               |         | directory node is used (i.e the  |
|                               |         | '-n' command line option will    |
|                               |         | not be specified when issuing    |
|                               |         | the 'pwpolicy' command). Cannot  |
|                               |         | be blank.                        |
+-------------------------------+---------+----------------------------------+
| check_existence               | string  | Defines how many items should    |
|                               |         | be collected.                    |
+-------------------------------+---------+----------------------------------+
:strong:`NOTE: The ``target_user``, ``username``, ``userpass``, and ``directory_node`` parameters are governed by a constraint allowing only values conforming to the following regex pattern:` ``^.+$``

NOTE: The ``check_existence`` parameter is governed by a constraint allowing only the following values:
  - all_exist 
  - any_exist 
  - at_least_one_exists 
  - none_exist 
  - only_one_exists

Supported Test Types
~~~~~~~~~~~~~~~~~~~~

-  macos:pwpolicy59

Test Type Parameters
~~~~~~~~~~~~~~~~~~~~

**macos.pwpolicy59_v1**

+-----------------------------------------+---------+----------------------------------+
| Name                                    | Type    | Description                      |
+=========================================+=========+==================================+
| check                                   | string  | Defines how many collected items |
|                                         |         | must match the  expected state.  |
+-----------------------------------------+---------+----------------------------------+
| target_user                             | string  | The target_user element          |
|                                         |         | specifies the user whose         |
|                                         |         | password policy information      |
|                                         |         | should be collected. Cannot be   |
|                                         |         | blank.                           |
+-----------------------------------------+---------+----------------------------------+
| target_user_operation                   | string  | Comparison operation.            |
+-----------------------------------------+---------+----------------------------------+
| target_user_datatype                    | string  | The data type of the value.      |
+-----------------------------------------+---------+----------------------------------+
| username                                | string  | The username element specifies   |
|                                         |         | the username of the              |
|                                         |         | authenticator. Cannot be blank.  |
+-----------------------------------------+---------+----------------------------------+
| username_operation                      | string  | Comparison operation.            |
+-----------------------------------------+---------+----------------------------------+
| username_datatype                       | string  | The data type of the value.      |
+-----------------------------------------+---------+----------------------------------+
| userpass                                | string  | The userpass element specifies   |
|                                         |         | the password of the              |
|                                         |         | authenticator as specified by    |
|                                         |         | the username element. Cannot be  |
|                                         |         | blank.                           |
+-----------------------------------------+---------+----------------------------------+
| userpass_operation                      | string  | Comparison operation.            |
+-----------------------------------------+---------+----------------------------------+
| userpass_datatype                       | string  | The data type of the value.      |
+-----------------------------------------+---------+----------------------------------+
| directory_node                          | string  | The directory_node element       |
|                                         |         | specifies the directory node     |
|                                         |         | that you would like to retrieve  |
|                                         |         | the password policy information  |
|                                         |         | from. Cannot be blank.           |
+-----------------------------------------+---------+----------------------------------+
| directory_node_operation                | string  | Comparison operation.            |
+-----------------------------------------+---------+----------------------------------+
| directory_node_datatype                 | string  | The data type of the value.      |
+-----------------------------------------+---------+----------------------------------+
| maxChars                                | integer | Maximum number of characters     |
|                                         |         | allowed in a password. Cannot be |
|                                         |         | blank.                           |
+-----------------------------------------+---------+----------------------------------+
| maxChars_operation                      | string  | Comparison operation.            |
+-----------------------------------------+---------+----------------------------------+
| maxChars_datatype                       | string  | The data type of the value.      |
+-----------------------------------------+---------+----------------------------------+
| maxFailedLoginAttempts                  | integer | Maximum number of failed logins  |
|                                         |         | before the account is locked.    |
|                                         |         | Cannot be blank.                 |
+-----------------------------------------+---------+----------------------------------+
| maxFailedLoginAttempts_operation        | string  | Comparison operation.            |
+-----------------------------------------+---------+----------------------------------+
| maxFailedLoginAttempts_datatype         | string  | The data type of the value.      |
+-----------------------------------------+---------+----------------------------------+
| passwordCannotBeName                    | boolean | Defines if the password is       |
|                                         |         | allowed to be the same as the    |
|                                         |         | username or not. Cannot be       |
|                                         |         | blank.                           |
+-----------------------------------------+---------+----------------------------------+
| passwordCannotBeName_operation          | string  | Comparison operation.            |
+-----------------------------------------+---------+----------------------------------+
| passwordCannotBeName_datatype           | string  | The data type of the value.      |
+-----------------------------------------+---------+----------------------------------+
| requiresAlpha                           | boolean | Defines if the password must     |
|                                         |         | contain an alphabetical          |
|                                         |         | character or not. Cannot be      |
|                                         |         | blank.                           |
+-----------------------------------------+---------+----------------------------------+
| requiresAlpha_operation                 | string  | Comparison operation.            |
+-----------------------------------------+---------+----------------------------------+
| requiresAlpha_datatype                  | string  | The data type of the value.      |
+-----------------------------------------+---------+----------------------------------+
| requiresNumeric                         | boolean | Defines if the password must     |
|                                         |         | contain a numeric character or   |
|                                         |         | not. Cannot be blank.            |
+-----------------------------------------+---------+----------------------------------+
| requiresNumeric_operation               | string  | Comparison operation.            |
+-----------------------------------------+---------+----------------------------------+
| requiresNumeric_datatype                | string  | The data type of the value.      |
+-----------------------------------------+---------+----------------------------------+
| maxMinutesUntilChangePassword           | integer | Maximum number of minutes until  |
|                                         |         | the password must be changed.    |
|                                         |         | Cannot be blank.                 |
+-----------------------------------------+---------+----------------------------------+
| maxMinutesUntilChangePassword_operation | string  | Comparison operation.            |
+-----------------------------------------+---------+----------------------------------+
| maxMinutesUntilChangePassword_datatype  | string  | The data type of the value.      |
+-----------------------------------------+---------+----------------------------------+
| minMinutesUntilChangePassword           | integer | Minimum number of minutes        |
|                                         |         | between password changes. Cannot |
|                                         |         | be blank.                        |
+-----------------------------------------+---------+----------------------------------+
| minMinutesUntilChangePassword_operation | string  | Comparison operation.            |
+-----------------------------------------+---------+----------------------------------+
| minMinutesUntilChangePassword_datatype  | string  | The data type of the value.      |
+-----------------------------------------+---------+----------------------------------+
| requiresMixedCase                       | boolean | Defines if the password must     |
|                                         |         | contain upper and lower case     |
|                                         |         | characters or not. Cannot be     |
|                                         |         | blank.                           |
+-----------------------------------------+---------+----------------------------------+
| requiresMixedCase_operation             | string  | Comparison operation.            |
+-----------------------------------------+---------+----------------------------------+
| requiresMixedCase_datatype              | string  | The data type of the value.      |
+-----------------------------------------+---------+----------------------------------+
| requiresSymbol                          | boolean | Defines if the password must     |
|                                         |         | contain a symbol character or    |
|                                         |         | not. Cannot be blank.            |
+-----------------------------------------+---------+----------------------------------+
| requiresSymbol_operation                | string  | Comparison operation.            |
+-----------------------------------------+---------+----------------------------------+
| requiresSymbol_datatype                 | string  | The data type of the value.      |
+-----------------------------------------+---------+----------------------------------+
| minutesUntilFailedLoginReset            | integer | Number of minutes after login    |
|                                         |         | has been disabled due to too     |
|                                         |         | many failed login attempts to    |
|                                         |         | wait before reenabling login.    |
|                                         |         | Cannot be blank.                 |
+-----------------------------------------+---------+----------------------------------+
| minutesUntilFailedLoginReset_operation  | string  | Comparison operation.            |
+-----------------------------------------+---------+----------------------------------+
| minutesUntilFailedLoginReset_datatype   | string  | The data type of the value.      |
+-----------------------------------------+---------+----------------------------------+
| usingHistory                            | integer | 0 = user can reuse the current   |
|                                         |         | password, 1 = user cannot reuse  |
|                                         |         | the current password, 2-15 =     |
|                                         |         | user cannot reuse the last n     |
|                                         |         | passwords. Cannot be blank.      |
+-----------------------------------------+---------+----------------------------------+
| usingHistory_operation                  | string  | Comparison operation.            |
+-----------------------------------------+---------+----------------------------------+
| usingHistory_datatype                   | string  | The data type of the value.      |
+-----------------------------------------+---------+----------------------------------+
| canModifyPasswordforSelf                | boolean | If true, the user can change     |
|                                         |         | the password. Cannot be blank.   |
+-----------------------------------------+---------+----------------------------------+
| canModifyPasswordforSelf_operation      | string  | Comparison operation.            |
+-----------------------------------------+---------+----------------------------------+
| canModifyPasswordforSelf_datatype       | string  | The data type of the value.      |
+-----------------------------------------+---------+----------------------------------+
| usingExpirationDate                     | boolean | If true, user is required to     |
|                                         |         | change password on the date in   |
|                                         |         | expirationDate GMT. Cannot be    |
|                                         |         | blank.                           |
+-----------------------------------------+---------+----------------------------------+
| usingExpirationDate_operation           | string  | Comparison operation.            |
+-----------------------------------------+---------+----------------------------------+
| usingExpirationDate_datatype            | string  | The data type of the value.      |
+-----------------------------------------+---------+----------------------------------+
| usingHardExpirationDate                 | boolean | If true, user's account is       |
|                                         |         | disabled on the date in          |
|                                         |         | hardExpireDate GMT. Cannot be    |
|                                         |         | blank.                           |
+-----------------------------------------+---------+----------------------------------+
| usingHardExpirationDate_operation       | string  | Comparison operation.            |
+-----------------------------------------+---------+----------------------------------+
| usingHardExpirationDate_datatype        | string  | The data type of the value.      |
+-----------------------------------------+---------+----------------------------------+
| expirationDateGMT                       | string  | Date for the password to expire, |
|                                         |         | format is: mm/dd/yyyy. NOTE: The |
|                                         |         | pwpolicy command returns the     |
|                                         |         | year as a two digit value, but   |
|                                         |         | OVAL uses four digit years; the  |
|                                         |         | pwpolicy value is converted to   |
|                                         |         | an OVAL compatible value. Cannot |
|                                         |         | be blank.                        |
+-----------------------------------------+---------+----------------------------------+
| expirationDateGMT_operation             | string  | Comparison operation.            |
+-----------------------------------------+---------+----------------------------------+
| expirationDateGMT_datatype              | string  | The data type of the value.      |
+-----------------------------------------+---------+----------------------------------+
| hardExpireDateGMT                       | string  | Date for the user's account to   |
|                                         |         | be disabled, format is:          |
|                                         |         | mm/dd/yyyy. NOTE: The pwpolicy   |
|                                         |         | command returns the yearas a two |
|                                         |         | digit value, but OVAL uses four  |
|                                         |         | digit years; the pwpolicy value  |
|                                         |         | is converted to an OVAL          |
|                                         |         | compatible value. Cannot be      |
|                                         |         | blank.                           |
+-----------------------------------------+---------+----------------------------------+
| hardExpireDateGMT_operation             | string  | Comparison operation.            |
+-----------------------------------------+---------+----------------------------------+
| hardExpireDateGMT_datatype              | string  | The data type of the value.      |
+-----------------------------------------+---------+----------------------------------+
| maxMinutesUntilDisabled                 | integer | User's account is disabled after |
|                                         |         | this interval. Cannot be blank.  |
+-----------------------------------------+---------+----------------------------------+
| maxMinutesUntilDisabled_operation       | string  | Comparison operation.            |
+-----------------------------------------+---------+----------------------------------+
| maxMinutesUntilDisabled_datatype        | string  | The data type of the value.      |
+-----------------------------------------+---------+----------------------------------+
| maxMinutesOfNonUse                      | integer | User's account is disabled if it |
|                                         |         | is not accessed by this          |
|                                         |         | interval. Cannot be blank.       |
+-----------------------------------------+---------+----------------------------------+
| maxMinutesOfNonUse_operation            | string  | Comparison operation.            |
+-----------------------------------------+---------+----------------------------------+
| maxMinutesOfNonUse_datatype             | string  | The data type of the value.      |
+-----------------------------------------+---------+----------------------------------+
| newPasswordRequired                     | boolean | If true, the user will be        |
|                                         |         | prompted for a new password at   |
|                                         |         | the next authentication. Cannot  |
|                                         |         | be blank.                        |
+-----------------------------------------+---------+----------------------------------+
| newPasswordRequired_operation           | string  | Comparison operation.            |
+-----------------------------------------+---------+----------------------------------+
| newPasswordRequired_datatype            | string  | The data type of the value.      |
+-----------------------------------------+---------+----------------------------------+
| notGuessablePattern                     | boolean | Defines if the pattern is        |
|                                         |         | guessable or not Cannot be       |
|                                         |         | blank.                           |
+-----------------------------------------+---------+----------------------------------+
| notGuessablePattern_operation           | string  | Comparison operation.            |
+-----------------------------------------+---------+----------------------------------+
| notGuessablePattern_datatype            | string  | The data type of the value.      |
+-----------------------------------------+---------+----------------------------------+

NOTE: The ``check`` parameter is governed by a constraint allowing only the following values:
   -  all
   -  at least one
   -  none satisfy
   -  only one

:strong:`NOTE: The following parameters:`
  +--------------------------------------------+--------------------------------------------+
  | ``target_user_operation``                  | ``username_operation``                     |
  +--------------------------------------------+--------------------------------------------+
  | ``userpass_operation``                     | ``directory_node_operation``               |
  +--------------------------------------------+--------------------------------------------+
  | ``maxChars_operation``                     | ``maxFailedLoginAttempts_operation``       |
  +--------------------------------------------+--------------------------------------------+
  | ``minChars_operation``                     | ``passwordCannotBeName_operation``         |
  +--------------------------------------------+--------------------------------------------+
  | ``requiresAlpha_operation``                | ``requiresNumeric_operation``              |
  +--------------------------------------------+--------------------------------------------+
  | ``maxMinutesUntilChangePassword_operation``| ``minMinutesUntilChangePassword_operation``|
  +--------------------------------------------+--------------------------------------------+
  | ``requiresMixedCase_operation``            | ``requiresSymbol_operation``               |
  +--------------------------------------------+--------------------------------------------+
  | ``minutesUntilFailedLoginReset_operation`` | ``usingHistory_operation``                 |
  +--------------------------------------------+--------------------------------------------+
  | ``canModifyPasswordforSelf_operation``     | ``usingExpirationDate_operation``          |
  +--------------------------------------------+--------------------------------------------+
  | ``usingHardExpirationDate_operation``      | ``expirationDateGMT_operation``            |
  +--------------------------------------------+--------------------------------------------+
  | ``hardExpireDateGMT_operation``            | ``maxMinutesUntilDisabled_operation``      |
  +--------------------------------------------+--------------------------------------------+
  | ``maxMinutesOfNonUse_operation``           | ``newPasswordRequired_operation``          |
  +--------------------------------------------+--------------------------------------------+
  | ``notGuessablePattern_operation``          |                                            |
  +--------------------------------------------+--------------------------------------------+
  are governed by a constraint allowing only the following values:
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

:strong:`NOTE: The following parameters:`
  +-------------------------------------------+-------------------------------------------+
  | ``target_user_datatype``                  | ``username_datatype``                     |
  +-------------------------------------------+-------------------------------------------+
  | ``userpass_datatype``                     | ``directory_node_datatype``               |
  +-------------------------------------------+-------------------------------------------+
  | ``maxChars_datatype``                     | ``maxFailedLoginAttempts_datatype``       |
  +-------------------------------------------+-------------------------------------------+
  | ``minChars_datatype``                     | ``passwordCannotBeName_datatype``         |
  +-------------------------------------------+-------------------------------------------+
  | ``requiresAlpha_datatype``                | ``requiresNumeric_datatype``              |
  +-------------------------------------------+-------------------------------------------+
  | ``maxMinutesUntilChangePassword_datatype``| ``minMinutesUntilChangePassword_datatype``|
  +-------------------------------------------+-------------------------------------------+
  | ``requiresMixedCase_datatype``            | ``requiresSymbol_datatype``               |
  +-------------------------------------------+-------------------------------------------+
  | ``minutesUntilFailedLoginReset_datatype`` | ``usingHistory_datatype``                 |
  +-------------------------------------------+-------------------------------------------+
  | ``canModifyPasswordforSelf_datatype``     | ``usingExpirationDate_datatype``          |
  +-------------------------------------------+-------------------------------------------+
  | ``usingHardExpirationDate_datatype``      | ``expirationDateGMT_datatype``            |
  +-------------------------------------------+-------------------------------------------+
  | ``hardExpireDateGMT_datatype``            | ``maxMinutesUntilDisabled_datatype``      |
  +-------------------------------------------+-------------------------------------------+
  | ``maxMinutesOfNonUse_datatype``           | ``newPasswordRequired_datatype``          |
  +-------------------------------------------+-------------------------------------------+
  | ``notGuessablePattern_datatype``          |                                           |
  +-------------------------------------------+-------------------------------------------+
  are governed by a constraint allowing only the following values:
    - boolean
    - float
    - int
    - string
    - version
    - set

:strong:`NOTE: The following parameters:`
  +----------------------------------+-----------------------------------+
  | ``target_user``                  | ``username``                      |
  +----------------------------------+-----------------------------------+
  | ``userpass``                     | ``directory_node``                |
  +----------------------------------+-----------------------------------+
  | ``maxChars``                     | ``maxFailedLoginAttempts``        |
  +----------------------------------+-----------------------------------+
  | ``minChars``                     | ``passwordCannotBeName``          |
  +----------------------------------+-----------------------------------+
  | ``requiresAlpha``                | ``requiresNumeric``               |
  +----------------------------------+-----------------------------------+
  | ``maxMinutesUntilChangePassword``| ``minMinutesUntilChangePassword`` |
  +----------------------------------+-----------------------------------+
  | ``requiresMixedCase``            | ``requiresSymbol``                |
  +----------------------------------+-----------------------------------+
  | ``minutesUntilFailedLoginReset`` | ``usingHistory``                  |
  +----------------------------------+-----------------------------------+
  | ``canModifyPasswordforSelf``     | ``usingExpirationDate``           |
  +----------------------------------+-----------------------------------+
  | ``usingHardExpirationDate``      | ``expirationDateGMT``             |
  +----------------------------------+-----------------------------------+
  | ``hardExpireDateGMT``            | ``maxMinutesUntilDisabled``       |
  +----------------------------------+-----------------------------------+
  | ``maxMinutesOfNonUse``           | ``newPasswordRequired``           |
  +----------------------------------+-----------------------------------+
  | ``notGuessablePattern``          |                                   |
  +----------------------------------+-----------------------------------+
  :strong:`are governed by a constraint allowing only values conforming to the following regex pattern:` ``^.+$``

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
          <ae:title>[ARTIFACT-TITLE]</ae:title>
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
              <ae:parameter dt="string" name="target_user">[target_user.value]</ae:parameter>
              <ae:parameter dt="string" name="target_user_operation">[target_user_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="target_user_datatype">[target_user_datatype.value]</ae:parameter>
              <ae:parameter dt="string" name="username">[username.value]</ae:parameter>
              <ae:parameter dt="string" name="username_operation">[username_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="username_datatype">[username_datatype.value]</ae:parameter>
              <ae:parameter dt="string" name="userpass">[userpass.value]</ae:parameter>
              <ae:parameter dt="string" name="userpass_operation">[userpass_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="userpass_datatype">[userpass_datatype.value]</ae:parameter>
              <ae:parameter dt="string" name="directory_node">[directory_node.value]</ae:parameter>
              <ae:parameter dt="string" name="directory_node_operation">[directory_node_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="directory_node_datatype">[directory_node_datatype.value]</ae:parameter>
              <ae:parameter dt="integer" name="maxChars">[maxChars.value]</ae:parameter>
              <ae:parameter dt="string" name="maxChars_operation">[maxChars_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="maxChars_datatype">[maxChars_datatype.value]</ae:parameter>
              <ae:parameter dt="integer" name="maxFailedLoginAttempts">[maxFailedLoginAttempts.value]</ae:parameter>
              <ae:parameter dt="string" name="maxFailedLoginAttempts_operation">[maxFailedLoginAttempts_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="maxFailedLoginAttempts_datatype">[maxFailedLoginAttempts_datatype.value]</ae:parameter>
              <ae:parameter dt="integer" name="minChars">[minChars.value]</ae:parameter>
              <ae:parameter dt="string" name="minChars_operation">[minChars_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="minChars_datatype">[minChars_datatype.value]</ae:parameter>
              <ae:parameter dt="boolean" name="passwordCannotBeName">[passwordCannotBeName.value]</ae:parameter>
              <ae:parameter dt="string" name="passwordCannotBeName_operation">[passwordCannotBeName_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="passwordCannotBeName_datatype">[passwordCannotBeName_datatype.value]</ae:parameter>
              <ae:parameter dt="boolean" name="requiresAlpha">[requiresAlpha.value]</ae:parameter>
              <ae:parameter dt="string" name="requiresAlpha_operation">[requiresAlpha_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="requiresAlpha_datatype">[requiresAlpha_datatype.value]</ae:parameter>
              <ae:parameter dt="boolean" name="requiresNumeric">[requiresNumeric.value]</ae:parameter>
              <ae:parameter dt="string" name="requiresNumeric_operation">[requiresNumeric_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="requiresNumeric_datatype">[requiresNumeric_datatype.value]</ae:parameter>
              <ae:parameter dt="integer" name="maxMinutesUntilChangePassword">[maxMinutesUntilChangePassword.value]</ae:parameter>
              <ae:parameter dt="string" name="maxMinutesUntilChangePassword_operation">[maxMinutesUntilChangePassword_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="maxMinutesUntilChangePassword_datatype">[maxMinutesUntilChangePassword_datatype.value]</ae:parameter>
              <ae:parameter dt="integer" name="minMinutesUntilChangePassword">[minMinutesUntilChangePassword.value]</ae:parameter>
              <ae:parameter dt="string" name="minMinutesUntilChangePassword_operation">[minMinutesUntilChangePassword_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="minMinutesUntilChangePassword_datatype">[minMinutesUntilChangePassword_datatype.value]</ae:parameter>
              <ae:parameter dt="boolean" name="requiresMixedCase">[requiresMixedCase.value]</ae:parameter>
              <ae:parameter dt="string" name="requiresMixedCase_operation">[requiresMixedCase_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="requiresMixedCase_datatype">[requiresMixedCase_datatype.value]</ae:parameter>
              <ae:parameter dt="boolean" name="requiresSymbol">[requiresSymbol.value]</ae:parameter>
              <ae:parameter dt="string" name="requiresSymbol_operation">[requiresSymbol_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="requiresSymbol_datatype">[requiresSymbol_datatype.value]</ae:parameter>
              <ae:parameter dt="integer" name="minutesUntilFailedLoginReset">[minutesUntilFailedLoginReset.value]</ae:parameter>
              <ae:parameter dt="string" name="minutesUntilFailedLoginReset_operation">[minutesUntilFailedLoginReset_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="minutesUntilFailedLoginReset_datatype">[minutesUntilFailedLoginReset_datatype.value]</ae:parameter>
              <ae:parameter dt="integer" name="usingHistory">[usingHistory.value]</ae:parameter>
              <ae:parameter dt="string" name="usingHistory_operation">[usingHistory_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="usingHistory_datatype">[usingHistory_datatype.value]</ae:parameter>
              <ae:parameter dt="boolean" name="canModifyPasswordforSelf">[canModifyPasswordforSelf.value]</ae:parameter>
              <ae:parameter dt="string" name="canModifyPasswordforSelf_operation">[canModifyPasswordforSelf_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="canModifyPasswordforSelf_datatype">[canModifyPasswordforSelf_datatype.value]</ae:parameter>
              <ae:parameter dt="boolean" name="usingExpirationDate">[usingExpirationDate.value]</ae:parameter>
              <ae:parameter dt="string" name="usingExpirationDate_operation">[usingExpirationDate_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="usingExpirationDate_datatype">[usingExpirationDate_datatype.value]</ae:parameter>
              <ae:parameter dt="boolean" name="usingHardExpirationDate">[usingHardExpirationDate.value]</ae:parameter>
              <ae:parameter dt="string" name="usingHardExpirationDate_operation">[usingHardExpirationDate_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="usingHardExpirationDate_datatype">[usingHardExpirationDate_datatype.value]</ae:parameter>
              <ae:parameter dt="string" name="expirationDateGMT">[expirationDateGMT.value]</ae:parameter>
              <ae:parameter dt="string" name="expirationDateGMT_operation">[expirationDateGMT_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="expirationDateGMT_datatype">[expirationDateGMT_datatype.value]</ae:parameter>
              <ae:parameter dt="string" name="hardExpireDateGMT">[hardExpireDateGMT.value]</ae:parameter>
              <ae:parameter dt="string" name="hardExpireDateGMT_operation">[hardExpireDateGMT_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="hardExpireDateGMT_datatype">[hardExpireDateGMT_datatype.value]</ae:parameter>
              <ae:parameter dt="integer" name="maxMinutesUntilDisabled">[maxMinutesUntilDisabled.value]</ae:parameter>
              <ae:parameter dt="string" name="maxMinutesUntilDisabled_operation">[maxMinutesUntilDisabled_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="maxMinutesUntilDisabled_datatype">[maxMinutesUntilDisabled_datatype.value]</ae:parameter>
              <ae:parameter dt="integer" name="maxMinutesOfNonUse">[maxMinutesOfNonUse.value]</ae:parameter>
              <ae:parameter dt="string" name="maxMinutesOfNonUse_operation">[maxMinutesOfNonUse_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="maxMinutesOfNonUse_datatype">[maxMinutesOfNonUse_datatype.value]</ae:parameter>
              <ae:parameter dt="boolean" name="newPasswordRequired">[newPasswordRequired.value]</ae:parameter>
              <ae:parameter dt="string" name="newPasswordRequired_operation">[newPasswordRequired_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="newPasswordRequired_datatype">[newPasswordRequired_datatype.value]</ae:parameter>
              <ae:parameter dt="boolean" name="notGuessablePattern">[notGuessablePattern.value]</ae:parameter>
              <ae:parameter dt="string" name="notGuessablePattern_operation">[notGuessablePattern_operation.value]</ae:parameter>
              <ae:parameter dt="string" name="notGuessablePattern_datatype">[notGuessablePattern_datatype.value]</ae:parameter>
            </ae:parameters>
          </ae:test>
          <ae:profiles>
            <ae:profile idref="xccdf_org.cisecurity.benchmarks_profile_Level_1" />
          </ae:profiles>
        </ae:artifact_expression>
      </xccdf:check-content>
    </xccdf:check>
  </xccdf:complex-check>

SCAP
^^^^

XCCDF
'''''

For ``macos.pwpolicy59_v1`` ``macos.pwpolicy59_v1`` artifacts, the XCCDF check looks like this. There is no Value element in the XCCDF for this artifact.

::

  <check system="http://oval.mitre.org/XMLSchema/oval-definitions-5">
    <check-content-ref
      href="[BENCHMARK-TITLE]-oval.xml"
      name="oval:org.cisecurity.benchmarks.[PLATFORM]:def:[ARTIFACT-OVAL-ID]">
    </check-content-ref>
  </check>

OVAL
''''

Test

::

  <pwpolicy59_test
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:tst:[ARTIFACT-OVAL-ID]"
    check_existence="[check_existence.value]"
    check="[check.value]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <object object_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]" />
    <state state_ref="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]" />
  </pwpolicy59_test>

Object

::

  <pwpolicy59_object 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:obj:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <target_user>[target_user.value]</target_user>
    <username>[username.value]</username>
    <userpass>[password.value]</userpass>
    <directory_node>[directory_node.value]</directory_node>
  </pwpolicy59_object>

State

::

   <pwpolicy59_state 
    xmlns="http://oval.mitre.org/XMLSchema/oval-definitions-5#macos"
    id="oval:org.cisecurity.benchmarks.[PLATFORM]:ste:[ARTIFACT-OVAL-ID]"
    comment="[ARTIFACT-TITLE]"
    version="1">
    <target_user 
      datatype="[datatype.value]"
      operation="[operation.value]">
        [target_user.value]
    </target_user>
    <username
      datatype="[datatype.value]"
      operation="[operation.value]">
        [username.value]
    </username>
    <userpass 
      datatype="[datatype.value]"
      operation="[operation.value]">
        [userpass.value]
    </userpass>
    <directory_node 
      datatype="[datatype.value]"
      operation="[operation.value]">
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
      operation="[operation.value]">
        [passwordCannotBeName.value]
    </passwordCannotBeName>
    <requiresAlpha 
      datatype="boolean"
      operation="[operation.value]">
        [requiresAlpha.value]
    </requiresAlpha>
    <requiresNumeric 
      datatype="boolean"
      operation="[operation.value]">
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
      operation="[operation.value]">
        [requiresMixedCase.value]
    </requiresMixedCase>
    <requiresSymbol 
      datatype="boolean"
      operation="[operation.value]">
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
      operation="[operation.value]">
        [canModifyPasswordforSelf.value]
    </canModifyPasswordforSelf>
    <usingExpirationDate 
      datatype="boolean"
      operation="[operation.value]">
        [usingExpirationDate.value]
    </usingExpirationDate>
    <usingHardExpirationDate 
      datatype="boolean"
      operation="[operation.value]">
        [usingHardExpirationDate.value]
    </usingHardExpirationDate>
    <expirationDateGMT 
      datatype="[datatype.value]"
      operation="[operation.value]">
        [expirationDateGMT.value]
    </expirationDateGMT>
    <hardExpireDateGMT 
      datatype="[datatype.value]"
      operation="[operation.value]">
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
      operation="[operation.value]">
        [newPasswordRequired.value]
    </newPasswordRequired>
    <notGuessablePattern 
      datatype="boolean"
      operation="[operation.value]">
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
      type: "[ARTIFACT-TYPE-NAME]"
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
            name: "target_user"
            dt: "string"
            value: "[target_user.value]"
        - parameter:
            name: "target_user_operation"
            dt: "string"
            value: "[target_user_operation.value]"
        - parameter:
            name: "target_user_datatype"
            dt: "string"
            value: "[target_user_datatype.value]"
        - parameter:
            name: "username"
            dt: "string"
            value: "[username.value]"
        - parameter:
            name: "username_datatype"
            dt: "string"
            value: "[username_datatype.value]"
        - parameter:
            name: "username_operation"
            dt: "string"
            value: "[username_operation.value]"
        - parameter:
            name: "userpass"
            dt: "string"
            value: "[userpass.value]"
        - parameter:
            name: "userpass_datatype"
            dt: "string"
            value: "[userpass_datatype.value]"
        - parameter:
            name: "userpass_operation"
            dt: "string"
            value: "[userpass_operation.value]"
        - parameter:
            name: "directory_node"
            dt: "string"
            value: "[directory_node.value]"
        - parameter:
            name: "directory_node_datatype"
            dt: "string"
            value: "[directory_node_datatype.value]"
        - parameter:
            name: "directory_node_operation"
            dt: "string"
            value: "[directory_node_operation.value]"
        - parameter:
            name: "maxChars"
            dt: "integer"
            value: "[maxChars.value]"
        - parameter:
            name: "maxChars_datatype"
            dt: "string"
            value: "[maxChars_datatype.value]"
        - parameter:
            name: "maxChars_operation"
            dt: "string"
            value: "[maxChars_operation.value]"
        - parameter:
            name: "maxFailedLoginAttempts"
            dt: "integer"
            value: "[maxFailedLoginAttempts.value]"
        - parameter:
            name: "maxFailedLoginAttempts_datatype"
            dt: "string"
            value: "[maxFailedLoginAttempts_datatype.value]"
        - parameter:
            name: "maxFailedLoginAttempts_operation"
            dt: "string"
            value: "[maxFailedLoginAttempts_operation.value]"
        - parameter:
            name: "minChars"
            dt: "integer"
            value: "[minChars.value]"
        - parameter:
            name: "minChars_datatype"
            dt: "string"
            value: "[minChars_datatype.value]"
        - parameter:
            name: "minChars_operation"
            dt: "string"
            value: "[minChars_operation.value]"
        - parameter:
            name: "passwordCannotBeName"
            dt: "boolean"
            value: "[passwordCannotBeName.value]"
        - parameter:
            name: "passwordCannotBeName_datatype"
            dt: "string"
            value: "[passwordCannotBeName_datatype.value]"
        - parameter:
            name: "passwordCannotBeName_operation"
            dt: "string"
            value: "[passwordCannotBeName_operation.value]"
        - parameter:
            name: "requiresAlpha"
            dt: "boolean"
            value: "[requiresAlpha.value]"
        - parameter:
            name: "requiresAlpha_datatype"
            dt: "string"
            value: "[requiresAlpha_datatype.value]"
        - parameter:
            name: "requiresAlpha_operation"
            dt: "string"
            value: "[requiresAlpha_operation.value]"
        - parameter:
            name: "requiresNumeric"
            dt: "boolean"
            value: "[requiresNumeric.value]"
        - parameter:
            name: "requiresNumeric_datatype"
            dt: "string"
            value: "[requiresNumeric_datatype.value]"
        - parameter:
            name: "requiresNumeric_operation"
            dt: "string"
            value: "[requiresNumeric_operation.value]"
        - parameter:
            name: "maxMinutesUntilChangePassword"
            dt: "integer"
            value: "[maxMinutesUntilChangePassword.value]"
        - parameter:
            name: "maxMinutesUntilChangePassword_datatype"
            dt: "string"
            value: "[maxMinutesUntilChangePassword_datatype.value]"
        - parameter:
            name: "maxMinutesUntilChangePassword_operation"
            dt: "string"
            value: "[maxMinutesUntilChangePassword_operation.value]"
        - parameter:
            name: "minMinutesUntilChangePassword"
            dt: "integer"
            value: "[minMinutesUntilChangePassword.value]"
        - parameter:
            name: "minMinutesUntilChangePassword_datatype"
            dt: "string"
            value: "[minMinutesUntilChangePassword_datatype.value]"
        - parameter:
            name: "minMinutesUntilChangePassword_operation"
            dt: "string"
            value: "[minMinutesUntilChangePassword_operation.value]"
        - parameter:
            name: "requiresMixedCase"
            dt: "boolean"
            value: "[requiresMixedCase.value]"
        - parameter:
            name: "requiresMixedCase_datatype"
            dt: "string"
            value: "[requiresMixedCase_datatype.value]"
        - parameter:
            name: "requiresMixedCase_operation"
            dt: "string"
            value: "[requiresMixedCase_operation.value]"
        - parameter:
            name: "requiresSymbol"
            dt: "boolean"
            value: "[requiresSymbol.value]"
        - parameter:
            name: "requiresSymbol_datatype"
            dt: "string"
            value: "[requiresSymbol_datatype.value]"
        - parameter:
            name: "requiresSymbol_operation"
            dt: "string"
            value: "[requiresSymbol_operation.value]"
        - parameter:
            name: "minutesUntilFailedLoginReset"
            dt: "integer"
            value: "[minutesUntilFailedLoginReset.value]"
        - parameter:
            name: "minutesUntilFailedLoginReset_datatype"
            dt: "string"
            value: "[minutesUntilFailedLoginReset_datatype.value]"
        - parameter:
            name: "minutesUntilFailedLoginReset_operation"
            dt: "string"
            value: "[minutesUntilFailedLoginReset_operation.value]"
        - parameter:
            name: "usingHistory"
            dt: "integer"
            value: "[usingHistory.value]"
        - parameter:
            name: "usingHistory_datatype"
            dt: "string"
            value: "[usingHistory_datatype.value]"
        - parameter:
            name: "usingHistory_operation"
            dt: "string"
            value: "[usingHistory_operation.value]"
        - parameter:
            name: "canModifyPasswordforSelf"
            dt: "boolean"
            value: "[canModifyPasswordforSelf.value]"
        - parameter:
            name: "canModifyPasswordforSelf_datatype"
            dt: "string"
            value: "[canModifyPasswordforSelf_datatype.value]"
        - parameter:
            name: "canModifyPasswordforSelf_operation"
            dt: "string"
            value: "[canModifyPasswordforSelf_operation.value]"
        - parameter:
            name: "usingExpirationDate"
            dt: "boolean"
            value: "[usingExpirationDate.value]"
        - parameter:
            name: "usingExpirationDate_datatype"
            dt: "string"
            value: "[usingExpirationDate_datatype.value]"
        - parameter:
            name: "usingExpirationDate_operation"
            dt: "string"
            value: "[usingExpirationDate_operation.value]"
        - parameter:
            name: "usingHardExpirationDate"
            dt: "boolean"
            value: "[usingHardExpirationDate.value]"
        - parameter:
            name: "usingHardExpirationDate_datatype"
            dt: "string"
            value: "[usingHardExpirationDate_datatype.value]"
        - parameter:
            name: "usingHardExpirationDate_operation"
            dt: "string"
            value: "[usingHardExpirationDate_operation.value]"
        - parameter:
            name: "expirationDateGMT"
            dt: "string"
            value: "[expirationDateGMT.value]"
        - parameter:
            name: "expirationDateGMT_datatype"
            dt: "string"
            value: "[expirationDateGMT_datatype.value]"
        - parameter:
            name: "expirationDateGMT_operation"
            dt: "string"
            value: "[expirationDateGMT_operation.value]"
        - parameter:
            name: "hardExpireDateGMT"
            dt: "string"
            value: "[hardExpireDateGMT.value]"
        - parameter:
            name: "hardExpireDateGMT_datatype"
            dt: "string"
            value: "[hardExpireDateGMT_datatype.value]"
        - parameter:
            name: "hardExpireDateGMT_operation"
            dt: "string"
            value: "[hardExpireDateGMT_operation.value]"
        - parameter:
            name: "maxMinutesUntilDisabled"
            dt: "integer"
            value: "[maxMinutesUntilDisabled.value]"
        - parameter:
            name: "maxMinutesUntilDisabled_datatype"
            dt: "string"
            value: "[maxMinutesUntilDisabled_datatype.value]"
        - parameter:
            name: "maxMinutesUntilDisabled_operation"
            dt: "string"
            value: "[maxMinutesUntilDisabled_operation.value]"
        - parameter:
            name: "maxMinutesOfNonUse"
            dt: "integer"
            value: "[maxMinutesOfNonUse.value]"
        - parameter:
            name: "maxMinutesOfNonUse_datatype"
            dt: "string"
            value: "[maxMinutesOfNonUse_datatype.value]"
        - parameter:
            name: "maxMinutesOfNonUse_operation"
            dt: "string"
            value: "[maxMinutesOfNonUse_operation.value]"
        - parameter:
            name: "newPasswordRequired"
            dt: "boolean"
            value: "[newPasswordRequired.value]"
        - parameter:
            name: "newPasswordRequired_datatype"
            dt: "string"
            value: "[newPasswordRequired_datatype.value]"
        - parameter:
            name: "newPasswordRequired_operation"
            dt: "string"
            value: "[newPasswordRequired_operation.value]"
        - parameter:
            name: "notGuessablePattern"
            dt: "boolean"
            value: "[notGuessablePattern.value]"
        - parameter:
            name: "notGuessablePattern_datatype"
            dt: "string"
            value: "[notGuessablePattern_datatype.value]"
        - parameter:
            name: "notGuessablePattern_operation"
            dt: "string"
            value: "[notGuessablePattern_operation.value]"

JSON
^^^^

::

  {
    "artifact-expression": {
      "artifact-unique-id": "[ARTIFACT-OVAL-ID]",
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
              "name": "target_user",
              "dt": "string",
              "value": "[target_user.value]"
            }
          },
          {
            "parameter": {
              "name": "target_user_operation",
              "dt": "string",
              "value": "[target_user_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "target_user_datatype",
              "dt": "string",
              "value": "[target_user_datatype.value]"
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
              "name": "username_datatype",
              "dt": "string",
              "value": "[username_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "username_operation",
              "dt": "string",
              "value": "[username_operation.value]"
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
              "name": "userpass_datatype",
              "dt": "string",
              "value": "[userpass_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "userpass_operation",
              "dt": "string",
              "value": "[userpass_operation.value]"
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
              "name": "directory_node_datatype",
              "dt": "string",
              "value": "[directory_node_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "directory_node_operation",
              "dt": "string",
              "value": "[directory_node_operation.value]"
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
              "name": "maxChars_datatype",
              "dt": "string",
              "value": "[maxChars_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "maxChars_operation",
              "dt": "string",
              "value": "[maxChars_operation.value]"
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
              "name": "maxFailedLoginAttempts_datatype",
              "dt": "string",
              "value": "[maxFailedLoginAttempts_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "maxFailedLoginAttempts_operation",
              "dt": "string",
              "value": "[maxFailedLoginAttempts_operation.value]"
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
              "name": "minChars_datatype",
              "dt": "string",
              "value": "[minChars_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "minChars_operation",
              "dt": "string",
              "value": "[minChars_operation.value]"
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
              "name": "passwordCannotBeName_datatype",
              "dt": "string",
              "value": "[passwordCannotBeName_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "passwordCannotBeName_operation",
              "dt": "string",
              "value": "[passwordCannotBeName_operation.value]"
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
              "name": "requiresAlpha_datatype",
              "dt": "string",
              "value": "[requiresAlpha_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "requiresAlpha_operation",
              "dt": "string",
              "value": "[requiresAlpha_operation.value]"
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
              "name": "requiresNumeric_datatype",
              "dt": "string",
              "value": "[requiresNumeric_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "requiresNumeric_operation",
              "dt": "string",
              "value": "[requiresNumeric_operation.value]"
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
              "name": "maxMinutesUntilChangePassword_datatype",
              "dt": "string",
              "value": "[maxMinutesUntilChangePassword_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "maxMinutesUntilChangePassword_operation",
              "dt": "string",
              "value": "[maxMinutesUntilChangePassword_operation.value]"
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
              "name": "minMinutesUntilChangePassword_datatype",
              "dt": "string",
              "value": "[minMinutesUntilChangePassword_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "minMinutesUntilChangePassword_operation",
              "dt": "string",
              "value": "[minMinutesUntilChangePassword_operation.value]"
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
              "name": "requiresMixedCase_datatype",
              "dt": "string",
              "value": "[requiresMixedCase_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "requiresMixedCase_operation",
              "dt": "string",
              "value": "[requiresMixedCase_operation.value]"
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
              "name": "requiresSymbol_datatype",
              "dt": "string",
              "value": "[requiresSymbol_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "requiresSymbol_operation",
              "dt": "string",
              "value": "[requiresSymbol_operation.value]"
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
              "name": "minutesUntilFailedLoginReset_datatype",
              "dt": "string",
              "value": "[minutesUntilFailedLoginReset_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "minutesUntilFailedLoginReset_operation",
              "dt": "string",
              "value": "[minutesUntilFailedLoginReset_operation.value]"
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
              "name": "usingHistory_datatype",
              "dt": "string",
              "value": "[usingHistory_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "usingHistory_operation",
              "dt": "string",
              "value": "[usingHistory_operation.value]"
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
              "name": "canModifyPasswordforSelf_datatype",
              "dt": "string",
              "value": "[canModifyPasswordforSelf_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "canModifyPasswordforSelf_operation",
              "dt": "string",
              "value": "[canModifyPasswordforSelf_operation.value]"
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
              "name": "usingExpirationDate_datatype",
              "dt": "string",
              "value": "[usingExpirationDate_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "usingExpirationDate_operation",
              "dt": "string",
              "value": "[usingExpirationDate_operation.value]"
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
              "name": "usingHardExpirationDate_datatype",
              "dt": "string",
              "value": "[usingHardExpirationDate_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "usingHardExpirationDate_operation",
              "dt": "string",
              "value": "[usingHardExpirationDate_operation.value]"
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
              "name": "expirationDateGMT_datatype",
              "dt": "string",
              "value": "[expirationDateGMT_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "expirationDateGMT_operation",
              "dt": "string",
              "value": "[expirationDateGMT_operation.value]"
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
              "name": "hardExpireDateGMT_datatype",
              "dt": "string",
              "value": "[hardExpireDateGMT_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "hardExpireDateGMT_operation",
              "dt": "string",
              "value": "[hardExpireDateGMT_operation.value]"
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
              "name": "maxMinutesUntilDisabled_datatype",
              "dt": "string",
              "value": "[maxMinutesUntilDisabled_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "maxMinutesUntilDisabled_operation",
              "dt": "string",
              "value": "[maxMinutesUntilDisabled_operation.value]"
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
              "name": "maxMinutesOfNonUse_datatype",
              "dt": "string",
              "value": "[maxMinutesOfNonUse_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "maxMinutesOfNonUse_operation",
              "dt": "string",
              "value": "[maxMinutesOfNonUse_operation.value]"
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
              "name": "newPasswordRequired_datatype",
              "dt": "string",
              "value": "[newPasswordRequired_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "newPasswordRequired_operation",
              "dt": "string",
              "value": "[newPasswordRequired_operation.value]"
            }
          },
          {
            "parameter": {
              "name": "notGuessablePattern",
              "dt": "boolean",
              "value": "[notGuessablePattern.value]"
            }
          },
          {
            "parameter": {
              "name": "notGuessablePattern_datatype",
              "dt": "string",
              "value": "[notGuessablePattern_datatype.value]"
            }
          },
          {
            "parameter": {
              "name": "notGuessablePattern_operation",
              "dt": "string",
              "value": "[notGuessablePattern_operation.value]"
            }
          }
        ]
      }
    }
  }