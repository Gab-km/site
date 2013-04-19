#now
```cpp
static time_point now() noexcept;
```
* time_point[link /reference/chrono/time_point.md]

##概要

<b>現在日時を取得する</b>
<b></b>


##戻り値

現在日時を指す[time_point](/reference/chrono/time_point.md)。


##例外

投げない


##例

```cpp
#include <iostream>
#include <chrono>

using namespace std::chrono;

int main()
{
  system_clock::time_point p = system_clock::now();

  std::time_t t = system_clock::to_time_t(p);
  std::cout << std::time(&t) << std::endl;
}
```
* system_clock::now()[color ff0000]

###出力例

```cpp
Tue Sep 27 14:21:13 2011
```

##バージョン


###言語


- C++11



###処理系

- [GCC, C++0x mode](/implementation#gcc.md): 4.6.1<h4></h4>
