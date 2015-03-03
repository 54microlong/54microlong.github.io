---
layout: post
title:  "Excel Sheet Column Number"
date:   2015-03-02 10:40:59
categories: jekyll update
---

## Questions1: Excel Sheet Column Title
Given a positive integer, return its corresponding column title.

    1 -> A
    2 -> B
    3 -> C
    ...
    26 -> Z
    27 -> AA
    28 -> AB 

###Boundary condition
        
    0 -> null
    1 -> A
    26 -> Z
    27 -> AA
    
    
###Good Answer:

        这题类似于十进制转换16进制的算法，只要使用除法和求余数的操作每次求出小数部分即可。
    需要注意的地方是 求余操作的结果范围是[0,n-1],但是在本题中数据范围是 [1,n],需要
    将这部分进行转换。
    
###Code:
{% highlight ruby %}
class Solution:
    # @return a string
    def convertToTitle(self, num):
        _baseline = ord('A')
        
        num = num - 1
        _re = ""
        while num / 26:
            _st = chr(num % 26 + _baseline)
            _re = _st + _re
            num = num / 26 - 1
            
        _re =  chr(num + _baseline)  + _re
        return(_re)

{% endhighlight %}
