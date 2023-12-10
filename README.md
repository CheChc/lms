## 简介

一个用Django+MySQL搭建的图书馆管理系统.

## 项目环境

+ Python 3.7
+ Django 3.1.1
+ MySQL 5.7
+ Pycharm 2019.2.4

## 为链接数据库进行修改

- 1、新建一个mysql数据库，假设名为test01
- 2、在settings里进行修改：

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'PORT': 3306,
        'HOST': 'localhost',
        'NAME': 'test01',  # 改为自己数据库名字
        'USER': 'root',
        'PASSWORD': '497*****' # 改为数据库密码
    }
}

```

- 3、修改_init.py文件

添加语句：

```sql 
import pymysql

pymysql.install_as_MySQLdb()//更换了数据库引擎
```

## 迁移数据库

- 创建APP

`python manage.py startapp web`

- 在setings中添加APP

``` sql
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'book',
    'web.apps.WebConfig',
]
```

- 迁移数据库

``` sql
python manage.py makemigrations
python manage.py migrate//同步了数据库
```

## 运行项目

确认已经正确安装 Python 3.4 以上的版本,但是版本不能过高，建议3.8

下载项目后，在命令行中进入项目目录，并创建**虚拟环境**：

```bash
python -m venv env
```

运行虚拟环境(MacOS)

```bash
source env/bin/activate
```

自动安装所有依赖项：

```bash
pip install -r requirements.txt
```

最后运行测试服务器：

```bash
python manage.py runserver
```

项目就运行起来了。

