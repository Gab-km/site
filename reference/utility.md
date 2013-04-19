#utility
`<utility>`ヘッダでは、その他のライブラリの至る所で使用される、幾つかの基本的な関数やクラステンプレートを定義する。
演算子定義

| | |
|-----------------------------------------------------------------------------------------------------|-----------------------------|
| [`rel_ops`](./utility/rel_ops.md) | 関係演算子(namespace)<br/> |
値の入れ替え

| | |
|------------------------------------------------------------------------------------------------|----------------------------------------------------------------------|
| [`swap`](./utility/swap.md)<br/> | 二つのオブジェクトの値を交換する(function template)<br/> |
転送と移動

| | |
|------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
| [`forward`](./utility/forward.md)<br/> | 関数テンプレートの引数を転送する(function template)<br/> |
| [`move`](./utility/move.md)<br/> | 左辺値を右辺値にキャストする(function template)<br/> |
| [`move_if_noexcept`](./utility/move_if_noexcept.md)<br/> | 例外を投げないオブジェクトをムーブする(function template)<br/> |
型の値

| | |
|------------------------------------------------------------------------------------------------------|-------------------------------------------------------|
| [`declval`](./utility/declval.md)<br/> | 指定された型の値を得る(function template)<br/> |
組

| | |
|-------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
| [`pair`](./utility/pair.md)<br/> | 異なる型の二つの値の組(class template)<br/> |
| [`tuple_size`](./utility/tuple_size.md) | `pair`の要素数を取得する(class template) |
| [`tuple_element`](./utility/tuple_element.md) | `pair`の`i`番目の要素型を取得する(class template) |
| [`get`](./utility/get.md) | `pair`の`i`番目の要素を参照する(function template) |
| [`piecewise_construct_t`](./utility/piecewise_construct.md) | `pair`の要素型のコンストラクタ引数を直接受け取って構築するためのタグ型(class) |
| [`piecewise_construct`](./utility/piecewise_construct.md) | `pair`の要素型のコンストラクタ引数を直接受け取って構築するためのタグ値(constant variable) |
| `tuple` | `tuple`型の先行宣言(class template) |

