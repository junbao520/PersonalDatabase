# PEP8 Error Codes对照表

|  code   | sample message  |
|  ----  | ----  |
E1	    | Indentation<br>缩进
E101	| indentation contains mixed spaces and tabs<br>缩进包含混合空格和制表符
E111	| indentation is not a multiple of four<br>缩进不是四的倍数
E112	| expected an indented block<br>需要缩进块
E113	| unexpected indentation<br>意外缩进
E114	| indentation is not a multiple of four (comment)<br>缩进不是四的倍数（注释）
E115	| expected an indented block (comment)<br>需要缩进块（注释）
E116	| unexpected indentation (comment)<br>意外缩进（注释）
E117	| over-indented<br>过度缩进
E121 (*^)	| continuation line under-indented for hanging indent<br>缩进下的续行，用于悬挂缩进
E122 (^)	| continuation line missing indentation or outdented<br>续行缺少缩进或缩进
E123 (*)	| closing bracket does not match indentation of opening bracket’s line<br>右括号与左括号行的缩进不匹配
E124 (^)	| closing bracket does not match visual indentation<br>右括号与视觉缩进不匹配
E125 (^)	| continuation line with same indent as next logical line<br>与下一逻辑行具有相同缩进的续行
E126 (*^)	| continuation line over-indented for hanging indent<br>用于挂起缩进的缩进上的续行
E127 (^)	| continuation line over-indented for visual indent<br>视觉缩进的缩进上的续行
E128 (^)	| continuation line under-indented for visual indent<br>缩进下的连续行，用于视觉缩进
E129 (^)	| visually indented line with same indent as next logical line<br>视觉缩进行，与下一逻辑行缩进相同
E131 (^)	| continuation line unaligned for hanging indent<br>未对齐的续行用于挂起缩进
E133 (*)	| closing bracket is missing indentation<br>右括号缺少缩进
E2	| Whitespace<br>空白
E201	| whitespace after ‘(‘ <br>  “（”后的空白
E202	| whitespace before ‘)’<br>“）”之前的空白
E203	| whitespace before ‘:’ <br> “：”前的空白
E211	| whitespace before ‘(‘ “（”前的空白
E221	| multiple spaces before operator <br>运算符前的多个空格<br><br>解决方法：只要去掉加号前一个空格就好了
E222	| multiple spaces after operator<br>运算符后的多个空格
E223	| tab before operator<br>操作员前的标签
E224	| tab after operator<br>操作员后标签
E225	| missing whitespace around operator<br>运算符周围缺少空格<br><br>解决方法：操作符前后缺少空格，加上即可
E226 (*)	| missing whitespace around arithmetic operator<br>算术运算符周围缺少空格<br><br>解决方法：操作符前后缺少空格，加上即可
E227	| missing whitespace around bitwise or shift operator<br>位或移位运算符周围缺少空格<br><br>解决方法：操作符前后缺少空格，加上即可
E228	| missing whitespace around modulo operator <br>模运算符周围缺少空格<br><br>解决方法：操作符前后缺少空格，加上即可
E231	| missing whitespace after ‘,’, ‘;’, or ‘:’ <br> “，”，“；”或“：”后缺少空格
E241 (*)	| multiple spaces after ‘,’ <br>'，'后有多个空格
E242 (*)	| tab after ‘,’  <br>'，'后的制表符
E251	| unexpected spaces around keyword / parameter equals<br> 关键字/参数等于的周围有意外空格
E261	| at least two spaces before inline comment  <br>内联注释前至少有两个空格
E262	| inline comment should start with ‘# ‘ <br> 内联注释应以“#”开头
E265	| block comment should start with ‘# ‘ <br> 块注释应以“35;”开头
E266	| too many leading ‘#’ for block comment<br> 块注释的前导“35;”太多
E271	| multiple spaces after keyword  <br>关键字后有多个空格
E272	| multiple spaces before keyword <br> 关键字前有多个空格
E273	| tab after keyword <br> 关键字后的制表符
E274	| tab before keyword<br>  关键字前的制表符
E275	| missing whitespace after keyword <br>关键字后缺少空格
E3	| Blank line  <br>空行
E301	| expected 1 blank line, found 0 <br> 应为1空行，找到0
E302	| expected 2 blank lines, found 0 <br> 需要2个空行，找到0
E303	| too many blank lines (3)   <br>空行太多（3）
E304	| blank lines found after function decorator <br> 函数decorator后发现空行
E305	| expected 2 blank lines after end of function or class <br>函数或类结束后需要2个空行
E306	| expected 1 blank line before a nested definition  <br>在嵌套定义之前需要1个空行
E4	| Import <br>导入
E401	| multiple imports on one line   <br>一条线上的多个导入
E402	| module level import not at top of file <br>  模块级导入不在文件顶部
E5	| Line length  <br> 线长度
E501 (^)	| line too long (82 > 79 characters)  <br> 行太长（82>79个字符）
E502	| the backslash is redundant between brackets  <br> 括号之间的反斜杠是多余的
E7	| Statement  <br> 报表
E701	| multiple statements on one line (colon)  <br> 一行多个语句（冒号）
E702	| multiple statements on one line (semicolon) <br>  一行多个语句（分号）
E703	| statement ends with a semicolon <br> 语句以分号结尾
E704 (*)	| multiple statements on one line (def) <br> 同一行有多个语句（def）
E711 (^)	| comparison to None should be ‘if cond is None:’ <br> 与None的比较不要用“==” 应该改为 'if cond is None:'
E712 (^)	| comparison to True should be ‘if cond is True:’ or ‘if cond:’ <br> 与True的比较 不要用“==” 应该改为 'if cond is True:'或'if cond:'
E713	| test for membership should be ‘not in’ <br> 成员资格测试应为  “not in”
E714	| test for object identity should be ‘is not’  <br>对象标识的测试应为  ‘is not”
E721 (^)	| do not compare types, use ‘isinstance()’  <br> 不要比较类型，要比的话请使用  'isinstance()'
E722	| do not use bare except, specify exception instead <br>  当捕获一个异常的时候，不要使用光秃秃的except: 语句，要用详细异常声明代替
E731	| do not assign a lambda expression, use a def   <br>不分配lambda表达式，使用def
E741	| do not use variables named ‘l’, ‘O’, or ‘I’  <br> 不使用名为“l”、“O”或“I”的变量
E742	| do not define classes named ‘l’, ‘O’, or ‘I’  <br>不定义名为“l”、“O”或“I”的类
E743	| do not define functions named ‘l’, ‘O’, or ‘I’ <br> 不定义名为“l”、“O”或“I”的函数
E9	| Runtime <br> 运行时
E901	| SyntaxError or IndentationError <br> 语法错误或缩进错误
E902	| IOError IO错误
W1	| Indentation warning <br> 缩进警告
W191	| indentation contains tabs <br> 缩进包含制表符  解决方法：缩进中有tab空格，推荐用四个空格缩进
W2	| Whitespace warning <br>空白警告
W291	| trailing whitespace <br>尾随空白 ，函数、或者代码段终止处出现了多余的空格
W292	| no newline at end of file  <br>文件末尾没有换行符
W293	| blank line contains whitespace <br> 空行包含空格 
W3	| Blank line warningW3<br> 空行警告
W391	| blank line at end of file<br> 文件末尾的空行
W5	| Line break warning<br> 断线警告
W503 (*)	| line break before binary operator<br> 二进制运算符前的换行符
W504 (*)	| line break after binary operator（*）<br> 二进制运算符后的换行符
W505 (*^)	| doc line too long (82 > 79 characters)<br> 文档行太长（82>79个字符）
W6	| Deprecation warning  <br> 折旧警告
W601	| .has_key() is deprecated, use ‘in’  <br>  .has_key（）已弃用，请使用“in”
W602	| deprecated form of raising exception  <br>  不推荐的引发异常的形式
W603	| ‘<>’ is deprecated, use ‘!=’ <br>   “<>”已弃用，请使用“！=’
W604	| backticks are deprecated, use ‘repr()’ <br>  反勾号已弃用，请使用'repr（）'
W605	| invalid escape sequence ‘x’ <br> 无效的转义序列“x”
W606	| ‘async’ and ‘await’ are reserved keywords starting with Python 3.7  <br> 'async'和'await'是从Python 3.7开始的保留关键字