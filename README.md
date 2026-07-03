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
flask-app-78c65cc4cd-5tz9h   0/1     Pending   0          31m
flask-app-78c65cc4cd-kqf2t   0/1     Pending   0          31m
redis-5df8746b7f-ktxmt       0/1     Pending   0          31m
root@srv-devops:/home/user/my_homework7# kubectl get svc
NAME            TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)        AGE
flask-service   NodePort    10.100.175.120   <none>        80:30080/TCP   31m
kubernetes      ClusterIP   10.96.0.1        <none>        443/TCP        36m
redis-service   ClusterIP   10.101.201.198   <none>        6379/TCP       31m
```
