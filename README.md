# AI_StackChan2 (LEDエフェクト版)

## 2024年8月16日:
画面中央のサーボ ON/OFF機能、中央左側の独り言モード、中央右側のバッテリー残量おしらせボタンの大きさと配置を修正しました。<br>

| 変更前のレイアウト              | 変更後のレイアウト              |
| ----------------------------- | ----------------------------- |
| ![h:800](images/AI_Stackchan2-00.png) | ![h:800](images/AI_Stackchan2-01.png) |


### 使い方 ###
* このソースを用いてVSCode＋PlatformIO環境でビルドすると、M5Stack Core2 for AWS、またはM5Stack Core2にM5GoBottom2を追加し、LEDエフェクトを直ぐに確認することができます。<br>
  (変更は下記並びに[main.cpp](https://github.com/ToshihiroMakuuchi/AI_StackChan2/blob/ToshihiroMakuuchi/LED_Effects/M5Unified_AI_StackChan/src/main.cpp)ソース内コメントをご確認ください)
* Core2 for AWSやM5GoBottom2のLEDバーの使用するデータピンは【25】が用いられ、またLED球は10個搭載されています。<br>
* 今回、外部L接続LEDとしてわししさんのわししショップ【Nekomimi LED】も用いました。<br>
* ソースコードでは#defineにてLEDの有効/無効を設けていますので、必要な方は調整してビルドをお願いします。<br>
* レベルメーター表示OFFの時、画面下部にタッチするとバルーンで曲名を表示します。<br>
* 画面左端の中央付近にタッチすると【独り言モード】に切り替えられます。<br>
* 画面中央にタッチすると首振りを止めます。<br>
* 画面右端の中央付近にタッチするとバッテリーの残量をおしらせします。<br><br>


## LEDエフェクト名称および有効パラメータ (11種)
| Name | Range | AoE | Delay | Color | Looping | Direction | Description |
| ----: | :-----: | :-----: |  :---: | :-----: | :-------: | :---------: | :--- |
| [RAINBOWWAVE](https://youtube.com/shorts/pfN8k_zY_gs?feature=share) | Y | N | Y | N | N | Y | 動的レインボーグラデーションエフェクト |
| [COMET](https://youtube.com/shorts/wfuuhPH90M0?feature=share) | Y | Y | Y | Y | Y | Y | LED光が尾をを引き設定範囲内を移動する流れ星エフェクト |
| [LARSON](https://youtube.com/shorts/xl6u4YCUk-E?feature=share) | Y | Y | Y | Y | Y | Y | LED光が設定範囲内を往復するエフェクト(ナイトライダー風) |
| [CHASE](https://youtube.com/shorts/lTgBS9gDuDU?feature=share) | Y | ? | Y | Y | N | Y | LEDを1つおきに交互に点滅させるエフェクト(工事現場風) |
| [STATIC](https://youtube.com/shorts/SkdqZ1L5pXA?feature=share) | Y | N | Y | Y | N | N | 同色がチラチラと点滅するキラキラ系エフェクト |
| [STOROBE](https://youtube.com/shorts/o3IekoJ9uqQ?feature=share) | Y | N | Y | Y | N | N | 設定範囲内でのストロボエフェクト(定期的に全LEDピカピカ) |
| [SINEWAVE](https://youtube.com/shorts/jg9CFqpYKt8?feature=share) | Y | N | Y | Y | N | Y | 設定範囲内のLED数だけ消灯しながら流れるエフェクト(COMETの逆イメージ) |
| [RANDOM](https://youtube.com/shorts/UXPfDr1h17c?feature=share) | Y | N | Y | N | N | N | LED全部がランダムに点灯するパレード(パリピ)エフェクト |
| [FADEINOUT](https://youtube.com/shorts/7j3RzVZ8V8k?feature=share) | N | N | N | Y | N | Y | LEDがフェードインアウトするエフェクト (色固定) |
| [NANAIRO](https://youtube.com/shorts/aiBonRR6LJo?feature=share) | N | N | N | N | N | Y | LEDがフェードインアウトするエフェクト(七色順番に点灯) |
| [MERAMERA](https://youtube.com/shorts/TvK8jyE4r2A?feature=share) | N | N | N | N | N | N | メラメラと燃えるようなエフェクト |
| NONE | N | N | N | N | N | N | エフェクトの停止 |


---


AIｽﾀｯｸﾁｬﾝ2です。
<br><br>

![画像1](images/image1.png)<br><br>

AIｽﾀｯｸﾁｬﾝ2の特徴<br>

* 音声合成にWeb版 VOICEVOXを使います。
* 音声認識に"Google Cloud STT"か"OpenAI Whisper"のどちらかを選択できます。
<br>

Google Cloud STTは、”MhageGH”さんの [esp32_CloudSpeech](https://github.com/MhageGH/esp32_CloudSpeech/ "Title") を参考にさせて頂きました。ありがとうございました。<br>
"OpenAI Whisper"が使えるようにするにあたって、多大なご助言を頂いた”イナバ”さん、”kobatan”さんに感謝致します。<br>
ウェイクワードには、”MechaUma”さんの[SimpleVox](https://github.com/MechaUma/SimpleVox/ "Title")ライブラリを使わせていただきました。

---


### M5GoBottom版ｽﾀｯｸﾁｬﾝ本体を作るのに必要な物、及び作り方 ###
こちらを参照してください。<br>
* [ｽﾀｯｸﾁｬﾝ M5GoBottom版組み立てキット](https://raspberrypi.mongonta.com/about-products-stackchan-m5gobottom-version/ "Title")<br>

### プログラムをビルドするのに必要な物 ###
* [M5Stack Core2](http://www.m5stack.com/ "Title")<br>
* VSCode<br>
* PlatformIO<br>

使用しているライブラリ等は"platformio.ini"を参照してください。<br>

~~【5/31の時点ではM5Unifiedの不具合の為、CoreS3では動きません。】~~<br>

---

### サーボモーターを使用するGPIO番号の設定 ###
* main.cppの46行目付近、サーボモーターを使用するGPIO番号を設定してください。


### 使い方 ###

こちらを参照してください。<br>

* [AI_StackChan2_README](https://github.com/robo8080/AI_StackChan2_README/ "Title")<br>
<br>
<br>
<br>
