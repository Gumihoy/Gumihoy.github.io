---
title: Oracle转EDB总结
date: 2019-08-15 23:26:31
categories: 
    - SQL转换
tags:
    - SQL转换
---


## 数据类型
### character datatypes

{% raw %}
<table>
    <thead>
        <tr>
            <th style="text-align:center" colspan="2">Oracle数据类型</th>
            <th style="text-align:center">EDB数据类型</th>
        </tr>
    </thead>    
    <tbody>
<!--CHAR -->
        <tr>
            <td style="text-align:center" rowspan="2">CHAR [(size [BYTE | CHAR]) ]</td>
            <td style="text-align:center">CHAR</td>
            <td style="text-align:center">CHAR</td>
        </tr>
         <tr>
            <td style="text-align:center">CHAR(size [BYTE | CHAR])</td>
            <td style="text-align:center">CHAR(size)</td>
        </tr>
<!--VARCHAR2 -->
        <tr>
            <td style="text-align:center" rowspan="2">VARCHAR2 [(size [BYTE | CHAR]) ]</td>
            <td style="text-align:center">VARCHAR2</td>
            <td style="text-align:center">VARCHAR2</td>
        </tr>
         <tr>
            <td style="text-align:center">VARCHAR2(size [BYTE | CHAR])</td>
            <td style="text-align:center">VARCHAR2(size)</td>
        </tr>
<!--NCHAR -->
        <tr>
            <td style="text-align:center" rowspan="2">NCHAR [ (size) ]</td>
            <td style="text-align:center">NCHAR</td>
            <td style="text-align:center">CHAR</td>
        </tr>
         <tr>
            <td style="text-align:center">NCHAR(size)</td>
            <td style="text-align:center">CHAR(size)</td>
        </tr>
<!--NVARCHAR2 -->
        <tr>
            <td style="text-align:center">NVARCHAR2 (size)</td>
            <td style="text-align:center">NVARCHAR2(size)</td>
            <td style="text-align:center">VARCHAR(size)</td>
        </tr>
    </tbody>
</table>
{% endraw %}


<br/>
### number datatypes

{% raw %}
<table>
    <thead>
        <tr>
            <th style="text-align:center" colspan="2">Oracle数据类型</th>
            <th style="text-align:center">EDB数据类型</th>
        </tr>
    </thead>    
    <tbody>
<!--CHAR -->
        <tr>
            <td style="text-align:center" rowspan="2">CHAR [(size [BYTE | CHAR]) ]</td>
            <td style="text-align:center">CHAR</td>
            <td style="text-align:center">CHAR</td>
        </tr>
         <tr>
            <td style="text-align:center">CHAR(size [BYTE | CHAR])</td>
            <td style="text-align:center">CHAR(size)</td>
        </tr>
<!--VARCHAR2 -->
        <tr>
            <td style="text-align:center" rowspan="2">VARCHAR2 [(size [BYTE | CHAR]) ]</td>
            <td style="text-align:center">VARCHAR2</td>
            <td style="text-align:center">VARCHAR2</td>
        </tr>
         <tr>
            <td style="text-align:center">VARCHAR2(size [BYTE | CHAR])</td>
            <td style="text-align:center">VARCHAR2(size)</td>
        </tr>
<!--NCHAR -->
        <tr>
            <td style="text-align:center" rowspan="2">NCHAR [ (size) ]</td>
            <td style="text-align:center">NCHAR</td>
            <td style="text-align:center">CHAR</td>
        </tr>
         <tr>
            <td style="text-align:center">NCHAR(size)</td>
            <td style="text-align:center">CHAR(size)</td>
        </tr>
<!--NVARCHAR2 -->
        <tr>
            <td style="text-align:center">NVARCHAR2 (size)</td>
            <td style="text-align:center">NVARCHAR2(size)</td>
            <td style="text-align:center">VARCHAR(size)</td>
        </tr>
    </tbody>
</table>
{% endraw %}


