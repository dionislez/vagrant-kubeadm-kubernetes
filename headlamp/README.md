## Применение манифеста

```sh
$ cd /vagrant
$ kubectl apply -f headlamp/kubernetes-headlamp.yaml
```

## Создание сервисного аккаунта

```sh
$ kubectl -n kube-system create serviceaccount headlamp-admin
```

## Выдача прав

```sh
$ kubectl create clusterrolebinding headlamp-admin --serviceaccount=kube-system:headlamp-admin --clusterrole=cluster-admin
```

## Проброс портов

```sh
$ kubectl port-forward --address 0.0.0.0 -n kube-system service/headlamp 8080:80 &
```

## Удаление проброса

```sh
$ pkill -f "kubectl port-forward.*headlamp"
```

## Генерация токена

```sh
$ kubectl create token headlamp-admin -n kube-system
```
