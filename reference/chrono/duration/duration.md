#コンストラクタ
```cpp
constexpr duration() = default;
template <class Rep2>
constexpr explicit duration(const Rep2& r);
template <class Rep2, class Period2>
constexpr duration(const duration<Rep2, Period2>& d);
duration(const duration&) = default;
```

###durationの構築
`duration`オブジェクトを次に示す通りの要素で初期化する。

- `constexpr duration() = default;`<br/>デフォルトコンストラクタ。
- `template <class Rep2>`<br/>`constexpr explicit duration(const Rep2& r);`<br/>`rep`型に変換可能な型の値から`duration`を構築する。<br/>[`treat_as_floating_point`](/reference/chrono/treat_as_floating_point.md)`<rep>::value == true`もしくは[`treat_as_floating_point`](/reference/chrono/treat_as_floating_point.md)`<Rep2>::value == false`の場合にオーバーロード解決される。
- `template <class Rep2, class Preriod2>`<br/>`constexpr duration(const duration<Rep2, Period2>& d);`<br/>他のテンプレートパラメータを持つ`duration`から`duration`を構築する。
- `duration(const duration&) = default;`<br/>コピーコンストラクタ


###例
```cpp
#include <iostream>
#include <chrono>

using std::chrono::duration;
using std::milli; using std::micro;

int main()
{
  duration<int, milli> d1;        // デフォルトコンストラクト

  duration<int, milli> d2(3);     // 値を指定して構築(ミリ秒)
  duration<int, micro> d3 = d2;   // ミリ秒からマイクロ秒に変換

  duration<int, micro> d4 = d3;   // コピー

  std::cout << d2.count() << std::endl;
  std::cout << d3.count() << std::endl;
  std::cout << d4.count() << std::endl;
}
```

###出力
```
3
3000
3000
```

###言語
- C++11

###処理系
- GCC, C++0x mode: 4.5.1, 4.6


