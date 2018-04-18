# Javascript 中的二进制操作


ECMAScrept中，所有的数值都以64位格式存储，但位操作符并不直接操作64位的值，而是先将64位的值转换成32位的整数，执行操作后再转回64位。因此看起来就像是只存在32位的整数一样。
32位中，前31位用于表示整数的值，第32位是符号位。0代表正数，1代表负数。
负数的存储形式是二进制补码。
求反码过程：
1. 求这个数的绝对值的二进制码。
2. 求二进制反码（按位取反）。
3. 反码+1。

### 按位非 ～（返回数值的反码）

```Javascript
var num1 = 25;          // 00000000000000000000000000011001
var num2 = ~num1;  //  11111111111111111111111111100110
alert(num2); // -26
```
按位非本质是：操作数的负值-1。

使用二进制操作是最底层的操作，速度更快。

### 按位与 `&`
### 按位或 `|`
### 按位异或 `^`
### 左移 `<<` 所有位向左移动指定的位数，多出的空位用0填补。
```Javascript
2 << 5 // 64  二进制10 -> 1000000
```
相当于除以2的n次方，n为左移数

### 有符号的右移 >> 数值向右移动指定的位数，保留符号位，多出的空位用符号位的值填补
相当于乘以2的n次方，n为右移数

### 无符号的右移 `>>>` 所有位右移指定位数