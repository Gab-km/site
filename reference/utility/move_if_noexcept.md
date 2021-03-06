#move_if_noexcept(C++11)
```cpp
namespace std {
  template <class T>
  typename conditional<
    !is_nothrow_move_constructible<T>::value && is_copy_constructible<T>::value,
    const T&, T&&
  >::type move_if_noexcept(T& x) noexcept;
}
```

##概要
例外を投げないオブジェクトをムーブする。

この関数は、対象のオブジェクトが例外を投げないムーブコンストラクタを持っている場合に右辺値参照を返し、そうでなければconst左辺値参照を返す。

この関数は、複数のオブジェクトをムーブする際に、例外安全の強い保証を得ることを目的として使用される。


##戻り値
`std::`[`move`](/reference/utility/move.md)`(x)`


##例外
投げない


##例
```cpp
#include <iostream>
#include <utility>

struct A {
  A() {}

  A(const A&)
    { std::cout << "copy" << std::endl; }

  A(A&&) noexcept
    { std::cout << "move" << std::endl; }
};

struct B {
  B() {}

  B(const B&)
    { std::cout << "copy" << std::endl; }

  B(B&&)
    { std::cout << "move" << std::endl; }
};

int main()
{
  // ムーブコンストラクタが例外を投げないのでムーブされる
  A a;
  A a1 = std::move_if_noexcept(a);

  // ムーブコンストラクタが例外を投げる可能性があるのでコピーされる
  B b;
  B b1 = std::move_if_noexcept(b);
}
```
* move_if_noexcept[color ff0000]

###出力
```
move
copy
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


