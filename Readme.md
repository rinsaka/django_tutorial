# Django Tutorial の プロジェクト
## 参考サイト
- https://docs.djangoproject.com/ja/3.0/intro/tutorial01/

## 環境
- OS : macOS Catalina 10.15.3
- Python : Python 3.7.5
- Conda : conda 4.7.12
- Django : Django 3.0.4

## クローンの作成

~~~
% git clone git@github.com:rinsaka/django_tutorial.git
~~~

## クローン後の作業

- データベーステーブルの作成（マイグレーション）

~~~
% cd django_tutorial
% python manage.py migrate
~~~

- Shell からデータを投入する (Question)

~~~
% python manage.py shell

In [1]: from polls.models import Choice, Question

In [2]: from django.utils import timezone

In [3]: q = Question(question_text="What's up?", pub_date=timezone.now())

In [4]: q.save()

In [5]: exit
~~~

- Shell からデータを投入する (Choice)

~~~
% python manage.py shell
Python 3.7.5 (default, Oct 25 2019, 10:52:18)
Type 'copyright', 'credits' or 'license' for more information
IPython 7.9.0 -- An enhanced Interactive Python. Type '?' for help.

In [1]: from polls.models import Choice, Question

In [2]: from django.utils import timezone

In [3]: q = Question.objects.get(pk=1)

In [4]: q.choice_set.create(choice_text='Not much', votes=0)
Out[4]: <Choice: Not much>

In [5]: q.choice_set.create(choice_text='The sky', votes=0)
Out[5]: <Choice: The sky>

In [6]: exit
~~~


- 管理者ユーザを作成する

~~~
% python manage.py createsuperuser
ユーザー名: admin
メールアドレス: admin@example.com
Password:
Password (again):
~~~


## Web サーバの起動とブラウザからのアクセス

- Web サーバの起動
~~~
% python manage.py runserver
~~~

- ブラウザからアクセスする

~~~
http://127.0.0.1:8000/polls/
http://127.0.0.1:8000/admin/
~~~
