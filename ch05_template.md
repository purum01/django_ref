# Chapter5

* [Template API](https://docs.djangoproject.com/en/2.1/ref/templates/api/)
* [resolve_url( )](https://github.com/django/django/blob/master/django/shortcuts.py#LC119)
* [Built-in template tags and filters](https://docs.djangoproject.com/en/2.1/ref/templates/builtins)
* [Custom template tags and filters](https://docs.djangoproject.com/en/2.1/howto/custom-template-tags/)
* [Date Format](https://docs.djangoproject.com/en/2.1/ref/templates/builtins/#date)
* [Time Format](https://docs.djangoproject.com/en/2.1/ref/templates/builtins/#time)



date/time filter 코드
---
~~~python
# views.py
from django.utils import timezone

def test(request):
    now = timezone.now()
    past_dt = timezone.datetime(1971,8,22,0,0)
    criteria_dt = timezone.datetime(2001,3,19,0,0)
    future_dt = timezone.datetime(2037,1,1,0,0)
    return render(request, 'mytest/test.html', 'datetime_obj':now,
                                               'past_dt':past_dt, 
                                               'criteria_dt':criteria_dt, 
                                               'future_dt':future_dt})

# test.html
<hr>
{{ datetime_obj|date:"D d M Y" }} <br/>
{{ datetime_obj|date:"DATE_FORMAT" }} <br/>
{{ datetime_obj|date:"DATETIME_FORMAT" }} <br/>
{{ datetime_obj|date:"SHORT_DATE_FORMAT" }} <br/>
{{ datetime_obj|date:"SHORT_DATETIME_FORMAT" }} <br/>
{{ datetime_obj|time:"TIME_FORMAT" }} <br/>
<hr>
{{ past_dt|timesince }} <br/>
{{ past_dt|timesince:criteria_dt }} <br/>
{{ future_dt|timeuntil }} <br/>
{{ future_dt|timeuntil:past_dt}} <br/>
~~~

linebreaks 코드
---
~~~python
    value ='''
        Miracles happen to only those who believe in them.
        Think like a man of action and act like man of thought.
        Courage is very important. Like a muscle, it is strengthened by use.
        Life is the art of drawing sufficient conclusions from insufficient premises.
        By doubting we come at the truth.
        A man that has no virtue in himself, ever envies virtue in others.
        When money speaks, the truth keeps silent.
        Better the last smile than the first laughter.
    '''
 ~~~
