# Домашнее задание к занятию "`Базовые объекты K8S`" - `Макаров Денис`

---

### Задание 1. Создать Pod с именем hello-world

1. Создать манифест (yaml-конфигурацию) Pod.

Создал Pod c именем hello-world представлен ниже:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: hello-world
spec:
  containers:
  - name: hello-world
    image: gcr.io/kubernetes-e2e-test-images/echoserver:2.2
    ports:
    - containerPort: 8080
```
2. Использовать image - gcr.io/kubernetes-e2e-test-images/echoserver:2.2.

Выполнение представлено на скриншотах ниже:

![pod](https://github.com/user-attachments/assets/fb5523fc-bb57-4d2d-a046-23affd6fc40c)

![status pod](https://github.com/user-attachments/assets/130a6d82-f40b-4e4b-9ea1-c22d646e2b93)

3. Подключиться локально к Pod с помощью `kubectl port-forward` и вывести значение (curl или в браузере).

Выполнение представлено на скриншоте ниже:

![web](https://github.com/user-attachments/assets/f52f2a32-9214-4de0-8099-2b1c621c5536)

------

### Задание 2. Создать Service и подключить его к Pod

1. Создать Pod с именем netology-web.

Создал Pod с именем netology-web представлен ниже:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: netology-web
  labels:
    app: netology
spec:
  containers:
  - name: netology-web
    image: gcr.io/kubernetes-e2e-test-images/echoserver:2.2
```
2. Использовать image — gcr.io/kubernetes-e2e-test-images/echoserver:2.2.

Выполнение представлено на скриншотах ниже:

![netology-web pod](https://github.com/user-attachments/assets/118f6397-1365-4d3f-8d88-d90fcab130bd)

4. Создать Service с именем netology-svc и подключить к netology-web.

Создал Service c именем netology-svc и подключил к netology-web представлено ниже:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: netology-svc
spec:
  ports:
    - name: web
      port: 8080
  selector:
    app: netology
```
![service](https://github.com/user-attachments/assets/f64f8b9b-12f2-4fd5-851b-995000919f27)

![status svc](https://github.com/user-attachments/assets/ff20a500-9fba-4e92-b3c9-c506077a42b1)

4. Подключиться локально к Service с помощью `kubectl port-forward` и вывести значение (curl или в браузере).

Выполнение представлено на скриншоте ниже:

![curl](https://github.com/user-attachments/assets/7963aca3-2ee2-4107-982e-17e617460b3a)


![netology-web](https://github.com/user-attachments/assets/f7a6d1dc-1e52-433d-a9f7-d2651a0f2005)

------
