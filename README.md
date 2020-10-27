# jnmouse_sim

Gaezbo上でJetson Nano MouseをシミュレーションするためのROSパッケージ一式です。

![](https://rt-net.github.io/images/jetson-nano-mouse/jnmouse_gazebo_disparity.png)

## ROS Package Status

| main develop<br>(master)|Melodic + Ubuntu Bionic<br>(melodic-devel)|
|:---:|:---:|
|[![industrial_ci](https://github.com/rt-net/jnmouse_sim/workflows/industrial_ci/badge.svg?branch=master)](https://github.com/rt-net/jnmouse_sim/actions?query=branch%3Amaster+workflow%3Aindustrial_ci) | [![industrial_ci](https://github.com/rt-net/jnmouse_sim/workflows/industrial_ci/badge.svg?branch=melodic-devel)](https://github.com/rt-net/jnmouse_sim/actions?query=branch%3Amelodic-devel+workflow%3Aindustrial_ci) |

## 動作環境

* Ubuntu
  * Ubuntu Bionic Beaver 18.04.*
* ROS
  * ROS Melodic Morenia
* Gazebo
  * Gazebo 9.x

## インストール

このROSパッケージをダウンロードします。

```
cd ~/catkin_ws/src
git clone https://github.com/rt-net/jnmouse_sim.git
```

依存関係にあるROSパッケージをダウンロード、インストールします。

```
cd ~/catkin_ws/src
git clone https://github.com/ryuichiueda/raspimouse_ros_2.git
git clone https://github.com/rt-net/jnmouse_description.git
rosdep install -r -y -i --from-paths .
```

`catkin build`コマンドでこのROSパッケージを含む`~/catkin_ws`以下のROSパッケージをビルド、インストールします

```
cd ~/catkin_ws && catkin build
source ~/catkin_ws/devel/setup.bash
```

Gazeboにて使用するハードウェアモデルデータをダウンロードします。

```
rosrun jnmouse_gazebo download_gazebo_models.sh
```

## クイックスタート

インストール完了後、以下のコマンドを実行することで机＋缶ジュースの環境にてロボットを起動できます。

```
roslaunch jnmouse_gazebo jnmouse_with_table.launch
```

また、Gazeboが起動した状態で以下のコマンドを実行することで`odom`可視化用のRVizと[teleop_twist_keyboard](https://wiki.ros.org/teleop_twist_keyboard)を同時に起動できます。

```
roslaunch jnmouse_gazebo keyboard_teleop.launch rviz:=true
```

その他の詳しい使い方は[wiki](https://github.com/rt-net/jnmouse_sim/wiki)を参照してください。

## スクリーンショット

![](https://rt-net.github.io/images/jetson-nano-mouse/jnmouse_gazebo_1.gif)

![](https://rt-net.github.io/images/jetson-nano-mouse/jnmouse_gazebo_2.gif)

## ライセンス

(C) 2020 RT Corporation \<support@rt-net.jp\>

各ファイルはライセンスがファイル中に明記されている場合、そのライセンスに従います。特に明記されていない場合は、Apache License, Version 2.0に基づき公開されています。  
ライセンスの全文は[LICENSE](./LICENSE)または[https://www.apache.org/licenses/LICENSE-2.0](https://www.apache.org/licenses/LICENSE-2.0)から確認できます。

※このソフトウェアは基本的にオープンソースソフトウェアとして「AS IS」（現状有姿のまま）で提供しています。本ソフトウェアに関する無償サポートはありません。  
バグの修正や誤字脱字の修正に関するリクエストは常に受け付けていますが、それ以外の機能追加等のリクエストについては社内のガイドラインを優先します。