<br/>
### long and raw datatypes
{% raw %}
<table>
    <thead>
        <tr>
            <th style="text-align:center" colspan="2">Oracle数据类型</th>
            <th style="text-align:center">EDB数据类型</th>
        </tr>
    </thead>    
    <tbody>
<!--CHAR -->
        <tr>
            <td style="text-align:center" rowspan="2">CHAR [(size [BYTE | CHAR]) ]</td>
            <td style="text-align:center">CHAR</td>
            <td style="text-align:center">CHAR</td>
        </tr>
         <tr>
            <td style="text-align:center">CHAR(size [BYTE | CHAR])</td>
            <td style="text-align:center">CHAR(size)</td>
        </tr>
<!--VARCHAR2 -->
        <tr>
            <td style="text-align:center" rowspan="2">VARCHAR2 [(size [BYTE | CHAR]) ]</td>
            <td style="text-align:center">VARCHAR2</td>
            <td style="text-align:center">VARCHAR2</td>
        </tr>
         <tr>
            <td style="text-align:center">VARCHAR2(size [BYTE | CHAR])</td>
            <td style="text-align:center">VARCHAR2(size)</td>
        </tr>
<!--NCHAR -->
        <tr>
            <td style="text-align:center" rowspan="2">NCHAR [ (size) ]</td>
            <td style="text-align:center">NCHAR</td>
            <td style="text-align:center">CHAR</td>
        </tr>
         <tr>
            <td style="text-align:center">NCHAR(size)</td>
            <td style="text-align:center">CHAR(size)</td>
        </tr>
<!--NVARCHAR2 -->
        <tr>
            <td style="text-align:center">NVARCHAR2 (size)</td>
            <td style="text-align:center">NVARCHAR2(size)</td>
            <td style="text-align:center">VARCHAR(size)</td>
        </tr>
    </tbody>
</table>
{% endraw %}

<br/>
### datetime datatypes
{% raw %}
<table>
    <thead>
        <tr>
            <th style="text-align:center" colspan="2">Oracle数据类型</th>
            <th style="text-align:center">EDB数据类型</th>
        </tr>
    </thead>    
    <tbody>
<!--CHAR -->
        <tr>
            <td style="text-align:center" rowspan="2">CHAR [(size [BYTE | CHAR]) ]</td>
            <td style="text-align:center">CHAR</td>
            <td style="text-align:center">CHAR</td>
        </tr>
         <tr>
            <td style="text-align:center">CHAR(size [BYTE | CHAR])</td>
            <td style="text-align:center">CHAR(size)</td>
        </tr>
<!--VARCHAR2 -->
        <tr>
            <td style="text-align:center" rowspan="2">VARCHAR2 [(size [BYTE | CHAR]) ]</td>
            <td style="text-align:center">VARCHAR2</td>
            <td style="text-align:center">VARCHAR2</td>
        </tr>
         <tr>
            <td style="text-align:center">VARCHAR2(size [BYTE | CHAR])</td>
            <td style="text-align:center">VARCHAR2(size)</td>
        </tr>
<!--NCHAR -->
        <tr>
            <td style="text-align:center" rowspan="2">NCHAR [ (size) ]</td>
            <td style="text-align:center">NCHAR</td>
            <td style="text-align:center">CHAR</td>
        </tr>
         <tr>
            <td style="text-align:center">NCHAR(size)</td>
            <td style="text-align:center">CHAR(size)</td>
        </tr>
<!--NVARCHAR2 -->
        <tr>
            <td style="text-align:center">NVARCHAR2 (size)</td>
            <td style="text-align:center">NVARCHAR2(size)</td>
            <td style="text-align:center">VARCHAR(size)</td>
        </tr>
    </tbody>
</table>
{% endraw %}

<br/>
### large object datatypes

{% raw %}
<table>
    <thead>
        <tr>
            <th style="text-align:center" colspan="2">Oracle数据类型</th>
            <th style="text-align:center">EDB数据类型</th>
        </tr>
    </thead>    
    <tbody>
