---
layout: post
title: 通过使用goagent提高git clone速度
category: [git,goagent]
---

通过使用goagent提高git clone速度

<!--break-->

---

```shell
vim ~/.gitconfig
添加：
[http]
	proxy=http://127.0.0.1:8087
	sslVerify=false
```
