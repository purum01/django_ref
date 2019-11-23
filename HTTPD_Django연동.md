
C:\Apache24\conf\httpd.conf 파일 수정
---
'''xml

  Define SRVROOT "C:/Apache24"
  ServerRoot "${SRVROOT}"
  Listen 80
  ServerName localhost
  DocumentRoot "${SRVROOT}/htdocs"
  
'''