<!--CHAR -->
        <tr>
            <td style="text-align:center" rowspan="2">CHAR [(size [BYTE | CHAR]) ]</td>
            <td style="text-align:center">CHAR</td>
            <td style="text-align:center">CHAR</td>
        </tr>
         <tr>
            <td style="text-align:center">CHAR(size [BYTE | CHAR])</td>
            <td style="text-align:center">CHAR(size)</td>
        </tr>
<!--VARCHAR2 -->
        <tr>
            <td style="text-align:center" rowspan="2">VARCHAR2 [(size [BYTE | CHAR]) ]</td>
            <td style="text-align:center">VARCHAR2</td>
            <td style="text-align:center">VARCHAR2</td>
        </tr>
         <tr>
            <td style="text-align:center">VARCHAR2(size [BYTE | CHAR])</td>
            <td style="text-align:center">VARCHAR2(size)</td>
        </tr>
<!--NCHAR -->
        <tr>
            <td style="text-align:center" rowspan="2">NCHAR [ (size) ]</td>
            <td style="text-align:center">NCHAR</td>
            <td style="text-align:center">CHAR</td>
        </tr>
         <tr>
            <td style="text-align:center">NCHAR(size)</td>
            <td style="text-align:center">CHAR(size)</td>
        </tr>
<!--NVARCHAR2 -->
        <tr>
            <td style="text-align:center">NVARCHAR2 (size)</td>
            <td style="text-align:center">NVARCHAR2(size)</td>
            <td style="text-align:center">VARCHAR(size)</td>
        </tr>
    </tbody>
</table>
{% endraw %}


<br/>
### rowid datatypes
{% raw %}
<table>
    <thead>
        <tr>
            <th style="text-align:center" colspan="2">Oracle数据类型</th>
            <th style="text-align:center">EDB数据类型</th>
        </tr>
    </thead>    
    <tbody>
<!--CHAR -->
        <tr>
            <td style="text-align:center" rowspan="2">CHAR [(size [BYTE | CHAR]) ]</td>
            <td style="text-align:center">CHAR</td>
            <td style="text-align:center">CHAR</td>
        </tr>
         <tr>
            <td style="text-align:center">CHAR(size [BYTE | CHAR])</td>
            <td style="text-align:center">CHAR(size)</td>
        </tr>
<!--VARCHAR2 -->
        <tr>
            <td style="text-align:center" rowspan="2">VARCHAR2 [(size [BYTE | CHAR]) ]</td>
            <td style="text-align:center">VARCHAR2</td>
            <td style="text-align:center">VARCHAR2</td>
        </tr>
         <tr>
            <td style="text-align:center">VARCHAR2(size [BYTE | CHAR])</td>
            <td style="text-align:center">VARCHAR2(size)</td>
        </tr>
<!--NCHAR -->
        <tr>
            <td style="text-align:center" rowspan="2">NCHAR [ (size) ]</td>
            <td style="text-align:center">NCHAR</td>
            <td style="text-align:center">CHAR</td>
        </tr>
         <tr>
            <td style="text-align:center">NCHAR(size)</td>
            <td style="text-align:center">CHAR(size)</td>
        </tr>
<!--NVARCHAR2 -->
        <tr>
            <td style="text-align:center">NVARCHAR2 (size)</td>
            <td style="text-align:center">NVARCHAR2(size)</td>
            <td style="text-align:center">VARCHAR(size)</td>
        </tr>
    </tbody>
</table>
{% endraw %}

<br/>
### ANSI supported datatypes
{% raw %}
<table>
    <thead>
        <tr>
            <th style="text-align:center" colspan="2">Oracle数据类型</th>
            <th style="text-align:center">EDB数据类型</th>
        </tr>
    </thead>    
    <tbody>
