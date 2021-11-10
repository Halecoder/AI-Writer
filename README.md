# AI-Writer
用魔改 GPT 生成网文。Tuned GPT for novel generation. 现已支持 N卡 A卡 I卡 GPU 加速。

1. 下载模型，在右边 Release（或者看QQ群文件），解压到 model 目录（自己新建目录）。欢迎分享下载后的模型。
2. 运行 python run.py（或双击run.bat）。

***也支持纯 CPU 快速生成，每秒生成 10 个字，下载请加：技术和用户 QQ 群 143626394（加入时请简单自我介绍）。***

安装方法：
```
Windows小白：进QQ群，先试纯 CPU exe版
Windows有N卡：装python3.8，CUDA 11.1，CUDNN，torch1.9.1+cu111
Windows有A/I卡：装python3.8，pip install torch onnxruntime-directml
WindowsCPU版：装python3.8，pip install torch onnxruntime
Linux有N卡：参考Windows有N卡
Linux有A/I卡：装python3.8，pip install torch onnxruntime-gpu
LinuxCPU版：参考WindowsCPU版
Mac：目前只能CPU版。参考WindowsCPU版。
```

常见问题：
```
0. 先打开 run.py 和 server.py 看里面的设置。例如，玄幻和言情模型，需要在里面手工切换。
1. model 目录在哪里 --> 自己新建 model 目录。
2. no module named 'xxx' --> 执行 pip install xxx 缺什么就装什么。注意N卡GPU版需要装pytorch的cuda版。注意A/I卡GPU版需要装onnxruntime-directml。
3. module 'torch' has no attribute 'tile' --> 需要 pytorch 1.9 以后版本。
4. no such file or directory: 'model/xxx' --> 先确定模型解压到 model 目录。然后在命令行需要先进入项目所在的目录，再用python运行py。
5. 怎么设置每次续写多少字 --> 修改run.py和server.py的LENGTH_OF_EACH。
6. 怎么训练？ --> https://github.com/BlinkDL/RWKV-LM 不懂就加QQ群143626394（加入时请简单自我介绍）。
7. 写作原理？ --> 每次分析最后的512个字，得到下一个字的概率分布（xx%概率是x字，等等），根据概率写一个字。这样一个个字写下去。
```
最新加入网页界面，执行 python server.py（或双击server.bat）然后打开 web-client 中的 index.html（推荐用Chrome）。

![Screenshot](server.jpg)

注意：模型的训练数据全部来自网文，缺乏生活常识。***生成的文字仅供娱乐。请遵守法律法规。***

***采用我的 RWKV 模型，比 GPT 更快，训练代码：https://github.com/BlinkDL/RWKV-LM***

同时使用了特殊采样方法，改善小模型的生成质量（介绍见 https://zhuanlan.zhihu.com/p/394766831 ）。

我的知乎是 https://www.zhihu.com/people/bopengbopeng 。

网友移植的 Paddle 版：https://github.com/JunnYu/Paddle-AI-Writer 。

新玄幻模型效果：

![Screenshot](AI-Writer.jpg)

旧模型效果：

![Screenshot](AI-Writer.gif)

> 魔皇突然倒退了一步，伸手摸了一下身上的伤口，然后朝着四周的虚空一指，原本在地下的虚空魔法阵直接消失无踪，这里顿时恢复了活性。
  “来了……”魔皇喃喃的自语着，然后死死的盯着魔王的背影，不敢有丝毫的怠慢，在一个黑袍大汉的带领下，朝着人类的方向搜寻了过去。
  几分钟之后，在前面的虚空魔法阵眼前一空，所有的人都露了出来，大家一个个的瞪大了眼睛。
  “原来是魔皇大人。”听到魔皇的声音后，所有的人都感到惊讶，因为在他们眼中，这就是魔皇大人的魔导师，终于踏上了辉煌的魔法师之路，按理来说，能够拥有神力的魔导师是当之无愧的人类。
  但是此刻魔皇的身影却消失在这片大海之中，似乎早就看穿了这一切，这让众人的心都悬了起来。
  片刻之后，众人感觉到了空气中的清爽，所有人都猛的抬起头来，那巨大的眼睛里充满了向往，这样的表现让他们觉得此行不枉。
  他们不由的弯下了嘴唇，暗自在心里偷笑，“还真是可怜这个少女，哪怕是族中最优秀的天才魔导

> 魔皇原本还想留下来帮助魔族重新实现宇宙皇庭，进入宇宙国之中，但是他们无法理解罗云阳的想法，纷纷开始接受宇宙国的鲜血，红颜的血液，在魔皇的支持之下，将一具完整的尸体交给了大罗龙族。
  无一例外。
  加上不知道如何改造的龙族族人，整个魔族，都是法则大打折扣的，大罗龙族之中，大多数族人，都是凡蜕境界的修炼者，并不是修炼的全部。
  不过即便如此，所有人族也都是神通境界的强者，他们的血液，也是魔族的真血。
  末世到来，整个魔族族人，都被献祭到了宇宙之中。
  罗云阳和魔皇，曾经做过一些调查，想要杀害无辜的生命，但是无论他怎么做，没有丝毫的效果。
  而在无数年前，同样的一些动手，让魔族损兵折将，没有对人族的敌人动手，也都是因为自己没有能够在魔界还保留在人族，而且在这个时候，魔界遭受重创的事情，却是一直没有发生。
  因为他们也看出来，整个魔族，已经死于非命。
  这些魔族，将在人族的战争之中，归属人族。
  毕竟，人类发展到如今的

> 魔皇冲向洛寒，为什么没有动手，是因为洛寒身上释放出一种焚空气机，没有半点可以防御的地方。
  他身上涌出恐怖的火焰，这股火焰团似乎是一个小火球，赤红色的火球让整个天空都是冒着一股可怕的黑气。
  “明明是不受世界之力束缚的。”
  魔皇双掌猛地一抱，以他的法力，在和洛寒的玄火火团对抗时，即便是伤了他，这点法力也没有放在眼里。
  可洛寒就是这么不被世界之力束缚的火焰，身上燃烧着，死亡的恐怖气息似乎和天地能量结合在一起，魔皇手中一掌拍出，元神和本命精血之间产生出无尽的震动。
  “死！”
  魔皇周身同样结出魔灵附体，魔灵本源的修炼从高灵魔法转变为魔灵本源，正好对洛寒有克制力。
  此刻身为天地之力合身，洛寒的火焰本源燃烧出了七个魔灵本源。
  “阴阳生火术！”
  洛寒灵识爆发，低喝一声，顿时手中双剑蕴含天地之力化作一个黑白色的龙形刀影，向洛寒的玉手迎去，三位魔皇分身见此，也紧随而上，全都在洛寒强大无比的灵识中施展各种神通，攻敌
