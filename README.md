# AnimationImageView
## 概要  
コマごとの秒数を指定してアニメーションを設定できるUIImageViewの拡張クラスです。  
## 使い方
AnimationImageView.swiftをダウンロードして、任意のswiftプロジェクトに組み込んでください。
### サンプルコード
    let imageList = [image1, image2, image3, image4];
    let animationTimeList: Array<TimeInterval> = [0.2, 0.3, 0.4, 0.5]
    var animationFrameList = Array<AnimationFrame>()
    for i in 0..<imageList.count {
        animationFrameList.append(AnimationFrame(image: imageList[i], time: animationTimeList[i]))
    }
    // アニメーションのフレームを設定
    animationImageView.animationFrameList = animationFrameList
    // ループ回数（0なら無限）
    animationImageView.numberOfLoopTimes = 0
    // アニメーション終了後に初期画像に戻すかどうか
    animationImageView.backToFirstImage = false
### AnimationFrameについて
    class AnimationFrame {
        private(set) var image: UIImage?
        private(set) var time: TimeInterval?
    
        /// アニメーションフレーム
        ///
        /// - Parameters:
        ///   - image: フレームの画像
        ///   - time: フレームを表示する時間
        init(image: UIImage, time: TimeInterval) {
            self.image = image
            self.time = time
        }
    }
### デリゲート
numberOfLoopTimesの値が0でない場合、下記delegateメソッドにてアニメーションの完了が通知されます。  

    func animationImageView(didFinishedAnimation animationImageView: AnimationImageView) {  
    }
## ライセンス
AnimationImageView is released under the MIT license. See [LICENSE](https://github.com/bravesoft-lab/AnimationImageView/blob/master/LICENSE) for details.
