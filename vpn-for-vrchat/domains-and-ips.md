---
title: Домены и IP VRChat
description: Списки доменов и IP, которые использует VRChat.
---


[⬅️ Назад](./)


# Домены VRChat
Ниже приведены списки доменов и IP, которые использует VRChat.

Вы можете использовать их для настройки zapret, XRay, v2rayN, NekoBox и т.п.

Списки не полные и требуют дополнения.


### Домены самого VRChat:
```
vrchat.com
vrchat.net
vrchat.cloud
```

### Известные поддомены VRChat:
```
api.vrchat.cloud
pipeline.vrchat.cloud
status.vrchat.com
assets.vrchat.com
creators.vrchat.com
docs.vrchat.com
wiki.vrchat.com
files.vrchat.cloud
cdn.vrchat.com
vrcpm.vrchat.cloud
ask.vrchat.com
feedback.vrchat.com
help.vrchat.com
hello.vrchat.com
dev-api.vrchat.cloud
redirect.vrchat.com
file-variants.vrchat.cloud
api.vrchat.com
files.vrchat.com
```

### Сторонние сервисы, которые использует VRChat:
```
cloudfront.net
dbinj8iahsbec.cloudfront.net
cloud.unity3d.com
internal.unity3d.com
ns.photonengine.io
amplitude.com
```

### Другие домены, которые могут быть интересны:
```
vrchat.community
vrchatassets.com
vrcdn.live
vrcdn.video
vrcdn.cloud
```


# IP VRChat

### Основные блоки адресов Proton:
Адресы Photon, с которыми работает VRChat по UDP:
~~`5055`, `5056`, `5058`~~, `27001`, `27002`
```
80.93.0.0/16
85.234.0.0/16

37.9.0.0/16
86.105.0.0/16

5.8.0.0/16
188.241.0.0/16

87.120.0.0/16
82.117.0.0/16

203.0.113.113/32
216.120.180.0/23
```

### Эти IP однажды дала техподдержка:
```
216.120.180.0/23
91.199.81.0/24
185.67.124.0/24
```
но они явно не полные

### Также:
- См. [файлы zapret от kotrik](https://github.com/KotRikD/zapret-win/tree/master/zapret-bundle/files), содержит нужные домены и IP.

Перечисленые здесь адресы -- не все, и возможно у вас другие -- часто зависит от региона и провайдера.

В идеале, вы резолвите домены выше вашим DNS в IP, а у IP находите AS-подсеть, а подсети смотрите все прфеиксы.

Это нужно делать периодически, т.к. они теряют актуальность и меняются.

В API VRChat есть ping-эндпоинт: `https://api.vrchat.cloud/api/1/ping`, на что должен придти ответ `"pong"`.

### Скрипт на python, что бы узнать список IP Amazon AWS:
```python
import subprocess
import json
result = subprocess.run(['curl', '-s', 'https://ip-ranges.amazonaws.com/ip-ranges.json'], capture_output=True, text=True)
data = json.loads(result.stdout)
ip_prefixes = [prefix['ip_prefix'] for prefix in data['prefixes']]
with open('aws_cidr.txt', 'w') as f:
    for ip in ip_prefixes:
        f.write(ip + '\n')
    print(f"Сохранено {len(ip_prefixes)} IP")
```
([Сам список](https://ip-ranges.amazonaws.com/ip-ranges.json).)


# Имена процессов VRChat
```
start_protected_game.exe
VRChat.exe
yt-dlp.exe
launch.exe
```
Например, если вы хотите заворачивать трафик.