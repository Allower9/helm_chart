# helm_chart

####  ``` запускаем от битнами 
helm install my-release oci://registry-1.docker.io/bitnamicharts/nginx -n web --create-namespace
```

####  Чтобы использовать наш index.html мы пишем configmap-index.yaml и custom-values.yaml
####  ``` Запускаем
kubectl apply  -f configmap-index.yaml -n web        
```

####  ```  Обновляем
helm upgrade my-release oci://registry-1.docker.io/bitnamicharts/nginx -n web -f custom-values.yaml
```

####  ```Смотрим вывод
Pulled: registry-1.docker.io/bitnamicharts/nginx:21.1.23
Digest: sha256:954a3f427402f3e6789d7d495767f32ec4b506c3eb991639ad85b6856927e633
Release "my-release" has been upgraded. Happy Helming!
NAME: my-release
LAST DEPLOYED: Wed Sep 24 23:43:43 2025
NAMESPACE: web
STATUS: deployed
REVISION: 4
TEST SUITE: None
NOTES:
CHART NAME: nginx
CHART VERSION: 21.1.23
APP VERSION: 1.29.1
```


#### Видим что у нас было 4 изменения (REVISION: 4), чтобы откатиться до 3 изменения используем команду
```
helm rollback my-release 3 -n web
```




#### ===================Создание_своего=================
```
<имя чарта>
├── charts
├── Chart.yaml
├── templates
│   ├── deployment.yaml
│   ├── _helpers.tpl
│   ├── hpa.yaml
│   ├── ingress.yaml
│   ├── NOTES.txt
│   ├── serviceaccount.yaml
│   ├── service.yaml
│   └── tests
│       └── test-connection.yaml
└── values.yaml
```
#### Создание
` helm create <имя чарта> `
