---
title: 记录第一次在宝塔部署Flask框架遇到的坑
date: 2021-2-18
tags: 
	- python 
	- btpanel
	- flask
categories: Flask后端搭建启动
---

最后在简书找到相关解决方案



### 报错内容如下

Python项目管理器启动Flask项目 报错ModuleNotFoundError: No module named  'json'

```jsx
[2020-11-10 23:55:08 +0800] [29539] [INFO] Starting gunicorn 20.0.4
[2020-11-10 23:55:08 +0800] [29539] [INFO] Listening at: http://0.0.0.0:40000 (29539)
[2020-11-10 23:55:08 +0800] [29539] [INFO] Using worker: geventwebsocket.gunicorn.workers.GeventWebSocketWorker
[2020-11-10 23:55:08 +0800] [29547] [INFO] Booting worker with pid: 29547
[2020-11-10 23:55:08 +0800] [29547] [ERROR] Exception in worker process
Traceback (most recent call last):
  File "/root/gobes.client/client_venv/lib/python3.7/site-packages/gunicorn/arbiter.py", line 583, in spawn_worker
    worker.init_process()
  File "/root/gobes.client/client_venv/lib/python3.7/site-packages/gunicorn/workers/ggevent.py", line 162, in init_process
    super().init_process()
  File "/root/gobes.client/client_venv/lib/python3.7/site-packages/gunicorn/workers/base.py", line 119, in init_process
    self.load_wsgi()
  File "/root/gobes.client/client_venv/lib/python3.7/site-packages/gunicorn/workers/base.py", line 144, in load_wsgi
    self.wsgi = self.app.wsgi()
  File "/root/gobes.client/client_venv/lib/python3.7/site-packages/gunicorn/app/base.py", line 67, in wsgi
    self.callable = self.load()
  File "/root/gobes.client/client_venv/lib/python3.7/site-packages/gunicorn/app/wsgiapp.py", line 49, in load
    return self.load_wsgiapp()
  File "/root/gobes.client/client_venv/lib/python3.7/site-packages/gunicorn/app/wsgiapp.py", line 39, in load_wsgiapp
    return util.import_app(self.app_uri)
  File "/root/gobes.client/client_venv/lib/python3.7/site-packages/gunicorn/util.py", line 358, in import_app
    mod = importlib.import_module(module)
  File "/www/server/panel/pyenv/lib/python3.7/importlib/__init__.py", line 127, in import_module
  File "<frozen importlib._bootstrap>", line 1006, in _gcd_import
  File "<frozen importlib._bootstrap>", line 983, in _find_and_load
  File "<frozen importlib._bootstrap>", line 967, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 677, in _load_unlocked
  File "<frozen importlib._bootstrap_external>", line 728, in exec_module
  File "<frozen importlib._bootstrap>", line 219, in _call_with_frames_removed
  File "/root/gobes.client/clients.py", line 8, in <module>
    from flask import Flask, jsonify, request, abort
  File "/root/gobes.client/client_venv/lib/python3.7/site-packages/flask/__init__.py", line 14, in <module>
    from jinja2 import escape
  File "/root/gobes.client/client_venv/lib/python3.7/site-packages/jinja2/__init__.py", line 9, in <module>
    from .bccache import BytecodeCache
  File "/root/gobes.client/client_venv/lib/python3.7/site-packages/jinja2/bccache.py", line 24, in <module>
    from .utils import open_if_exists
  File "/root/gobes.client/client_venv/lib/python3.7/site-packages/jinja2/utils.py", line 2, in <module>
    import json
ModuleNotFoundError: No module named 'json'
[2020-11-10 23:55:08 +0800] [29547] [INFO] Worker exiting (pid: 29547)
[2020-11-10 23:55:08 +0800] [29539] [INFO] Shutting down: Master
[2020-11-10 23:55:08 +0800] [29539] [INFO] Reason: Worker failed to boot.
```

### 其实并不是没有json模块，而是因为启动配置文件的权限问题，导致没有模块，只需要将配置文件的权限修改：



```bash
bind = '0.0.0.0:40000'
user = 'root' # 将www改为root重启即可
workers = 1
threads = 2
backlog = 512
daemon = True
chdir = '/root/gobes.client/'
access_log_format = '%(t)s %(p)s %(h)s "%(r)s" %(s)s %(L)s %(b)s %(f)s" "%(a)s"'
loglevel = 'info'
worker_class = 'geventwebsocket.gunicorn.workers.GeventWebSocketWorker'
errorlog = chdir + '/logs/error.log'
accesslog = chdir + '/logs/access.log'
pidfile = chdir + '/logs/client.pid'
```



作者：大鹏科技2020
链接：https://www.jianshu.com/p/ca57f787eb41
来源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。


