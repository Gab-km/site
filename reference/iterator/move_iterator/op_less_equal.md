#operator<=(C++11)
```cpp
namespace std {
  template <class Iterator1, class Iterator2>
  bool operator<=(const move_iterator<Iterator1>& x,
                  const move_iterator<Iterator2>& y);
}
```

##概要
2つの`move_iterator`オブジェクトにおいて、左辺が右辺以下かを判定する。


##戻り値
`return !(y < x);`


##例
```cpp
#include <iostream>
#include <vector>
#include <memory>
#include <algorithm>
#include <iterator>

int main()
{
  std::vector<std::unique_ptr<int>> v;
  for (int i = 0; i < 5; ++i)
    v.emplace_back(new int(i));

  auto it1 = std::make_move_iterator(v.begin());
  auto it2 = std::make_move_iterator(v.begin() + 1);

  if (it1 <= it2) {
    std::cout << "less" << std::endl;
  }
  else {
    std::cout << "not less" << std::endl;
  }
}
```

###出力
```
less
```

##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation#clang.md): ??
- [GCC](/implementation#gcc.md): 
- [GCC, C++0x mode](/implementation#gcc.md): 4.7.0
- [ICC](/implementation#icc.md): ??
- [Visual C++](/implementation#visual_cpp.md) ??


##参照


