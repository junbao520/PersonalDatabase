## Roslynator规则对照表

更多详细资料请到GitHub查阅： https://github.com/JosefPihrt/Roslynator  
以下表格中的***New Rule***列即为部门内部自定义规则。

- [Roslynator规则对照](#Roslynator规则对照表)
  - [Formatting](#Formatting)    
  - [Design](#Design)
  - [General](#General)
  - [Maintainability](#Maintainability)
  - [Naming](#Naming)
  - [Performance](#Performance)
  - [Readability](#Readability)
  - [Redundancy](#Redundancy)
  - [Simplification](#Simplification)
  - [Style](#Performance)
  - [Usage](#Usage)


### Formatting

| Id  | Title | Category | Severity | *New Rule* |
| --- | ----- | -------- | -------- | ---------- |
| RCS0001 | Add empty line after embedded statement | Formatting | None | |
| RCS0002 | Add empty line after #region | Formatting | None | ***Info*** |
| RCS0003 | Add empty line after using directive list | Formatting | None | ***Info*** |
| RCS0004 | Add empty line before closing brace of 'do' statement | Formatting | None | |
| RCS0005 | Add empty line before #endregion | Formatting | None | ***Info*** |
| RCS0006 | Add empty line before using directive list | Formatting | None | |
| RCS0007 | Add empty line between accessors | Formatting | None | |
| RCS0008 | Add empty line between block and statement | Formatting | None | |
| RCS0009 | Add empty line between declaration and documentation comment | Formatting | None | ***Info*** |
| RCS0010 | Add empty line between declarations | Formatting | None | |
| RCS0011 | Add empty line between single-line accessors (or vice versa) | Formatting | None | |
| RCS0012 | Add empty line between single-line declarations | Formatting | None | |
| RCS0013 | Add empty line between single-line declarations of different kind | Formatting | None | |
| RCS0014 | Add empty line between switch sections | Formatting | None | ***Info*** |
| RCS0015 | Add empty line between using directives with different root namespace (or vice versa) | Formatting | None | |
| RCS0016 | Add newline after attribute list | Formatting | None | ***Error*** |
| RCS0020 | Add newline after opening brace of accessor | Formatting | None | ***Error*** |
| RCS0021 | Add newline after opening brace of block | Formatting | None | ***Error*** |
| RCS0022 | Add newline after opening brace of empty block | Formatting | None | ***Error*** |
| RCS0023 | Add newline after opening brace of type declaration | Formatting | None | ***Error*** |
| RCS0024 | Add newline after switch label | Formatting | None | ***Error*** |
| RCS0025 | Add newline before accessor of full property | Formatting | None | ***Error*** |
| RCS0027 | Add newline before binary operator instead of after it (or vice versa) | Formatting | None | |
| RCS0028 | Add newline before conditional operator instead of after it (or vice versa) | Formatting | None | |
| RCS0029 | Add newline before constructor initializer | Formatting | None | |
| RCS0030 | Add newline before embedded statement | Formatting | None | ***Error*** |
| RCS0031 | Add newline before enum member | Formatting | None | ***Error*** |
| RCS0032 | Add newline before expression-body arrow instead of after it (or vice versa) | Formatting | None | |
| RCS0033 | Add newline before statement | Formatting | None | ***Error*** |
| RCS0034 | Add newline before type parameter constraint | Formatting | None | |
| RCS0036 | Remove empty line between single-line declarations of same kind | Formatting | None | |
| RCS0038 | Remove empty line between using directives with same root namespace | Formatting | None | |
| RCS0039 | Remove newline before base list | Formatting | None | |
| RCS0041 | Remove newline between 'if' keyword and 'else' keyword | Formatting | None | ***Info*** |
| RCS0042 | Remove newlines from accessor list of auto-property | Formatting | None | |
| RCS0043 | Remove newlines from accessor with single-line expression | Formatting | None | |
| RCS0044 | Use carriage return + linefeed as newline | Formatting | None | |
| RCS0045 | Use linefeed as newline | Formatting | None | |
| RCS0046 | Use spaces instead of tab | Formatting | None | ***Warning*** |
| RCS0048 | Remove newlines from initializer with single-line expression | Formatting | None | |
| RCS0049 | Add empty line after top comment | Formatting | None | |
| RCS0050 | Add empty line before top declaration | Formatting | None | ***Info*** |
| RCS0051 | Add newline between closing brace and 'while' keyword (or vice versa) | Formatting | None | ***Error*** |
| RCS0052 | Add newline before equals sign instead of after it (or vice versa) | Formatting | None | |
| RCS0053 | Fix formatting of a list | Formatting | None | |
| RCS0054 | Fix formatting of a call chain | Formatting | None | ***Info*** |
| RCS0055 | Fix formatting of a binary expression chain | Formatting | None | |
| RCS1100 | Format documentation summary on a single line | Formatting | None | |
| RCS1101 | Format documentation summary on multiple lines | Formatting | None | ***Error*** |


### Design
| Id  | Title | Category | Severity | *New Rule* |
| --- | ----- | -------- | -------- | ---------- |
| RCS1059 | Avoid locking on publicly accessible instance | Design | Warning | ***Error*** |
| RCS1075 | Avoid empty catch clause that catches System.Exception | Design | Warning | |
| RCS1090 | Add call to 'ConfigureAwait' (or vice versa) | Design | Info | |
| RCS1102 | Make class static | Design | Warning | |
| RCS1110 | Declare type inside namespace | Design | Info | |
| RCS1135 | Declare enum member with zero value (when enum has FlagsAttribute) | Design | Info | |
| RCS1157 | Composite enum value contains undefined flag | Design | Info | |
| RCS1158 | Static member in generic type should use a type parameter | Design | Info | |
| RCS1160 | Abstract type should not have public constructors | Design | Info | |
| RCS1169 | Make field read-only | Design | Info | |
| RCS1170 | Use read-only auto-implemented property | Design | Info | |
| RCS1187 | Use constant instead of field | Design | Info | |
| RCS1193 | Overriding member should not change 'params' modifier | Design | Warning | |
| RCS1194 | Implement exception constructors | Design | Warning | |
| RCS1203 | Use AttributeUsageAttribute | Design | Warning | |
| RCS1224 | Make method an extension method | Design | Info | |
| RCS1225 | Make class sealed | Design | Info | |
| RCS1227 | Validate arguments correctly | Design | Info | |
| RCS1241 | Implement non-generic counterpart | Design | Hidden | ***Error*** |


### General

| Id  | Title | Category | Severity | *New Rule* |
| --- | ----- | -------- | -------- | ---------- |
| RCS1078 | Use "" instead of string.Empty (or vice versa) | General | None | |
| RCS1079 | Throwing of new NotImplementedException | General | Info | |
| RCS1118 | Mark local variable as const | General | Info | |
| RCS1130 | Bitwise operation on enum without Flags attribute | General | Info | |
| RCS1181 | Convert comment to documentation comment | General | Hidden | ***Info*** |
| RCS1243 | Duplicate word in a comment | General | Info | |


### Maintainability

| Id  | Title | Category | Severity | *New Rule* |
| --- | ----- | -------- | -------- | ---------- |
| RCS1015 | Use nameof operator | Maintainability | Info | |
| RCS1044 | Remove original exception from throw statement | Maintainability | Warning | ***Error*** |
| RCS1060 | Declare each type in separate file | Maintainability | None | |
| RCS1138 | Add summary to documentation comment | Maintainability | Warning | |
| RCS1139 | Add summary element to documentation comment | Maintainability | Warning | |
| RCS1140 | Add exception to documentation comment | Maintainability | Hidden | |
| RCS1141 | Add 'param' element to documentation comment | Maintainability | Hidden | ***Info*** |
| RCS1142 | Add 'typeparam' element to documentation comment | Maintainability | Hidden | ***Info*** |
| RCS1168 | Parameter name differs from base name | Maintainability | Hidden | |


### Naming

| Id  | Title | Category | Severity | *New Rule* |
| --- | ----- | -------- | -------- | ---------- |
| RCS1045 | Rename private field to camel case with underscore | Naming | None | ***Error*** |
| RCS1046 | Asynchronous method name should end with 'Async' | Naming | None | ***Warning*** |
| RCS1047 | Non-asynchronous method name should not end with 'Async' | Naming | Info | |


### Performance
| Id  | Title | Category | Severity | *New Rule* |
| --- | ----- | -------- | -------- | ---------- |
| RCS1077 | Optimize LINQ method call | Performance | Info | |
| RCS1080 | Use 'Count/Length' property instead of 'Any' method | Performance | Info | |
| RCS1096 | Convert 'HasFlag' call to bitwise operation (or vice versa) | Performance | Info | |
| RCS1197 | Optimize StringBuilder.Append/AppendLine call | Performance | Info | |
| RCS1198 | Avoid unnecessary boxing of value type | Performance | None | |
| RCS1231 | Make parameter ref read-only | Performance | None | |
| RCS1235 | Optimize method call | Performance | Info | |
| RCS1242 | Do not pass non-read-only struct by read-only reference | Performance | Warning | |


### Readability

| Id  | Title | Category | Severity | *New Rule* |
| --- | ----- | -------- | -------- | ---------- |
| RCS1008 | Use explicit type instead of 'var' (when the type is not obvious) | Readability | None | |
| RCS1009 | Use explicit type instead of 'var' (foreach variable) | Readability | None | |
| RCS1012 | Use explicit type instead of 'var' (when the type is obvious) | Readability | None | |
| RCS1014 | Use explicitly typed array (or vice versa) | Readability | None | |
| RCS1018 | Add accessibility modifiers (or vice versa) | Readability | Info | ***Error*** |
| RCS1019 | Order modifiers | Readability | None | ***Warning*** |
| RCS1052 | Declare each attribute separately | Readability | None | ***Error*** |
| RCS1056 | Avoid usage of using alias directive | Readability | None | |
| RCS1081 | Split variable declaration | Readability | None | ***Error*** |
| RCS1094 | Declare using directive on top level | Readability | None | ***Error*** |
| RCS1098 | Constant values should be placed on right side of comparisons | Readability | Info | |
| RCS1099 | Default label should be the last label in a switch section | Readability | Info | |
| RCS1108 | Add 'static' modifier to all partial class declarations | Readability | Info | |
| RCS1123 | Add parentheses when necessary | Readability | Info | |
| RCS1154 | Sort enum members | Readability | Info | |
| RCS1161 | Enum should declare explicit values | Readability | Hidden | |
| RCS1162 | Avoid chain of assignments | Readability | None | ***Info*** |
| RCS1189 | Add or remove region name | Readability | Hidden | |
| RCS1191 | Declare enum value as combination of names | Readability | Info | |
| RCS1192 | Unnecessary usage of verbatim string literal | Readability | Info | |
| RCS1205 | Order named arguments according to the order of parameters | Readability | Info | |
| RCS1209 | Order type parameter constraints | Readability | Info | |
| RCS1217 | Convert interpolated string to concatenation | Readability | Hidden | |
| RCS1218 | Simplify code branching | Readability | Info | |
| RCS1222 | Merge preprocessor directives | Readability | Info | |
| RCS1228 | Unused element in documentation comment | Readability | Hidden | ***Info*** |
| RCS1230 | Unnecessary explicit use of enumerator | Readability | Info | |
| RCS1232 | Order elements in documentation comment | Readability | Info | |
| RCS1234 | Duplicate enum value | Readability | Info | |
| RCS1238 | Avoid nested ?: operators | Readability | Hidden | |
| RCS1239 | Use 'for' statement instead of 'while' statement | Readability | Info | |
| RCS1247 | Fix documentation comment tag | Readability | Info | |


### Redundancy

| Id  | Title | Category | Severity | *New Rule* |
| --- | ----- | -------- | -------- | ---------- |
| RCS1031 | Remove unnecessary braces | Redundancy | Hidden | |
| RCS1032 | Remove redundant parentheses | Redundancy | Info | |
| RCS1033 | Remove redundant boolean literal | Redundancy | Info | ***Error*** |
| RCS1034 | Remove redundant 'sealed' modifier | Redundancy | Hidden | |
| RCS1035 | Remove redundant comma in initializer | Redundancy | None | ***Warning*** |
| RCS1036 | Remove redundant empty line | Redundancy | Info | |
| RCS1037 | Remove trailing white-space | Redundancy | Info | |
| RCS1038 | Remove empty statement | Redundancy | Info | |
| RCS1039 | Remove argument list from attribute | Redundancy | Hidden | |
| RCS1040 | Remove empty 'else' clause | Redundancy | Hidden | ***Info*** |
| RCS1041 | Remove empty initializer | Redundancy | Info | |
| RCS1042 | Remove enum default underlying type | Redundancy | Hidden | ***Info*** |
| RCS1043 | Remove 'partial' modifier from type with a single part | Redundancy | Hidden | ***Info*** |
| RCS1055 | Avoid semicolon at the end of declaration | Redundancy | Hidden | ***Info*** |
| RCS1066 | Remove empty 'finally' clause | Redundancy | Hidden | ***Info*** |
| RCS1069 | Remove unnecessary case label | Redundancy | Hidden | |
| RCS1070 | Remove redundant default switch section | Redundancy | Hidden | |
| RCS1071 | Remove redundant base constructor call | Redundancy | Hidden | |
| RCS1072 | Remove empty namespace declaration | Redundancy | Info | |
| RCS1074 | Remove redundant constructor | Redundancy | Hidden | ***Info*** |
| RCS1091 | Remove empty region | Redundancy | Hidden | |
| RCS1093 | Remove file with no code | Redundancy | Info | |
| RCS1097 | Remove redundant 'ToString' call | Redundancy | Info | |
| RCS1106 | Remove empty destructor | Redundancy | Info | |
| RCS1107 | Remove redundant 'ToCharArray' call | Redundancy | Info | |
| RCS1114 | Remove redundant delegate creation | Redundancy | Info | |
| RCS1129 | Remove redundant field initalization | Redundancy | Hidden | |
| RCS1132 | Remove redundant overriding member | Redundancy | Info | |
| RCS1133 | Remove redundant Dispose/Close call | Redundancy | Hidden | ***Info*** |
| RCS1134 | Remove redundant statement | Redundancy | Hidden | ***Info*** |
| RCS1145 | Remove redundant 'as' operator | Redundancy | Hidden | ***Info*** |
| RCS1151 | Remove redundant cast | Redundancy | Hidden | ***Info*** |
| RCS1163 | Unused parameter | Redundancy | Info | |
| RCS1164 | Unused type parameter | Redundancy | Info | |
| RCS1174 | Remove redundant async/await | Redundancy | None | ***Info*** |
| RCS1175 | Unused this parameter | Redundancy | Info | |
| RCS1182 | Remove redundant base interface | Redundancy | Hidden | |
| RCS1188 | Remove redundant auto-property initialization | Redundancy | Hidden | |
| RCS1199 | Unncessary null check | Redundancy | Info | |
| RCS1211 | Remove unnecessary 'else' | Redundancy | Hidden | ***Info*** |
| RCS1212 | Remove redundant assignment | Redundancy | Info | |
| RCS1213 | Remove unused member declaration | Redundancy | Info | |
| RCS1215 | Expression is always equal to true/false | Redundancy | Warning | |
| RCS1216 | Unnecessary unsafe context | Redundancy | Info | |
| RCS1240 | Operator is unnecessary | Redundancy | Info | |



### Simplification

| Id  | Title | Category | Severity | *New Rule* |
| --- | ----- | -------- | -------- | ---------- |
| RCS1005 | Simplify nested using statement | Simplification | Hidden | |
| RCS1006 | Merge 'else' with nested 'if' | Simplification | Hidden | ***Warning*** |
| RCS1010 | Use 'var' instead of explicit type (when the type is obvious) | Simplification | None | ***Warning*** |
| RCS1020 | Simplify Nullable\<T> to T? | Simplification | Info | |
| RCS1021 | Convert lambda expression body to expression-body | Simplification | Info | |
| RCS1049 | Simplify boolean comparison | Simplification | Info | ***Error*** |
| RCS1058 | Use compound assignment | Simplification | Info | |
| RCS1061 | Merge 'if' with nested 'if' | Simplification | Hidden | |
| RCS1068 | Simplify logical negation | Simplification | Info | |
| RCS1073 | Convert 'if' to 'return' statement | Simplification | Info | |
| RCS1084 | Use coalesce expression instead of conditional expression | Simplification | Info | |
| RCS1085 | Use auto-implemented property | Simplification | Info | |
| RCS1089 | Use --/++ operator instead of assignment | Simplification | Info | |
| RCS1103 | Convert 'if' to assignment | Simplification | Info | |
| RCS1104 | Simplify conditional expression | Simplification | Info | |
| RCS1105 | Unncessary interpolation | Simplification | Info | |
| RCS1112 | Combine 'Enumerable.Where' method chain | Simplification | Info | |
| RCS1124 | Inline local variable | Simplification | Hidden | |
| RCS1128 | Use coalesce expression | Simplification | Info | |
| RCS1136 | Merge switch sections with equivalent content | Simplification | Hidden | |
| RCS1143 | Simplify coalesce expression | Simplification | Hidden | |
| RCS1171 | Simplify lazy initialization | Simplification | Info | |
| RCS1172 | Use 'is' operator instead of 'as' operator | Simplification | Warning | |
| RCS1173 | Use coalesce expression instead of 'if' | Simplification | Info | |
| RCS1176 | Use 'var' instead of explicit type (when the type is not obvious) | Simplification | None | |
| RCS1177 | Use 'var' instead of explicit type (in foreach) | Simplification | None | ***Warning***  |
| RCS1179 | Unnecessary assignment | Simplification | Info | |
| RCS1180 | Inline lazy initialization | Simplification | Info | |
| RCS1190 | Join string expressions | Simplification | Info | |
| RCS1195 | Use ^ operator | Simplification | Info | |
| RCS1201 | Use method chaining | Simplification | Hidden | |
| RCS1207 | Convert anonymous function to method group (or vice versa) | Simplification | None | ***Info*** |
| RCS1214 | Unnecessary interpolated string | Simplification | Info | |
| RCS1244 | Simplify 'default' expression | Simplification | Hidden | |


### Style

| Id  | Title | Category | Severity | *New Rule* |
| --- | ----- | -------- | -------- | ---------- |
| RCS1001 | Add braces (when expression spans over multiple lines) | Style | Info | |
| RCS1002 | Remove braces | Style | None | |
| RCS1003 | Add braces to if-else (when expression spans over multiple lines) | Style | Info | |
| RCS1004 | Remove braces from if-else | Style | None | |
| RCS1007 | Add braces | Style | None | ***Error*** |
| RCS1017 | \deprecated\ Avoid multiline expression body | Style | None | |
| RCS1050 | Add argument list to object creation expression (or vice versa) | Style | None | |
| RCS1051 | Parenthesize condition of conditional expression | Style | None | |
| RCS1063 | Avoid usage of do statement to create an infinite loop | Style | Info | |
| RCS1064 | Avoid usage of for statement to create an infinite loop | Style | None | ***Info*** |
| RCS1065 | Avoid usage of while statement to create an inifinite loop | Style | None | |
| RCS1111 | Add braces to switch section with multiple statements | Style | None | |
| RCS1126 | Add braces to if-else | Style | None | ***Error*** |
| RCS1196 | Call extension method as instance method | Style | Info | |
| RCS1208 | Reduce 'if' nesting | Style | None | ***Info*** |
| RCS1248 | Use 'is null' pattern instead of comparison (or vice versa) | Style | None | |


### Usage
| Id  | Title | Category | Severity | *New Rule* |
| --- | ----- | -------- | -------- | ---------- |
| RCS1013 | Use predefined type | Usage | None | ***Error*** |
| RCS1016 | Convert block body to expression-body (or vice versa) | Usage | None | |
| RCS1048 | Use lambda expression instead of anonymous method | Usage | Info | |
| RCS1113 | Use 'string.IsNullOrEmpty' method | Usage | Info | |
| RCS1146 | Use conditional access | Usage | Info | |
| RCS1155 | Use StringComparison when comparing strings | Usage | Warning | ***Error*** |
| RCS1156 | Use string.Length instead of comparison with empty string | Usage | Info | |
| RCS1159 | Use EventHandler\<T> | Usage | Info | |
| RCS1165 | Unconstrained type parameter checked for null | Usage | Hidden | |
| RCS1166 | Value type object is never equal to null | Usage | Info | |
| RCS1186 | Use Regex instance instead of static method | Usage | Hidden | |
| RCS1200 | Call 'Enumerable.ThenBy' instead of 'Enumerable.OrderBy' | Usage | Info | |
| RCS1202 | Avoid NullReferenceException | Usage | Info | |
| RCS1204 | Use EventArgs.Empty | Usage | Info | |
| RCS1206 | Use conditional access instead of conditional expression | Usage | Info | |
| RCS1210 | Return completed task instead of returning null | Usage | Warning | |
| RCS1220 | Use pattern matching instead of combination of 'is' operator and cast operator | Usage | Info | |
| RCS1221 | Use pattern matching instead of combination of 'as' operator and null check | Usage | Info | |
| RCS1223 | Mark publicly visible type with DebuggerDisplay attribute | Usage | None | |
| RCS1226 | Add paragraph to documentation comment | Usage | Info | |
| RCS1229 | Use async/await when necessary | Usage | Info | |
| RCS1233 | Use short-circuiting operator | Usage | Info | |
| RCS1236 | Use exception filter | Usage | Info | |
| RCS1237 | Use bit shift operator | Usage | Hidden | |
| RCS1246 | Use element access | Usage | Info | |








