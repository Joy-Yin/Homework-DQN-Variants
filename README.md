# Homework-DQN-Variants
## DQN更新流程圖:
![DQN](https://github.com/Joy-Yin/Homework-DQN-Variants/assets/76059067/2c2df1f5-a9cf-47e6-b7de-49e7554f991d)
## 詳細流程:
![image](https://github.com/Joy-Yin/Homework-DQN-Variants/assets/76059067/0e84a291-d371-42b7-aa62-ec88f21f5f21)

1. 在狀態S中，透過ε-greedy來選擇action，圖中選到機率最大的a4
2. 得到相對應的Q值Q(s,a4)
3. 狀態轉移到S'
4. 透過目標網路(target network)得到目標Q值Q(s',a2')
5. 計算目標Q hat=reward+γ*Q(s',a2')
6. 將Q hat與Q(s,a4)相減即可得到預測誤差Error(loss)
7. 使用此誤差更新網路
8. 重複步驟1~7直到走到終點或掉入陷阱即完成一次訓練(1 epoch/episode)
9. 1~7的步驟每執行500次(C)就須更新目標網路參數一次
## 程式碼區段說明
程式碼來源:DeepReinforcementLearningInAction/Chapter 3
* 程式3.1:建立GridWorld的環境
  * 大小為4*4的矩陣
  * +代表終點，reward=10
  * -代表陷阱，reward=-10
  * W代表牆
  * P代表玩家，即當前位置
  * 除終點陷阱以外的格子reward=-1
* 程式3.2:建立DQN架構
* 程式3.3:訓練模型學習random產生的環境
* 程式3.4:建立測試用的模型
* 程式3.5:訓練含經驗回放(replay buffer)的DQN模型
* 程式3.6:測試含經驗回放的DQN模型
* 程式3.7:建立目標網路(target network)
* 程式3.8:訓練含經驗回放與目標網路的DQN模型並測試
