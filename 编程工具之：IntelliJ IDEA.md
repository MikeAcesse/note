# 最重要的功能。可以搜索全部快捷键：help--Find Action
# 一、高效定位代码之跳转
## 1.项目之间的跳转
window--Next Project Window || Previous Project Window
## 2.文件之间的跳转
Recent Files：最近查看过的文件
Recent Changed Files：最近修改过的文件
## 3.浏览修改位置跳转
Navigate--Last Edit Location（Next Edit Location）：跳转到上回（下次）编辑的地方
Navigate--Back（Forward）：跳转到上回（下次）浏览的地方，**光标停的地方**
## 4.利用书签跳转（快速学习源码）
Bookmarks书签--toggle Bookmarks 加书签
Bookmarks书签--toggle Bookmarks with Mnemonic 加带有数字标记书签
## 5.收藏位置和文件
Favorites（收藏）--Add To Favorites：收藏类，光标放置在类上。收藏方法，光标放置在方法上。
## 6.字符跳转插件emacsIdea
Find Action，搜索Plugins：安装插件
emacsIdea使用的快捷键：Ctrl+J，快速定位（使用了此技能，鼠标从此是路人）
## 7.编辑区与文件区之间来回跳转
Command+1：进入文件区
Esc：进入编辑区
## 8.利用vim 进行多编辑区跳转（好像不需要）
--------------------
# 二、高效定位代码之精准搜索
## 1.类
Navigate--Class：Command+N 搜索类。Include non-project classes排除jar包。
## 2.文件
Navigate--File：Shift+Command+N搜索文件。可搜目录+文件名。可选搜索jar包文件
## 3.符号（两层含义函数名|属性）
Navigate--Symbol：搜索符号
## 4.字符串搜索
- Edit--Find--Find In Path：ctrl+shift+F。File mask 指在那类文件中搜索
--------------------
# 三、代码助手
## 1.列操作
- Move caret to next word ：移动一个单词位ctrl+➡️。加Shift回移动并选中一个单词
- Toggle Case：大小写切换：Ctrl+Shift+U
- Move Caret To Line Start：移动到行首
- Move Caret To Line End：移动到行尾
- Select All Occurrences：批量选中相同行：Ctrl+Shift+Alt+J。注意右下角有标示出选中了多少carets
- Code--Reformat Code：格式化代码

## 2.Live template（几种玩法比如：生成定义好的input控件html代码，生成页面固定的结构代码）支持自定义
- 自定义一个main：$END$ 代码自动生成后光标到达的位置
- psfi：public static final int：$var1$ = $var2$，var1代码生成光标落到的位置，var2，第一处代码写完敲回车进入的下一位置。
- psfs：public static final String；
- pi：private int
- ps：private String

## 3.postfix ，不支持自定义
- 100.forin：普通for循环，
- list.forof：高级for循环
- name.field：生成属性值
- new Date().sout：输出new Date()
- user.return：返回语句自动生成
- user.nn：判断语句自动生成

## 4.快捷键Alter + enter：Show Intention Action
- 自动创建函数（create method）
- list replace：Replace with foreach，自动简化代码的书写，让代码看起来更简单
- 对sout的字符串的format或者转换StringBuilder：
- 快速实现接口：
- 纠正单词拼写：Type Change to
- 自动提示导包：
--------------------
## 四、编写高质量代码
- 重构变量Rename：Shift+F6。语意清晰；
- 重构方法：Refactor -- change signature
-  Add String as 2nd parameter to method ***
-  抽取变量： Refactor--Extract--Variable
-  抽取静态变量：Refactor--Extract--Contant
-  抽取成员变量：Refactor--Extract--Field
-  抽取方法参数：Refactor--Extract--Parameter
-  抽取函数：Refactor--Extract--Method
Replace all occurrences（地方）
--------------------
## 五、寻找修改轨迹
1.git的集成
- annotate：查看代码作者
- 移动改动地方：previous change：change Navigation Action
- 撤销版本控制中的改动：撤销整个文件、撤销改动部位、撤销整个工程
2.local history
- show history
- Put Label：本地的提交功能
--------------------
## 六、关联
1.spring的关联
- File--Project Structure--Facets：配置好与Spring的关联
- Navigate to the autowired dependemcies：
- Navigate to the Spring bean declarations：链接到声明bean的位置。
- Navigate to Componets：显示Spring自动扫描的所有bean
2.关联数据库
- 有利于写sql，但这种方式并不好用。很难调试sql是否正常。比较建议在navicate里写查询，调试完成后翻译到map.xml中。
--------------------
##七、断点调试
- Toggle Line Breakpoint ：添加断点
- 单步运行：F8
- Resume Program：F9
- Breakpoints：查看所有断点 Shift + Command + F8，
- Mute Breakpoints：禁止所有断点
- 条件断点：Command+F8，用于多次循环中跳转到指定的循环中。
- Evaluate Expression：表达式求值
- Run to Cursor：运行到指定行
- setValue：动态改变运行时对象的值
--------------------
## 八、其他操作
1.文件操作
- 在当前文件同一级目录下新建文件：在当前文件编辑区内使用快捷键Ctrl+N
- 复制当前文件：F5
- 移动当前文件：拖拽啊！

2.文本操作
- 复制文件名：Ctrl +C
- 复制文件路径：Ctrl +Shift+C
- 剪切板工具：Ctrl+Shift+V

**3.结构图：超有用的功能**
- File Structure：查看当前文件的大纲Field，method：Ctrl+F12
- 查看maven 依赖，类图：pom.xml里右击--Maven--show Dependencies （jar包依赖图中可以进行搜索）
- 在类的里边，也可以看到继承关系
- 查看类的继承结构，方法的调用层次：
- Hierarchy Class Son：Ctrl + H，继承结构。另一种方式：Diagram for Son。
- Call Hierarchy：显示方法的调用层次：
- Caller Methods Hierarchy：谁调用这个方法
- Callee Methods Hierarchy：这个方法调用谁了
