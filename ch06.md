# Chapter6

* [Class-based views](https://docs.djangoproject.com/en/2.1/topics/class-based-views/)
* [django.views.generic](https://github.com/django/django/tree/2.1/django/views/generic)
* [Built-in class-based views API](https://docs.djangoproject.com/en/2.1/ref/class-based-views/)
* [View](https://github.com/django/django/blob/master/django/views/generic/base.py)
* [ListView](https://github.com/django/django/blob/2.1/django/views/generic/list.py)
* [DetailView](https://github.com/django/django/blob/2.1/django/views/generic/detail.py)
* [Generic Editing Views](https://github.com/django/django/blob/2.1/django/views/generic/edit.py)




DetailView
---
~~~python

class DetailView(object):
        
    def __init__(self, model):
        self.model = model

    def get_object(self, *args, **kwargs):
        return get_object_or_404(self.model, pk=kwargs['pk'])

    def get_template_name(self):
        return '{}/{}_detail.html'.format(self.model._meta.app_label, self.model._meta.model_name)

    def dispatch(self, request, *args, **kwargs):
        return render(request, self.get_template_name(), {self.model._meta.model_name: self.get_object(*args, **kwargs),})
    
    @classmethod
    def as_view(cls, model):
        def view(request, *args, **kwargs):
            self = cls(model)
            return self.dispatch(request, *args, **kwargs)
        return view

article_detail = DetailView.as_view(Article)
~~~
