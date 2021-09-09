## filtrite(Bromite用広告ブロックフィルタ生成ツール)
xarantolus氏が作成した[filtrite](https://github.com/xarantolus/filtrite)に日本語の説明文を追加したものです。※現在工事中

一部README.mdに改変があります。必ずフォーク元の[filtrite](https://github.com/xarantolus/filtrite)もご確認ください。

filtriteは、[Bromite](https://www.bromite.org/).のフィルターリストを生成するためのプロジェクトです。

詳細についてはこちらをご覧ください。[Custom Ad Block Filters](https://www.bromite.org/custom-filters) 

# Lists(リスト)
以下から任意のリストを選択し、リンクをコピーしてBromiteに追加できます。 設定に移動して、AdBlock settingsを選択。次に、フィルターURLをコピーしたものに設定します。

リストは次のとおりです。


| リンク | 説明 |
| ------ | ------|
| [Bromite Default](https://github.com/mikadukiken/filtrite-japanese/releases/latest/download/bromite-default.dat) | Bromiteの[デフォルトリスト](https://github.com/bromite/filters)と同じ内容(このツールで生成したもの) |
| [Bromite Extended](https://github.com/mikadukiken/filtrite-japanese/releases/latest/download/bromite-extended.dat) | デスクトップの[uBlockOrigin](https://github.com/gorhill/uBlock)で使用する追加の迷惑ブロッカーを含むデフォルトのリスト |
| [japanese](https://github.com/mikadukiken/filtrite-japanese/releases/latest/download/bromite-default+tamago.dat) | Bromiteデフォルトに、もちお氏の[たまごフィルタ](https://raw.githubusercontent.com/eEIi0A5L/adblock_filter/master/tamago_filter.txt)をマージしたもの|

これらのリストは、GitHubアクションを使用して定期的に自動的に更新されます。

**注意**: 全ての広告ブロックフィルタに対応してる訳ではありません。フィルタ生成に失敗する時もあります。
CSSルールが使えないらしいです。


## 独自のフィルターリストを使用する
このプログラムは、新しいリストを簡単に追加できるように設計されています。

新しいリストを作成するには:

1. このリポジトリをフォークしてください。
2. lists→add file→Create new fileを選択して、txtファイルを作成します。ファイル名を入力してください(例:Myfilter.txt)
3. 使用したいフィルタのURLをコピペしてCommit new fileをタップしてください。1行につき1つのURLを指定します。
```
    # Lines starting with # are comments, empty lines are also allowed
    # List one URL per line:
    https://easylist.to/easylist/easylist.txt
    https://...

    # The following line doesn't work, only put either a comment or an URL in one line, not both
    http://  # Invalid comment on URL
 ```
4. Actionsに移動し、Select workflow→Build filterlists→Enable workflowを選択してしばらくお待ちください。
5. 黄色のクルクルが止まるまで待ちましょう。緑の✔が出たら成功です！
6. Codeに戻り右側のReleasesを選択してください。2で作成したファイル名が表示されているはずなので長押しして、リンクアドレスをコピーしてください。この様なファイルがあれば成功です。 `https://github.com/USERNAME/filtrite/releases/latest/download/FILENAME.dat`. 
7. BromiteのAdBlock settingsを開きFilters URL欄に6でコピーしたアドレスをペーストして保存を選択してください。
8. Bromiteを再起動すれば完了です。お疲れ様でした！

注意. 使用出来るフィルタのサイズは最大[10MB](https://github.com/bromite/bromite/blob/e5771ef891cf01dd5aeaaec5e092841929a9a541/build/patches/Bromite-AdBlockUpdaterService.patch#L1152-L1153)です。それ以上の場合はリストを削除する必要があります。
### [LICENSE](LICENSE)
This is free as in freedom software. Do whatever you like with it.

ご自由にどうぞ
