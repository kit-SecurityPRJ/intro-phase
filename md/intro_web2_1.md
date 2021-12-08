# Webハンズオン

[スライド資料](../pdf/intro_web2_1.pdf)


## 概要
- WebサイトとWebページってどう違うの
- ローカルWebサーバーを構築する

## ハンズオン内容
## WebサイトとWebページってどう違うの
- 自分自身Webサイト，Webページの違いを1年生の頃考えていなかったので軽く説明．
- URLの構造を改めて説明しながら，Webサイトがどのように構成されているかを説明．

## ローカルWebサーバーを構築する
- Flaskでローカルサーバを建てて，HTMLファイルをパス指定で表示させるまでを行う．
- コードは配布せず写経した．
- IPを指定して．ペアの人のHTMLファイルを表示させる

- 使用したプログラム
```python
from flask import Flask, render_template

app = Flask(__name__)

@app.route("/", methods=["GET"])
def hello_world():
    return "<h1>Hello World!!</h1>"

@app.route("/index", methods=["GET"])
def index():
    return render_template("index.html")

if __name__ == "__main__":
  app.run()
```

