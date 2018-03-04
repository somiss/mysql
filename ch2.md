# mysql数据类型  

1.支持的数据类型


|type|size|desc|
|-|-|-|
|tinyint|1B|-128～127
|smallint|2B||
|mediumint|3B||
|int,integer|4B||
|bigint|8B||
|decimal(m,d)|M+2B|取值范围与double相同，精度由整数部分m，小数部分d决定|
|bit|1-8B|存储位类型
|以下是近似数值|
|float|4||
|double|8||
|以下是时间类型|||
|date|4B|0000-00-00|
|datetime|8B|0000-00-00 00:00:00|
|time|3B|00:00:00 时分秒|
|timestamp|4B|最大值2038年。插入和查询都能随时区同步变化|
|以下是字符串类型|||
|char|||
|varchar|||
|binary||只存储2进制字符串|
|varbinary|||
|enum||enum('male','female'),需要提前指定,只能取其中一个值|
|set||与enum区别是可以取范围内的多个值|

>整型的都可以使用属性auto_increment,一个表只能有一列使用.     

2.mysql运算符

|name|desc|
|-|-|
|+，-，*，/，%|算数运算符|
|>,>=,<,<=,!=|比较运算符|
|<>|同!=|
|<=>|安全的等于 *null=null*->FALSE,*null<=>null*->TRUE|
|between,in,like,is null,is not null||
|regexp/rlike|正则表达式|
|!/not,and,&&|逻辑运算符，操作数为null则返回null，*not null=null*|
|or | 逻辑运算符，不同的是 1 or null -> 1,其余则有null返回null。返回值有0，1，null三个|
|xor|异或|
|&,&#124;|位与，或运算|
|^|位异或|
|～|位取反|
|>>,<<|按位右移，左移|


3.函数

|name|desc|
|concat(s1,s2)||
|insert(str,start,len,instr)|把str第start字符开始的len个字符替换成instr|
|lower(str),upper(str)|大小写转换|
|left(str,len),right(str,len)||
|ltrim,rtrim||
|replace(str,s1,s2)|s2替换s1|
|strcmp(s1,s2)|比较s1,s2的asc码大小|
|数值函数||
|abs(x)||
|ceil(x),floor(x)|大于x的最小整数,小于x的最大整数
|rand()|0～1的随机值|
|round(x,y)|x的y位有效数字，四舍五入，y默认0|
|truncate(x,y)|同round,但是直接截断，非四舍五入|
|日期，时间||
|curdate()||
|curtime||
|now()|等同于current_timestammp|
|unix_timestamp(datetime)|时间戳|
|from_unixtime(timestamp)|unix_timestamp逆操作|
|week,year,hour,minute|获取相应的属性值|
|date_format(date,format)|格式化|
|date_add(date,interval -1 minute)|增加时间|
|流程函数||
|if(c,t,f)|c?t:f|
|ifnull(c,c2)|c<=>null?c2:c|
|case when c then v1 else v2 end|c?v1:v2|
|case exp when c1 then v1 when c2 then v2 else vd end||
|other||
|md5(),datebase(),user(),version()|


