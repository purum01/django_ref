# Chapter3

### Django Model

* [파이썬 ORM](https://github.com/vinta/awesome-python#orm)
* [django.db.backends](https://github.com/django/django/tree/master/django/db/backends)
* [models](https://docs.djangoproject.com/en/2.1/topics/db/models/)
* [Field types](https://docs.djangoproject.com/ko/2.1/ref/models/fields/#model-field-types)
* [Field options](https://docs.djangoproject.com/ko/2.1/ref/models/fields/#common-model-field-options)
* [Model Meta options](https://docs.djangoproject.com/en/2.1/ref/models/options/)
* [SQLite Browser](http://sqlitebrowser.org/)
* [Many-to-one relationships](https://docs.djangoproject.com/ko/2.1/topics/db/examples/many_to_one/)
* [Many-to-many relationships](https://docs.djangoproject.com/ko/2.1/topics/db/examples/many_to_many/)
* [One-to-one relationships](https://docs.djangoproject.com/ko/2.1/topics/db/examples/one_to_one/)
* [django.contrib.auth.models](https://github.com/django/django/blob/master/django/contrib/auth/models.py)
* [Migrations](https://docs.djangoproject.com/ko/2.1/topics/migrations/)


### Django admin app
* [The Django admin site](https://docs.djangoproject.com/en/2.1/ref/contrib/admin/)
* [ModelAdmin 소스](https://docs.djangoproject.com/en/2.1/_modules/django/contrib/admin/options/#ModelAdmin)
* [ModelAdmin options](https://docs.djangoproject.com/en/2.1/ref/contrib/admin/#modeladmin-options)


DB 환경 변수
---
~~~python

DATABASES = {
  'default': {
    'ENGINE': 'django.db.backends.mysql',
    'HOST': DB  서버 주소,
    'PORT': DB 서버 포트,
    'NAME': DB명,
    'USER': 계정,
    'PASSWORD': 비밀번호,
  },
}
~~~
