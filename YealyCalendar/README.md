# Yealy Calendar

1年のカレンダーを表示する。  

オフィスのカレンダーが1年をとおして確認できる形で公開されていない。  
印刷して冷蔵庫に貼っておきたいため、  
1年間の予定を印刷可能な形で閲覧できる状態にしたい。  

## 要件

- 4月〜翌年3月までを1ページに表示する
- 営業日 or 非営業日 を表示する
- 非営業日について
  - 土日は常に非営業日
  - 日本の祝日は常に非営業日
  - 土日祝日以外でオフィスが非営業日の場合は土日祝日と異なることが見てわかる  

## 前提条件

- オフィスにこのコードを簡単に持ち込めるよう、ローカルに何もインストールしない。  
- 簡単に使うためにファイルを分散させたくなく、全コードを1ファイルに纏める。  

## 利用ライブラリ

- [jQuery](https://jquery.com/)
- [Bootstrap](https://getbootstrap.jp/)

## コード利用方法

### 基本的な使い方

```
 5:    const FISCAL_START_DATE='2020/04/01'; // 表示したい年度の最初の日
 6:    const START_WEEKDAY = 0; // 週初めとする曜日。0:日曜日 〜 6:土曜日
 7:    const OFF_WEEKDAYS = [0, 6]; // 常に非営業日とする曜日
 8:    const OFFICE_DAYS_OFF = [ // オフィスの非営業日（フォーマット：YYYY/MM/DD）
 9:      '2020/12/07'
10:    ];
```

### 色の変更

- 以下を修正する。
```
15:    .office-day-off { /* 非営業日 */
16:      background-color: #fdd;
17:    }
18:    .day-off { /* 休日／祝日 */
19:      background-color: #eee;
20:    }
```

- 休日／祝日と非営業日が重なった場合に非営業日の色を優先したい場合は、  
  上記のCSSの記述順を逆転させる。  

## コード捕捉

- 日本の祝日は[Holidays JP API](https://holidays-jp.github.io/) を使用して取得する。  

## 課題

- [Bootstrap](https://getbootstrap.jp/) で作成したテーブルを印刷しようとすると、  
  背景色が無視される orz  
  - 回避方法  
    フル画面キャプチャをとり、これを印刷する（未確認）。  

## その他

- 最初は [Vuetify](https://vuetifyjs.com/) を利用しようと思ったが、  
  スタイルの変更が難しかったため断念    
 （そもそも静的HTML向きでは無い）。  

- Google Calendar が使えるのでは？と[G-calize](https://chrome.google.com/webstore/detail/g-calize/piiljfhidimfponnkjlkecnpjhdijfde)を試して見たが、  
  年で表示した場合に土日に色がつかないなど、  
  微妙に手が届かない。  
