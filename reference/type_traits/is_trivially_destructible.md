#is_trivially_destructible(C++11)
```cpp
namespace std {
  template <class T>
  struct is_trivially_destructible;
}
```

##概要
型`T`がトリビアルに破棄可能か調べる。


##要件
型`T`は完全型であるか、`const`/`volatile`修飾された(あるいはされていない)`void`か、要素数不明の配列型でなければならない。


##効果
`is_trivially_destructible`は、`T`がトリビアルに破棄可能な型であるならば[`true_type`](./integral_constant-true_type-false_type.md)から派生し、そうでなければ[`false_type`](./integral_constant-true_type-false_type.md)から派生する。  
「トリビアルに破棄可能」とは、ユーザー定義されないデストラクタを持っているということを意味する。


##例
```cpp
#include <type_traits>

struct C1 {
  // トリビアルなデストラクタを持っていない

  // 特殊関数ではないメンバ関数は持っている
  int f(int x) const { return x; }
};

struct C2 {
  // トリビアルなデストラクタを持っている
  ~C2() {}
};

// 組み込み型は全てトリビアルに破棄可能
static_assert(std::is_trivially_destructible<int>::value == true, "int is trivially destructible");
static_assert(std::is_trivially_destructible<int*>::value == true, "int* is trivially destructible");

// ユーザー定義型は、ユーザー定義のデストラクタを持っていなければトリビアルに破棄可能
static_assert(std::is_trivially_destructible<C1>::value == true, "C1 is trivially destructible");
static_assert(std::is_trivially_destructible<C2>::value == false, "C2 isn't trivially destructible");

int main() {}
```

###出力
```
```

##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation#clang.md): 3.0
- [GCC, C++0x mode](/implementation#gcc.md): 4.8.2


