**zIndex**

ios下的zIndex层级问题，主要发生在iphone7和iphoneX下，绝对定位必须有一个共同的父元素。

**左右边框不生效**

当边框的宽度设置为奇数的时候，可能会不生效。

解决办法：将宽度设置为偶数的时候，在ios下就可以解决。

**marginBottom**

尽量不使用margin-bottom，当元素是在整个页面的最底部的似乎，在ios下可能margin-bottom会失效，所以可使用padding-bottom。