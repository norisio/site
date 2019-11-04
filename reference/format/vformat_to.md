# vformat_to

* format[meta header]
* function[meta id-type]
* std[meta namespace]
* cpp20[meta cpp]

```cpp
namespace std {
  template<class Out, class... Args>
  Out format_to(Out out, string_view fmt, const Args&... args); // (1)

  template<class Out, class... Args>
  Out format_to(Out out, wstring_view fmt, const Args&... args); // (2)
}
```

## 概要

書式文字列`fmt`に従ったフォーマットで`args`の文字列表現を出力イテレーター`out`に出力する。

* (1): マルチバイト文字列版
* (2): ワイド文字列版

[`format_to`](format_to.md)のフォーマット引数を型消去したバージョンであり、内部的に使用される。文字列をフォーマットする目的で直接利用する必要はない。
ただし、`format_to`のような関数を自作する場合は、`vformat_to`を使って実装すると便利である。

## テンプレートパラメータ制約

`Out`は以下の制約を満たす。

* (1): `OutputIterator<const char&>`
* (2): `OutputIterator<const wchar_t&>`

## 事前条件

`out`は以下の制約を満たす型の有効なオブジェクトである。

* (1): `OutputIterator<const char&>`
* (2): `OutputIterator<const wchar_t&>`

## 効果

書式文字列`fmt`に従ったフォーマットで`args`の文字列表現を出力イテレーター`out`の`[out, out + N)`の範囲に出力する。
(ただし、`N`=`formatted_size(fmt, args...)`)

## 戻り値

`out + N` (ただし、`N`=`formatted_size(fmt, args...)`)

## 例外

書式文字列が正しくなかったり、フォーマット実行時に失敗したりした場合、[`format_error`](format_error.md)を投げる。

## バージョン
### 言語
- C++20

### 処理系
- [Clang](/implementation.md#clang): ??
- [GCC](/implementation.md#gcc): ??
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): ??

## 参照

* [P0645R10 Text Formatting](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p0645r10.html)