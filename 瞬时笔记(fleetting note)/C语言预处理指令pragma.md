#CS/c语言 #CS/cpp语言编程 #CS/编程语言/预处理指令 #程序员 #程序员/Windows编程
# excecution_character_set()
![[Pasted image 20230202165945.png]]
用于解决Visual Studio下的UTF-8中文乱码问题：

```
#if _MSC_VER >= 1600 

﻿﻿﻿﻿﻿﻿#pragma execution_character_set("utf-8") 

#endif
```
