# vacationPlanner
This is a tutorial for learning how to use basic animations
# 第17回: １時間でiPhoneアプリを作ろう
## 割り勘アプリ

  <div style="text-align:center"><img src ="https://github.com/iosClassForBeginner/sampleWarikanApp/blob/master/Assets/sample.png" /></div>
  
  当アカウントへ訪れていただき、誠にありがとうございます。第17回アプリ教室では、割り勘アプリを作ります。自分のペースで勉強したい、勉強前に予習したい、内容を復習したい場合、ご利用ください。
  
## アプリ教室に興味ある方、歓迎します。  
  Meetup  
  http://www.meetup.com/ios-dev-in-namba/
  
## 別途アプリ教室(有料)も開いております  
  http://learning-ios-dev.esy.es/  

## 問い合わせ
  株式会社ジーライブ
  http://geelive-inc.com  

## アプリ作成手順

#### 0, 開発準備
> 0-1. xcodeで新規プロジェクトを立ち上げる
<img src="https://raw.githubusercontent.com/iosClassForBeginner/XcodeHowToImage/master/Assets/create_new_project.gif" width="320px">

#### 1, Storyboardで、アプリのデザイン
> 1-1. main.storyboardを選択し、UI部品から下記を配置します。(ドラッグ&ドロップ)
- TextView 人数入力
- TextView 金額入力
- UILabel 結果出力
- UIButton 計算実行
![image](https://raw.githubusercontent.com/iosClassForBeginner/XcodeHowToImage/master/Assets/set_uilabel.gif)
![image](https://raw.githubusercontent.com/iosClassForBeginner/XcodeHowToImage/master/Assets/set_button.gif)

> 1-2. Storyboardの下記UI部品を、ViewController.swiftに紐づけます（control押しながらドラッグ）
- TextView 人数入力
- TextView 金額入力
- UILabel 結果出力
- UIButton 計算実行 (actionで紐付ける)
![image](https://raw.githubusercontent.com/iosClassForBeginner/XcodeHowToImage/master/Assets/tying_button_action.gif)
![image](https://raw.githubusercontent.com/iosClassForBeginner/XcodeHowToImage/master/Assets/tying_textfield.gif)
![image](https://raw.githubusercontent.com/iosClassForBeginner/XcodeHowToImage/master/Assets/tying_uilabel.gif)

#### 2, ViewController.swiftにコード記述
- 以下コードブロックを記入
  
```Swift
import UIKit

class ViewController: UIViewController {

    @IBOutlet weak var ninzu: UITextField!
    @IBOutlet weak var kingaku: UITextField!
    @IBOutlet weak var kekka: UILabel!

    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view, typically from a nib.
        
        // 数字のみ入力できるように設定
        ninzu.keyboardType = .numberPad
        kingaku.keyboardType = .numberPad
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }


    @IBAction func keisan(_ sender: Any) {
        // 入力値を取得
        let intNinzu = Int(ninzu.text!)!
        let intKingaku = Int(kingaku.text!)!

        // 総金額/人数 = 一人あたり
        let intKekka = intKingaku / intNinzu
        // ラベルに結果を表示
        kekka.text = "\(intKekka)円"
        
        // キーボード閉じる
        ninzu.endEditing(true)
        kingaku.endEditing(true)
    }
}

```
