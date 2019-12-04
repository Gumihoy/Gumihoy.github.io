---
title: SQL运算符优先级
date: 2019-06-21 16:34:56
categories: 
    - SQL
tags:
    - SQL
---


### MySQL

级别 | 运算符
---|----
1   |   INTERVAL
2   |   BINARY, COLLATE
3   |   !
4   |   - (unary minus), ~ (unary bit inversion)
5   |   ^
6   |   *, /, DIV, %, MOD
7   |   -, +
8   |   <<, >>
9   |   &
10  |   &#124;  
11  |   = (comparison), <=>, >=, >, <=, <, <>, !=, IS, LIKE, REGEXP, IN
12  |   BETWEEN, CASE, WHEN, THEN, ELSE
13  |   NOT
14  |   AND, &&
15  |   XOR
16  |   OR, &#124;&#124;
17  |   = (assignment), :=


<br/>
### Oracle
级别   |   运算符  |   Purpose
------|-------|--------
1   |   +, - (as unary operators), PRIOR, CONNECT_BY_ROOT, COLLATE  |   Identity, negation, location in hierarchy
2   |   *, /    |   Multiplication, division
3   |   +, - (as binary operators), &#124;&#124;  |   Addition, subtraction, concatenation    
4   |   =, !=, <, >, <=, >= |   comparison
5   |   IS [NOT] NULL, LIKE, [NOT] BETWEEN, [NOT] IN, EXISTS, IS OF type    |   comparison
6   |   NOT |   exponentiation, logical negation
7   |   AND |   conjunction
8   |   OR  |   disjunction

<br/>
### PostgreSQL
级别    |   Operator/Element    |   Associativity   |   Description
-------|------------------------|------------------|---------
1   |   .   |   left    |   table/column name separator
2   |   ::  |   left    |   PostgreSQL-style typecast
3   |   [ ]	|   left	|   array element selection
4   |   + -	|   right	|   unary plus, unary minus
5   |   ^   |   left	|   exponentiation
6   |   * / %   |	left	|   multiplication, division, modulo
7   |   + - |   left	|   addition, subtraction
8   |   (any other operator)	|   left	|   all other native and user-defined operators
9   |   BETWEEN IN LIKE ILIKE SIMILAR	 	|   |   range containment, set membership, string matching
10  |   < > = <= >= <>	 	|   |   comparison operators
11  |   IS ISNULL NOTNULL   |   |   IS TRUE, IS FALSE, IS NULL, IS DISTINCT FROM, etc
12  |   NOT	|   right	|   logical negation
13  |   AND	|   left	|   logical conjunction
14  |   OR	|   left	|   logical disjunction

<br/>
### Transact-SQL
级别 | 运算符
---|----
1 | ~（位非）
2 | *（乘）、/（除）、%（取模）
3 | +（正）、-（负）、+（加）、+（串联）、-（减）、&（位与）、^（位异或）、&#124;（位或）
4 | =、>、<、>=、<=、<>、!=、!>、!<（比较运算符）
5 | NOT
6 | 和
7 | ALL、ANY、BETWEEN、IN、LIKE、OR、SOME
8 | =（赋值）

---
参考
[MySQL运算符优先级](https://dev.mysql.com/doc/refman/8.0/en/operator-precedence.html)
[Oracle运算符优先级1](https://docs.oracle.com/en/database/oracle/oracle-database/18/sqlrf/About-SQL-Operators.html)
[Oracle运算符优先级2](https://docs.oracle.com/en/database/oracle/oracle-database/18/sqlrf/About-SQL-Conditions.html)
[PostgreSQL运算符优先级](https://www.postgresql.org/docs/current/sql-syntax-lexical.html#SQL-PRECEDENCE)
[Transact-SQL运算符优先级](https://docs.microsoft.com/zh-cn/sql/t-sql/language-elements/operator-precedence-transact-sql?view=sql-server-ver15)