<!--CHAR -->
        <tr>
            <td style="text-align:center" rowspan="2">CHAR [(size [BYTE | CHAR]) ]</td>
            <td style="text-align:center">CHAR</td>
            <td style="text-align:center">CHAR</td>
        </tr>
         <tr>
            <td style="text-align:center">CHAR(size [BYTE | CHAR])</td>
            <td style="text-align:center">CHAR(size)</td>
        </tr>
<!--VARCHAR2 -->
        <tr>
            <td style="text-align:center" rowspan="2">VARCHAR2 [(size [BYTE | CHAR]) ]</td>
            <td style="text-align:center">VARCHAR2</td>
            <td style="text-align:center">VARCHAR2</td>
        </tr>
         <tr>
            <td style="text-align:center">VARCHAR2(size [BYTE | CHAR])</td>
            <td style="text-align:center">VARCHAR2(size)</td>
        </tr>
<!--NCHAR -->
        <tr>
            <td style="text-align:center" rowspan="2">NCHAR [ (size) ]</td>
            <td style="text-align:center">NCHAR</td>
            <td style="text-align:center">CHAR</td>
        </tr>
         <tr>
            <td style="text-align:center">NCHAR(size)</td>
            <td style="text-align:center">CHAR(size)</td>
        </tr>
<!--NVARCHAR2 -->
        <tr>
            <td style="text-align:center">NVARCHAR2 (size)</td>
            <td style="text-align:center">NVARCHAR2(size)</td>
            <td style="text-align:center">VARCHAR(size)</td>
        </tr>
    </tbody>
</table>
{% endraw %}


<br/>
### any types
{% raw %}
<table>
    <thead>
        <tr>
            <th style="text-align:center" colspan="2">Oracle数据类型</th>
            <th style="text-align:center">EDB数据类型</th>
        </tr>
    </thead>    
    <tbody>
<!--CHAR -->
        <tr>
            <td style="text-align:center" rowspan="2">CHAR [(size [BYTE | CHAR]) ]</td>
            <td style="text-align:center">CHAR</td>
            <td style="text-align:center">CHAR</td>
        </tr>
         <tr>
            <td style="text-align:center">CHAR(size [BYTE | CHAR])</td>
            <td style="text-align:center">CHAR(size)</td>
        </tr>
<!--VARCHAR2 -->
        <tr>
            <td style="text-align:center" rowspan="2">VARCHAR2 [(size [BYTE | CHAR]) ]</td>
            <td style="text-align:center">VARCHAR2</td>
            <td style="text-align:center">VARCHAR2</td>
        </tr>
         <tr>
            <td style="text-align:center">VARCHAR2(size [BYTE | CHAR])</td>
            <td style="text-align:center">VARCHAR2(size)</td>
        </tr>
<!--NCHAR -->
        <tr>
            <td style="text-align:center" rowspan="2">NCHAR [ (size) ]</td>
            <td style="text-align:center">NCHAR</td>
            <td style="text-align:center">CHAR</td>
        </tr>
         <tr>
            <td style="text-align:center">NCHAR(size)</td>
            <td style="text-align:center">CHAR(size)</td>
        </tr>
<!--NVARCHAR2 -->
        <tr>
            <td style="text-align:center">NVARCHAR2 (size)</td>
            <td style="text-align:center">NVARCHAR2(size)</td>
            <td style="text-align:center">VARCHAR(size)</td>
        </tr>
    </tbody>
</table>
{% endraw %}

<br/>
### XML types
{% raw %}
<table>
    <thead>
        <tr>
            <th style="text-align:center" colspan="2">Oracle数据类型</th>
            <th style="text-align:center">EDB数据类型</th>
        </tr>
    </thead>    
    <tbody>
<!--CHAR -->
        <tr>
            <td style="text-align:center" rowspan="2">CHAR [(size [BYTE | CHAR]) ]</td>
            <td style="text-align:center">CHAR</td>
            <td style="text-align:center">CHAR</td>
        </tr>
         <tr>
            <td style="text-align:center">CHAR(size [BYTE | CHAR])</td>
            <td style="text-align:center">CHAR(size)</td>
        </tr>
