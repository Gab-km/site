#equal_range
```cpp
namespace std {
  template<class ForwardIterator, class T>
  pair<ForwardIterator, ForwardIterator> equal_range(
      ForwardIterator first, ForwardIterator last, const T& value);

  template<class ForwardIterator, class T, class Compare>
  pair<ForwardIterator, ForwardIterator> equal_range(
      ForwardIterator first, ForwardIterator last, const T& value, Compare comp);
}
```
* pair[link /reference/utility/pair.md]

##概要
[`lower_bound()`](/reference/algorithm/lower_bound.md)と[`upper_bound()`](/reference/algorithm/upper_bound.md)の結果を組で取得する。


##要件
`[first,last)` の要素 `e` は `e < value && !(value < e)` または `comp(e, value) && !comp(value, e)` によってパーティションされていなければならない。
また、`[first, last)` の要素 `e` は全て暗黙に、`e < value` が `!(value < e)` または `comp(e, value)` が `!comp(value, e)` を意味している必要がある。


##戻り値
[`make_pair`](/reference/utility/pair/make_pair.md)([`lower_bound`](/reference/algorithm/lower_bound.md)`(first, last, value), `[`upper_bound`](/reference/algorithm/upper_bound.md)`(first, last, value))`または
[`make_pair`](/reference/utility/pair/make_pair.md)([`lower_bound`](/reference/algorithm/lower_bound.md)`(first, last, value, comp), `[`upper_bound`](/reference/algorithm/upper_bound.md)`(first, last, value, comp))`


##計算量
最大で 2 * log2(`last - first`) + O(1) 回の比較を行う


##例
```cpp
#include <iostream>
#include <vector>
#include <algorithm>

int main()
{
  std::vector<int> v = {3, 1, 4, 2, 5};

  std::sort(v.begin(), v.end());

  // 3以上の要素と、3より大きい要素を二分探索で検索
  auto result = std::equal_range(v.begin(), v.end(), 3);

  std::cout << *result.first << std::endl;
  std::cout << *result.second << std::endl;
}
```
* equal_range[color ff0000]

###出力
```
3
4
```

##実装例
```cpp
```

##参照
