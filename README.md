## 手順
- requirements.txt 作成
- dockerfile 作成
- docker-compose.yml 作成

## コンテナ作成
```
docker-compose run web django-admin startproject myprj
```

## setting.py修正
```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'postgres',
        'USER': 'postgres',
        'PASSWORD': 'postgres',
        'HOST': 'db',
        'PORT': 5432,
    }
}
```
## フォルダ階層修正(階層を上げないと「python: can't open file '/code/manage.py': [Errno 2] No such file or directory」が出る)
```
myprj/
    manage.py
    myprj/
        __init__.py
        settings.py
        urls.py
        asgi.py
        wsgi.py
```
  ↓ すべて階層を一つ上げる。
```
docker-compose.yml
manage.py
myprj/
    __init__.py
    settings.py
    urls.py
    asgi.py
    wsgi.py
```

## 起動
```
docker-compose up
```
![image](https://user-images.githubusercontent.com/45359669/144755440-a84df391-443f-49cd-b982-0ee0c3d281b1.png)
