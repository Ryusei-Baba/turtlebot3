# turtlebot3
セットアップ済み(exportなどは~/.bashrcに書き込み済み)   
※IPアドレスが変わっている場合は~/.bashrcのアドレス部分を変更する   
### [デモ動画(ナビゲーション)](https://youtu.be/02gZeIksStU)   
### [デモ動画(SLAM)](https://youtu.be/nOOk7smzSCU)
***
## 動かし方
1.リモートPCのwifi設定（テザリング）   

2.raspberry piにモニターとキーボードを接続し、ユーザー名：ubuntu、password：turtlebotでログインする。ip aなどでIPアドレスを確認（wlan0が無線接続）する   

3.ssh ubuntu@｛IPアドレス(wlan0)｝でリモートPCからraspberry piにログインする[**ターミナルA1**]   

4.リモートPCでターミナルを立ち上げ、以下を実行する[**ターミナルB1**]    
```
roscore
```

5.sshで入ったターミナルで以下を実行する[**ターミナルA1**]   
```
export OPENCR_PORT=/dev/ttyACM0
```
```
cd ./opencr_update
```
```
./update.sh $OPENCR_PORT $OPENCR_MODEL.opencr
```
```
roslaunch turtlebot3_bringup turtlebot3_robot.launch
```

6.リモートPCから新しいターミナルを開き、SLAMノードを起動[**ターミナルB2**]   
```
roslaunch turtlebot3_slam turtlebot3_slam.launch
```

7.キーボードを使用して遠隔操作のためにリモートPCからノードを起動する[**ターミナルB3**]   
```
roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```
```
Control Your Turtlebot3
Moving around
     w
 a   s   d
     x
w/x : increase/decrease linear velocity
a/d : increase/decrease angular velocity
space key, s : force stop
CTRL-C to quit
```

8.リモートPCで新たにターミナルを立ち上げ以下のコマンドを実行しマップを保存する[**ターミナルB4**]
```
rosrun map_server map_saver -f ~/map
```

9.SLAMノード[**ターミナルB2**]をctrl+Cで終了し、以下のコマンドでナビゲーションノードを実行する
```
roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$HOME/map.yaml
```

10.その後はRVizメニューの2D Pose Estimateボタンや[**ターミナルB3**]のキーボード操作などで初期位置を設定し、RVizメニューの2D Nav Goalボタンで目的地を設定する。
***
# link
[タートルボット３ eマニュアル](https://emanual.robotis.com/docs/en/platform/turtlebot3/quick-start/#pc-setup)   
[TurtleBot3 Burger のファームウェアのアップロード エラー](https://www.blue-weblog.com/entry/2017/11/23/204902)   
