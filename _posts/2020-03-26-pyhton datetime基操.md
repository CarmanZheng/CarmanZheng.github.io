datetime ģ��
===
datetime��һ������ʱ��Ŀ⣬��Ҫ���������У�

* datetime.date����ʾ���ڵ��ࡣ���õ�������year, month, day��
* datetime.time����ʾʱ����ࡣ���õ�������hour, minute, second, microsecond��
* datetime.datetime����ʾ����ʱ�䡣
* datetime.timedelta����ʾʱ������������ʱ���֮��ĳ��ȡ�
* datetime.tzinfo����ʱ���йص������Ϣ�������ﲻ��ϸ������۸��࣬����Ȥ��ͯЬ���Բο�python�ֲᣩ
ע��������Щ���͵Ķ����ǲ��ɱ䣨immutable���ġ�

### 1.dateģ��
### datatime.date
##### ��ȡ��ǰ���� 
```
tday= date.today()

```

ʵ����tday�а����������յ����ԣ�ʹ�� tday.year month day ����֪���ꡢ�¡��յ�
```
from datetime import date
date = datetime.date(2018, 8, 23)
print(date)
2018-8-23

```
##### ʱ��¾ת��->date

```
date.fromtimestamp(timestamp)
```
ʵ��
```
import time
from datetime import date

print (time.time())
print (date.fromtimestamp(time.time()))
 
# 1429587111.21
# 2015-04-21

```

##### ����ʱ��
```
now = date( 2010 , 04 , 06 ) 
```
ʵ��
```
now = date( 2010 , 04 , 06 ) 
tomorrow = now.replace(day = 07 ) 
print  ('now:' , now, ', tomorrow:' , tomorrow )
print  ('timetuple():' , now.timetuple())
print  ('weekday():' , now.weekday() )
print  ('isoweekday():' , now.isoweekday() )
print  ('isocalendar():' , now.isocalendar() )
print  ('isoformat():' , now.isoformat())
  
# # ---- ��� ----  
# now: 2010-04-06 , tomorrow: 2010-04-07  
# timetuple(): (2010, 4, 6, 0, 0, 0, 1, 96, -1)  
# weekday(): 1  
# isoweekday(): 2  
# isocalendar(): (2010, 14, 2)  
# isoformat(): 2010-04-06
```

### 2.timeģ��
### datatime.time
time���ʾʱ�䣬��ʱ���֡����Լ�΢����ɡ�time��Ĺ��캯�����£�
```
 class datetime.time(hour[ , minute[ , second[ , microsecond[ , tzinfo] ] ] ] ) 
```
�����������岻�����ͣ���������һ�²���tzinfo������ʾʱ����Ϣ��
* ע��һ�¸�������ȡֵ��Χ��
```
hour�ķ�ΧΪ[0, 24)��
minute�ķ�ΧΪ[0, 60)��
second�ķ�ΧΪ[0, 60)��
microsecond�ķ�ΧΪ[0, 1000000)
```

#### time�ඨ��������ԣ�
```
time.min��time.max��
time�����ܱ�ʾ����С�����ʱ�䡣
���У�time.min = time(0, 0, 0, 0)�� time.max = time(23, 59, 59, 999999)��
time.resolution��ʱ�����С��λ��������1΢�룻
```

* time���ṩ��ʵ�����������ԣ�
```
time.hour��time.minute��time.second��time.microsecond��ʱ���֡��롢΢�룻
time.tzinfo��ʱ����Ϣ��
time.replace([ hour[ , minute[ , second[ , microsecond[ , tzinfo] ] ] ] ] )������һ���µ�ʱ������ò���ָ����ʱ���֡��롢΢�����ԭ�ж����е����ԣ�ԭ�ж����Ա��ֲ��䣩��
time.isoformat()����������"HH:MM:SS"��ʽ���ַ�����ʾ��
time.strftime(fmt)�������Զ����ʽ���ַ�������������ϸ����
```
ʵ��
```
from datetime import time
tm = time(23 , 46 , 10 ) 
print ( 'tm:' , tm ��
print  'hour: %d, minute: %d, second: %d, microsecond: %d' \ 
    % (tm.hour, tm.minute, tm.second, tm.microsecond) 
tm1 = tm.replace(hour = 20 ) 
print  ('tm1:' , tm1 )
print  ('isoformat():' , tm.isoformat())
  ``
# # ---- ��� ----  
# tm: 23:46:10  
# hour: 23, minute: 46, second: 10, microsecond: 0  
# tm1: 20:46:10  
# isoformat(): 23:46:10


```

### 3.datatimeģ��
### datatime.time
datetime��date��time�Ľ���壬����date��time��������Ϣ�����Ĺ��캯�����£�
```
datetime.datetime (year, month, day[ , hour[ , minute[ , second[ , microsecond[ , tzinfo] ] ] ] ] )
```
�������ĺ�����date��time�Ĺ��캯���е�һ����Ҫע�����ֵ�ķ�Χ��

