# Chapter9

* [AUTHENTICATION](https://github.com/django/django/blob/master/django/conf/global_settings.py#LC493)
* [auth/models.py](https://github.com/django/django/blob/master/django/contrib/auth/models.py#LC288)
* [User 주요 함수](https://github.com/django/django/blob/master/django/contrib/auth/base_user.py#LC47)
* [auth/context_processors.py](https://github.com/django/django/blob/master/django/contrib/auth/context_processors.py#LC46)
### auth/forms.py
* [회원가입 폼](https://github.com/django/django/blob/2.1/django/contrib/auth/forms.py#LC64)
* [로그인 폼](https://github.com/django/django/blob/2.1/django/contrib/auth/forms.py#LC155)
* [암호변경 리셋 요청폼](https://github.com/django/django/blob/2.1/django/contrib/auth/forms.py#LC231)
* [암호 변경폼](https://github.com/django/django/blob/2.1/django/contrib/auth/forms.py#LC342)
* [암호 설정폼](https://github.com/django/django/blob/2.1/django/contrib/auth/forms.py#LC298)
### Signals
* [Signals](https://docs.djangoproject.com/en/2.1/ref/signals/)
* [dispatch/dispatcher.py](https://github.com/django/django/blob/master/django/dispatch/dispatcher.py)
* [db/models/signals.py](https://github.com/django/django/blob/master/django/db/models/signals.py)
* [auth/signals.py](https://github.com/django/django/blob/master/django/contrib/auth/signals.py)
### Email
* [Django Email library](https://docs.djangoproject.com/en/2.1/topics/email/)
* [장고 Email 기본 환경 변수](https://github.com/django/django/blob/master/django/conf/global_settings.py#L184)

### auth/views.py
* [auth/views.py](https://github.com/django/django/blob/master/django/contrib/auth/views.py)
* [user_logged_in](https://github.com/django/django/blob/2.1/django/contrib/auth/__init__.py#L161)

### Session
* [SessionMiddleware](https://github.com/django/django/blob/2.1.1/django/contrib/sessions/middleware.py)
* [SessionStore](https://github.com/django/django/blob/master/django/contrib/sessions/backends/db.py)
* [MiddlewareMixin](https://github.com/django/django/blob/2.1.1/django/utils/deprecation.py#LC82)
* [session문서](https://docs.djangoproject.com/en/4.0/topics/http/sessions/)

OAuth
---
* [django-allauth](https://django-allauth.readthedocs.io/en/latest/providers.html)
* [django-allauth/allauth/socialaccount/models.py](https://github.com/pennersr/django-allauth/blob/master/allauth/socialaccount/models.py)
* [facebook](https://developers.facebook.com/)
* [Naver](https://developers.naver.com/)
* [kakao](https://developers.kakao.com/)


이메일 환경 변수
---
~~~python
EMAIL_BACKEND = 'django.core.mail.backends.smtp.EmailBackend'
EMAIL_HOST = 'smtp.naver.com'
EMAIL_PORT = 465
EMAIL_HOST_USER = 'ID'
EMAIL_HOST_PASSWORD = '비밀번호'
EMAIL_USE_SSL = True
~~~

accounts/models.py
---
~~~python
from django.core.mail import send_mail
from django.db.models.signals import post_save

def on_send_mail(sender, **kwargs):
    if kwargs['created']:
        user = kwargs['instance']
        Profile.objects.create(user=user)

        send_mail(
            '가입 인사',
            '가입을 환영합니다.',
            'purum01@naver.com',
            [user.email],
            fail_silently=False,
        )

post_save.connect(on_send_mail, sender=settings.AUTH_USER_MODEL)
~~~


accounts/login_form.html
---
~~~html
    <ul>
        {% for provider in providers %}
            <li>
                {% if provider.social_app %}
                    <a href="{% provider_login_url provider.id %}">{{provider.name}}</a>
                {% else %}
                    <a>
                        Provider {{provider.name}}설정이 필요합니다.
                    </a>
                {% endif %}
            </li>
        {% endfor %}
    </ul>
~~~

OAuth 설정
---
~~~python
INSTALLED_APPS = [
    'django.contrib.sites',
    'allauth',
    'allauth.account',
    'allauth.socialaccount',
    'allauth.socialaccount.providers.facebook',
    'allauth.socialaccount.providers.kakao',
    'allauth.socialaccount.providers.naver',
]

AUTHENTICATION_BACKENDS = [
    'django.contrib.auth.backends.ModelBackend',
    'allauth.account.auth_backends.AuthenticationBackend',
]
SITE_ID = 1
SOCIALACCOUNT_EMAIL_VERIFICATION = 'none'
~~~
