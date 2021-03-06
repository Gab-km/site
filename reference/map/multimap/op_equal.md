#operator==
```cpp
template <class Key, class T, class Compare, class Allocator>
bool operator==(const multimap<Key,T,Compare,Allocator>& x, const multimap<Key,T,Compare,Allocator>& y);
```

##概要
`x` が `y` と等しいかどうかの判定を行う。


##パラメータ
- `x`, `y`<br/>
比較するコンテナ


##戻り値
二つのコンテナが等しい場合に `true`, そうでない場合に `false`。


##計算量
[`size()`](/reference/map/multimap/size.md) に対して線形時間


##例
```cpp
#include <iostream>
#include <map>
using namespace std;

int main()
{
  multimap<int,char> c1;
  c1.insert( std::make_pair(0,'a'));

  auto c2 = c1;

  cout << (c1 == c2) << endl;

  c2.insert( std::make_pair(0,'b'));

  cout << (c1 == c2) << endl;

  return 0;
}
```

###出力
```
1
0
```

###処理系
- [Clang](/implementation#clang.md): ??
- [GCC](/implementation#gcc.md): ??
- [GCC, C++11 mode](/implementation#gcc.md): ??
- [ICC](/implementation#icc.md): ??
- [Visual C++](/implementation#visual_cpp.md): ??, 11.0



