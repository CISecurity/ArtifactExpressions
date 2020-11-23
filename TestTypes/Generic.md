# Generic Test Types

The following generic test types utilize common parameters and constraints:
- Equal
- Equal To
- Equals
- Greater Than
- Greater Than or Equal
- Less Than
- Less Than or Equal
- Not Equal
- Pattern Match
- Pattern Not Match


## Description
The generic data types utilize common parameters and constraints to enable the appropriate comparison between collected values and expected values.

## Technical Details
### Parameters
| Name                  |Type    | Description |
| ----------------------|--------| ----------- |
| data_type | String | Identifies the datatype of the value parameter.  The content of the `data_type` element is constrained by the "Data Types" enumeration, below. |
| value | String | The value included within the set of results/value to be tested.  When the TestType is "Pattern Match" or "Pattern Not Match", the `value` parameter represents the regular expression applied to collected values to determine a match. |

### Constraints
| Name       | Type           | Content     |
| -----------|----------------| ----------- |
| Data Types | Static Options | `boolean`, `float`, `int`, `string`, `version`, `set` |
