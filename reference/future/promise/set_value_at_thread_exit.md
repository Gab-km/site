#set_value_at_thread_exit
```cpp
// テンプレートパラメータRが下記特殊ケースでない場合
void promise::set_value_at_thread_exit(const R& r);
void promise::set_value_at_thread_exit(R&& r);

// テンプレートパラメータRが参照の場合
void promise<R&>::set_value_at_thread_exit(R& r);

// テンプレートパラメータRがvoidの場合
void promise<void>::set_value_at_thread_exit();
```

##概要

<b>スレッド終了時に結果の値を設定する</b>


##効果

値`r`を、すぐに準備完了状態([`future_status::ready`](/reference/future/future_status.md))にはせずに共有状態に格納する。現在のスレッドが終了し、スレッドローカル記憶域を持つ全てのオブジェクトを破棄したあと、準備完了状態にする。


##戻り値

なし



##例外

この関数は、以下のerror conditionを持つ[future_error](/reference/future/future_error.md)例外オブジェクトを送出する可能性がある：

- [`promise_already_satisfied`](/reference/future/future_errc.md) ： すでに値もしくは例外が設定されている
- `[no_state](/reference/future/future_errc.md) `： `*this`が共有状態を持っていない(`promise`オブジェクトがムーブされると起こりうる)



##例

```cpp
#include <iostream>
#include <future>
#include <thread>
#include <utility>
#include <functional>

// promiseを左辺値参照にしているのはVisual C++ 2012のバグのため
// http://connect.microsoft.com/VisualStudio/feedback/details/737812
void calc(std::promise<int>& p)
{
  int sum = 0;
  for (int i = 0; i < 10; ++i) {
    sum += i + 1;
  }

  // 結果値を書き込み、スレッド終了時に準備完了状態にする
  p.set_value_at_thread_exit(sum);
}

int main()
{
  std::promise<int> p;
  std::future<int> f = p.get_future();

  // 別スレッドで計算を行う
  std::thread t(calc, std::ref(p));

  // calc()によって書き込まれた結果を取得
  std::cout << f.get() << std::endl;

  t.join();
}
```
* http://connect.microsoft.com/VisualStudio/feedback/details/737812[link http://connect.microsoft.com/VisualStudio/feedback/details/737812]
* set_value_at_thread_exit[color ff0000]

###出力

```cpp
55
```

##例：promise<R&>
```cpp
#include <iostream>
#include <future>
#include <thread>
#include <utility>
#include <functional>
 
class Calculator {
  int sum_;
  std::future<int&> async_calc_;
  std::promise<int&> p_;
 
public:
  Calculator() : sum_(0) {}

  void start()
  {
    async_calc_ = p_.get_future();
 
    std::thread t(&Calculator::calc, this, std::ref(p_));
    t.detach();
  }
 
  int get()
  {
    return async_calc_.get();
  }
 
  void calc(std::promise<int&>& p)
  {
    int sum = 0;
    for (int i = 0; i < 10; ++i) {
      sum += i + 1;
    }
 
    // メンバ変数への参照を結果値として書き込み、
    // スレッド終了時に準備完了状態にする
    sum_ = sum;
    p.set_value_at_thread_exit(sum_);
  }
};
 
int main()
{
  Calculator c;
 
  // 非同期に計算を開始する
  c.start();
 
  // 計算結果を取得する
  int result = c.get();
 
  std::cout << result << std::endl;
}
```
* set_value_at_thread_exit[color ff0000]

###出力
```cpp
55
```

##例：promise<void>
```cpp
#include <iostream>
#include <future>
#include <thread>
#include <utility>
#include <functional>
 
class Calculator {
  int sum_;
  std::promise<void> p_;
  std::future<void> async_calc_;
 
public:
  Calculator() : sum_(0) {}

  void start()
  {
    async_calc_ = p_.get_future();
 
    std::thread t(&Calculator::calc, this, std::ref(p_));
    t.detach();
  }
 
  int get()
  {
    async_calc_.get();
    return sum_;
  }
 
  void calc(std::promise<void>& p)
  {
    int sum = 0;
    for (int i = 0; i < 10; ++i) {
      sum += i + 1;
    }
 
    // メンバ変数として結果を保持し、promiseでは計算終了の通知のみ行う
    // 通知はスレッド終了時に行われる
    sum_ = sum;
    p.set_value_at_thread_exit();
  }
};
 
int main()
{
  Calculator c;
 
  // 非同期に計算を開始する
  c.start();
 
  // 計算結果を取得する
  int result = c.get();
 
  std::cout << result << std::endl;
}
```
* set_value_at_thread_exit[color ff0000]

###出力
```cpp
55
```

##バージョン


###言語


- C++11



###処理系

- [Clang](/implementation#clang.md): ??
- [GCC](/implementation#gcc.md): 
- [GCC, C++0x mode](/implementation#gcc.md): 
- [ICC](/implementation#icc.md): ??
- [Visual C++](/implementation#visual_cpp.md) 11.0



##参照
[_at_thread_exit系の関数が存在している理由](/article/at_thread_exit.md)

