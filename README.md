# Nala
We propose the Nala markup, to turn a "Natural Language" sentence into a code-like statement.

关于 Nala 标注的中文介绍，请看 https://zhuanlan.zhihu.com/p/406792308 。

Examples for English:

```
I.love(you)                   // write SVO as S.V(O)

I.agree()

I.give(him, <a>pen)           // use <> for semantic "decorations" including adj / adv / ...

I.have(dinner)<at home>       // use space after a preposition ("at")

I.am(taller)<than him>

Bob.gets(excited)<when he.watches(<action>movies)>          // use <> for clauses

#.Call(me, Ishmael)           // use # to denote a implied token (here # = "you")

Please #.go()                 // use space for all other cases, i.e., after "Please" (here # = "you")

What #(<a nice> day)!         // here # = "is"

Isn't it.#(great)?            // here # = "is"
```

Examples for Chinese:
```
我.爱(你)

我.同意()

我.给(他, <一/支>笔)            // 这里 <> 是借用 C++ 模板符号，里面放修饰（形容词、副词、量词、时态等等），这里 / 是分词标记

我.<在/家>吃(晚饭)              // 也可也写成【我<在/家>.吃(晚饭)】，看你希望强调哪种语义
```

下面是中文中常见的"主题句"：
```
我.#<比/他>(高)                 // 其中 # 代表省略的动词，类似英文的 be

<这件>事.#(你.<也>知道()).吧     // 语气词直接写

酒.<被.我>#(喝<完/了>)          // 我认为，中文被动句，是用介词短语修饰，类似 by me

王冕.#<三/岁>(#.死<了>(父亲))    // 括号中的 # 代表某个特殊 context（就像语言模型中的隐状态），可让后续动词的 S 和 O 颠倒
```
换种写法，【王冕三岁时，他的父亲死了】，标注：
```
王冕.#(三/岁).时，<他的>父亲.死<了>()   // 我认为"时"是关联词，所以直接写，代表这个 token 修改语言模型的 context
```
下面是更多的中文语法现象，粗略分析，欢迎讨论：
```
<这碗/猪都不喝的>汤.#(你.<还是>倒<了>().吧))

小张.#(把.眼睛.<哭>肿<了>())

他.<今年/天天>吃<食堂>()

这女孩.#(<见过的>#.<都>说(漂亮))

如果.#.可以(<重新>选择).那么.你.<会>看好(谁)

如果 #.可以(<重新>选择) 那么 你.<会>看好(谁) // 省略累赘的“.”
```
