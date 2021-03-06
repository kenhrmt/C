# C言語まとめ

目次

[基本文法](#基本文法)<br>
  - helloworld
  - 変数の型
  - 演算子
  - 条件分岐
  - 繰り返し
  - 配列
  - 文字列
  
[関数](#関数)<br>
[ポインタ](#ポインタ)<br>
[構造体](#構造体)<br>
[マクロ](#マクロ)<br>
[その他](#その他)<br>
 
 
# 基本文法

## hello world

~~~cpp
#include <stdio.h>
int main()
{
　　　　//　コメント
  pruntf("Hello world!\n");
  return 0;
}
~~~
## エスケープシーケンス　特殊文字

| エスケープシーケンス | 意味 |
|:---|:---| 
|` \n `| 改行 |
|` \f `| 改ページ |
|` \' `| シングルクォーテーション(') |
|` \" `| ダブルクォーテーション(") |
|` \\ `| バックスラッシュ(\\) |
|` \? `| クエスチョン(?)　|
|` \a `| 警報音 |
|` \0 `| Null |
|` \ccc `| 8進数の文字コードを持つ文字 |
|` \xhh `| 16進数の文字コードを持つ文字 |

## 変数の型

~~~
・変数の宣言
データ型　変数名;
データ型　変数名,変数名,・・・;

・変数の初期化
データ型　変数名　=　初期値;

・変数を用いたprintfによる画面出力
printf("変換書式", 出力したい変数);

・変数を用いたscanfによる入力
scanf("変換書式", 入力先の変数のアドレス);
<例>　scanf("%d", &foo)
~~~

~~~
// 変数の宣言
int foo;

//複数
float hoge,fuga;

//変数の初期化
int foo = 2;
~~~
| データ型 | データ | データの範囲 |
|:---|:---|:---|
|void |型なし | - |
|int |整数 | ２バイトor4バイト |
|short |整数 |intよりサイズが小さい |
|long |整数 |intよりサイズが大きい |
|float |実数 |(単精度)浮動小数点　4or8バイト |
|double |実数 |(倍精度)浮動小数点 |
|char |文字 | 1バイト|

各型のサイズはsizeof()で調べることができる


| 変換書式 | 出力内容|
|:---|:---|
|%d |int型 10進数表記で出力 |
|%x |int型 16進数 |
|%f |float,double　小数点付き　10進数 |
|%lf |double　小数点付き　10進数 |
|%c |char　　1文字 |
|%s |文字列 |


## 演算子
・算術演算子

| 演算子 | 演算名 | 演算の内容 |
|:---|:---|:---|
| + |加算 | 足し算 |
| - |減算 | 引き算 |
| * |乗算 | 掛け算 |
| / |除算 | 割り算 商 |
| % |剰余算 | 割り算　余り |

・複合代入演算子

| 演算子 | 書き方 | 式の意味 |
|:---|:---|:---|
|`+= `|a += b | a = a + b (a + b を a に代入) |
|`-= `|a -= b | - |
|`*= `|a *= b  | - |
|`/= `|a /= b   | - |
|`%=` |a %= b   | - |

## 条件分岐
~~~
//if文、else文
if (条件1)　｛
  条件1を満たした場合の処理;
} else if (条件2)　{
  条件1を満たさず、条件2を満たした場合の処理;
} else　{
　　　　すべての条件を満たさなかった場合の処理;
} 

//switch文
switch (式){
  case 式1:
     処理1;
    break;
  case 式1:
     処理1;
    break;
    :
    :
    :
  default:
  すべて一致しなかった場合
}
~~~
~~~
//if文、else文
if(x<0){
  printf("lower than 0.");
}else if(x<5){
  printf("between 0 and 5");
}else{
  printf("bigger than 5");
}

//switch文
switch(c){
  case '+':
    printf("a+b=%d", a+b);
    break;

  case '-':
    printf("a-b=%d", a-b);
    break;

  default:
    printf("other");
    break;
}
~~~
・関係演算子

| 演算子 | 書き方 | 式の意味 |
|:---|:---|:---|
|`== `|a == b | aとbが等しい |
|`!= `|a != b | aとbが等しくない |
|`> `|a > b | aがbより大きい |
|`< `|a < b | aがbより小さい |
|`>= `|a >= b | aがb以上 |
|`<= `|a <= b | aがb以下 |

・論理演算子

| 演算子 | 演算名 | 使い方 |式の意味 |
|:---|:---|:---|:---|
|`&&` |論理積　AND |`a && b` | aかつb |
|&#124;&#124; |論理和　OR | a &#124;&#124; b | aまたはb |
|`! ` |否定　NOT |` !a ` | aではない |

## 繰り返し
~~~
・for文による繰り返し
for(初期値; 継続条件; 再設定式){
  繰り返したい処理;
}

・インクリメント演算子(++)
i++　は,iの処理をしてから１つ値を増やす
++iは,1つ値を増やしてからiの処理を行う

・デクリメント演算子(--)
i--　インクリメントのマイナスバージョン
--i　インクリメントのマイナスバージョン
~~~
~~~
// for
//for文
for(i=0;i<10;i++){
  total = total+i;
}

//while文
while(i<10){
  total = total+i;
  i++;
}

//do-while文
do{
  total = total+i;
  i++;
}while(i<10);

~~~
## 配列
~~~
・配列
データ型　配列名　[要素数];
int a[10];  //a[0]~[9]

・配列の初期化
データ型　配列名[要素数]　=　{初期値1，　初期値2,...}；

・2次元配列
データ型　配列名[縦の要素数][横の要素数];
int　a[2][3];   // 2x3　(2行3列)

・2次元配列の初期化
データ型 配列名　[要素数][要素数]　=　{{1行目の初期値1, ...},
                             {2行目の初期値1...}};
~~~

## 文字と文字列
~~~
・文字と文字列の初期化
char 変数名 = '文字';
char 配列名 = "文字列";
~~~
# 関数
~~~
・関数の記述方法
型 関数名(仮引数1,仮引数2,...){
　　変数の宣言　;
 処理;
 return 戻り値;
}
~~~

仮引数:　関数の定義内で値を受け取る変数
実引数:　関数を呼び出す時に渡す値
戻り値: 関数の呼び出し元に戻す値

・変数スコープ
関数内で宣言した変数は,その関数内でしか利用できない

・グローバル変数
プログラムの開始から終了までメモリ上で保持され,すべての関数で共通に利用できる変数

staticなローカル関数
関数内でstaticを付けて変数宣言を行うことで,プログラムの開始から終了までメモリ上に保持される変数

| 演算子 | 書き方 | 式の意味 |
|:---|:---|:---|
|`+`|p+1|aとbが等しい|
|`++`|p++|aとbが等しくない|
|`-`|p-1|aとbが等しい|
|`--`|p--|aとbが等しくない|
~~~
//sum関数の宣言(グローバル変数)
int sum(int a, int b);

//main関数
int main(void){
  int x = 3;
  int y = 5;
  printf("%d", sum(x,y));

  return 0;
}

//sum関数の定義
int sum(int a, int b){
  return a+b;
}
~~~

# ポインタ
・ポインタ宣言方法

ポインタ変数　変数名に*をつける
~~~
int *pnum, char *b
~~~

・ポインタとアドレス

ポインタにはアドレスが格納できる<br>

~~~
num ->変数num
&num　->変数numのアドレス
↓↓↓
pnum = &num;　　　//変数numのアドレスをポインタpnumに代入
↓↓↓
pnum ->変数numのアドレスが格納されたポインタ
*pnum ->ポインタpnumが指す先の値(=変数numの値)
~~~

・ポインタ演算(pはポインタで,アドレスが格納されているものとする)



# 構造体
~~~
struct 構造体名 { 
    メンバ1; 
    メンバ2; 
    ・・・
};


struct date{
  int year;
  int month;
  int day;
}

struct date today; // 構造体data型の変数todayの宣言　(コンパイラでは, 境界調整(アライメント)を行ってから記憶領域確保される)
today.year = 2018;
today.month = 8;
today.day = 4;

printf("%d / %d / %d", today.year, today.month, today.day);
~~~

・構造体の宣言方法

~~~
// 基本的な宣言方法
struct TEST {
    char subject[10];
    int score;
    char result;
};
struct TEST kamoku[3];

// 構造体の宣言と構造体変数(配列)の宣言を同時に行う方法
struct TEST {
    char subject[10];
    int score;
    char result;
} lamoku[3];

// typedef を用いる方法
typedef struct {
    char subject[10];
    int score;
    char result;
 } TEST;
 TEST kamoku[3];
~~~
・構造体メンバを利用

構造体変数名.メンバ名
~~~
構造体配列　[　要素番号　].メンバ名
~~~

・ポインタを用いた構造体メンバの参照
~~~
構造体ポインタ名　->　メンバ名
~~~

※構造体のメンバは、実体からドット演算子(「.」)を使って呼び出します。<br>
※実体のポインタからメンバを呼び出すには、アロー演算子(「->」)を使用します。

# マクロ
define文
~~~
#define 置き換えたい文字列　置き換えた後の文字列

#define NUM 5    // NUM を ５ に置き換える
~~~

# その他

## キャスト演算子

(変換したい型)式;
~~~
double　num;
(int)num;　　// double型変数numを　int型に変換
~~~

## ビット演算
・ビット演算子とは,２進数で表現されたビット列のビットを直接操作したいときに用いる演算子です.<br>


・論理演算子

| 演算子 | 演算名 | 書き方 | 意味 | 
|:---|:---|:---|:---|
|`&` |論理値　AND |`a & b` |aとbの論理値(AND)をとる |
|&#124 |論理和 OR |a &#124 b |aとbの論理和(OR)をとる |
|`^` |排他的論理和 EOR |`a ^ b` |aとbの排他的論理和 (EOR)をとる |
|`~` |1の補数 |`~a` |すべてのビットを反転する |

・シフト演算子

| 演算子 | 演算名 | 書き方 | 意味 | 
|:---|:---|:---|:---|
|>> |右シフト |a >> 2 |aの値を右に２ビットシフトする |
|<< |左シフト |a << 2 |aの値を左に２ビットシフトする |


・複合代入演算子

| 演算子 | 演算名 | 書き方 | 意味 | 
|:---|:---|:---|:---|
|`&=` |論理値　AND |`a &= b` |a= a & b|
|&#124;= |論理和 OR |a &#124;= b |- |
|`^=` |排他的論理和 EOR |`a ^= b` | - |
|>>= |右シフト |a >>= 2 |- |
|<<= |左シフト |a <<= 2 |- |


## 条件演算子
条件演算子とは,簡単な条件判断を行いたいときに,if文の代わりとして使われます.
~~~
条件 ? 真のときの処理 : 偽のときの処理

x = (a == b ? a=b : a-b);
~~~


