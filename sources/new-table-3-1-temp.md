> NOTE: the following is a partially updated replacement for the Table 3-1
> (above). Completion is pending further development of the v2 JADN Spec.

|  **Option**  | **Type** | **ID** | **Description**                                                   |       **JADN Spec<br>Reference**       |
|:------------:|:--------:|:------:|-------------------------------------------------------------------|:--------------------------------------:|
|      id      |  Boolean |   `=`  | Items and Fields are denoted by FieldID rather than FieldName     |       4.2.2 / Table 4-2<br>4.2.3       |
|     vtype    |  String  |   `*`  | Value type for ArrayOf and MapOf                                  |            4.2.2 / Table 4-2           |
|     ktype    |  String  |   `+`  | Key type for MapOf                                                |            4.2.2 / Table 4-2           |
|     enum     |  String  |   `#`  | Extension: Enumerated type derived from a specified type          |                                        |
|    pointer   |  String  |   `>`  | Extension: Enumerated type pointers derived from a specified type |                                        |
|    format    |  String  |   `/`  | Semantic validation keyword                                       |                                        |
|    pattern   |  String  |   `%`  | Regular expression used to validate a String type                 |            4.2.1 / Table 4-1           |
| minExclusive |  Number  |   `w`  | Minimum numeric/string value, excluding bound                     |            4.2.1 / Table 4-1           |
| maxExclusive |  Number  |   `x`  | Maximum numeric/string value, excluding bound                     |            4.2.1 / Table 4-1           |
| minInclusive |  Number  |   `y`  | Minimum numeric/string value                                      |            4.2.1 / Table 4-1           |
| maxInclusive |  Number  |   `z`  | Maximum numeric/string value                                      |            4.2.1 / Table 4-1           |
|   minLength  |  Integer |   `{`  | Minimum byte or text string length, collection item count         | 4.2.1 / Table 4-1<br>4.2.2 / Table 4-2 |
|   maxLength  |  Integer |   `}`  | Maximum byte or text string length, collection item count         | 4.2.1 / Table 4-1<br>4.2.2 / Table 4-2 |
|    unique    |  Boolean |   `q`  | ArrayOf instance must not contain duplicate values                |            4.2.2 / Table 4-2           |
|      set     |  Boolean |   `s`  | ArrayOf instance is unordered and unique                          |            4.2.2 / Table 4-2           |
|   unordered  |  Boolean |   `b`  | ArrayOf instance is unordered and not unique (bag)                |            4.2.2 / Table 4-2           |
|    combine   |  Boolean |   `C`  | Choice instance is a logical combination (anyOf, allOf, oneOf)    |             4.2.3 / 4.2.3.3            |
|   abstract   |  Boolean |   `a`  | Inheritance: abstract, non-instantiatable                         |                                        |
|   restricts  |  Boolean |   `r`  | Inheritance: restriction - subset of referenced type              |                                        |
|    extends   |  Boolean |   `e`  | Inheritance: extension - superset of referenced type              |                                        |
|     final    |  Boolean |   `f`  | Inheritance: final - cannot have subtype                          |                                        |
|    default   |  String  |   `!`  | Default value                                                     |                                        |