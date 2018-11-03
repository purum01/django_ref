myproject/templates/layout.html
---
```html
{% load static %}

<!doctype html>
<html>
<head>
<meta charset="utf-8" />
<title>{% block title %}TheBrains Article{% endblock %}</title>
<link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" />
<style>
    html {position: relative; min-height: 100%}
    body{margin-bottom: 60px}
    #page-footer{
        position: absolute;
        bottom: 0;
        width:100%;
        height: 60;
        line-height: 60px;
        background-color: #f5f5f5;
    }
</style>
<script src="//code.jquery.com/jquery-2.2.4.min.js"></script>
<script src="//maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>

</head>
<body>
        <nav class="navbar navbar-default">
            <div class="container">
                <div class="navbar-header">
                    <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#navbar">
                        <span class="icon-bar"></span>
                        <span class="icon-bar"></span>
                        <span class="icon-bar"></span>
                    </button>
                    <a class="navbar-brand" href="#">TheBrains</a>
                </div>
                <div id="navbar" class="collapse navbar-collapse">
                    <ul class="nav navbar-nav">
                        <li class="active"><a href="#">Home</a></li>
                        <li><a href="#">About</a></li>
                        <li><a href="#">Contact</a></li>
                    </ul>
                    <ul class="nav navbar-nav navbar-right">
                        <li> <a href="">회원가입</a> </li>
                        <li> <a href="">로그인</a> </li>
                        <li> <a href="">프로필</a> </li>
                        <li> <a href="">로그아웃</a> </li>

                    </ul>
                </div>
            </div>
        </nav>



    <div class="container">
        <div class="row">
            <div class="col-sm-12">
                {% block content %}
                {% endblock %}
            </div>            
        </div>
    </div>

    <div id="page-footer">
        <div class="container">
            <p class="text-muted">
                Copyright © 2003 TheBrains All Right Reserved
            </p>
        </div>
    </div>
</body>
</html>
```
