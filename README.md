# C# 文字列拡張クラス

## 概要

文字列クラス ([string class](https://docs.microsoft.com/ja-jp/dotnet/api/system.string)) に対する拡張メソッド群

1. static メソッドラッパー
	* string クラスの static メソッドのラッパーメソッド群
	* Python ライクなアクセス
1. 追加メソッド
	* こういうのがあるといいな、な機能を追加

## 名前空間
```cs
namespace ExString
```

## 例外
従来の API 呼び出しに対して例外が送出されるパターンにおいては、  
当該メソッドにおいても同様に例外が送出される。

## 機能
#### Parse 系
文字列形式をプリミティブな型へ変換する

##### bool
```bool.Parse()``` および ```bool.TryParse()``` の Wrapper
```cs
bool result = "true".ToBool();						// result = true
bool result = "false".TryParse(out bool value);		// result = true , value = false
```
##### char
```char.Parse()``` および ```char.TryParse()``` の Wrapper
```cs
char result = "A".ToChar();							// result = 'A'
bool result = "A".TryParse(out char value);			// result = true , value = 'A'
```
##### byte
```byte.Parse()``` および ```byte.TryParse()``` の Wrapper
```cs
byte result = "10".ToByte();						// result = 10
bool result = "100".TryParse(out byte value);		// result = true , value = 100
```
##### sbyte
```sbyte.Parse()``` および ```sbyte.TryParse()``` の Wrapper
```cs
sbyte result = "-10".ToSbyte();						// result = -10
bool result = "100".TryParse(out sbyte value);		// result = true , value = 100
```
##### short
```short.Parse()``` および ```short.TryParse()``` の Wrapper
```cs
short result = "10".ToShort();						// result = 10
bool result = "100".TryParse(out short value);		// result = true , value = 100
```
##### ushort
```ushort.Parse()``` および ```ushort.TryParse()``` の Wrapper
```cs
ushort result = "10".ToUshort();					// result = 10
bool result = "100".TryParse(out ushort value);		// result = true , value = 100
```
##### int
```int.Parse()``` および ```int.TryParse()``` の Wrapper
```cs
int result = "10".ToInt();							// result = 10
bool result = "100".TryParse(out int value);		// result = true , value = 100
```
##### uint
```uint.Parse()``` および ```uint.TryParse()``` の Wrapper
```cs
uint result = "10".ToUint();						// result = 10
bool result = "100".TryParse(out uint value);		// result = true , value = 100
```
##### long
```long.Parse()``` および ```long.TryParse()``` の Wrapper
```cs
long result = "10".ToLong();						// result = 10
bool result = "100".TryParse(out long value);		// result = true , value = 100
```
##### ulong
```ulong.Parse()``` および ```ulong.TryParse()``` の Wrapper
```cs
ulong result = "10".ToUlong();						// result = 10
bool result = "100".TryParse(out ulong value);		// result = true , value = 100
```
##### float
```float.Parse()``` および ```float.TryParse()``` の Wrapper
```cs
float result = "1.0".ToFloat();						// result = 1.0
bool result = "100".TryParse(out float value);		// result = true , value = 100
```
##### double
```double.Parse()``` および ```double.TryParse()``` の Wrapper
```cs
double result = "1.0".ToDouble();					// result = 1.0
bool result = "100".TryParse(out double value);		// result = true , value = 100
```
##### decimal
```decimal.Parse()``` および ```decimal.TryParse()``` の Wrapper
```cs
decimal result = "10".ToDecimal();					// result = 10
bool result = "100".TryParse(out decimal value);	// result = true , value = 100
```
##### enum
定義済 enum へ変換する
```cs
enum Number {
	FIRST = 1,
	SECOND = 2,
	THIRD = 3
}
Number result = "FIRST".ToEnum();					// result = Number.FIRST
```
##### Generic Parse
ジェネリック形式を用いた汎用的 ```Parse()``` および ```TryParse()```
```cs
int result = "10".Parse<int>();
bool result = "1000".TryParse<int>(out int value);
```
##### CanParse
```Parse()``` が可能かを調べる
```cs
// Generic
bool result = "1000".CanParse<int>();
// 型を引数で与える
bool result = "1.25".CanParse(typeof(double));
```

#### Format
```string.Format()``` の Wrapper
```cs
string formatted = "{0}-{1}".Format("abc", "def");		// formatted = "abc-def"
```

#### Join
```string.Join()``` の Wrapper
```cs
string[] src = { "1", "2", "3" };
string joined = "-".Join(src);		// joined = "1-2-3"
```

#### IsEmpty
```string.IsNullOrEmpty()``` の Wrapper
空文字列または半角空白のみであるかを判定する
```cs
// 空文字列
bool isEmpty;
isEmpty = "".IsEmpty();			// true
isEmpty = "AAA".IsEmpty();		// false

// 空白文字列
isEmpty = " ".IsEmpty();				// false
isEmpty = " ".IsEmptyOrWhiteSpace();	// true
```

## 注意事項
* MSTest にて簡易な単体テストまでは確認していますが、全ての状況において正しい動作をすることを保証しません。




