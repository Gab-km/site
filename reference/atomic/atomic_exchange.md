```cpp
namespace std {

  template <class T>
  T atomic_exchange(volatile atomic<T>* object, T desired) noexcept;

  template <class T>
  T atomic_exchange(atomic<T>* object, T desired) noexcept;

}
```
* atomic[link /reference/atomic/atomic]

##概要

<b>アトミックに値を入れ替える</b>


##効果

[memory_order_seq_cst](/reference/atomic/memory_order)のメモリオーダーにしたがって、現在の値を`desired`でアトミックに置き換える



##戻り値

変更前の値が返される



##例外

投げない


##備考

この関数は、特殊化された[`atomic`](/reference/atomic/atomic)型に対して定義される。



##例

```cpp
#include <iostream>
#include <atomic>

int main()
{
  std::atomic<int> x(1);

  if (std::atomic_exchange(&x, 2) == 1) {
    std::cout << "replaced 1 by 2" << std::endl;
  }
  else {
    std::cout << "replace failed" << std::endl;
  }
}
```
* atomic_exchange[color ff0000]

###出力

```cpp
replaced 1 by 2
```

##バージョン


###言語


- C++11



###処理系

- [Clang](/implementation#clang): ??
- [GCC](/implementation#gcc): 
- [GCC, C++0x mode](/implementation#gcc): 4.7.0
- [ICC](/implementation#icc): ??
- [Visual C++](/implementation#visual_cpp) ??



##参照

