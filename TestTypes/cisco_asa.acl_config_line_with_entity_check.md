# Cisco ASA: ACL Config Line w/Entity Check

| Human ID|
| ----------------------|
| cisco_asa.acl_config_line_with_entity_check |

## Description
This TestType allows for the comparison of Cisco ASA Access Control List (ACL) configuration lines.  The additional `entity_check` parameter gives a certain level of extra control over this test, allowing an enumeration specifying the number of configuration lines that must match in order to reach a positive result.

## Technical Details
### Parameters
| Name                  |Type/Constraint    | Description |
| ----------------------|-------------------| ----------- |
| operation | Test Types | The operation to be used when performing the comparison between the collected configuration line and the expected `config_line` |
| config_line | string | The expected value for the ACL configuration line.  This could be represented as an exact match or a regular expression. |
| entity_check | OVAL: Entity Check | This enumeration represents the complement of collected configuration lines which must successfully match the expected `config_line` value in order for this test to reach a positive result.|

### Constraints
| Name       | Type           | Content     |
| -----------|----------------| ----------- |
| Test Types | Static Options | bitwise and, bitwise or, case insensitive equals, case insensitive not equal, equals, greater than, greater than or equal, less than, less than or equal, pattern match, not equal, set white list, set is empty|
| OVAL: Entity Check | Static Options | all_exist, any_exist, at_least_one_exists, none_exist, only_one_exists |