<!--VARCHAR2 -->
        <tr>
            <td style="text-align:center" rowspan="2">VARCHAR2 [(size [BYTE | CHAR]) ]</td>
            <td style="text-align:center">VARCHAR2</td>
            <td style="text-align:center">VARCHAR2</td>
        </tr>
         <tr>
            <td style="text-align:center">VARCHAR2(size [BYTE | CHAR])</td>
            <td style="text-align:center">VARCHAR2(size)</td>
        </tr>
<!--NCHAR -->
        <tr>
            <td style="text-align:center" rowspan="2">NCHAR [ (size) ]</td>
            <td style="text-align:center">NCHAR</td>
            <td style="text-align:center">CHAR</td>
        </tr>
         <tr>
            <td style="text-align:center">NCHAR(size)</td>
            <td style="text-align:center">CHAR(size)</td>
        </tr>
<!--NVARCHAR2 -->
        <tr>
            <td style="text-align:center">NVARCHAR2 (size)</td>
            <td style="text-align:center">NVARCHAR2(size)</td>
            <td style="text-align:center">VARCHAR(size)</td>
        </tr>
    </tbody>
</table>
{% endraw %}


<br/>
### spatial types
{% raw %}
<table>
    <thead>
        <tr>
            <th style="text-align:center" colspan="2">Oracle数据类型</th>
            <th style="text-align:center">EDB数据类型</th>
        </tr>
    </thead>    
    <tbody>
<!--CHAR -->
        <tr>
            <td style="text-align:center" rowspan="2">CHAR [(size [BYTE | CHAR]) ]</td>
            <td style="text-align:center">CHAR</td>
            <td style="text-align:center">CHAR</td>
        </tr>
         <tr>
            <td style="text-align:center">CHAR(size [BYTE | CHAR])</td>
            <td style="text-align:center">CHAR(size)</td>
        </tr>
<!--VARCHAR2 -->
        <tr>
            <td style="text-align:center" rowspan="2">VARCHAR2 [(size [BYTE | CHAR]) ]</td>
            <td style="text-align:center">VARCHAR2</td>
            <td style="text-align:center">VARCHAR2</td>
        </tr>
         <tr>
            <td style="text-align:center">VARCHAR2(size [BYTE | CHAR])</td>
            <td style="text-align:center">VARCHAR2(size)</td>
        </tr>
<!--NCHAR -->
        <tr>
            <td style="text-align:center" rowspan="2">NCHAR [ (size) ]</td>
            <td style="text-align:center">NCHAR</td>
            <td style="text-align:center">CHAR</td>
        </tr>
         <tr>
            <td style="text-align:center">NCHAR(size)</td>
            <td style="text-align:center">CHAR(size)</td>
        </tr>
<!--NVARCHAR2 -->
        <tr>
            <td style="text-align:center">NVARCHAR2 (size)</td>
            <td style="text-align:center">NVARCHAR2(size)</td>
            <td style="text-align:center">VARCHAR(size)</td>
        </tr>
    </tbody>
</table>
{% endraw %}

<br/>
### media types
{% raw %}
<table>
    <thead>
        <tr>
            <th style="text-align:center" colspan="2">Oracle数据类型</th>
            <th style="text-align:center">EDB数据类型</th>
        </tr>
    </thead>    
    <tbody>
<!--CHAR -->
        <tr>
            <td style="text-align:center" rowspan="2">CHAR [(size [BYTE | CHAR]) ]</td>
            <td style="text-align:center">CHAR</td>
            <td style="text-align:center">CHAR</td>
        </tr>
         <tr>
            <td style="text-align:center">CHAR(size [BYTE | CHAR])</td>
            <td style="text-align:center">CHAR(size)</td>
        </tr>
<!--VARCHAR2 -->
        <tr>
            <td style="text-align:center" rowspan="2">VARCHAR2 [(size [BYTE | CHAR]) ]</td>
            <td style="text-align:center">VARCHAR2</td>
            <td style="text-align:center">VARCHAR2</td>
        </tr>
         <tr>
            <td style="text-align:center">VARCHAR2(size [BYTE | CHAR])</td>
            <td style="text-align:center">VARCHAR2(size)</td>
        </tr>
