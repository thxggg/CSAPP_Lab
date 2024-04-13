 * bitAnd - x&y using only ~ and | 
 *   Example: bitAnd(6, 5) = 4
 *   Legal ops: ~ |
 *   Max ops: 8
 *   Rating: 1
 * 思路：德摩根定律: <img width="181" alt="image" src="https://github.com/thxggg/HNU_CSAPP_Lab/assets/126254976/0d9bdb8c-c0a8-489a-890a-7e64c8be016e">
 * 所以可以得到相应的代码：
```shell
int bitAnd(int x, int y) {
	return ~(~x | ~y) ;
}
```
