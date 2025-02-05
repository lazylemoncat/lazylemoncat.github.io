[TOC]

## 创建 django 项目

1.   控制台输入 `django-admin startproject <项目名>`
2.   如果已经进入文件夹目录,则可以输入 `django-admin startproject <项目名> .`

## 创建项目内应用

1.   控制台输入 `python manage.py startapp <app>名`

## 注册 app

1.   在新应用中的 `apps.py` 中找到以 `Config` 为结尾的类,复制类名
2.   在 `settings.py` 的 `INSTALLED_APPS` 中加入 `'<新应用>.apps.<类名>'`

## 运行 django

1.   `python manage.py runserver 8000`