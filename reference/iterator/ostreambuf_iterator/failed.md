```cpp
bool failed() const noexcept;
```

##概要

<b>書き込みに失敗したかを判定する</b>


##戻り値

前回の[`operator=`](/reference/iterator/ostreambuf_iterator/op_assign)での`sbuf_->sputc()`呼び出しが`Traits::eof()`を返した場合は`true`、そうでなければ`false`を返す。


##例

```cpp
```

###出力

```cpp
##参照
```