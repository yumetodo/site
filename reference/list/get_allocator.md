#get_allocator
* list[meta header]
* std[meta namespace]
* list[meta class]
* function[meta id-type]

```cpp
allocator_type get_allocator() const;          // C++03
allocator_type get_allocator() const noexcept; // C++11
```

##概要
このコンテナで使用されているアロケータオブジェクトを取得する。


##戻り値
このコンテナで使用されているアロケータオブジェクト


##例外
投げない


##例
```cpp
#include <cassert>
#include <list>

int main()
{
  std::allocator<int> alloc;
  std::list<int> ls(alloc);

  std::allocator<int> result = ls.get_allocator();

  assert(result == alloc);
}
```
* get_allocator()[color ff0000]
* std::allocator[link /reference/memory/allocator.md]

###出力
```
```


##バージョン
###言語
- C++03
- C++11

###処理系
- [Clang](/implementation.md#clang): ?
- [GCC](/implementation.md#gcc): ?
- [ICC](/implementation.md#icc): ?
- [Visual C++](/implementation.md#visual_cpp): 7.0, 7.1, 8.0, 9.0, 10.0, 11.0, 12.0, 14.0, 14.1
	- 11.0, 12.0は、`noexcept`が実装されていないため、`throw()`が修飾されている。
	- 14.0からは、`noexcept`が修飾されている。
