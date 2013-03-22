```cpp
istreambuf_iterator<CharT, Traits>& operator++();
proxy operator++(int);
```

##概要

<b>イテレータを進める</b>


##効果

前置インクリメント：

`sbuf_->sbumpc();``return *this;`
後置インクリメント：
`sbuf->sbumpc()`を行い、前の状態を`proxy`オブジェクトとして返す。
`proxy`クラスは実装定義。

※`sbuf_`は、メンバ変数として保持している`streambuf_type`オブジェクトへのポインタ


##例

```cpp
#include <iostream>
#include <iterator>
#include <sstream>

int main()
{
  std::stringstream ss;
  ss << "123";

  std::istreambuf_iterator<char> it(ss);

  ++it; // 前置インクリメント
  std::cout << *it << std::endl;
  std::cout << *(it++) << std::endl; // 後置インクリメント
  std::cout << *it << std::endl;
}
```
* ++it[color ff0000]
* it++[color ff0000]

###出力

```cpp
2
2
3
```

##参照

