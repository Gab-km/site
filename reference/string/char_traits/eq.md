#eq
```cpp
// C++03まで
static bool eq(const char_type& c1, const char_type& c2);

// C++11以降
static constexpr bool eq(char_type c1, char_type c2) noexcept;
```

##概要
2つの文字を比較し、同じかどうかを判定する。


##戻り値
標準で定義される`char_traits`の特殊化では、`c1 == c2`の結果を返す。


##計算量
定数時間


##例
```cpp
#include <iostream>
#include <string>

int main()
{
  if (std::char_traits<char>::eq('a', 'a')) {
    std::cout << "equal" << std::endl;
  }
  else {
    std::cout << "not equal" << std::endl;
  }
}
```

###出力
```
equal
```

##参照

