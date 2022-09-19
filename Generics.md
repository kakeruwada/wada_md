# ジェネリクスについて
本来こう書かなければいけないところを、、
```rust
struct i32Point<i32> { //int型
    x: i32,
    y: i32,
}

struct f32Point<f32> {//float型
    x: f32,
    y: f32,
}

fn main() {
    let integer = i32Point { x: 5, y: 10 };
    let float = f32Point { x: 1.0, y: 4.0 };
}

```

型以外の共通部分を共通化できる
```rust
struct Point<T> {
    x: T,
    y: T,
}

fn main() {
    let integer = Point { x: 5, y: 10 };
    let float = Point { x: 1.0, y: 4.0 };
}

```

こういう感じにもできる
xとyは違う型を持つという表現
```rust
struct Point<T, U> {
    x: T,
    y: U,
}

fn main() {
    let integerAndFloat = Point { x: 5, y: 4.0 };
    let integerAndStr = Point { x: 1, y: "Hello" };
}

```

## ちなみにphpでは

ジェネリクスは存在しない？が、型宣言(型ヒント)はある
引数や戻り値の前に付ける
```php
function add(int $a, int $b): int 
{
	return $a + $b;	
}
```
ただしこれだと`a = 2.3`や`a = "1"`、`a[] = 1`でも動作してしまうので

`declare(strict_types=1);`を(定義元と呼び出し元)ファイルの最初で呼ぶ