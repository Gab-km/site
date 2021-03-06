#operator[](C++11)
```cpp
reference operator[](size_type n);
const_reference operator[](size_type n) const;
```

##概要
n番目の要素を参照する。


##戻り値
`a[n]` は`n`番目の要素への参照を返す。`a`が`const`である場合には`const`参照を返す。


##計算量
定数時間


##備考
`a[n]` と `*(a.`[`begin()`](./begin.md)` + n)` は同じ結果になる。


##例
```cpp
#include <iostream>
#include <array>

int main()
{
  std::array<int, 3> ar = {3, 1, 4};
  const std::array<int, 3>& car = ar;

  int& a = ar[2];
  const int& b = car[2];

  std::cout << a << std::endl;
  std::cout << b << std::endl;
}
```
* [2][color ff0000]


###出力
```
4
4
```


##バージョン
###言語
- C++11


###処理系
- [Clang](/implementation#clang.md): ??
- [GCC](/implementation#gcc.md): 
- [GCC, C++0x mode](/implementation#gcc.md): 4.7.0
- [ICC](/implementation#icc.md): ??
- [Visual C++](/implementation#visual_cpp.md): 9.0 (std::tr1), 10.0, 11.0


##参照


