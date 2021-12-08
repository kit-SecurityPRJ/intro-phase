# Webハンズオン

[スライド資料](../pdf/intro_web2_2.pdf)


## 概要
- DiceAPIを叩いてみよう
- ところでAPIとは
- WebAPIを作ろう

## ハンズオン内容
## DiceAPIを叩いてみよう
- 大畑さんが以前作ったDiceAPIを叩いてみる．
- パラメータを自由に変えて遊んでみる．

## ところでAPIとは
- APIとはとは何かを説明．
- 特にWebAPIとは何かを説明．
- HTTPメソッドも説明．

## WebAPIを作ろう
- cloneしてきてapp.pyを写経で書き直す
- clone先（https://github.com/silmin/dice-api）


- 使用したDiceAPIのプログラム
```python
import random
from flask import *

app = Flask(__name__)

@app.route("/")
def hello():
    return render_template("hello.html", title="Dice API");

@app.route("/roll", methods=['GET', 'POST'])
def roll():
    if request.method == 'GET':
        method = 'GET'
        faces = request.args.get('faces')
        cnt = request.args.get('cnt')
        times = request.args.get('times')

    elif request.method == 'POST':
        method = 'POST'
        faces = request.json['faces']
        cnt = request.json['cnt']
        times = request.json['times']

    faces = int(faces)
    cnt = int(cnt)
    times = int(times)

    result = []
    for t in range(times):

        r = []
        for c in range(cnt):
            top = random.randint(1, faces)
            r.append(top)

        result.append(r)

    data = [
        {"method": method},
        {"faces": faces},
        {"cnt": cnt},
        {"times": times},
        {"result": result}
    ]

    return jsonify({
        "status": "OK",
        "data": data
        })

if __name__ == "__main__":
    app.run()
```

