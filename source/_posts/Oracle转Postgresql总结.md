---
title: Oracle转Postgresql总结
date: 2019-08-15 23:26:48
categories: 
    - SQL转换
tags:
    - SQL转换
---

## 数据类型
Oracle数据类型  Postgresql数据类型


## 方法

数字函数：（总共 26）
	1、PG 支持 ACOS、ASIN、ATAN、ATAN2、CEIL、COS、FLOOR、ROUND、SIN/TAN/TRUNC ，但是转换的时候，函数中字段 如果是 小数 转换成Char ，不是Number，SQLNumberExpr clone 只赋值了number，其他字段抛弃了 ；看 SelectTableTest_2_ACOS、SelectTableTest_3_ASIN 
	2、PG 不支持 BITAND(x1, x2) :两个数值型数值在按位进行AND , 可以改为：x1 & x2 看：SelectTableTest_6_BITAND
	3、PG 不支持 COSH 反余弦值 ；SINH 反正弦值， TANH 看 ： SelectTableTest_9_COSH、SelectTableTest_19_SINH、SelectTableTest_24_TANH
	4、PG 不支持 NANVL(n1,n2) 如果n1是数字就返回n1，否则返回n2，看：SelectTableTest_15_NANVL
	5、 PG 不支持  REMAINDER（n1, n2） 四舍六入五取偶； 看：SelectTableTest_17_REMAINDER
	6、PG 不支持 SIGN(n1） 取数字n的符号,大于0返回1,小于0返回-1,等于0返回0; 看 ：SelectTableTest_19_SIGN


字符函数：（总共28）
	1、pg 不支持 NLS_INITCAP, 可以使用 INITCAP 替代；看 ：SelectTableTest_7_NLS_INITCAP
	2、pg 不支持 NLS_LOWER , 可以使用 LOWER 替代；看： SelectTableTest_8_NLS_LOWER
	3、pg 不支持 NLS_UPPER , 可以使用 UPPER 替代；看： SelectTableTest_10_NLS_UPPER
	4、pg 不支持 NLSSORT、NLS_SORT 看： SelectTableTest_9_NLSSORT
	5、pg 不支持 SOUNDEX  : 四个字符组成的代码 (SOUNDEX) 以评估两个字符串的相似性 ; 看： SelectTableTest_16_SOUNDEX
	6、pg 不支持 NLS_CHARSET_ID  : 字符集对应的 ID ; 看： SelectTableTest_23_NLS_CHARSET_ID
	7、pg 不支持 NLS_CHARSET_DECL_LEN  : 声明长度（也就是字符个数） ; 看： SelectTableTest_22_NLS_CHARSET_DECL_LEN 
	8、pg 不支持 NLS_CHARSET_NAME  : 字符集 ID 对应的字符集名称 ; 看： SelectTableTest_24_NLS_CHARSET_NAME 


日期时间函数：（总共25）
	1、oracle CURRENT_DATE(日期+时间) 转PG CURRENT_DATE（只有日期）, 可以用 SYSDATE 代替 ， 看: SelectTableTest_CURRENT_DATE
	2、pg 不支持 DBTIMEZONE  : 数据库时区  ; 看： SelectTableTest_4_DBTIMEZONE
	3、pg 不支持 FROM_TZ  : 将一个timstamp和timzone拼成一个timestamp with timezone  ; 看： SelectTableTest_6_FROM_TZ
	4、pg 不支持 NEXT_DAY  : 日期开始得到到未来  星期数  的日期  ; 看： SelectTableTest_11_NEXT_DAY
	5、pg 不支持 NUMTODSINTERVAL  :  把数字转换为时间 ；  且 parser 异常  ; 看： SelectTableTest_12_NUMTODSINTERVAL
	6、pg 不支持 NUMTOYMINTERVAL  :  把数字转换为时间 ；  且 parser 异常  ; 看： SelectTableTest_13_NUMTOYMINTERVAL
	7、pg 不支持 SESSIONTIMEZONE  :  会话时区  ; 看： SelectTableTest_15_SESSIONTIMEZONE 
	8、pg 不支持 TO_TIMESTAMP_TZ  :  时间+时区 字符串 转 时间  ; 看： SelectTableTest_21_TO_TIMESTAMP_TZ 
	9、pg 不支持 TO_DSINTERVAL  :  字符串转时间  ; 看： SelectTableTest_22_TO_DSINTERVAL
   10、pg 不支持 TO_YMINTERVAL  :  字符串转 年 和月  ; 看： SelectTableTest_23_TO_YMINTERVAL
   11、pg 不支持 TZ_OFFSET  :  将时区别名转换为以UTC为标准的OFFSET  ; 看： SelectTableTest_25_TZ_OFFSET  ： https://yq.aliyun.com/articles/61071


一般比较功能函数：（总共2）

转换函数：（总共 34）
	1、pg 不支持 ASCIISTR  : 字符在ASCII码表中有,则转成ASCII表中的字符, 如果没有,则转成\xxxx格式,xxxx是UTF-16的编码.  ; 看： SelectTableTest_1_ASCIISTR
	2、pg 不支持 BIN_TO_NUM  : 二进制到十进制的转换 ，可以转换： select int4(bit(4) '1010'); ; 看： SelectTableTest_1_ASCIISTR ： https://yq.aliyun.com/articles/61074
	3、pg 不支持 CHARTOROWID  : 把包含外部格式的ROWID的CHAR或VARCHAR2数值转换为内部的二进制格式 ; 看： SelectTableTest_4_CHARTOROWID  
	4、pg 不支持 COMPOSE   ; 看： SelectTableTest_5_COMPOSE   
	5、pg 不支持 DECOMPOSE   ; 看： SelectTableTest_7_DECOMPOSE   
	6、pg 不支持 RAWTONHEX  ，     可以：TO_NCHAR(RAWTOHEX(raw))   ; 看： SelectTableTest_12_RAWTONHEX
	7、pg 不支持 ROWIDTOCHAR  将ROWID转换为字符串，长度18 ，   看： SelectTableTest_13_ROWIDTOCHAR
	8、pg 不支持 ROWIDTONCHAR ，   看： SelectTableTest_14_ROWIDTONCHAR
	9、pg 不支持 TO_BINARY_DOUBLE , 可以： 通过PPAS语法使用 xxxx::newtype 实现  看： SelectTableTest_17_TO_BINARY_DOUBLE
   10、pg 不支持 TO_BINARY_FLOAT , 可以：  通过PPAS语法使用 xxxx::newtype 实现  看： SelectTableTest_18_TO_BINARY_FLOAT
   11、pg 不支持 TO_CLOB ,可以：  过PPAS语法使用 xxxx::newtype 实现  看： SelectTableTest_20_TO_CLOB
   12、pg 支持 TO_DATE， 但是只支持 两个参数，  看：  SelectTableTest_21_TO_DATE
   13、pg 不支持 TO_LOB ， 通过PPAS语法使用 xxxx::newtype 实现,  看：  SelectTableTest_23_TO_LOB
   14、pg 不支持 TO_MULTI_BYTE ： 将字符串转换为双字节表示 ，   看：  SelectTableTest_24_TO_MULTI_BYTE
   15、pg 不支持 TO_NCHAR  ； 可以： 通过PPAS语法使用 xxxx::newtype 实现 ；  看： SelectTableTest_25_TO_NCHAR
   16、pg 不支持 TO_NCLOB   将字符串转换为NCLOB类型 ； 可以： 通过PPAS语法使用 xxxx::newtype 实现 ；  看： SelectTableTest_26_TO_NCLOB
   17、pg 不支持 TO_SINGLE_BYTE  全角字符转换为半角的字符 ； 看：  SelectTableTest_29_TO_SINGLE_BYTE
   18、pg 不支持 TRANSLATE_USING  将字符串转换为规定的字符集 ；  看：  SelectTableTest_33_TRANSLATE_USING
   19、pg 不支持 UNISTR    将字符串转换为AL16UTF16或 UTF8字符 ；  看： SelectTableTest_34_UNISTR


NULL 相关函数：(总共 5)
	1、pg 不支持 LNNVL 用于某个语句的where子句中的条件，如果条件为true就返回false；如果条件为UNKNOWN或者false就返回true  ， 看： SelectTableTest_2_LNNVL
	2、PG 不支持 NVL2（x, n1, n2） 如果X是空值，返回n2， 否则返回n1 ， pg 可以用 case : SELECT case WHEN null = null then  'Not Applicable' else '1' end  ， 看： SelectTableTest_5_NVL2
	

聚合函数：(总共 36)
	1、pg 不支持 COLLECT  转换为一个嵌套表 ， 看：  SelectTableTest_2_COLLECT
	2、pg 不支持 CUME_DIST  ； 看：  SelectTableTest_7_CUME_DIST
	3、pg 不支持 DENSE_RANK  ； 看：  SelectTableTest_8_DENSE_RANK
	4、pg 不支持 GROUP_ID  消除GROUP BY子句返回的重复记录 ， 且  parse 错误； 看： SelectTableTest_10_GROUP_ID
	5、pg 不支持 GROUPING  区分常规行与合计(总计)行 ； 看：  SelectTableTest_11_GROUPING
	6、pg 不支持 GROUPING_ID 返回GROUPING位向量的十进制值 ； 看： SelectTableTest_12_GROUPING_ID
	7、pg 不支持 MEDIAN  中位数； 看： SelectTableTest_15_MEDIAN

	8、pg 不支持 PERCENTILE_CONT  ， 看： SelectTableTest_17_PERCENTILE_CONT
	9、pg 不支持 PERCENTILE_DISC  ， 看： SelectTableTest_18_PERCENTILE_DISC
   10、pg 不支持 PERCENT_RANK  ， 看： SelectTableTest_19_PERCENT_RANK
   11、pg 不支持 RANK  ， 看： SelectTableTest_20_RANK

   12、pg 不支持 统计二项测试 BINOMIAL_TEST  ； SelectTableTest_21_STATS_BINOMIAL_TEST
   13、pg 不支持 分析两个变量 STATS_CROSSTAB ； SelectTableTest_22_STATS_CROSSTAB
   14、pg 不支持 STATS_F_TEST          SelectTableTest_23_STATS_F_TEST
   15、pg 不支持 STATS_MODE            SelectTableTest_24_STATS_KS_TEST
   16、pg 不支持 STATS_MODE            SelectTableTest_25_STATS_MODE
   17、pg 不支持 STATS_MW_TEST         SelectTableTest_26_STATS_MW_TEST
   18、pg 不支持 STATS_ONE_WAY_ANOVA	  SelectTableTest_27_STATS_ONE_WAY_ANOVA
   19、pg 不支持 STATS_T_TEST  		  SelectTableTest_28_STATS_T_TEST
   20、pg 不支持 STATS_WSR_TEST  		  SelectTableTest_29_STATS_WSR_TEST


## create table
安装自带UUID，不是需要手动安装：select rds_manage_extension('create','uuid-ossp'); / CREATE EXTENSION "uuid-ossp";


## Select
SELECT:
	1、 分页：minus、intersect 、Union、Union all 与分页结合 的查询； LIMIT XX OFFSET XX
	2、 WMSYS.WM_CONCAT、WM_CONCAT、listagg -> STRING_AGG
	3、 ^= -> !=
	4、子查询 加上别名，多个子查询同样加上不同的别名
	5、rowid 不支持
	6、UTL_RAW.CAST_TO_RAW 不支持
	7、update 不能有别名 
	8、采样： sample ()、sample block () 、sample block () seed() :  https://github.com/digoal/blog/blob/master/201706/20170602_02.md
	9、select sequence_name.nextval   --> select nextval('testseq_id_seq')
	10、connect by ：  fix
	11、 oracle（+）转 左连接、右连接
	12、limit union /limit union all 处理 -> (xx limit ) union / union all xxxx
	
	13、update/delete  有 rownum -> with 处理 ： https://yq.aliyun.com/articles/59451   没有处理

	14、select count(*) xx order by xx  处理：count sql 不能有 order by
	15、or SELECT DISTINCT, ORDER BY expressions must appear in select list LINE ，fix
	16、
	17、
    
---
参考
- http://www.sqlines.com/oracle-to-postgresql
- [Oracle官网文档](https://docs.oracle.com/en/database/oracle/oracle-database/18/sqlrf/index.html)
- [Postgresql官网文档](https://www.postgresql.org/docs/devel/)
