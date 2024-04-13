# logicalshift
## 要求如下：
 * logicalShift - shift x to the right by n, using a logical shift
 *   Can assume that 0 <= n <= 31
 *   Examples: logicalShift(0x87654321,4) = 0x08765432
 *   Legal ops: ! ~ & ^ | + << >>
 *   Max ops: 20
 *   Rating: 3
## 思路
* 逻辑右移即将所补高位置 0
* 首先我们要知道>>是算术右移
* 考虑所要处理的有负数和非负数两种情况，即对符号位进行处理 
* 设某数为 yxxx...，算术右移的结果为 yyy...yyyxxxx...（n+1 个 y） 
* 提取出来其符号位 t=y<<31，即 y000...000，再右移 n-1 位得到 yyy...yyy0...000(n 个 y）
* 注意当 n=0 时，不可以直接右移 n-1 位，故对 t 右移 n-1 位的运算为 (t>>n)<<1。 
* 将右移后所得 t 按位取反得到：y’y’y’...y’y’y’1111...
* (x>>n)&~t 即为最后结果：
    * x>>n:yyy...yyyxxxx...
    * ~t:y’y’y’...y’y’y’111...
    * (x>>n)&~t:0000...000xxxx...
## 代码
```shell
int logicalShift(int x, int n) {
	int t=(1<<31)&x;//100000000..
	t=~((t>>n)<<1); //注意 n=0 的情况 011111111
	return (x>>n)&t; 
}
```
