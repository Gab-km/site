```cpp
namespace std {

  template <class T>
  void atomic_init(volatile atomic<T>* object, T desired) noexcept;

  template <class T>
  void atomic_init(atomic<T>* object, T desired) noexcept;

}
```
* atomic[link /reference/atomic/atomic]

##概要

<b>アトミックオブジェクトを初期化する</b>


##効果

この関数は、アトミックオブジェクト`object`を値`desired`で非アトミックに初期化する。この関数は、デフォルト構築されたオブジェクトに対して一度だけ呼びださなければならない。変数の初期化中に並行アクセスされた場合、それがアトミックな操作であったとしてもデータ競合を引き起こす。


##戻り値

なし


##例外

投げない


##備考

この関数は、C言語との互換性のために存在している。


##例

```cpp
```

###出力

```cpp
##バージョン
```

###言語


- C++11



###処理系

- [Clang](/implementation#clang): 
- [GCC](/implementation#gcc): 
- [GCC, C++0x mode](/implementation#gcc): 
- [ICC](/implementation#icc): ??
- [Visual C++](/implementation#visual_cpp) ??<h4>備考</h4>
この関数は、GCC 4.7およびClang 3.1では実装が存在しなかった。動作する環境がないため、サンプルコードは記載していない。



##参照

