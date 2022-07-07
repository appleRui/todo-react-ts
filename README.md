# Todo-react-ts
[ステートフックの利用法](https://ja.reactjs.org/docs/hooks-state.html)

```
1:  import React, { useState } from 'react';
2:
3:  function Example() {
4:    const [count, setCount] = useState(0);
5:
6:    return (
7:      <div>
8:        <p>You clicked {count} times</p>
9:        <button onClick={() => setCount(count + 1)}>
10:         Click me
11:        </button>
12:      </div>
13:    );
14:  }
```
**1 行目：** useState フックを React からインポートします。これにより関数コンポーネント内でローカル state が使えるようにになります。

**4 行目：** Example コンポーネント内で useState フックを呼び出すことで新しい state 変数を宣言します。2 つの値のペアが返されるので、それらに名前を与えます。ボタンのクリック回数を保持するための変数ですので count と名付けましょう。useState 唯一の引数として 0 を渡すことで、変数をゼロへと初期化します。返り値の 2 つ目はそれ自体が関数です。これにより count を更新するので、setCount という名前にします。

**9 行目：** ユーザがクリックした時に、新しい値で setCount を呼びます。React は Example コンポーネントを再レンダーし、その際には新たな count の値を渡します。

[イミュータビリティ](https://ja.reactjs.org/tutorial/tutorial.html#why-immutability-is-important)

上記のコード例において、現在の配列を直接変更する代わりに、.slice() メソッドを使って square 配列のコピーを作成することをお勧めしました。ここでイミュータビリティ（immutability; 不変性）について解説し、それがなぜ重要なのかについて説明します。

一般的に、変化するデータに対しては 2 種類のアプローチがあります。1 番目のアプローチはデータの値を直接いじってデータをミューテート（mutate; 書き換え）することです。2 番目のアプローチは、望む変更を加えた新しいデータのコピーで古いデータを置き換えることです。

```
var player = {score: 1, name: 'Jeff'};
player.score = 2;
// Now player is {score: 2, name: 'Jeff'}
```

ミューテートを伴わないデータの変化
```
var player = {score: 1, name: 'Jeff'};

var newPlayer = Object.assign({}, player, {score: 2});
// Now player is unchanged, but newPlayer is {score: 2, name: 'Jeff'}

// Or if you are using object spread syntax, you can write:
// var newPlayer = {...player, score: 2};
```

最終的な結果は同じですが、直接データのミューテート（すなわち内部データの書き換え）をしないことで、以下に述べるようないくつかの利点が得られます。

[Readonly](https://typescript-jp.gitbook.io/deep-dive/type-system/readonly)
