
C:\Apache24\conf\httpd.conf 파일 수정
---
```xml

  Define SRVROOT "C:/Apache24"
  ServerRoot "${SRVROOT}"
  Listen 80
  ServerName localhost
  DocumentRoot "${SRVROOT}/htdocs"

  LoadModule wsgi_module modules/mod_wsgi.cp36-win_amd64.pyd

  #Python 설치 디렉터리를 지정 또는 가상환경
  WSGIPythonHome "C:/ProgramData/Anaconda3"
  <VirtualHost *:80>
    ServerName localhost
    Define PUBDIR "mysite"
    
    # Apache가 wsgi.py을 액세스할 수 있도록 경로 지정과 권한 설정
    WSGIScriptAlias / "${SRVROOT}/htdocs/${PUBDIR}/mysite/wsgi.py"
    <Directory "${SRVROOT}/htdocs/${PUBDIR}/mysite">
      <Files "wsgi.py">
        Require all granted
      </Files>
    </Directory>
    
    # 정적 파일에 대한 경로 지정과 권한 설정
    Alias /static "c:/Apache24/htdocs/${PUBDIR}/pubstatic"
    <Directory "c:/Apache24/htdocs/${PUBDIR}/pubstatic">
      Require all granted
    </Directory>
  </VirtualHost>
  
```
wsgi.py
---
```python
import sys
sys.path.append('C:/Apache24/htdocs/mysite')
```

settings.py
---
```python
STATIC_ROOT = os.path.join('c:/apache24/htdocs/','mysite', 'pubstatic')

```