* datetime�ඨ����������뷽����
```
datetime.min��datetime.max��datetime���ܱ�ʾ����Сֵ�����ֵ��
datetime.resolution��datetime��С��λ��
datetime.today()������һ����ʾ��ǰ����ʱ���datetime����
datetime.now([tz])������һ����ʾ��ǰ����ʱ���datetime��������ṩ�˲���tz�����ȡtz������ָʱ���ı���ʱ�䣻
datetime.utcnow()������һ����ǰutcʱ���datetime����
datetime.fromtimestamp(timestamp[, tz])������ʱ��¾����һ��datetime���󣬲���tzָ��ʱ����Ϣ��
datetime.utcfromtimestamp(timestamp)������ʱ��¾����һ��datetime����
datetime.combine(date, time)������date��time������һ��datetime����
datetime.strptime(date_string, format)������ʽ�ַ���ת��Ϊdatetime����
```
ʵ��
```
dt = datetime.now() 
print  ((%Y-%m-%d %H:%M:%S %f): ' , dt.strftime( '%Y-%m-%d %H:%M:%S %f' ))
print  ((%Y-%m-%d %H:%M:%S %p): ' , dt.strftime( '%y-%m-%d %I:%M:%S %p' )) 
print  ��%%a: %s ' % dt.strftime( '%a' ) ��
print  (%%A: %s ' % dt.strftime( '%A' ) )
print  (%%b: %s ' % dt.strftime( '%b' )) 
print  (%%B: %s ' % dt.strftime( '%B' ) )
print  (����ʱ��%%c: %s ' % dt.strftime( '%c' ) )
print  (����%%x��%s ' % dt.strftime( '%x' ) )
print  (ʱ��%%X��%s ' % dt.strftime( '%X' ) )
print (���������ܵĵ�%s�� ' % dt.strftime( '%w' ) )
print  (�����ǽ���ĵ�%s�� ' % dt.strftime( '%j' ) )
print  (�����ǽ���ĵ�%s�� ' % dt.strftime( '%U' )) 
  
# # ---- ��� ----  
# (%Y-%m-%d %H:%M:%S %f): 2010-04-07 10:52:18 937000  
# (%Y-%m-%d %H:%M:%S %p): 10-04-07 10:52:18 AM  
# %a: Wed  
# %A: Wednesday  
# %b: Apr  
# %B: April  
# ����ʱ��%c: 04/07/10 10:52:18  
# ����%x��04/07/10  
# ʱ��%X��10:52:18  
# ���������ܵĵ�3��  
# �����ǽ���ĵ�097��  
# �����ǽ���ĵ�14��   

```
#### python֮time,datetime,stringת��

###### ��datetimeת���ַ��� 
```
def datetime_toString(dt): 
  return dt.strftime("%Y-%m-%d-%H") 
 ``` 
 ###### ���ַ���ת��datetime 
```
def string_toDatetime(string): 
  return datetime.strptime(string, "%Y-%m-%d-%H") 
```
###### ���ַ���ת��ʱ�����ʽ
``` 
def string_toTimestamp(strTime): 
  return time.mktime(string_toDatetime(strTime).timetuple()) 
```  
###### ��ʱ���ת���ַ�����ʽ 
```
def timestamp_toString(stamp): 
  return time.strftime("%Y-%m-%d-%H", tiem.localtime(stamp)) 
```  
###### ��datetime����ת��ʱ�����ʽ 
```
def datetime_toTimestamp(dateTim): 
  return time.mktime(dateTim.timetuple()) 

```
## ����
��ʽ�ַ�������
===
```
%a   ���ڵļ�д���� ������ΪWeb|
%A   ���ڵ�ȫд���� ������ΪWednesday|
%b   �·ݵļ�д����4�·�ΪApr
%B   �·ݵ�ȫд����4�·�ΪApril
%c:  ����ʱ����ַ�����ʾ�����磺 04/07/10 10:43:39��
%d:  ����������е�������������µĵڼ��죩
%f:  ΢�루��Χ[0,999999]��
%H:  Сʱ��24Сʱ�ƣ�[0, 23]��
%I:  Сʱ��12Сʱ�ƣ�[0, 11]��
%j:  �������е����� [001,366]���ǵ���ĵڼ��죩
%m:  �·ݣ�[01,12]��
%M:  ���ӣ�[00,59]��
%p:  AM����PM
%S:  �루��ΧΪ[00,61]��Ϊʲô����[00, 59]���ο�python�ֲ�~_~��
%U:  ���ڵ������������ĵڼ��ܣ�����������Ϊ�ܵĵ�һ��
%w:  ���������ܵ���������ΧΪ[0, 6]��6��ʾ������
%W:  ���ڵ�����������ǵ���ĵڼ��ܣ�������һ��Ϊ�ܵĵ�һ��
%x:  �����ַ������磺04/07/10��
%X:  ʱ���ַ������磺10:43:39��
%y:  2�����ֱ�ʾ�����
%Y:  4�����ֱ�ʾ�����
%z:  ��utcʱ��ļ�� ������Ǳ���ʱ�䣬���ؿ��ַ�����
%Z:  ʱ�����ƣ�����Ǳ���ʱ�䣬���ؿ��ַ�����
%%:  %% => %
```

