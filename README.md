一、vs code 的常用快捷键列表

1、注释：

　　a) 单行注释：[ctrl+k,ctrl+c] 或 ctrl+/

　　b) 取消单行注释：[ctrl+k,ctrl+u] (按下ctrl不放，再按k + u)

　　c) 多行注释：[alt+shift+A]

　　d) 多行注释：/**

2、移动行：alt+up/down

3、显示/隐藏左侧目录栏 ctrl + b

4、复制当前行：shift + alt +up/down

5、删除当前行：shift + ctrl + k

6、控制台终端显示与隐藏：ctrl + ~

7、查找文件/安装vs code 插件地址：ctrl + p

8、代码格式化：shift + alt +f

9、新建一个窗口: ctrl + shift + n

10、行增加缩进: ctrl + [

11、行减少缩进: ctrl + ]

12、裁剪尾随空格(去掉一行的末尾那些没用的空格) : ctrl + shift + x

13、字体放大/缩小: ctrl + ( + 或 - )

14、拆分编辑器 :ctrl + 1/2/3

15、切换窗口:  ctrl + shift + left/right

16、关闭编辑器窗口:  ctrl + w

17、关闭所有窗口 : ctrl + k + w

18、切换全屏 :F11

19、自动换行:  alt + z

20、显示git:   ctrl + shift + g

21、全局查找文件：ctrl + p

22、显示相关插件的命令(如：git log)：ctrl + shift + p

23、选中文字：shift + left / right / up / down

24、折叠代码： ctrl + k + 0-9 (0是完全折叠)

25、展开代码： ctrl + k + j (完全展开代码)

26、删除行 ： ctrl + shift + k

27、快速切换主题：ctrl + k / ctrl + t

28、快速回到顶部 ： ctrl + home

29、快速回到底部 : ctrl + end

30、格式化选定代码 ：ctrl + k / ctrl +f

31、选中代码 ： shift + 鼠标左键

32、多行同时添加内容（光标） ：ctrl + alt + up/down

33、全局替换：ctrl + shift + h

34、当前文件替换：ctrl + h

35、打开最近打开的文件：ctrl + r

36、打开新的命令窗：ctrl + shift + c

 

二、vs code 的常用插件

1、Auto Rename Tag 修改html标签，自动帮你完成尾部闭合标签的同步修改，和webstorm一样。

2、Auto Close Tag 自动闭合HTML标签

4、Beautiful 格式化代码的工具

5、Dash Dash是MacOS的API文档浏览器和代码段管理器

6、Ejs Snippets ejs 代码提示

7、ESLint 检查javascript语法错误与提示

8、File Navigator 快速查找文件

9、Git History(git log)查看git log

10、Gulp Snippets 写gulp时用到，gulp语法提示。

11、HTML CSS Support  在HTML标签上写class智能提示当前项目所支持的样式

12、HTML Snippets 超级好用且初级的H5代码片段以及提示

13、Debug for Chrome让vs code映射chrome的debug功能，静态页面都可以用vscode来打断点调试、配饰稍微复杂一点

14、Document this Js的注释模板

15、jQuery Code Snippets jquery提示工具

16、Html2jade html模板转pug模板

17、JS-CSS-HTML Formatter 格式化

18、Npm intellisense require 时的包提示工具

19、Open in browser 打开默认浏览器

20、One Dark Theme 一个vs code的主题

21、Path Intellisense 自动路径补全、默认不带这个功能

22、Project Manager多个项目之间快速切换的工具

23、Pug(Jade) snippets pug语法提示

24、React Components 根据文件名创建反应组件代码。

25、React Native Tools reactNative工具类为React Native项目提供了开发环境。

26、Stylelintcss/sass代码审查

27、Typings auto installer 安装vscode 的代码提示依赖库，基于typtings的

28、View In Browser 默认浏览器查看HTML文件（快捷键Ctrl+F1可以修改）

29、Vscode-icons 让vscode资源目录加上图标、必备

30、VueHelper Vue2代码段（包括Vue2 api、vue-router2、vuex2）

31、Vue 2 Snippets vue必备vue代码提示

32、Vue-color vue语法高亮主题

33、Auto-Open Markdown Preview markdown文件自动开启预览

34、EverMonkey 印象笔记

35、atom one dark atom的一个高亮主题(个人推荐)

 

三、常用的电脑快捷键

1、ctrl + shift + delete 快速清除浏览器缓存

2、ctrl + alt + delete 快速进入任务管理器页面

3、window + L  快速锁定电脑

4、window + d  所有窗口最小化

5、 window + e  打开我的资源管理器(我的电脑)

6、 window + f  快速打开搜索窗口

7、 alt + tab快速查看打开的应用与窗口

借鉴别人的博客的啦。。。。。。

 

四、这是我在后期使用中得到的一些小快捷，很好用哦

每次在代码调试的时候都需要输入console.log（），但是每次都要敲好多字

文件---首选项---用户代码片段----搜 javaScript ，进入JavaScript.json，可以自定义好多有用的快捷键，

下面这个例子就是打出c然后tab就乐意直接出来console.log(‘’)啦

"Print to console": {
    "prefix": "c",
    "body": [
      "console.log('$1')"
    ],
    "description": "Log output to console"
  }


# django
#### 安装django
```cmd
python -m pip install Django
```
#### 查看django版本
```cmd
python -m django --version
```
#### 创建项目
```cmd
django-admin startproject mysite
```
#### 启动服务
```cmd
python manage.py runserver
python manage.py runserver 0:8000
```
#### 创建投票应用
```cmd
python manage.py startapp polls
```
#### 编写第一个视图 polls/views.py
```python
from django.http import HttpResponse


def index(request):
    return HttpResponse("Hello, world. You're at the polls index.")
```

####  在polls 目录里新建一个 urls.py 文件
```python
from django.urls import path

from . import views

urlpatterns = [
    path('', views.index, name='index'),
]
```
#### 在根 URLconf 文件中指定我们创建的 polls.urls 模块。在 mysite/urls.py 文件的 urlpatterns 列表里插入一个 include()， 如下：
```python
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path('polls/', include('polls.urls')),
    path('admin/', admin.site.urls),
]
```
#### 安装psycopg2
```cmd
pip install psycopg2
pip install pylint-django
```
#### 使用他们之前需要在数据库中创建一些表。请执行以下命令：
```cmd
python manage.py migrate
```
#### 编辑 polls/models.py 文件：
```python
from django.db import models


class Question(models.Model):
    question_text = models.CharField(max_length=200)
    pub_date = models.DateTimeField('date published')


class Choice(models.Model):
    question = models.ForeignKey(Question, on_delete=models.CASCADE)
    choice_text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)
```
#### 为了在我们的工程中包含这个应用，我们需要在配置类 INSTALLED_APPS 中添加设置。因为 PollsConfig 类写在文件 polls/apps.py 中，所以它的点式路径是 'polls.apps.PollsConfig'。在文件 mysite/settings.py 中 INSTALLED_APPS 子项添加点式路径后，它看起来像这样：
```python
INSTALLED_APPS = [
    'polls.apps.PollsConfig',
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]
```
#### 现在你的 Django 项目会包含 polls 应用。接着运行下面的命令：
```cmd
python manage.py makemigrations polls
```
#### Django 有一个自动执行数据库迁移并同步管理你的数据库结构的命令 - 这个命令是 migrate，我们马上就会接触它 - 但是首先，让我们看看迁移命令会执行哪些 SQL 语句。sqlmigrate 命令接收一个迁移的名称，然后返回对应的 SQL：
```cmd
python manage.py sqlmigrate polls 0001
```
#### 你也可以试试运行 python manage.py check ;这个命令帮助你检查项目中的问题，并且在检查过程中不会对数据库进行任何操作。
#### 再次运行 migrate 命令，在数据库里创建新定义的模型的数据表：
```cmd
python manage.py migrate
```
#### 现在，你只需要记住，改变模型需要这三步：
1. 编辑 models.py 文件，改变模型。
2. 运行 python manage.py makemigrations 为模型的改变生成迁移文件。
3. 运行 python manage.py migrate 来应用数据库迁移。

#### 来试试 database API 吧:
```python
from django.utils import timezone
q = Question(question_text="What's new?", pub_date=timezone.now())
q.save()
q.id
q.question_text
q.pub_date
q.question_text = "What's up?"
q.save()
Question.objects.all()
```
#### 给 Question 和 Choice 增加 __str__() 方法(polls/models.py)。
```python
from django.db import models

class Question(models.Model):
    # ...
    def __str__(self):
        return self.question_text

class Choice(models.Model):
    # ...
    def __str__(self):
        return self.choice_text
```

### 介绍 Django 管理页面
#### 创建一个管理员账号
```cmd
python manage.py createsuperuser
```
#### 只需要再做一件事：我们得告诉管理员，问题 Question 对象需要一个后台接口。打开 polls/admin.py 文件，把它编辑成下面这样：
```python
from django.contrib import admin

from .models import Question

admin.site.register(Question)
```
### 编写更多视图
#### 让我们向 polls/views.py 里添加更多视图
```python
def detail(request, question_id):
    return HttpResponse("You're looking at question %s." % question_id)

def results(request, question_id):
    response = "You're looking at the results of question %s."
    return HttpResponse(response % question_id)

def vote(request, question_id):
    return HttpResponse("You're voting on question %s." % question_id)
```