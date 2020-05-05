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