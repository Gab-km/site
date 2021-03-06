#operator!=(C++11)
```cpp
namespace std {
  template <class RealType>
  bool operator!=(
    const piecewise_linear_distribution<RealType>& a,
    const piecewise_linear_distribution<RealType>& b);
}
```

##概要
非等値比較を行う。


##戻り値
`!(a == b)`


##計算量
定数時間


##例
```cpp
#include <iostream>
#include <random>
#include <array>

int main()
{
  std::array<double, 3> intervals1 = {0.0, 5.0, 10.0};
  std::array<double, 3> intervals2 = {0.0, 5.0, 11.0};
  std::array<double, 3> densities = {0.0, 0.5,  0.1};

  std::piecewise_linear_distribution<> a(
    intervals1.begin(),
    intervals1.end(),
    densities.begin()
  );

  std::piecewise_linear_distribution<> b(
    intervals2.begin(),
    intervals2.end(),
    densities.begin()
  );

  if (a != b) {
    std::cout << "not equal" << std::endl;
  }
  else {
    std::cout << "equal" << std::endl;
  }
}
```

###出力
```
not equal
```

##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation#clang.md): ??
- [GCC](/implementation#gcc.md): 
- [GCC, C++0x mode](/implementation#gcc.md): 4.7.2
- [ICC](/implementation#icc.md): ??
- [Visual C++](/implementation#visual_cpp.md) ??


##参照


