#operator delete
* new[meta header]
* function[meta id-type]

```cpp
// 単純な記憶域の解放
void operator delete(void* ptr) throw();											// (1) C++03 まで
void operator delete(void* ptr) noexcept;											// (1) C++11 から
void operator delete(void* ptr, std::size_t size) noexcept;							// (2) C++14 から

// 単純な記憶域の解放（例外をスローしない）
void operator delete(void* ptr, const std::nothrow_t&) throw();						// (3) C++03 まで
void operator delete(void* ptr, const std::nothrow_t&) noexcept;					// (3) C++11 から
void operator delete(void* ptr, std::size_t size, const std::nothrow_t&) noexcept;	// (4) C++14 から

// replacement-new に対応する記憶域の解放
void operator delete(void* ptr, void*) throw();										// (5) C++03 まで
void operator delete(void* ptr, void*) noexcept;									// (5) C++11 から
```
* nothrow_t[link /reference/new/nothrow_t.md]
* std::size_t[link /reference/cstddef/size_t.md]

##効果
[`new`](op_new.md)演算子によって動的に確保した記憶域を解放する。

`nothrow`版の`delete`演算子は、`nothrow`版の[`new`](op_new.md)演算子によって生成されたオブジェクトのコンストラクタが例外を送出した場合に呼び出される。

##例
```cpp
#include <iostream>
#include <new>

int main()
{
  try {
    // int型変数を動的に作成
    // 確保失敗時にbad_alloc例外が送出される
    int* p1 = new int();
    delete p1; // p1の領域を解放

    // int型変数を動的に作成
    // 確保失敗時にヌルポインタが返される
    int* p2 = new (std::nothrow) int();
    delete p2;
  }
  catch (std::bad_alloc& e) {
    std::cout << e.what() << std::endl;
    throw;
  }
}
```

###出力
```
```


##参照
- [C++14 サイズ付きデアロケーション](/lang/cpp14/sized_deallocation.md)