<!--NCHAR -->
        <tr>
            <td style="text-align:center" rowspan="2">NCHAR [ (size) ]</td>
            <td style="text-align:center">NCHAR</td>
            <td style="text-align:center">CHAR</td>
        </tr>
         <tr>
            <td style="text-align:center">NCHAR(size)</td>
            <td style="text-align:center">CHAR(size)</td>
        </tr>
<!--NVARCHAR2 -->
        <tr>
            <td style="text-align:center">NVARCHAR2 (size)</td>
            <td style="text-align:center">NVARCHAR2(size)</td>
            <td style="text-align:center">VARCHAR(size)</td>
        </tr>
    </tbody>
</table>
{% endraw %}


### Other datatypes


<br/>
## 方法
{% raw %}
<table>
    <thead>
        <tr>
            <th style="text-align:center" colspan="2">Oracle数据类型</th>
            <th style="text-align:center">EDB数据类型</th>
        </tr>
    </thead>   
    <tbody>
<!--CHAR -->
        <tr>
            <td style="text-align:center" rowspan="2">CHAR [(size [BYTE | CHAR]) ]</td>
            <td style="text-align:center">CHAR</td>
            <td style="text-align:center">CHAR</td>
        </tr>
         <tr>
            <td style="text-align:center">CHAR(size [BYTE | CHAR])</td>
            <td style="text-align:center">CHAR(size)</td>
        </tr>
<!--VARCHAR2 -->
        <tr>
            <td style="text-align:center" rowspan="2">VARCHAR2 [(size [BYTE | CHAR]) ]</td>
            <td style="text-align:center">VARCHAR2</td>
            <td style="text-align:center">VARCHAR2</td>
        </tr>
         <tr>
            <td style="text-align:center">VARCHAR2(size [BYTE | CHAR])</td>
            <td style="text-align:center">VARCHAR2(size)</td>
        </tr>
<!--NCHAR -->
        <tr>
            <td style="text-align:center" rowspan="2">NCHAR [ (size) ]</td>
            <td style="text-align:center">NCHAR</td>
            <td style="text-align:center">CHAR</td>
        </tr>
         <tr>
            <td style="text-align:center">NCHAR(size)</td>
            <td style="text-align:center">CHAR(size)</td>
        </tr>
<!--NVARCHAR2 -->
        <tr>
            <td style="text-align:center">NVARCHAR2 (size)</td>
            <td style="text-align:center">NVARCHAR2(size)</td>
            <td style="text-align:center">VARCHAR(size)</td>
        </tr>
    </tbody>
</table>
{% endraw %}




<br/>
## DDL

### FUNCTION

<br/>
### MATERIALIZED VIEW
#### CREATE
- 物理属性、字段属性等无关信息去掉

#### ALTER
- 物理属性、字段属性等无关信息去掉

#### DROP
- 物理属性、字段属性等无关信息去掉

<br/>
### TABLE
CREATE
- 物理属性、字段属性等无关信息去掉

ALTER
- 物理属性、字段属性等无关信息去掉

DROP
- 物理属性、字段属性等无关信息去掉

### TYPE

### TYPE BODY

### PROCEDURE

### TRIGGER

### VIEW
#### CREATE
- 物理属性、字段属性等无关信息去掉

#### ALTER
#### DROP

<br/>
## DML
### SELECT

### INSERT

### DELETE

### UPDATE



---
参考
- http://www.sqlines.com/oracle-to-postgresql
- [Oracle官网文档](https://docs.oracle.com/en/database/oracle/oracle-database/18/sqlrf/index.html)
- [EDB官网文档](https://www.enterprisedb.com/edb-docs/d/edb-postgres-advanced-server/user-guides/database-compatibility-for-oracle-developers-guide/11/toc.html)