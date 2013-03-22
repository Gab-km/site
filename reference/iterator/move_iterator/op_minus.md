```cpp
move_iterator operator-(difference_type n) const;
```

##概要

<b>イテレータをN回逆に進める。</b>


##戻り値

`return move_iterator([base](/reference/iterator/move_iterator/base)() - n);`

##例

```cpp
#include <iostream>
#include <vector>
#include <memory>
#include <iterator>

int main()
{
  std::vector<std::unique_ptr<int>> v;
  for (int i = 0; i < 5; ++i)
    v.emplace_back(new int(i));

  auto it = std::make_move_iterator(v.end());
  auto it2 = it - 2;
  std::unique_ptr<int> p = *it2;

  std::cout << *p << std::endl;
}
```
* it - 2[color ff0000]

###出力

```cpp
3
```

##バージョン


###言語


- C++11



###処理系

- [Clang](/implementation#clang): ??
- [GCC](/implementation#gcc): 
- [GCC, C++0x mode](/implementation#gcc): 4.6.1
- [ICC](/implementation#icc): ??
- [Visual C++](/implementation#visual_cpp) ??



##参照

