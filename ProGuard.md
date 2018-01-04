#混淆
##目的
防止被反编译  
## 规则
* _需要在混淆文件“proguard-project.txt” or “proguard-rules.pro”中定义混淆规则 ：哪些类不被混淆_  
* _混淆后生成mapping文件：列出了原始类，方法和字段名与混淆后代码间的映射。当收到bug时，可用mapping文件翻译被混淆的代码。其目录为\app\build\outputs\mapping\release_  
* _ProGuard默认对第三方库做混淆，如果第三方库已经做了混淆，或者使用java反射技术，需要排除这些第三方库_

## 还原混淆后的代码
须知：build后，proguard会生成以下几个txt文件 ，为于\build\outputs 
* dump.txt  : 所有class文件的内部结构介绍
* mapping.txt  ：混淆前后的映射
* seeds.txt  ：没有混淆的类和成员
* usage.txt  ：从apk删除的代码

### 1 通过命令行还原
* 使用<sdk-root>/tools/proguard/ 的retrace把需要还原的堆栈信息保存在obfuscated_trace文件中
* 终端输入“retrace.bat -verbose mapping.txt obfuscated_trace.txt”

### 2 通过GUI工具还原
1. 运行proguardgui.bat(<sdk-root>/tools/proguard/bin)
2. 左边菜栏选择“ReTrace”
3. mapping file中选择对应的mapping，在下面的输入框输入出现bug的堆栈信息
4. 点击右下方的“ReTrace”



