* [Cross Site Request Forgery protection](https://docs.djangoproject.com/en/2.1/ref/csrf/)
* [MultiValueDict](https://github.com/django/django/blob/2.1/django/utils/datastructures.py#L43)
* [QueryDict](https://docs.djangoproject.com/en/2.1/ref/request-response/#querydict-objects)
* [Form fields](https://docs.djangoproject.com/en/2.1/ref/forms/fields/)
* [ModelForm](https://docs.djangoproject.com/en/2.1/topics/forms/modelforms/)
* [Django 폼 처리 과정](https://developer.mozilla.org/ko/docs/Learn/Server-side/Django/Forms#Django_%ED%8F%BC_%EC%B2%98%EB%A6%AC_%EA%B3%BC%EC%A0%95)
* [full_clean()](https://github.com/django/django/blob/master/django/forms/forms.py#LC368)
* [validators](https://docs.djangoproject.com/en/2.1/ref/validators/)
* [Built-in validators](https://docs.djangoproject.com/en/2.1/ref/validators/#built-in-validators)
* [Form.add_error(field, error)](https://docs.djangoproject.com/en/2.1/ref/forms/api/#django.forms.Form.add_error)


MultiValueDict&QueryDict
---
~~~python
from django.utils.datastructures import MultiValueDict
from django.http import QueryDict

d = MultiValueDict({'name':['Amy','Tobey'], 'position':['Developer']})
qd = QueryDict('name=Amy&name=Tobey&position=Developer', encoding='utf8')
~~~
