# rand5()生成rand7()
## 题目描述
给定生成1-5的随机函数rand5()，如何得到生成1-7的随机函数rand7()？

## 思路
生成随机数要向取模运算的方向思考，则需要大随机数生成小随机数  
则需要由rand5来生成更大的等概率随机数  
若考虑用乘法来实现，则乘n就会等概率生成5个差值为n的数字，又因为可以用+rand5()来填补差值，故我们选择n=5，这样我们就可以等概率生成1-25之间的数字了。
```
rand25() = 5*(rand5()-1)+rand5()
```
又因为要等概率生成1-7，所以我们仅保留21（3\*7=21<25<4\*7=28）以前的数字  
```c
int rand7(){
    int x = 5*(rand5()-1)+rand5();
    while(x > 21){
        x = 5*(rand5()-1)+rand5();
    }
    return x%7+1;
}
```

## 总结
```
randa^2() = a*(randa()-1)+randa()  
```
