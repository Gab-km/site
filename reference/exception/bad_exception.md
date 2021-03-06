#bad_exception
```cpp
namespace std {
  class bad_exception : public exception;
}
```
* exception[link /reference/exception/exception.md]

##概要

`bad_exception`クラスは、関数に対して例外の型を制限し、指定外の型を送出した場合に発生する例外である。このクラスの例外オブジェクトは自動で送出されるわけではなく、ユーザー自身が[`unexpected_handler`](/reference/exception/set_unexpected.md)を指定してその中で例外オブジェクトの再送出を行うことで、`bad_exception`例外が送出される。

###メンバ関数

| | |
|----------------------------------------------------------------------------------------------------|-----------------------------------------------|
| `bad_exception() noexcept;` `bad_exception(const bad_exception&) noexcept;` | コンストラクタ |
| `virtual ~bad_exception() = default;` | デストラクタ |
| `bad_exception& operator=(const bad_exception&) noexcept;` | 代入演算子 |
| `virtual const char* what() const noexcept;` | 実装定義のエラー内容を取得する |

###例
```cpp
#include <exception>
#include <stdexcept>
#include <iostream>

using namespace std;

void user_unexpected()
{
  throw;
}

void not_runtime_error_throw() throw(runtime_error, bad_exception)
{
  throw invalid_argument( "throw invalid_argument." );
}

int main()
{
  set_unexpected(user_unexpected);

  // runtime_error以外を送出
  try {
    not_runtime_error_throw();
  }
  catch (runtime_error& ex) {
    cout << "caught: " << ex.what() << endl;
  }
  catch (bad_exception ex) {
    cout << "caught: bad_exception." << endl;
  }
}
```

###出力
```
caught: bad_exception.
```

##参照

