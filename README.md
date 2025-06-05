# Домашнее задание к занятию "`Конфигурация приложений`" - `Маркин Алексей`

### Цель задания

В тестовой среде Kubernetes необходимо создать конфигурацию и продемонстрировать работу приложения.

### Задание 1. Создать Deployment приложения и решить возникшую проблему с помощью ConfigMap. Добавить веб-страницу

1. Создать [Deployment](https://github.com/Markin-AI/kub-8/blob/main/deploy-nm.yaml) приложения, состоящего из контейнеров nginx и multitool.
2. Решить возникшую проблему с помощью [ConfigMap](https://github.com/Markin-AI/kub-8/blob/main/cfm-nm.yaml).
3. Продемонстрировать, что pod стартовал и оба конейнера работают.

![1](https://github.com/Markin-AI/kub-8/blob/main/img/1.png)

4. Сделать простую веб-страницу и подключить её к Nginx с помощью ConfigMap. Подключить [Service](https://github.com/Markin-AI/kub-8/blob/main/svc-nm.yaml) и показать вывод curl или в браузере.

[Ingress](https://github.com/Markin-AI/kub-8/blob/main/ingress-nm.yaml)

![2](https://github.com/Markin-AI/kub-8/blob/main/img/2.png)

5. Предоставить манифесты, а также скриншоты или вывод необходимых команд.



------

### Задание 2. Создать приложение с вашей веб-страницей, доступной по HTTPS 

1. Создать [Deployment](https://github.com/Markin-AI/kub-8/blob/main/deploy-n.yaml) приложения, состоящего из Nginx.
2. Создать собственную веб-страницу и подключить её как [ConfigMap](https://github.com/Markin-AI/kub-8/blob/main/cfm-n.yaml) к приложению.
3. Выпустить самоподписной сертификат SSL. Создать [Secret](https://github.com/Markin-AI/kub-8/blob/main/nginx-tls.yaml) для использования сертификата.

```
openssl req -x509 -days 365 -newkey rsa:2048 -sha256 -nodes -keyout nginx.key -out nginx.crt -subj "/CN=markin.ai"

kubectl create secret tls nginx-tls --cert=nginx.crt --key=nginx.key

kubectl get secret -o yaml
```

4. Создать [Ingress](https://github.com/Markin-AI/kub-8/blob/main/ingress-n.yaml) и необходимый [Service](https://github.com/Markin-AI/kub-8/blob/main/svc-n.yaml), подключить к нему SSL в вид. Продемонстировать доступ к приложению по HTTPS. 

![3](https://github.com/Markin-AI/kub-8/blob/main/img/3.png)

5. Предоставить манифесты, а также скриншоты или вывод необходимых команд.

------

### Правила приёма работы

1. Домашняя работа оформляется в своём GitHub-репозитории в файле README.md. Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории.
2. Файл README.md должен содержать скриншоты вывода необходимых команд `kubectl`, а также скриншоты результатов.
3. Репозиторий должен содержать тексты манифестов или ссылки на них в файле README.md.

------