# 简单的公历转农历算法 #

## 原理: ##

不需查表通过经验公式获得指定公历月的朔月时刻与本年度25个节气的定气时刻，从冬至开始按农历规则进行计算。  
虽然经验公式有小时级别的误差，但由于农历日期只需要精确到日，故经验公式使用上没有问题。  
然而由于误差的累积，本方法只能用于计算2000-2100年的农历日期。(20世纪的农历没有核算)  
如果需要精确地跨多世纪的算法，可以使用VSOP87行星理论与ELP-2000/82理论计算太阳月球准确位置从而获得农历，此精确算法公元前5000年内经度有效（但迭代项很多），详见另一个repo。

-------

## 使用方法 ##
直接调用函数 GetLunar($year,&$month,&$day,&$lunar) $year为公历年，$month为公历月，$day为公历日，*$lunar*请传入任意整数。  
返回值为汉字描述的农历，如闰六月二十，函数执行完后$month,$day的值即为数字描述的农历月农历日，$lunar值为0或1,0代表不是闰月，1则代表是闰月。
 ```
 <?php
 require("lunar.php");
 $year=2017;
 $month=8;
 $day=21;
 $lunar=0;
 echo GetLunar($year,$month,$day); //显示为：闰六月三十
  //此时$month值为6,$day值为30，$lunar值为1
 ?>
 ```
