#wbuffer_convert(C++11)
```cpp
namespace std {
  template <class Codecvt,
            class Elem = wchar_t,
            class Tr = std::char_traits<Elem> >
  class wbuffer_convert : public std::basic_streambuf<Elem, Tr>;
}
```
* char_traits[link /reference/string/char_traits.md]

##概要
(ここに、クラスの概要を記載する)

###メンバ関数

| | |
|----------------------------|--------------------------------------------------|
| `(constructor)` | コンストラクタ |
| `rdbuf` | ストリームバッファのリダイレクト |
| `state` | 変換の状態を取得する |

###メンバ型

| | |
|-------------------------|------------------------------------------------------------------------------------------------------------|
| `state_type` | ストリームのマルチバイト文字の変換の状態を表す型 `Codecvt::state_type` |

###例
```cpp
```

###出力
```
```

##バージョン
###言語
- C++11:

###参照

