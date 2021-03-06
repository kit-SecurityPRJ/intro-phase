# ネットワーク

[スライド資料](../pdf/intro_network.pdf )

## 概要
ネットワークについての説明

- プロトコルとは
- ネットワークアーキテクチャ(OSI参照モデル／TCP/IP)
- ネットワーク機器
- IPアドレスとMACアドレス

## Q&A
- インターネットは，ネットワークっていうグループの塊ってことですかね？
	- インターネットもネットワーク
	- ネットワークがたくさん集まったくそでかネットワークがインターネット
- プロトコルってどれくらい存在するんですか？
	- いっぱい
	- 自作もできるし企業独自のもある(Wellknownなのは1024,それ以外も含めると無限)
- プロトコルをオリジナルにしたら外部漏洩を防げるって感じですか？
	- オリジナルにしても解析される可能性はあって，漏洩するかどうかとは関係ない
	- インターネットを介す以上そのリスクはある
	- 解析を防ぐには暗号化とか暗号化されたプロトコルを用いる
- 電話もプロトコルみたいにいろんな仕様が決まってるから違うメーカーの携帯電話やスマホで電話できるってことですかね？
  	- はい
  	- いわゆる標準化
- AppleデバイスのAirDropも独自のプロトコルってことですか？
  	- Appleのオリジナルか，既存のものの組み合わせか
- プロトコル自作ってどんな感じなんですか？
	- アプリケーション層のプロトコルは，ネットワークを使うプログラムを書いたらそれがそのままアプリケーション層のプロトコルになる（厳密にはならないかもだけど，同義）
  	- ネットワーク層のプロトコルをやりたい場合は，ルータ(そのプロトコルを読む側)も作らないといけない
  	- 物理層は，新しいケーブルを作ればOK
- メール送信の例 のところって，「送信」を押した後に行われてるんですか？
  	- はい．送信後に各プロトコルのヘッダが付加されてパケットとなります
  	- クライアントによっては事前になにかしておくとか細かい違いはある
- ゲームとかはコネクションレス型通信ですか
  	- ゲームによる
  	- コネクション型通信でも十分早いので，おそらくこっち
- MACアドレスって，AppleのあのMacと関係ありますか
  	- ない
  	- MAC = Media Access Control
- パケットが見えるってことは，他の人が何をしてるかわかっちゃうんですか？
  	- 全体に届くパケットであれば見える
- 暗号化とかされてないんですか
  	- プロトコルや回線による
- 大学で，MACアドレスを申請しないと使えないのはブリッジを使っているからですか？
  	- ではない
  	- 安全性のため
  	- 許可したMACアドレスだけパケットを通す という仕組みを使っている(おそらく)
	- ブリッジ（L2スイッチ）はポートとMACアドレスとの対応表を自動で作成する
- バッファとはなんですか？社名的なやつですか
  	- 一時的に覚えておく場所やメモリのこと
- 暗号化されたデータは、時間をかければ解読できたりするんですか？
  	- 不可能ではないが，実質不可能
	- 今のコンピュータの性能では一生終わらない（これが担保になっている）
- ルータBは，ルータAがLAN1を持ってそう(知ってそう？) ってどうやって知るんですか
  	- 静的ルーティングと動的ルーティングがある
  	- デフォルトゲートウェイをあらかじめ決めておいて，知らなかったらそいつに託す
- ルータは誰が管理しているものですか？
  	- その家の人とか，企業の人
  	- インターネットであれば，
- 僕の家は無線LANルータの前にモデム？みたいな機械があるのですが、これは何層の機械になるんですか？
  	- モデム,ONU=変換器
  	- 層でいうと，物理層かデータリンク層
  	- 電話回線，光回線(アナログ信号)をルータが解釈できる形式(デジタル信号)に変換する
  	- 一体型も存在する
- 1番近い転送先を間違えることはあるんですか？
  	- ルーティングプロトコルが間違えることはない
  	- 静的ルーティングで，人が間違えることはある
- ルータに，信号増幅とかリピータの機能が入ってたりするんですか？
  	- 入ってる
  	- 用途によって使い分ける
- IPアドレスやMACアドレスは，一生同じものを使うことになるんですか
  	- IPアドレスは変わる
  	- MACアドレスは端末で固有(やろうと思えば書き換えられる)
  	- IPv4, IPv6などによって変わってくるが
- 郵便みたいなシステムって感じですか？
  	- 一番近い事業所に持ってくる みたいな仕組みという話であればそう
- ２つのアドレスってどこで確認できますか？
  	- Windows → ipconfig
  	- Mac → ifconfig
  	- Linux(Ubuntu) → ip a
