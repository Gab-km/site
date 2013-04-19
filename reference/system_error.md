#system_error
`<system_error>`ヘッダでは、OSが出力するエラーを扱う機能を提供する。

| | |
|------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
| [`error_category`](./system_error/error_category.md) | エラーを分類するための基本クラス(class) |
| [`generic_category`](./system_error/generic_category.md) | 汎用のエラーに関する情報を返す(function) |
| [`system_category`](./system_error/system_category.md) | 環境固有のエラーに関する情報を返す(function) |
| [`error_code`](./system_error/error_code.md) | 環境依存のエラーコード(class) |
| [`error_condition`](./system_error/error_condition.md) | 環境非依存のエラーコード(class) |
| [`system_error`](./system_error/system_error.md) | システムエラーの例外クラス(class) |
| [`is_error_code_enum`](./system_error/is_error_code_enum.md) | `error_code`の列挙値として見なせる型か判別する(class template) |
| [`is_error_condition_enum`](./system_error/is_error_condition_enum.md) | `error_condition`の列挙値として見なせる型か判別する(class template) |
| [`errc`](./system_error/errc.md) | エラー値を表す列挙型(enum class) |
| [`make_error_code`](./system_error/make_error_code.md) | `errc`から`error_code`オブジェクトを生成する(function) |
| [`make_error_condition`](./system_error/make_error_condition.md) | `errc`から`error_condition`オブジェクトを生成する(function) |
| [`operator==`](./system_error/equal.md) | `error_code`、`error_condition`の等値比較(function) |
| [`operator!=`](./system_error/not_equal.md) | `error_code`、`error_condition`の非等値比較(function) |
| [`operator<`](./system_error/less.md) | `error_code`、`error_condition`の小なり比較(function) |
| [`operator<<`](./system_error/output_stream.md) | `error_code`のストリーム出力(function) |
| `hash` | `error_code`での特殊化(class template) |

参考：
[System error support in C++0x part1-5 - Thinking Asynchronously in C++](http://blog.think-async.com/search/label/system_error)
[Boost System Library Documentation](http://www.boost.org/doc/libs/release/libs/system/doc/index.html)

