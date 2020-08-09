学习笔记

##为什么 first-letter 可以设置 float 之类的，而 first-line 不行呢？
我认为first-letter是只渲染所选的第一个字母，而first-line渲染的是所选的第一行。
那么在布局结束之后，再对其操作，first-letter小号的性能就更小，first-line的性能消耗就会更大。
