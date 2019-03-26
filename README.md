# fr-Compiler-1.0
A simple compiler written in python

本编译程序是基于自设计的类c模板语言开发的，样本语言的文法如下所述，为LL(1)文法，其中产生式左边的单词表示非终结符，这将成为之后设计递归子程序的依据。
This compiler is developed based on the self-designed class c template language. 
The grammar of the sample language is the LL(1) grammar, where the word on the left side of the production represents a non-terminal.
This will become the design of the recursive subroutine.

基本文法：
P ->  begin DS end
D -> int id; D|@
S -> if (B) then S1 A S| while (B) do S1 S | {L} S | id = E;S | for(S;B;S) S1 S| read(id);S|write(id);S   |@
S1->{L}
A -> else S1 |@
L -> SH
H -> L|@
B -> B1B2
B1 -> B3B4
B2 -> '|'B1B2|@
B4 -> &B3B4|@
B3 -> E Q
Q -> relop E|@
E -> E1E2
E2 -> +E1E2|-E1E2|@
E1 -> FE3
E3 -> *FE3|/FE3|@
F -> (E)|num|id 

非终结符号	  含义及功能
    P	         程序
    D	        变量定义
    S	        程序主体
    S1	   分支循环主体程序
    A	        else分支
   L、H	  生成任意数量的S
B、B1-4、Q	生成布尔表达式 
E、E1-3、F	生成算术表达式

重点非终结符号	  含义及功能
     @	          空字符
     &	          与运算
     |	          或运算
   relop	      关系运算符
    num	           数字
    id	        变量标识符
    read	  从键盘读入值赋给目标id
    write	     将目标id写到屏幕
    
词法分析器对于特定的输入处理方法如下：
		a. 换行符：将当前的行号加一。
		b. 连续空格：继续读入，直至更新跳转到下一状态。
		c. 注释：遇到//的注释将按注释信息进行储存。
    
本编译器可实现所有功能包括：
    a. 词法分析
    b. 语法分析（递归下降法）
    c. 语义分析
    d. 中间代码生成
    e. 中间代码解释（四元式）
 
具体功能块说明及异常处理在代码注释中
The specific function block description and exception handling have been marked in the code comments.

牛刀小试作品，喜欢就给一颗星星吧~
A simple try case, give me a star if you like me :)
