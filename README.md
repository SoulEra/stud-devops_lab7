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
NAME                         READY   STATUS    RESTARTS      AGE
flask-app-857697bd79-2rjhb   0/1     Running   1 (33s ago)   2m4s
flask-app-857697bd79-jcnv7   0/1     Running   1 (33s ago)   2m4s
redis-79fc96f7c9-9jv9l       1/1     Running   0             2m4s
root@srv-devops:/home/user/my_homework7# kubectl get svc
NAME            TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
flask-service   NodePort    10.99.212.131   <none>        5000:30080/TCP   2m18s
kubernetes      ClusterIP   10.96.0.1       <none>        443/TCP          3m42s
redis-service   ClusterIP   10.110.110.34   <none>        6379/TCP         2m18s
```
