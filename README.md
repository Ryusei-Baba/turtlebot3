# turtlebot3
セットアップ済み
***
## 動かし方
1.リモートPCのwifi設定（テザリング）   
2.raspberry piにモニターとキーボードを接続し、ユーザー名：ubuntu、password：turtlebotでログインする。ip aなどでIPアドレスを確認（wlan0が無線接続）する   
3.ssh ubuntu@｛IPアドレス(wlan0)｝でリモートPCからubuntuに入る   
4.**リモートPC**でターミナルを立ち上げ、以下を実行する    
```
roscore
```
5.**sshで入ったターミナル**で以下を実行する   
```
roslaunch turtlebot3_bringup turtlebot3_robot.launch
```
6.リモートPCから新しいターミナルを開き、SLAMノードを起動   
```
roslaunch turtlebot3_slam turtlebot3_slam.launch
```
7.キーボードを使用して遠隔操作のために**リモートPC**からノードを起動する   
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
8.リモートPCで新たにターミナルを立ち上げ以下のコマンドを実行しマップを保存する
```
rosrun map_server map_saver -f ~/map
```
***
# link
[タートルボット３ eマニュアル](https://emanual.robotis.com/docs/en/platform/turtlebot3/quick-start/#pc-setup)   
[TurtleBot3 Burger のファームウェアのアップロード エラー](https://www.blue-weblog.com/entry/2017/11/23/204902)   
