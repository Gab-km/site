#system_category
```cpp
namespace std {
  const error_category& system_category() noexcept;

}
```
* error_category[link /reference/system_error/error_category.md]

##概要

<b>環境固有のエラーに関するerror_categoryを返す。</b>


##戻り値

[`error_category`](/reference/system_error/error_category.md)クラスを継承したクラスオブジェクトへの参照を返す。
この関数を呼び出すことによって返されるオブジェクトは、同じオブジェクトを指す。

この関数によって返されるオブジェクトのクラスは以下の特徴を持つ：

- [`name()`](/reference/system_error/error_category/name.md)関数によって返される文字列は`"system"`
- [`equivalent()`](/reference/system_error/error_category/equivalent.md)仮想関数の挙動は、基本クラスである[`error_category`](/reference/system_error/error_category.md)と同じである
- [`default_error_condition()`](/reference/system_error/error_category/default_error_condition.md)仮想関数は、パラメータ`ev`がPOSIXの`errno`であった場合 [`error_condition`](/reference/system_error/error_condition.md)(ev, [generic_category()](/reference/system_error/generic_category.md));` を返し、そうでない場合は`[error_condition](/reference/system_error/error_condition.md)(ev, system_category());` を返す。特定のOSに関する処理は未規定。ただし、POSIXのエラー値に対応していない場合がありえるため、環境によっては`[generic_category()](/reference/system_error/generic_category.md)が返される挙動はサポートされない。



##例外

投げない


##例

```cpp
#include <iostream>
#include <system_error>
#include <string>

int main()
{
  const std::error_category& cat = std::system_category();

  std::cout << cat.name() << std::endl;
  std::cout << cat.message(static_cast<int>(std::errc::invalid_argument)) << std::endl;
}
```
* system_category[color ff0000]

###出力

```cpp
system
Invalid argument
```

##バージョン


###言語


- C++11



###処理系

- [Clang](/implementation#clang.md): ??
- [GCC](/implementation#gcc.md): 
- [GCC, C++0x mode](/implementation#gcc.md): 4.6.1
- [ICC](/implementation#icc.md): ??
- [Visual C++](/implementation#visual_cpp.md) 10.0<h4>備考</h4>
(処理系やライブラリのバグや不完全な実装などをここに書く。なければ備考欄を削除)



##実装例

```cpp
```

##参照
```