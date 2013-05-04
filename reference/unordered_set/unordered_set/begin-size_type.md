#begin(size_type)
```cpp
<pre style='margin:0'><code style='color:black'>local_iterator begin(size_type n);
const_local_iterator begin(size_type n) const;
</pre>
```

##概要

インデックス（添え字）で指定したバケット内の先頭の要素を指すイテレータを取得する。
<code style='color:black'>unordered_set</code> は非順序連想コンテナであるため「先頭」に特に意味はないが、<code style='color:red'>begin(size_type)</code> で得られたイテレータを <code style='color:black'>[end(size_type)](/reference/unordered_set/unordered_set/end-size_type.md)</code> まで <code style='color:black'>operator++()</code> でイテレートすることで当該バケットの要素を漏れなくダブりなく走査することができる。


##要件

引数 <code style='color:black'>n</code> は <code style='color:black'>[0, [bucket_count](/reference/unordered_set/unordered_set/bucket_count.md)())</code> の範囲でなければならない。


##戻り値

インデックス（添え字） <code style='color:black'>n</code> で指定したバケット内の先頭の要素を指すイテレータ


##計算量

定数


##備考

<code style='color:black'>const</code> 版ではない <code style='color:black'>begin</code> が返す <code style='color:black'>local_iterator</code> も読み取り専用イテレータである。
（が、<code style='color:black'>local_iterator</code> と <code style='color:black'>const_local_iterator</code> が同じ型とは限らないと思われる）


##例

```cpp
<pre style='margin:0'><code style='color:black'>#include <iostream>
#include <string>
#include <unordered_set>
#include <algorithm>
#include <iterator>

int main()
{
  std::unordered_set<std::string> us{ "A", "B", "C", "D", "E", };

  decltype(us)::size_type c = us.bucket_count();
  std::cout << "bucket_count() = " << c << std::endl;

  for (decltype(us)::size_type b = 0; b < c; ++b) {
    decltype(us)::size_type s = us.bucket_size(b);
    std::cout << "bucket = " << b << ", bucket_size = " << s << ", keys = { ";
    std::copy(us.begin(b), us.end(b), std::ostream_iterator<std::string>(std::cout, ", "));
    std::cout << "}" << std::endl;
  }
}</pre>
```
* iostream[link /site/cpprefjp/reference/iostream]
* string[link /reference/string.md]
* unordered_set[link /reference/unordered_set.md]
* algorithm[link /reference/algorithm.md]
* iterator[link /reference/iterator.md]
* bucket_count[link /reference/unordered_set/unordered_set/bucket_count.md]
* bucket_size[link /reference/unordered_set/unordered_set/bucket_size.md]
* copy[link /reference/algorithm/copy.md]
* end[link /reference/unordered_set/unordered_set/end-size_type.md]
* ostream_iterator[link /reference/iterator/ostream_iterator.md]

###出力

```cpp
<pre style='margin:0'><code style='color:black'>bucket_count() = 5
bucket = 0, bucket_size = 1, keys = { E, }
bucket = 1, bucket_size = 1, keys = { D, }
bucket = 2, bucket_size = 0, keys = { }
bucket = 3, bucket_size = 1, keys = { A, }
bucket = 4, bucket_size = 2, keys = { C, B, }</pre>
```

##バージョン


###言語

- C++11

###処理系

- [Clang](/implementation#clang.md): -

- [Clang, C++0x mode](/implementation#clang.md): 3.1

- [GCC](/implementation#gcc.md): -

- [GCC, C++0x mode](/implementation#gcc.md): 4.7.0

- [ICC](/implementation#icc.md): ?

- [Visual C++](/implementation#visual_cpp.md): ?

##参照

<table style='border-collapse:collapse;border-color:rgb(136,136,136);border-width:1px' cellspacing='0' bordercolor='#888' border='1'>
<tbody>
<tr style='height:17px'>
<td style='padding:1px 0.5em;vertical-align:baseline'><code style='color:black'>[begin](/reference/unordered_set/unordered_set/begin.md)</code></td>
<td style='padding:1px 0.5em;vertical-align:baseline'>先頭要素を指すイテレータの取得</td>
</tr>
<tr style='height:17px'>
<td style='padding:1px 0.5em;vertical-align:baseline'><code style='color:black'>[end](/reference/unordered_set/unordered_set/end.md)</code></td>
<td style='padding:1px 0.5em;vertical-align:baseline'>最終要素の次を指すイテレータの取得</td>
</tr>
<tr style='height:17px'>
<td style='padding:1px 0.5em;vertical-align:baseline'><code style='color:black'>[cbegin](/reference/unordered_set/unordered_set/cbegin.md)</code></td>
<td style='padding:1px 0.5em;vertical-align:baseline'>先頭要素を指す読み取り専用イテレータの取得</td>
</tr>
<tr style='height:17px'>
<td style='padding:1px 0.5em;vertical-align:baseline'><code style='color:black'>[cend](/reference/unordered_set/unordered_set/cend.md)</code></td>
<td style='padding:1px 0.5em;vertical-align:baseline'>最終要素の次を指す読み取り専用イテレータの取得</td>
</tr>
<tr style='height:17px'>
<td style='padding:1px 0.5em;vertical-align:baseline'><code style='color:black'>[end(size_type)](/reference/unordered_set/unordered_set/end-size_type.md)</code></td>
<td style='padding:1px 0.5em;vertical-align:baseline'>インデックス（添え字）で指定したバケット内の最終要素の次を指すイテレータを取得</td>
</tr>
<tr style='height:17px'>
<td style='padding:1px 0.5em;vertical-align:baseline'><code style='color:black'>[cbegin(size_type)](/reference/unordered_set/unordered_set/cbegin-size_type.md)</code></td>
<td style='padding:1px 0.5em;vertical-align:baseline'>インデックス（添え字）で指定したバケット内の先頭要素を指す読み取り専用イテレータを取得</td>
</tr>
<tr style='height:17px'>
<td style='padding:1px 0.5em;vertical-align:baseline'><code style='color:black'>[cend(size_type)](/reference/unordered_set/unordered_set/cend-size_type.md)</code></td>
<td style='padding:1px 0.5em;vertical-align:baseline'>インデックス（添え字）で指定したバケット内の最終要素の次を指す読み取り専用イテレータを取得</td>
</tr>
</tbody>
</table>