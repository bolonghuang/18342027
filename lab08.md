###Construct 2 小游戏制作和软件设计
construct 2是一款无需开发者具备编程基础就能上手体验的小游戏开发软件。之前有了初步了解和尝试，这次算是再次体会它的功能。

#游戏：一个简单容易上手的射击游戏

#游戏策划

1.楔子（setting）:

一个持枪猎人误入一个神秘荒地，荒地中的野怪看到有猎人侵入自己的领地，纷纷朝猎人扑去，企图消灭猎人。猎人见机不妙，慌乱之中回过神，朝着手中的枪，进行反击，当猎人狙击野怪超过1000时，野怪将不再攻击猎人，猎人脱离绝境。

2.游戏要素：

角色：Player(猎人)，Boss(野怪)，Bullet(子弹)。

道具：爆炸图像，背景图像，累计器(累计猎人消灭的怪数）。

3.游戏玩法：

通过键盘上的上下左右键控置Player的移动，以避开野怪的撞击；通过鼠标控置Player的面对方向，同过单击鼠标发射子弹。当Player消灭掉1000个野怪时，Player脱离危险，即胜利，在此之前如果猎人被也怪击中一次，游戏失败，游戏重新开始。

#2.游戏设计（游戏对象的CRC卡片）：

| Object Name :  |  Player   |
| Attibutes   :  |Sprite,Main Layer,365,366|
|---------------|------------------|
|  Collaborator  |    Events & Action  |
|----------------|----------------------|
|      bullet    |      fire            | 
|    platform    |   get scores when boss died |
|    " victory  "   |  apear when scores=1000 |
|   " game over"   |    apear when scores<1000,and Player is knocked by Boss|

| Object Name :  |  Boss          |
| Attibutes   :  |Main Layer,Speed 80,health 3|
|---------------|------------------|
|  Collaborator  |    Events & Action  |
|----------------|----------------------|
|       Boss     |   go forward to Player to kill him | 
|       Bang       |    apear  when Boss 'health=0     |
      

#游戏过程gif图展示
