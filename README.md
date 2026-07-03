Задание:
Куберизировать приложение flask+redis: 
создать манифесты для запуска приложения flask и БД redis в кластере, и сервисы сетевого доступа к ним.

После установки пакетов Kubernetes
Запуск 
```
minikube start
eval $(minikube docker-env)
docker build -t flask-counter:latest .
kubectl apply -f.
```
Проверка запущенного 
```
root@srv-devops:/home/user/my_homework7# kubectl get pods
NAME                         READY   STATUS    RESTARTS   AGE
flask-app-6776677dbf-7lxdz   1/1     Running   0          22s
flask-app-6776677dbf-pn57t   1/1     Running   0          22s
redis-79fc96f7c9-h57mq       1/1     Running   0          27s
root@srv-devops:/home/user/my_homework7# kubectl get svc
NAME            TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
flask-app       NodePort    10.111.94.236   <none>        5000:30080/TCP   28s
kubernetes      ClusterIP   10.96.0.1       <none>        443/TCP          82s
redis-service   ClusterIP   10.106.12.22    <none>        6379/TCP         33s
```
```
root@srv-devops:/home/user/my_homework7# minikube service flask-app
┌───────────┬───────────┬─────────────┬───────────────────────────┐
│ NAMESPACE │   NAME    │ TARGET PORT │            URL            │
├───────────┼───────────┼─────────────┼───────────────────────────┤
│ default   │ flask-app │ 5000        │ http://192.168.49.2:30080 │
└───────────┴───────────┴─────────────┴───────────────────────────┘
* Opening service default/flask-app in default browser...
/usr/bin/xdg-open: 882: www-browser: not found
/usr/bin/xdg-open: 882: links2: not found
/usr/bin/xdg-open: 882: elinks: not found
/usr/bin/xdg-open: 882: links: not found
/usr/bin/xdg-open: 882: lynx: not found
/usr/bin/xdg-open: 882: w3m: not found
xdg-open: no method available for opening 'http://192.168.49.2:30080'

X Exiting due to HOST_BROWSER: open url failed: [default flask-app 5000 http://192.168.49.2:30080]: exit status 3
*
╭─────────────────────────────────────────────────────────────────────────────────────────────╮
│                                                                                             │
│    * If the above advice does not help, please let us know:                                 │
│      https://github.com/kubernetes/minikube/issues/new/choose                               │
│                                                                                             │
│    * Please run `minikube logs --file=logs.txt` and attach logs.txt to the GitHub issue.    │
│    * Please also attach the following file to the GitHub issue:                             │
│    * - /tmp/minikube_service_fdc583956da372c96a1365aae00a575feef092e9_0.log                 │
│                                                                                             │
╰─────────────────────────────────────────────────────────────────────────────────────────────╯

root@srv-devops:/home/user/my_homework7# curl http://192.168.49.2:30080
Hello, World! This page has been visited 1 times.root@srv-devops:/home/user/my_homework7#
```
