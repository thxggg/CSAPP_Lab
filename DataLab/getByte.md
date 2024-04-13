# getByte
## 各项要求如下：
 * getByte - Extract byte n from word x
 *   Bytes numbered from 0 (LSB) to 3 (MSB)
 *   Examples: getByte(0x12345678,1) = 0x56
 *   Legal ops: ! ~ & ^ | + << >>
 *   Max ops: 6
 *   Rating: 2
## 思路
 * 求到 x 的第 n 个 byte，编号是从LSB（Least Significant Bit，最低有效位为0）到MSB（Most Significant Bit，最高有效位为3）。
 * 最低位字节（编号为 0 的字节）保留 x 的第 n 个 byte，将 word 右 
移 n 个 byte，一个字节是八位，即 n*8（n<<3）位； 
 * 1&X=X，0&X=0
 * 清除高三位字节的信息而保留最低位字节的信息，即与 0xff(11111111) 进行&运算。
## 代码
```shell
int getByte(int x, int n) {
	return x>>(n<<3)&0xff;
}
```
