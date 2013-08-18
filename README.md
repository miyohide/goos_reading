# このページについて

* このページは横浜タネマキさんで毎週土曜日の朝に開催している『実践テスト駆動開発』読書会の私的なメモです。
* 読書会のメモをちまちま書いていくつもりです。

# 進め方

* 参加者が1ページぐらいを音読する。
* コードが出てきたら写経する。

# 参加したい人は

* @miyohide や @1syo に連絡をとってみてください。

# 読書会メモ

## 2013年8月17日（土）第15回読書会
### 実施ページ

* 「第20章 テストの声を聴く」

### 話した内容

* 各章の先頭に書かれている何かの本から取ってきた一節ってなんなんだろうね。
* P241に書かれているClockとはなんだろう。
  * 時間を取り扱う情報を生成するClockクラスではないか。
  * Rubyで時間のテストを行うなら、[delorean](https://github.com/bebanjo/delorean)や[Timecop](https://github.com/travisjeffery/timecop)を使うな。
* ここで言いたいことは、時間のテストをどうするかということから更に深堀りして、時間のテストってやりにくいから、実コードをどのように分解して、やりやすいテストとやりにくいテストに分けるかということを書いているのではないか。
* P244に記されているログの分類の考え方は、ごっちゃになりやすいので気をつけたい。
* P248の「値をモックしない」について。なんとなく分かるようで、わからない。
  * 不変な値をモックするのは意味がなく、インスタンスを作ればいいこと。
  * モックを使うのは、テスト対象のものに対して、前提条件を置くときにモックを書くべきであって、それ以外はテスト自身が無意味になるのでやめたほうがよい。

## 2013年8月3日（土）第14回読書会
### 実施ページ

* 「第18章 詳細を詰める」から「第19章 エラー処理」まで

### 話した内容

* P217にある『「値型」（63ページ）で説明した発芽の一例』がよくわからない。
  * これまでString型でアイテムのIDを保持していたのをItemクラスを導入することを指している。発芽の説明は64ページを参照すればよい。
* P219に書かれているテストがよくわからない。特に、`alTleast(1).of(sniperListener).sniperStateChanged`の部分。
  * RSpecでいう`expect_to change`のものに相当するかな。
* 第19章のエラー処理は結構大変。
* エラー処理って普段はどうしてますか？
  * 業務系だと、リトライ処理はやらずに、普通に落とすかなぁ。
  * エラーログは「何が起きたか」を詳細に書くようにしている。
* P230にある『「単一責任」原則』というのがピンと来ない。
  * 変化の粒度を示している。
  * 何か変更するものがあった時に、その変更するものが最小限になるように設計を行う。それが「単一責任」原則。
* P231の『依存ピア』とは？
  * 索引を見るとP252に書かれているようなので、今後のテーマとしよう。
* 第19章を終わったということで、auctionsniperの写経は終了。お疲れ様でした。
* ソースは[ここ](https://github.com/miyohide/GOOSjpSampleCode:'ここ')においてあります。各章ごとにタグつけしてて、コミットコメントにもページ数を記すようにしているので、参考になると幸いです。

## 2013年6月8日（土）第13回読書会
### 実施ページ

* 「第16章 複数の商品をスナイプする」の「ユーザーインターフェイスから商品を追加する」（P190）から「第17章 Mainクラスを分解する」まで

### 話した内容

* P194に書かれている「Announcer」はjMockのサンプルプログラムとして用意されているクラスのこと。このクラスが何をするのか、読み切れていない。
* P199で書かれているMainクラスの複雑度をみるのにimportの数を見るのは面白いと感じた。言われてみると確かに。
* P208で『notToBeGCdを取り除くことができる』とあるが、本当に取り除いて良いのか不安。前のバージョンで取り除いた場合、どうなっていたのだろう。
* 本文中で出てきたインテグレーションテストとは、RSpecでは何に該当する？
  * ここでのインテグレーションは外部接続テストを意味していると思う。
  * RSpecはすべてユニットテストとなるので、該当するものはないのかも。

## 2013年5月25日（土）第12回読書会
### 実施ページ

* 「第16章 複数の商品をスナイプする」の「ユーザーインターフェイスから商品を追加する」（P190）の直前まで

### 話した内容

* P183に書かれている「偽陽性（false positive）」とはなんだろう。
* P184で失敗メッセージの変更がされているが、RSpecだとnamed_letを使うと良い
  * named_letはこれのことかな？ ( http://yuroyoro.hatenablog.com/entry/20120225/1330139547 )
* P190の囲み記事で「インデックス」とあるが、これはなんだろうか。
  * データベースのインデックス（検索を早くする代物）ではないだろう。
  * データを一意に表現するものとして定義するものではないだろうか。

## 2013年5月18日（土）第11回読書会
### 実施ページ

* 「第15章 実際のユーザーインターフェイスに向けて」

### 話した内容

* 「プログラマの過敏症」は何を言っているのだろうか。
  * 自分の時間とコードの綺麗さはトレードオフという話？
* P165に「switchを使うことには抵抗がある」と書かれているが、その気持ちがわからない。
  * オブジェクト指向だとポリモーフィズムの考え方があるので、そこからくる考えなのでは？
  * ここで書かれているのは、カラムの項目に対してどのような値を設定するかの処理なので、ポリモーフィズムとは一致しないように思える。
* P166で『「status」と「state」があまりに似通っているので簡単には区別できない』と書かれていて、簡単に名前を変更している。JavaでIDEを使っていると簡単に変更できるが、Rubyだと難しいよね。最初っから名前をかなり真剣に考えないといけない。
* P173に書かれている手法でswitch文が排除されたのはすごい。

## 2013年5月4日（土）第10回読書会

### 実施ページ

* 「第14章 スナイパーがオークションで落札する」

### 話した内容

* この章での目標は「商品ひとつで、参加し、入札し、落札する」こと。
* P145のPriceSourceについて。Javaのenumを使っているのだが、これが「値型」（P63）の例ということ。
  * 議論ではMagickNumberの代わりという話が出たが、P63の解説を読むとより深い意味を持っているように思う。
* P146にて、「新しいテストが失敗する」の部分で「org.hamcrest.Matcher.describeMismatch」というメッセージが出たら、jarファイルの読み込み順序を変えると幸せになれるかも。詳細はここ（ http://stackoverflow.com/questions/7869711/getting-nosuchmethoderror-org-hamcrest-matcher-describemismatch-when-running ）を。
* P148のテスト失敗の状態にもっていけない。とりあえずどんどん先に進む。
* P149のテストについて。まずはテストが通っている部分においてstateの確認を行う。
* jMockのstateやallowing/when/thenの記述がなんとも気持ち悪い。
  * 気持ち悪いと感じるのは、Javaとしてはセミコロンで文が切れているのに、言葉としては続いているというアンバランスを感じるからと推定。
* P151の「jMOckがサポートすべき抽象が何であるかを突き止め、・・・」の記述はよくわからない部分。
  * ソースコードを書かされているという状態だからかなぁ。
* 結局、最後までsniperWinningの実装が出て来なかった。当然、テストも落ちる。
  * 一番最後で実装することによってすべてのテストが通るようになった。OK！
* 第15章はかなり難しそう。事前に予習が必要かと。

## 2013年4月27日（土）第9回読書会

### 実施ページ

* 「第13章 スナイパーが入札する」

### 話した内容

* 図13-1と図13-2って同じじゃないかな。何が違うんだろう。 →　正誤表がありました。（ http://www.shoeisha.co.jp/book/errata/14720/list ）
* P133に「コンパイルされずにいることを避けるため、AuctionSniperクラスにAuctionのnull実装を渡す」とあるが、この前以前にもnullを渡していればコンパイルは通る。テストも通る。
  * nullを渡せるということは、著者の発見のように書かれている（P134）。実際に内部実装まで深くみるためには実装を確認するしかないよね。
  * null実装というのは今回新しく知ったテクニックだけど、interfaceを空実装するのはいいテクニックだと思った。
  * P136に記載されている「その準備はまだ出来ていない。これも覚えておこう」について。TODOリストに加えないのかな。
  * 実装が紙面で追えないのは辛いなあ。

## 2013年4月20日（土）第8回読書会

### 実施ページ

* 「第12章 入札を準備する」

### 話した内容

* P115で書かれている「意外な失敗」について。これって実際に本番環境で試さないとわからないことでは？
  * 後々考えてみると、第11章の「最初のテストを通す」でOpenfireの設定にある「resource policy」を「Never kick」にすることがポイントかなと思う。
  * テストはまず、外部接続部分から埋めていくこと。
* P119のNoteに書かれている「nullオブジェクト」とはなんのことだろう。
* この時点ではまだEndToEndテストは通らない。そのことはあまり心配せずに突き進もう。

## 2013年4月13日（土）第7回読書会

### 実施ページ

* 「第11章 最初のテストを通す」

### 話した内容

* ここから実際の実装に入る。
  * 実際にコードを書いてみると、本に書いていない記述がたくさんある。
  * 本を読みながら実装を追えないのは辛いな。
  * あとできちんと実装をしよう。
    * 書いてみた。（ https://github.com/miyohide/GOOSjpSampleCode ）

## 2013年3月23日（土）第6回読書会

### 実施ページ

* 「第9章 オークションスナイパーを作動させる」「第10章 動くスケルトン」

### 話した内容

* 基本的な用語の合意は必要。
* DDDの世界では用語集がクラスになるように設計を進めていく。
* 環境設定で悪戦苦闘。以下にそのログを記します。
  * windowlickerのビルド
    * [windowlickerのサイト](https://code.google.com/p/windowlicker/ "windowlickerのサイト")ではjarファイルを配布しておらず、自分でビルドする必要がある。
    * `svn export http://windowlicker.googlecode.com/svn/trunk`でソースを取得
    * Java_HOMEを設定（`export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.7.0_17.jdk/Contents/Home`）
    * `./build.sh`を実行
    * BUILD FAILEDとでるが、jarファイルがbuild/jars以下にできているので、`windowlicker-swing-DEV.jar`と`windowlicker-core-DEV.jar`をクラスパスに通す
  * Openfireのインストール
    * [Openfireのサイト](http://www.igniterealtime.org/index.jsp "Openfireのサイト")からOpenfireをダウンロードする。
    * Macの場合、インストーラを実行すると「システム環境設定」に「Openfire」のアイコンができているのでそれをクリック。
    * 「Open Admin Console」ボタンをクリックし、Webブラウザで設定を行う
    * 設定内容は、93ページのコラムに記載の内容に従う
* ソースコードは[githubのリポジトリ](https://github.com/sf105/goos-code "githubのリポジトリ")を適宜参考にして進めていく。

## 2013年3月9日（土）第5回読書会

### 実施ページ

* 「第6章 オブジェクト指向スタイル」「第7章 オブジェクト指向設計を実現する」「第8章 サードパーティーコードの上に構築する」

### 話した内容

* 書いていること難しい・・・
* あとで復習、きっとする。

## 2013年3月2日（土）第四回読書会

### 実施ページ

* 「第4章 テスト駆動のサイクルに火を入れる」「第5章 テスト駆動開発のサイクルを保つ」

### 話した内容

* デプロイを手でやる人ってすごく多い。
* 自動化できると分かっていても、なかなかその構築に手を付けないこともある。
* 最初の「動くスケルトン」はscaffoldでいいのではと思う。
* Railsだとscaffoldでいいと思う。リクエストに対するcontroller/actionとモデル、マイグレーションがひと通り揃う。
* 作業の自動化などをしてもなかなか評価されないよね。
* インクリメンタルな開発の最初は大変。
* 受け入れテスト用のテストとはどこまで書くべきか。リクエストに対して画面遷移が行われることを確認すればOKか。それとも、次の画面のDOMまで解析すべきか。おそらく後者。
* テストの書き始めについて。シンプルな正常系から書き始める。
* コンパイルすらできないテストコードを書くのはものすごく不安感にとらわれる。
* 「振る舞いのユニットテストを行え、メソッドをテストするのではない」は言わんとしていることは分かるけど、じゃぁどうすればよいのかが分からない。あとで説明があるのかな。

## 2013年2月16日（土）第三回読書会

### 実施ページ

* 「第2章 オブジェクトをテスト駆動開発する」と「第3章 ツールの紹介」を実施。

### 話した内容

* 「オブジェクトの網の目」から「"値"と"オブジェクト"」で書かれていることは、オブジェクト指向の深い考え方と思う。少なくとも、オブジェクト指向の説明である「動物クラス、犬クラス、猫クラス」といった説明からは更に一歩進めた説明。
* 「列車事故」コードについて。オブジェクトを取得するようなメソッドの呼び出しがある場合は、リファクタリングの対象。ラッパークラスを作り、値（プリミティブ型）を返すようにする。
* テスト対象オブジェクトの隣接オブジェクトを、テスト中に代用品と置き換える。この代用品がモックオブジェクト。
* 22ページから23ページに書かれている「モッカリー」の話がよくわからない。あとのコードでわかってくるか？
* 第3章はさらっと流す感じで。
* 30ページから書かれているjMockの説明について。コードが読み慣れないせいか、読みにくいと感じる。
* モッカリーの使い方の例について。モックをmockメソッドで登録して、checkingメソッドで呼び出し方法を記述するという認識で良いのかな。
* Javaを使ったコードを書くのはもう少し先。準備もうちょっと後で。

## 2013年2月9日（土）第二回読書会

* 「フィードバックは欠かせないツール」とあるが、思いつきで意見を言ってくる人っているよね。その人にどのように対応するのか。
* TDDのプロセスを始めるに当たって、ユニットテストを書きたくなるという気持ちを抑え、受け入れテストを書くことから始める。
* 受け入れテストは失敗していてもOK、ユニットテストのものは失敗したものをリポジトリに上げない。
* 一番最初に受け入れテストを書くことは物凄く難しい。
* 本書のインテグレーションテストはRailsでのインテグレーションテストとは意味合いが異なる。
* Rails（というかRuby）では、自分たちが変更できないコードというのは余り無いので、ほとんどユニットテストと受け入れテストに集約されるのではないか。


## 2013年2月2日（土）第一回読書会

### 実施ページ

* 「まえがき」から「目次」まで

### 話した内容

* 『テスト駆動開発入門』を読んだことがないと言ったら、『実践テスト駆動開発』よりも分かりやすいということなので、読むべきと言われる。
* 個人的に「モック」って単語は情報処理で使われる定義と、RSpecなどでの定義とは違いがあるように思う。
* それは情報処理で使われている定義が間違っているのでは？
* それとも実際に使われるようになってきて、意味が変わってきているかも。
* まだ本文に到達していない。来週から。


