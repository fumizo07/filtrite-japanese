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
| [Bromite Extended](https://github.com/mikadukiken/filtrite-japanese/releases/latest/download/bromite-extended.dat) | The default list with additional annoyance blockers I use with [uBlock Origin](https://github.com/gorhill/uBlock) on Desktop |
| [japanese](https://github.com/mikadukiken/filtrite-japanese/releases/latest/download/bromite-default+tamago.dat) | Bromiteデフォルトに、もちお氏の[たまごフィルタ](https://raw.githubusercontent.com/eEIi0A5L/adblock_filter/master/tamago_filter.txt)をマージしたもの|

これらのリストは、GitHubアクションを使用して定期的に自動的に更新されます。

**Note**: I'm not 100% sure if all list formats that are used are actually supported by [the ruleset generation tool](https://github.com/xarantolus/subresource_filter_tools) (as the output indicates some failures). If you have a comment on that, please open an issue :)

### 独自のフィルターリストを使用する
このプログラムは、新しいリストを簡単に追加できるように設計されています。

新しいリストを作成するには:

1. このリポジトリをフォークしてください。
2. lists→add file→Create new fileを選択して、txtファイルを作成します。ファイル名を入力してください(例:Myfilter.txt)
3. 使用したいフィルタのURLをコピペしてCommit new fileをタップしてください。
Enable GitHub Actions by switching to the "Actions" tab of your repo, then confirming that you want to enable them
4. Actionsに移動し、Select workflow→Build filterlists→Enable workflowを選択してしばらくお待ちください。Choose a name for the list, e.g. `example-list`
5. 黄色のクルクルが止まるまで待ちましょう。緑の✔が出たら成功です！
Search for filter lists you want to use. You can for example find them [here](https://filterlists.com/), use those in "uBlock Origin" or "AdBlock Plus" format (however, it's possible that [not all types of rules are supported](https://github.com/bromite/bromite/wiki/AdBlocking)). Go to info, then "View" and copy the URL to the list.
6. Codeに戻り右側のReleasesを選択してください。2で作成したファイル名が表示されているはずなので長押しして、リンクアドレスをコピーしてください。Create a file `lists/example-list.txt` (aka in the `lists` directory) that contains the URLs to filter lists you copied before. It should look like this:
    ```
    # Lines starting with # are comments, empty lines are also allowed
    # List one URL per line:
    https://easylist.to/easylist/easylist.txt
    https://...

    # The following line doesn't work, only put either a comment or an URL in one line, not both
    http://  # Invalid comment on URL
    ```
7. BromiteのAdBlock settingsを開きFilters URL欄に6でコピーしたアドレスをペーストして保存を選択してください。Save your file, commit and push. GitHub actions should now build the list and create a release
8. Bromite再起動すれば完了です。お疲れ様でした！をAfter GitHub Actions generated the release, you can copy the linked URL in the release to always get the latest generated version. This URL looks something like `https://github.com/USERNAME/filtrite/releases/latest/download/FILENAME.dat`. 
7. Check that the generated filter file size is less than the allowed maximum of [10 MB](https://github.com/bromite/bromite/blob/e5771ef891cf01dd5aeaaec5e092841929a9a541/build/patches/Bromite-AdBlockUpdaterService.patch#L1152-L1153). If it isn't, you must remove some lists
8. Set this URL as the filter file in Bromite settings.

### [LICENSE](LICENSE)
This is free as in freedom software. Do whatever you like with it.

ご自由にどうぞ
