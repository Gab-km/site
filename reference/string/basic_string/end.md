#end
```cpp
iterator end() noexcept;
const_iterator end() const noexcept;
```

##概要
末尾の次を指すイテレータを取得する。


##戻り値
末尾の次を指すイテレータ


##例外
投げない


##備考
`basic_string`クラスのイテレータ範囲は、ヌル文字(`'\0'`)終端ではない。


##例
```cpp
#include <iostream>
#include <string>
#include <algorithm>

int main()
{
  std::string s = "hello";
  s.insert(s.begin() + 2, '\0');

  // 文字列オブジェクトsに含まれる、ヌル文字を除く全ての要素を出力
  std::for_each(s.begin(), s.end(), [](char c) {
    if (c != '\0')
      std::cout << c << std::endl;
  });
}
```

###出力
```
h
e
l
l
o
```

##参照
