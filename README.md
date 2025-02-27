# Решение Домашнего задания к занятию «Helm»
https://github.com/netology-code/kuber-homeworks/blob/main/2.5/2.5.md

## Задание 1. Подготовить Helm-чарт для приложения
Ссылка на чарт https://github.com/pkostua/kuber-2.5/tree/master/ngginx-app  
Для разделения разных версий приложения в рамках одного неймспейса использовал {{ .Release.Name }}


## Задание 2. Запустить две версии в разных неймспейсах
### Запуск первой версии в первом неймспейсе
```
helm install web1 nginx-app -n app1 -f web1-values.yaml
```
web1-values.yaml
```
ingress:
  enabled: true
  className: "nginx"
  hosts:
    - host: microk8s.mylocalserver.com
      paths:
        - path: /web1
          pathType: ImplementationSpecific
  tls:
    crt: LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSURLekNDQWhPZ0F3SUJBZ0lVR0p3dDdnYjk4QXg4S1U3czJOT25zeEZrQ3JZd0RRWUpLb1pJaHZjTkFRRUwKQlFBd0pURWpNQ0VHQTFVRUF3d2FiV2xqY205ck9ITXViWGxzYjJOaGJITmxjblpsY2k1amIyMHdIaGNOTWpVd
    key: LS0tLS1CRUdJTiBQUklWQVRFIEtFWS0tLS0tCk1JSUV2Z0lCQURBTkJna3Foa2lHOXcwQkFRRUZBQVNDQktnd2dnU2tBZ0VBQW9JQkFRREUrUWMvR3FkOFk2OEoKblpNdFZlZGRmQ1prUHlvVWk1VjhLMDlZcGljRHFncklyd1ROT1FiUHJZOEwzVE9uOEVoNjlhTEpyeXg4eEVDQ
```

### Запуск второй версии в первом неймспейсе
```
helm install web2 nginx-app -n app1 -f web2-values.yaml
```
web2-values.yaml
```
ingress:
  enabled: true
  className: "nginx"
  hosts:
    - host: microk8s.mylocalserver.com
      paths:
        - path: /web2
          pathType: ImplementationSpecific
  tls:
    crt: LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSURLekNDQWhPZ0F3SUJBZ0lVR0p3dDdnYjk4QXg4S1U3czJOT25zeEZrQ3JZd0RRWUpLb1pJaHZjTkFRRUwKQlFBd0pURWpNQ0VHQTFVRUF3d2FiV2xqY205ck9ITXViWGxzYjJOaGJITmxjblpsY2k1amIyMHdIaGNOTWpVd
    key: LS0tLS1CRUdJTiBQUklWQVRFIEtFWS0tLS0tCk1JSUV2Z0lCQURBTkJna3Foa2lHOXcwQkFRRUZBQVNDQktnd2dnU2tBZ0VBQW9JQkFRREUrUWMvR3FkOFk2OEoKblpNdFZlZGRmQ1prUHlvVWk1VjhLMDlZcGljRHFncklyd1ROT1FiUHJZOEwzVE9uOEVoNjlhTEpyeXg4eEVDQ
```
### Запуск третей версии во втором неймспейсе
```
helm install web3 nginx-app -n app2 -f web3-values.yaml
```
web3-values.yaml
```
ingress:
  enabled: true
  className: "nginx"
  hosts:
    - host: microk8s.mylocalserver.com
      paths:
        - path: /web3
          pathType: ImplementationSpecific
  tls:
    crt: LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSURLekNDQWhPZ0F3SUJBZ0lVR0p3dDdnYjk4QXg4S1U3czJOT25zeEZrQ3JZd0RRWUpLb1pJaHZjTkFRRUwKQlFBd0pURWpNQ0VHQTFVRUF3d2FiV2xqY205ck9ITXViWGxzYjJOaGJITmxjblpsY2k1amIyMHdIaGNOTWpVd
    key: LS0tLS1CRUdJTiBQUklWQVRFIEtFWS0tLS0tCk1JSUV2Z0lCQURBTkJna3Foa2lHOXcwQkFRRUZBQVNDQktnd2dnU2tBZ0VBQW9JQkFRREUrUWMvR3FkOFk2OEoKblpNdFZlZGRmQ1prUHlvVWk1VjhLMDlZcGljRHFncklyd1ROT1FiUHJZOEwzVE9uOEVoNjlhTEpyeXg4eEVDQ
```

### Проверка доступности всех трех версий
![image](https://github.com/user-attachments/assets/1e279b3f-ec38-45d8-89f3-2dbe7e6dcf0d)

### Состояние depoyment и helm
![image](https://github.com/user-attachments/assets/a1051042-e503-4be7-9874-85845dee55e0)

