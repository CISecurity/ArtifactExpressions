# Cisco ASA: Existence Check

| Human ID|
| ----------------------|
| cisco_asa.existence_check |

## Description
The `existence_check` for Cisco ASA represents a test for retrieval of a number of lines from the Cisco ASA configuration, collected via the `show running-config` command

## Artifact Types Using this Test Type
- [cisco_asa.line_object](../../ArtifactTypes/ciscoASA/cisco_asa.line_object.md)
- [cisco_asa.snmp_group_object](../../ArtifactTypes/ciscoASA/cisco_asa.snmp_group_object.md)

## Technical Details
### Parameters
| Name                  |Type/Constraint    | Description |
| ----------------------|-------------------| ----------- |
| existence_check       | OVAL: Existence Enumerations (Extended)| This enumeration represents the complement of configuration lines which must be collected in order for this test to reach a positive result.|

### Constraints
| Name       | Type           | Content     |
| -----------|----------------| ----------- |
| OVAL: Existence Enumerations (Extended) | Static Options | `all_exist`, `any_exist`, `at_least_one_exists`, `none_satisfy`, `none_exist`, `only_one_exists` |
