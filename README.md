# 画像認識を用いた体験型外国語学習アプリ「iWiDen」の開発記録
2020年8月24日〜9月５日までの間、ヤフー主催の学生向けハッカソン「[OPEN HACKU 2020](https://hacku.yahoo.co.jp/2020/)」に参加しました。\
今回はオンラインの開催で、全３期間あるうちvol2に参加しました！初めてのハッカソンだったので、色々と戸惑ったり遠回りする事もありましたが、諦めず走りきれたので良かったです！\
自分たちの中ではかなり完成度が高かったように思えますが、他の参加者の作品を見ると全然で、受賞チームの格の違いに驚きました。正直、自分たちならと舐めてかかっていたので、「井の中の蛙大海を知らず」と言う感じで反省しました。\
初めて作ったiOSアプリなのでまだまだ未熟ではありますが、ここに記録させて頂きます。
#### 活動内容
開発期間：8月24日〜9月4日\
開発人数：２名\
開発形式：オンライン\
プロダクト名：iWiDen\
使用した技術：Xcode、Keras、CoreML、GoogleCloudTranslationAPIなど

# iWiDenとは？
- 外国語を学習するときに難しいと感じることはありませんか？
- 海外旅行で見たものをすぐに英語に翻訳して伝えたいことありませんか？

iWiDenは、機械学習の一例である画像認識を利用し、学習したい言語と知りたい画像を入力することで、翻訳された単語名と文法、類似画像まで知ることができるアプリケーションです。\
言語と画像を入力するだけでなぜ翻訳されるのか。この裏側には二つのステップがあります。\
1. ラベル付きの画像を学習させた画像認識モデルを使用することで、入力された写真が何の写真なのか、その写真内の主要のオブジェクトを予測することができます。
2. 画像認識によって出力された単語名（英語）をGoogleのCloudTranslationAPIを用いることで日本語や英語を含めた計８言語に翻訳して出力することができます。

# 現段階での改善点
1. 単純に予測が悪い。
これはAppleDeveloperに標準装備されているCoreMLを使用したからであり、CoreMLはImageNetと言う有名な画像データセットを使用して学習させているがその学習画像やラベルが実用性のないものまで含まれていたからである。
2. 単語の汎用性が低い。
しっかり予測できる単語数が少ない。これは１と同じ理由に帰着する。
3. 使用できるケースを再考する。
メンターさんから単純に海外旅行での画像翻訳として利用した方が売れそうと言われたし、発表会でも結局翻訳機だよね？と言われたのでショックだったが、そう言う方向へシフトチェンジしてもいいかもしれない。その場合は学習用途で必要な機能と別物になるのできちんと考えるべき。

