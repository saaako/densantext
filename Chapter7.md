# 7. アドレスとポインタ
## 目次
[7.1 アドレス](#71-アドレス)  
[7.2 ポインタ](#72-ポインタ)  
[演習問題](#演習問題)  

## 7.1 アドレス
プログラミングにおけるアドレスとは変数などの場所を表すものです。C言語では変数の前に `&` をつけることによって変数のアドレスを表します。例えば変数aのアドレスを出力するには次のように書きます。

```c
#include <stdio.h>

int main()
{
    int a = 10;
    
    printf("%p\n", &a);

    return 0;
}
```

実行すると数字とアルファベットの文字列が表示されますが、これがアドレスです。今までscanf関数を使用するときにも変数の前に&を書いていたと思いますが、scanf関数では「入力された値を変数のアドレスに代入する」ということを行っていたのです。

配列の要素にも&を使用することで要素のアドレスを表すことができますが、配列名だけを書いた場合も先頭の要素のアドレスを表します。

```c
#include <stdio.h>

int main()
{
    int ary[3];
    
    printf("%p\n", ary);     //先頭の要素のアドレス
    printf("%p\n", &ary[0]); //先頭の要素のアドレス
    printf("%p\n", &ary[1]); //2番目の要素のアドレス
    printf("%p\n", &ary[2]); //3番目の要素のアドレス

    return 0;
}
```

## 7.2 ポインタ
ポインタとはアドレスを入れるための変数のことです。ポインタの宣言は次のように行います。

```c
型 *変数名;

型* 変数名;
```

型の後ろや変数の前に `*` (アスタリスク)をつけることで、その変数の型のポインタを宣言することができます。以下に例を示します。

```c
#include <stdio.h>

int main()
{
    int a;
    int *p; //ポインタの宣言

    p = &a; //アドレスを代入するので&をつける
    printf("%p\n", p);

    return 0;
}
```

次に、ポインタに代入されているアドレスにある変数(ポインタの指す変数)にアクセスする方法を説明します。言葉では分かりづらいので例をあげて説明します。

```c
#include <stdio.h>

int main()
{
    int a;
    int *p;

    p = &a;
    *p = 10; //ポインタ変数の前に*をつける
    printf("%d\n", a); //aに10が代入されている

    return 0;
}
```

変数を宣言するときに `*` をつけるとポインタになり、ポインタ変数に `*` をつけるとポインタの指す変数を表すことに注意してください。また、ポインタ変数に別の変数のアドレスを代入していない状態でポインタの指す変数に値を代入することはできないので注意してください。

```c
#include <stdio.h>

int main()
{
    int *p;
    *p = 10; //こういうことはできない

    printf("%d\n", *p);

    return 0;
}
```

## 演習問題
１. 2つの変数の値を入れ替える関数を作成してください。(引数にポインタを利用する。)
