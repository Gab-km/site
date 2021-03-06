#swap(非メンバ関数)(C++11)
```cpp
namespace std {
  template <class T, class Container, class Compare>
  void swap(priority_queue<T, Container, Compare>& x,
            priority_queue<T, Container, Compare>& y) noexcept(noexcept(x.swap(y)));
}
```
* swap[link /reference/queue/priority_queue/swap.md]

##概要
2つの`priority_queue`オブジェクトを入れ替える。


##効果
`x.`[`swap`](./swap.md)`(y);`


##戻り値
なし


##例外
`x.`[`swap`](./swap.md)`(y)` が例外を投げない場合、この関数は決して例外を投げない。


##例
```cpp
#include <iostream>
#include <queue>

template <class PriorityQueue>
void pop_print(PriorityQueue& que)
{
  while (!que.empty()) {
    std::cout << que.top() << " ";
    que.pop();
  }
  std::cout << std::endl;
}

int main()
{
  std::priority_queue<int> x;
  x.push(1);
  x.push(2);
  x.push(3);

  std::priority_queue<int> y;
  y.push(4);
  y.push(5);
  y.push(6);

  std::swap(x, y);

  pop_print(x);
  pop_print(y);
}
```
* swap[color ff0000]

###出力
```
6 5 4 
3 2 1 
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
