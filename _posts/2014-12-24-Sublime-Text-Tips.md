---
layout: post
category: 程序媛
tags: [sublime, tutorial]
title: Sublime Text 使用技巧
bg-image: post-bg.jpg
photo-credit: NASA on The Commons
writer: Jia
---

- 基于mac版sublime 3
- 更新日期：2014-12-24

## 快捷键

- 选择一个选中项的下一个匹配项: ⌘ + D
  >把光标放在一个单词上，按下⌘+ D,将选择这个单词。一直按住⌘且按D多次，将选择当前选中项的下一个匹配项。通过按住⌘,再按D三次,将选择三个相同的文本。

  ![](http://mmbiz.qpic.cn/mmbiz/KovAgJ2aWyaIAgGSNJs3libcdWlkeroRhXJovrhUNXundF2Hr3Wm8DZL5nVbG0YYVNEKVABpUtEqB98Mg7NMrbA/0/mmbizgif)

  <!-- break -->

- 选择一个选中项的所有匹配项: CTRL + ⌘ + G
  >和上面一样,但它选择文件中的所有匹配项。小心使用这个,因为它能选择一个文件中的所有匹配项. .

  ![](http://mmbiz.qpic.cn/mmbiz/KovAgJ2aWyaIAgGSNJs3libcdWlkeroRh7E0QYZVTtnOuicRFmkakavyLbSHChEgvb3poJWuRkJwmbwg1VTib8dkg/0/mmbizgif)

- 选择容器内内容:CTRL + D
  >如果你把光标放在文本间再按下上面的键将选择文本,就像⌘+ D。但是再次按下它，将选择父容器,再按,将选择父容器的父容器。*需要Emmet插件

  ![](http://mmbiz.qpic.cn/mmbiz/KovAgJ2aWyaIAgGSNJs3libcdWlkeroRhiaYr2icg6JKsnFsRCiciafQmiclERYKLEewfUC7VMwoxm7wlsGia2eFBJUQA/0/mmbizgif)

- 上移或下移行: CTRL + ⌘ + ↑ 或 ↓

  ![](http://mmbiz.qpic.cn/mmbiz/KovAgJ2aWyaIAgGSNJs3libcdWlkeroRhIaf5wxDDuObT6hicj9ntp1YNJRrNzee0PAmDK6yflvvjc71UBwIP1Xg/0/mmbizgif)

- 复制行或选中项: ⌘ + ⇧ + D
  >如果你已经选中了文本,它会复制你的选中项。否则,把光标放在行上,会复制整行。

  ![](http://mmbiz.qpic.cn/mmbiz/KovAgJ2aWyaIAgGSNJs3libcdWlkeroRhhU7ynQeUm3UOicfxiaDclPHp2eOvcf1oKicYcxI3eNepkicQlEr6Q0SyDw/0/mmbizgif)

- 增加和减少缩进: ⌘ + [ 或 ]

  ![](http://mmbiz.qpic.cn/mmbiz/KovAgJ2aWyaIAgGSNJs3libcdWlkeroRh2lk5ZcHmnSjvbSNOIicZw3aD8ajWSym8vXe9xrf6aPqsgCk7ahZ7KBQ/0/mmbizgif)

- 剪切行或选中项: ⌘ + X
  >剪切一行到你的剪切板，你可以粘贴到其他地方.

  ![](http://mmbiz.qpic.cn/mmbiz/KovAgJ2aWyaIAgGSNJs3libcdWlkeroRhq33yzc3TId6RZQlevicJZiatoQdNnNWNsInl3CwibVIpkwXYE0E0ptx1g/0/mmbizgif)

- 粘贴并保持缩进: ⇧ + ⌘ + V
  >这是又一个我每次都用的快捷键。在gif中我显示了普通粘贴(⌘+ V)和缩进粘贴两种效果的对比。注意缩进如何排列。

  ![](http://mmbiz.qpic.cn/mmbiz/KovAgJ2aWyaIAgGSNJs3libcdWlkeroRhKgDCiacsocTeaAoQDmePgsEhSw1Zbibs899YC8F2P3c5eonRKpTiaqlOw/0/mmbizgif)

- 用标签包裹行或选中项: CTRL + ⇧ + W
  >使用标签包裹一行; 开始输入你想使用的标签,你成功了.

  ![](http://mmbiz.qpic.cn/mmbiz/KovAgJ2aWyaIAgGSNJs3libcdWlkeroRhqBqroCIabJvMiaK6TRKFv5A9IEdUTcicBVuibg9OHiczOKSicTd5jKleHhg/0/mmbizgif)

- 移除未闭合的容器元素: ⌘ + ’
  >这会移除与你的光标相关的父标签。对清除标记很有帮助。

  ![](http://mmbiz.qpic.cn/mmbiz/KovAgJ2aWyaIAgGSNJs3libcdWlkeroRh9PoFmcD2D8AePRyXj1G9TYo50dah3vx5wdUeBgEslicib3oAVibQhwZwQ/0/mmbizgif)


- 计算数学表达式: ⌘ + ⇧ + Y

  ![](http://mmbiz.qpic.cn/mmbiz/KovAgJ2aWyaIAgGSNJs3libcdWlkeroRhM23ZAIibsYV3xI69ibo2BS9ILFKCs1pkHoo4twsU0LKotXmmIWbNPbhw/0/mmbizgif)

- 递增和递减: ⇧ + OPTION + ↑ or ↓, OPTION + ↑ or ↓
  >按住 ⇧ 将以10的步长改变数字, 不按住以1为步长. 同时注意到你不需要选择数字, Sublime Text 足够聪明到更新本行最近的数字.

  ![](http://mmbiz.qpic.cn/mmbiz/KovAgJ2aWyaIAgGSNJs3libcdWlkeroRhLziceaR8hPKuKoc8jZku4MytevzXYvicEKyWef4dSF8Pnd930afVK5pw/0/mmbizgif)


- 大写和小写: ⌘ + K then U, ⌘ + K then L

  ![](http://mmbiz.qpic.cn/mmbiz/KovAgJ2aWyaIAgGSNJs3libcdWlkeroRh6LHr8ia8siaWaVkicWdqn5cQvFJq1Q5zLVpAPkYPk8W6ia5cz1icNIjNicyQ/0/mmbizgif)

- 注释选中项/行: ⌘ + /
  >这个在所有语言下都可用, 对行和选中项都可用.

  ![](http://mmbiz.qpic.cn/mmbiz/KovAgJ2aWyaIAgGSNJs3libcdWlkeroRhWOGgkepR8eqSWeAtJADIFYfnut2BOEIvz4yCpFCUHoMEy1DicUiabybQ/0/mmbizgif)

--------

## 插件

- package control 官方网站：https://sublime.wbond.net

### web开发常用的插件

- Emmet
- ColorHightlighter
- BracketHighlighter
- snippets: nodejs, jQuery, javascript
- httpRequest:Http Requester
- nettus fetch

### 界面
- SideBarEnhancements
- 流行主题推荐：soda，flat，space grey
- ColorSchemeSelector
- advancedNewFile:

### 其他编码

- AutoFileName
- Git
- GitGutter
- AllAutoComplete

--------

## 参考资料

- [Sublime Text 视频教程@iMooc](http://www.imooc.com/video/5466)
- [伯乐在线的sublime文章](http://blog.jobbole.com/tag/sublime-text/)
- [Sublime Text Setup Wiki](https://github.com/mrmartineau/SublimeTextSetupWiki/wiki)
