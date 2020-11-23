# Equals

## Description
The `Equals` test type compares just that; equality, between a collected value and an expected value.

## Technical Details
### Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| data_type | String | Identifies the datatype of the value parameter.  The content of the `data_type` element is constrained by the "Data Types" enumeration, below. |
| value | String | the value included within the set of results/ value to be tested |

### Constraints
| Name       | Type           | Content     |
| -----------|----------------| ----------- |
| Data Types | Static Options | boolean, float, int, string, version, set |
