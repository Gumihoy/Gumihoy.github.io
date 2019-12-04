---
title: Oracle转MySQL总结
date: 2019-08-15 23:26:56
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
<!--   -->    
        <tr>
            <td style="text-align:center" rowspan=3>CHAR [ (size [ BYTE | CHAR ]) ]</td>
            <td style="text-align:center">CHAR</td>
            <td style="text-align:center">CHAR</td>
        </tr>
         <tr>
            <td style="text-align:center">CHAR(size)</td>
            <td style="text-align:center">CHAR(size)</td>
        </tr>
        <tr>
            <td style="text-align:center">CHAR[256, )</td>
            <td style="text-align:center">CHAR[256, )</td>
        </tr>
<!--   -->  
    </tbody>
</table>
{% endraw %}


---
参考
- http://www.sqlines.com/oracle-to-postgresql
- [Oracle官网文档](https://docs.oracle.com/en/database/oracle/oracle-database/18/sqlrf/index.html)
- [MySQL官网文档](https://dev.mysql.com/doc/refman/8.0/en/)