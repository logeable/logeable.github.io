---
layout: post
title: GitHub Page 语法高亮
category: [syntax,highlight,github page]
---

在_config.yml里面加入下面这一行
```<pre>
markdown: redcarpet
redcarpet:
    extensions: ["fenced_code_blocks", "autolink", "tables", "strikethrough"]
```



```c++
#include <iostream>
using namespace std;

int main(int argc,char*argv[])
{
	int a=1;
	int b=2;
	cout<<a+b<<endl;
	return 0;
}

```
