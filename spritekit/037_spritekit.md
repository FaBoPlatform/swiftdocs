# Nodeをフェードインさせる

![Preview spritekit037](img/spritekit037.png)

## Swift3.0
### GameScene.swift
```swift
//
//  GameScene.swift
//  SpriteKit037
//
//  Created by Misato Morino on 2016/09/20.
//  Copyright © 2016年 Misato Morino. All rights reserved.
//

import SpriteKit

class GameScene: SKScene {
    
    private var ScaleAction : SKAction!
    private var rect : SKShapeNode!
    
    override func didMove(to view: SKView) {
        
        // フェードインさせるアクションを作る.
        ScaleAction = SKAction.fadeIn(withDuration: 2)
        
        // 赤い四角形のShapeNodeを生成.
        rect = SKShapeNode(rectOf: CGSize(width: 50.0, height: 50.0))
        rect.fillColor = UIColor.red
        rect.position = CGPoint(x: self.frame.midX, y: self.frame.midY)
        
        // アルファ値を0にして見えなくさせる.
        rect.alpha = 0.0
        
        // sceneの背景を黒色にする.
        self.backgroundColor = UIColor.black
        
        // sceneにshaoeNodeを追加する.
        self.addChild(rect)
    }
    
    /*
     touchを感知したときに呼ばれるメソッド
     */
    override func touchesBegan(_ touches: Set<UITouch>, with event: UIEvent?) {
        
        // アクションが実行中じゃなければ.
        if rect.hasActions() == false {
            
            // アクションを実行させる.
            rect.run(ScaleAction)
        }
    }
}
```

## Swift 2.3
### GameScene.swift
```swift
//
//  GameScene.swift
//  SpriteKit037
//
//  Created by Misato Morino on 2016/09/20.
//  Copyright © 2016年 Misato Morino. All rights reserved.
//

import SpriteKit

class GameScene: SKScene {
    
    private var ScaleAction : SKAction!
    private var rect : SKShapeNode!
    
    override func didMoveToView(view: SKView) {
        
        // フェードインさせるアクションを作る.
        ScaleAction = SKAction.fadeInWithDuration(2)
        
        // 赤い四角形のShapeNodeを生成.
        rect = SKShapeNode(rectOfSize: CGSizeMake(50.0, 50.0))
        rect.fillColor = UIColor.redColor()
        rect.position = CGPointMake(self.frame.midX, self.frame.midY)
        
        // アルファ値を0にして見えなくさせる.
        rect.alpha = 0.0
        
        // sceneの背景を黒色にする.
        self.backgroundColor = UIColor.blackColor()
        
        // sceneにshaoeNodeを追加する.
        self.addChild(rect)
    }
    
    /*
     touchを感知したときに呼ばれるメソッド
     */
    override func touchesBegan(touches: Set<UITouch>, withEvent event: UIEvent?) {
        
        // アクションが実行中じゃなければ.
        if rect.hasActions() == false {
            
            // アクションを実行させる.
            rect.runAction(ScaleAction)
        }
    }
}
```

## 2.3と3.0の差分
* ```didMoveToView(view: SKView)``` から ```didMove(to view: SKView)``` に変更
* ```runAction``` から ```run``` に変更

## Reference
* SKShapeNode
    * [https://developer.apple.com/reference/spritekit/skshapenode](https://developer.apple.com/reference/spritekit/skshapenode)
* SKAction
    * [https://developer.apple.com/reference/spritekit/skaction](https://developer.apple.com/reference/spritekit/skaction)
